# X Algorithm Core Knowledge

## Ranking System Architecture

The X For You feed uses a two-stage pipeline:

**Stage 1: Phoenix Candidate Pipeline**
- Query hydration (21 hydrators in parallel)
- Candidate sourcing (6 sources in parallel)
- Candidate hydration (18 hydrators in parallel)
- Pre-scoring filters (14 filters)
- Phoenix ML scoring (19 engagement predictions)
- Ranking scorer (weighted sum + diversity + OON adjustment)

**Stage 2: For You Candidate Pipeline**
- Scored posts from Stage 1
- Ads, WhoToFollow, Prompts blending
- Final feed assembly

## Engagement Weight Hierarchy

Based on algorithm source code analysis, engagement signals are weighted as follows (approximate relative weights from demo pipeline):

### Positive Signals (boost ranking)

| Rank | Signal | Weight | Description |
|------|--------|--------|-------------|
| 1 | **share_via_dm_score** | Very High | User DMs the post to someone |
| 2 | **share_via_copy_link_score** | Very High | User copies the post link |
| 3 | **follow_author_score** | Very High | User follows the post author |
| 4 | **reply_score** | High (~0.5x favorite) | User replies to the post |
| 5 | **favorite_score** | High (1.0x baseline) | User likes the post |
| 6 | **quote_score** | Medium-High (~0.3-0.4x) | User quote tweets |
| 7 | **repost_score** | Medium (~0.3x) | User reposts/retweets |
| 8 | **vqv_score** | High (conditional) | Video view quality (if duration > threshold) |
| 9 | **share_score** | High | General share signal |
| 10 | **dwell_score** | Medium (~0.2x) | User spends time on post |
| 11 | **profile_click_score** | Medium | User clicks author profile |
| 12 | **photo_expand_score** | Medium | User expands photos |
| 13 | **click_score** | Medium | User clicks links |
| 14 | **quoted_click_score** | Medium | Clicks in quoted tweets |

### Continuous Signals

| Signal | Description |
|--------|-------------|
| **dwell_time** | Seconds spent on post |
| **video_watch_time** | Seconds of video watched |
| **scroll_depth** | How far user scrolled |
| **click_dwell_time** | Time after clicking |

### Negative Signals (suppress ranking)

| Signal | Penalty Level | Description |
|--------|---------------|-------------|
| **report_score** | Catastrophic | User reports the post |
| **block_author_score** | Catastrophic | User blocks the author |
| **mute_author_score** | Catastrophic | User mutes the author |
| **not_interested_score** | High | User clicks "Not interested" |
| **not_dwelled_score** | Medium | User scrolled past quickly |

## Critical Time Windows

### Post Lifespan
- **Maximum age**: 80 hours (3.33 days)
- **Age bucketing**: 60-minute granularity
- **Age buckets**: 82 total (0 = missing, 1-80 = hourly, 81 = overflow)
- **AgeFilter**: Posts older than MAX_POST_AGE are dropped entirely

### Golden Ignition Period
- **First 2 hours**: Critical for algorithmic pickup
- **First 6 hours**: Peak distribution window
- **24-48 hours**: Decay begins
- **72-80 hours**: Rapid decline
- **80+ hours**: Completely filtered out

**Implication**: Front-load engagement in the first 2 hours. Engage with replies immediately. Share in relevant communities right after posting.

## Author Diversity Penalty

The algorithm applies an exponential decay multiplier for repeated authors in a user's feed:

```
multiplier(position) = (1 - floor) × decay^position + floor
```

**Typical values**: decay = 0.5, floor = 0.1

| Post # from same author | Score multiplier |
|-------------------------|------------------|
| 1st | 1.00x (no penalty) |
| 2nd | 0.55x (45% reduction) |
| 3rd | 0.325x (67.5% reduction) |
| 4th | 0.213x (78.7% reduction) |
| 5th+ | → converges to 0.1x |

**Implication**: Posting 10 times a day is worse than posting 3 high-quality times. Each post after the first loses competitive power.

## Out-of-Network (OON) Weight

Posts from accounts a user doesn't follow (out-of-network) receive a penalty:

```
If in_network:
    final_score = score
Else:
    final_score = score × OonWeightFactor  // < 1.0
```

**Special cases**:
- **New users** (account age < threshold): Use `NEW_USER_OON_WEIGHT_FACTOR` (likely higher to help them discover content)
- **Topic feeds**: Use `TopicOonWeightFactor`

**Implication**: 
- OON content has a natural disadvantage
- High-quality content can still break through if P(engagement) is very high
- Building followers (in-network) is critical for consistent distribution

## Pre-Scoring Filters (14 filters)

Posts are filtered BEFORE scoring. If a post is filtered, it never reaches the ranking stage.

