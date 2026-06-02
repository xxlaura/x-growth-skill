# CTA Patterns: Call-to-Action Trigger Templates

Every post must include at least one CTA targeting a high-value engagement signal. CTAs should feel natural, not forced.

## CTA Categories by Target Signal

### 1. Reply-Focused CTAs
**Algorithm signal**: `reply_score` (high weight, ~0.5x favorite)

**Question CTAs:**
- "What's your go-to [tool/model/approach]?"
- "What would you build with this?"
- "Have you tried this? How'd it go?"
- "What am I missing here?"
- "What's your experience with [X]?"
- "Agree or disagree?"
- "What's the wildest thing you've built with AI APIs?"

**Opinion CTAs:**
- "Hot take or cold take?"
- "Thoughts?"
- "Your take?"
- "Am I wrong?"
- "Convince me otherwise 👇"

**Challenge CTAs:**
- "Show me yours"
- "Drop your benchmarks below"
- "What's your setup? Show me"
- "Beat this number. I dare you 👇"

**Fill-in-the-blank CTAs:**
- "My favorite AI tool is ___"
- "The most underrated model is ___"
- "I switched to ___ and never looked back"

---

### 2. Share-Focused CTAs (Highest Value)
**Algorithm signals**: `share_score`, `share_via_dm_score` (very high), `share_via_copy_link_score` (very high)

**Save CTAs:**
- "Save this for later 🔖"
- "Bookmark this thread"
- "You'll want to come back to this"
- "Pin this for your next project"

**DM Share CTAs:**
- "DM this to a dev friend who needs to see this"
- "Send this to your team lead"
- "Tag someone who's still paying $0.03 per API call"
- "Share this with your CTO 👀"
- "Know someone building with AI? Send them this"

**Copy Link CTAs:**
- "Copy the link and share with your team"
- "Send this to your engineering channel"
- "Drop this in your #ai-tools Slack channel"

**Repost CTAs:**
- "Repost if you agree"
- "RT if you've been there"
- "Repost this to save a dev from overpaying for APIs"
- "Spread the word 🔄"

---

### 3. Follow-Focused CTAs
**Algorithm signal**: `follow_author_score` (very high weight)

**Series CTAs:**
- "Follow for Part 2"
- "Part 1 of X. Follow so you don't miss the rest"
- "Day 1 of [series]. Follow for daily updates"
- "This is a thread series. Follow for more"

**Value CTAs:**
- "Follow for more AI tips"
- "Follow @[handle] for daily benchmarks"
- "Follow if you want to stay ahead on AI APIs"
- "Follow for more open source spotlights"

**FOMO CTAs:**
- "Follow before we go viral and you lose us in your feed"
- "Follow now, thank yourself later"
- "Don't miss the next one — follow @[handle]"

**Personal CTAs:**
- "I post about [topic] daily. Follow if that's your thing"
- "Follow for behind-the-scenes of building Model Studio"
- "Follow to see what we ship next 👀"

---

### 4. Profile Click CTAs
**Algorithm signal**: `profile_click_score` (medium, but leads to follows)

**Link in bio CTAs:**
- "Try it → link in bio"
- "Full demo in bio"
- "Link in bio to get started"
- "Bio link for the curious"

**Profile CTAs:**
- "Check out our pinned post for the full story"
- "See our profile for more demos"
- "Our bio has the goods 👆"

---

### 5. Click/Link CTAs
**Algorithm signal**: `click_score` (medium)

**Direct link CTAs:**
- "Try it → [link]"
- "Get started → [link]"
- "Full docs → [link]"
- "GitHub repo → [link]"

**Curiosity gap CTAs:**
- "See what happens when you... [link]"
- "The results might surprise you → [link]"
- "Here's what we found → [link]"

---

## CTA Placement Rules

### Rule 1: End of Post (Primary CTA)
Place the main CTA at the end of the post. This is where readers who've dwelled will see it.

**Example:**
```
[Post content...]

What would you build with this? 👇
```

### Rule 2: Mid-Post (Secondary CTA)
For threads or long posts, add a secondary CTA in the middle to capture partial readers.

**Example:**
```
[First half of content]

Save this thread for later 🔖

[Second half of content]
```

### Rule 3: Pinned Comment (Tertiary CTA)
Add a CTA as the first reply to your own post (pinned to top).

**Example:**
```
[Main post]

[First reply, pinned:]
Try it yourself → [link]
```

---

## CTA Combination Formulas

### Formula 1: Reply + Share
```
[Post content]

What's your experience with [X]? 👇

(And DM this to a friend who needs to see it)
```

### Formula 2: Share + Follow
```
[Post content]

Save this for your next project 🔖

Follow @[handle] for more [topic]
```

### Formula 3: Reply + Follow
```
[Post content]

What would you build? Let me know 👇

Follow for Part 2 tomorrow
```

### Formula 4: All Three (Reply + Share + Follow)
```
[Post content]

Thoughts? Drop them below 👇

DM this to your team lead

Follow @[handle] for daily AI updates
```

---

## CTA Tone Guidelines

### Do:
- Use conversational language ("What's your take?" not "Please provide your opinion")
- Add emoji naturally (👇, 🔖, 👀, 🔄)
- Make it feel like a natural part of the post
- Vary CTAs across posts (don't use the same one every time)
- Match CTA to content type (question for benchmarks, save for tutorials)

### Don't:
- Use corporate language ("We invite you to share your thoughts")
- Add too many CTAs (max 2-3 per post)
- Make CTAs feel forced or desperate ("PLEASE FOLLOW!!!")
- Use generic CTAs that don't match the content
- Forget to include a CTA (every post should have one)

---

## CTA Examples by Content Type

### Demo Video
```
Try it yourself → link in bio

What would you build with this? 👇
```

### Benchmark
```
What's your go-to model for [task]? Drop it below 👇

(Save this comparison for your next decision 🔖)
```

### Use Case
```
What would you build with 240x speed? 💭

DM this to your engineering lead 👀
```

### Open Source Spotlight
```
Follow @[creator] for more AI builds

And follow us for more open source spotlights 👀
```

### Giveaway
```
To enter:
1. Follow @[handle]
2. Repost this
3. Reply: [question]

DM this to a dev friend for a bonus entry 👥
```

### Meme
```
Repost if you've been there 🔄

Tag someone who needs to switch to Model Studio 👇
```

### Technical Thread
```
If you found this useful:
1. Follow for more technical deep dives
2. Share this thread with your team

[Link to related resources]
```

---

## CTA Testing Framework

When A/B testing CTAs, track:

1. **Reply rate**: Replies / Impressions
2. **Share rate**: (Reposts + Quotes) / Impressions
3. **Profile visits**: Profile clicks / Impressions
4. **Link clicks**: Link clicks / Impressions
5. **Follow rate**: New followers / Profile visits

**Optimization loop:**
- Test 3 different CTAs per content type
- Run each for 1 week minimum
- Use the highest-performing CTA for that content type
- Re-test quarterly (audience preferences change)