| Filter | Logic | Growth Impact |
|--------|-------|---------------|
| **AgeFilter** | Post age > MAX_POST_AGE (80h) | Posts expire after 3.3 days |
| **DropDuplicatesFilter** | Exact duplicate tweet IDs | Don't post identical content |
| **SelfTweetFilter** | author_id == viewer_id | Your own posts don't appear in your own feed |
| **RetweetDeduplicationFilter** | Same retweeted_tweet_id | Only one version of a retweet appears |
| **PreviouslySeenPostsFilter** | Bloom filter of seen IDs | Once seen, won't appear again |
| **PreviouslyServedPostsFilter** | Recently served IDs | Won't re-serve in same session |
| **MutedKeywordFilter** | Token-level keyword matching | Avoid triggering common mute words |
| **AuthorSocialgraphFilter** | Block/mute relationships | Blocked/muted users' content filtered |
| **IneligibleSubscriptionFilter** | Paywalled content | Subscription content filtered for non-subscribers |
| **VideoFilter** | Video-specific rules | Video eligibility checks |
| **TopicIdsFilter** | Topic-based filtering | Topic relevance filtering |
| **NewUserTopicIdsFilter** | New user topic filtering | New users get different topic filtering |
| **CoreDataHydrationFilter** | Failed to hydrate metadata | Posts with missing data filtered |

## Post-Selection Filters

After scoring and selection, additional filters apply:

| Filter | Logic |
|--------|-------|
| **VFFilter** | Visibility filtering (safety, violence, gore, spam) |
| **AncillaryVFFilter** | Drops ancillary content (quote tweets of filtered posts) |
| **DedupConversationFilter** | Keeps only highest-scored post per conversation thread |

**DedupConversationFilter implication**: In a thread, only the highest-scoring tweet appears. Concentrate quality in fewer tweets rather than spreading across many.

## GROX Content Understanding Pipeline

Every post is processed by 9 concurrent plans:

| Plan | Function | Growth Impact |
|------|----------|---------------|
| **PlanInitialBanger** | Quality screening (quality_score, slop_score) | 🔥 quality_score ≥ 0.4 = "good content" |
| **PlanPostSafety** | Safety screening | Safety violations = suppressed |
| **PlanSpamComment** | Spam detection (low-follower accounts) | ⚠️ New accounts especially vulnerable |
| **PlanPostEmbeddingWithSummary** | Multimodal embedding generation | Affects content understanding |
| **PlanPostEmbeddingV5** | V5 embedding generation | Affects retrieval |
| **PlanReplyRanking** | Reply quality scoring | High-quality replies prioritized |
| **PlanSafetyPtos** | 7-category safety policy detection | Violence/adult/hate/self-harm/spam/illegal |

### Banger Quality Screen Output

```python
{
    "quality_score": float,      # ≥ 0.4 = positive signal
    "slop_score": int,           # AI-generated content detection
    "description": str,          # Grok-generated summary
    "tags": list[str],           # Auto-generated tags
    "taxonomy_categories": list, # Classification results
    "is_image_editable_by_grok": bool,
    "has_minor_score": float
}
```

**🔥 Critical: `slop_score` detects AI-generated content**
- High slop_score → content suppressed
- Must humanize AI-generated text
- Original analysis, personal voice, imperfect expression required

## Brand Safety System

Three-tier brand safety verdict: `Safe` > `LowRisk` > `MediumRisk`

**MediumRisk triggers (14 labels):**
- NSFW (high precision/recall/text/card image)
- Gore and violence
- DO_NOT_AMPLIFY
- Egregious NSFW
- Grok NSFA
- Community Note NSFA

**LowRisk triggers (3 labels):**
- NSFA_LIMITED_INVENTORY
- GROK_NSFA_LIMITED
- NSFA_HIGH_RECALL

**Implication**: MediumRisk content reduces ad adjacency → less visibility to brand-conscious users → indirect distribution impact.

## Candidate Sources

6 candidate sources run in parallel:

| Source | Type | Description |
|--------|------|-------------|
| **Thunder** | In-Network | Posts from followed users (2-day retention) |
| **TweetMixer** | OON (legacy) | X's legacy recommendation service |
| **Phoenix Retrieval** | OON (ML) | Two-tower model similarity search (top_k=200) |
| **Phoenix Topics** | Topic-based | Retrieval based on followed topics |
| **Phoenix MoE** | OON (MoE) | Mixture-of-Experts retrieval |
| **CachedPosts** | Cache | Previous request results |

**Thunder (In-Network) details:**
- Retention: 2 days (172,800 seconds)
- Storage: 3 timelines per user (original/replies+retweets/video)
- Selection: Reverse chronological, top max_results
- Refresh: Trims old posts every 2 minutes

**Phoenix Retrieval (OON) details:**
- Top-K: 200 candidates (demo)
- Similarity: User vector × Candidate vector (dot product)
- Corpus: ~537K pre-computed candidates (demo)

## Key Numbers Summary

| Parameter | Value |
|-----------|-------|
| Post max age | 80 hours (3.33 days) |
| Thunder retention | 2 days |
| Post age granularity | 60 minutes |
| Phoenix retrieval top-K | 200 |
| Final display top-K | 30 (demo) |
| User history length | 127-128 actions |
| Candidate sequence length | 32-64 |
| Transformer layers | 4 |
| Attention heads | 4 |
| Embedding dimension | 128 |
| Action types | 19 discrete + 8 continuous |
| WhoToFollow max | 3 users |
| Ad spacing | 1 ad per 3 organic posts |
| Ad max ratio | ≤ 50% of safe organic posts |
