# Opening Hooks: First Line Formulas

The first line (or first 3 seconds for video) determines whether a user dwells or scrolls past. This directly impacts `dwell_score` and all downstream engagement signals.

## Hook Formulas (Ranked by Effectiveness)

### 1. Question Hook
**Pattern**: Ask a question the reader wants to answer

**Template:**
```
[Question about pain point or curiosity]?
```

**Examples:**
- "Why are you still paying $0.03 per API call when you could pay $0.018?"
- "What if I told you Qwen-72B beats GPT-4o at coding?"
- "How long does your video processing pipeline take? Ours takes 45 seconds."
- "Still managing GPU clusters in 2026?"

**Why it works**: Creates an open loop the brain wants to close → dwell + read more

---

### 2. Contrarian Statement
**Pattern**: Challenge a commonly held belief

**Template:**
```
Hot take: [controversial opinion]
```

**Examples:**
- "Hot take: Most developers are overpaying for AI APIs"
- "Unpopular opinion: You don't need GPT-4o for 90% of tasks"
- "Controversial: Open-source models are better than closed ones for production"
- "Hot take: Managing your own LLM infra is a waste of time in 2026"

**Why it works**: Triggers disagreement or curiosity → reply + dwell

---

### 3. Data/Number Hook
**Pattern**: Lead with a specific, surprising number

**Template:**
```
[Specific number] [surprising fact]
```

**Examples:**
- "40% cheaper. Same quality. Just switched our entire stack to Model Studio."
- "240x faster. That's what happened when we switched to Model Studio's video API."
- "We processed 10,000 videos in 45 minutes. Here's how:"
- "$0.018 per API call. Let that sink in."

**Why it works**: Numbers create specificity and credibility → dwell + share

---

### 4. Before/After Hook
**Pattern**: Show transformation

**Template:**
```
Before: [pain point]
After: [solution]
```

**Examples:**
- "Before: 3-hour video processing. After: 45 seconds."
- "Before: $5k/month API costs. After: $3k/month. Same quality."
- "Before: Managing 12 GPU instances. After: Zero infra. Just API calls."
- "Before: 5-day integration. After: 2 hours. One endpoint."

**Why it works**: Shows clear value → dwell + click + share

---

### 5. "I Just..." Hook
**Pattern**: Personal announcement with excitement

**Template:**
```
I just [exciting action] and [surprising result]
```

**Examples:**
- "I just shipped video generation on Model Studio and it's actually insane"
- "I just ran 100 benchmarks and the results surprised me"
- "I just switched our entire backend to Model Studio and the CFO is happy for once"
- "I just built a RAG system in 20 minutes using Model Studio. Here's the code:"

**Why it works**: Personal voice + excitement → dwell + follow

---

### 6. "Stop..." Hook
**Pattern**: Command to stop a bad behavior

**Template:**
```
Stop [common mistake]
```

**Examples:**
- "Stop paying $0.03 per API call. Seriously."
- "Stop managing your own GPU clusters. It's 2026."
- "Stop using GPT-4o for everything. You're overpaying."
- "Stop building RAG from scratch. Here's a better way:"

**Why it works**: Creates urgency and curiosity → dwell + reply

---

### 7. "POV:" Hook
**Pattern**: Put reader in a scenario

**Template:**
```
POV: [relatable scenario]
```

**Examples:**
- "POV: You just realized you don't need to manage infra anymore"
- "POV: Your API costs just dropped 40% and you get to tell your boss"
- "POV: You built a multimodal app in 30 minutes"
- "POV: It's 2026 and you're still paying 2024 prices for AI APIs"

**Why it works**: Relatable scenario → favorite + repost

---

### 8. "Most People..." Hook
**Pattern**: Highlight what most people get wrong

**Template:**
```
Most people [common mistake]. Here's what actually works:
```

**Examples:**
- "Most people overpay for AI APIs. Here's what smart devs do:"
- "Most people think open-source models are weaker. The benchmarks say otherwise:"
- "Most people spend weeks building RAG. Here's how to do it in hours:"
- "Most people think you need GPT-4o for production. Here's why they're wrong:"

**Why it works**: Creates curiosity about the "right way" → dwell + click

---

### 9. Time-Bound Hook
**Pattern**: Emphasize speed or time savings

**Template:**
```
[Task] in [surprisingly short time]
```

**Examples:**
- "Built a video summarizer in 90 seconds"
- "Deployed a RAG system in 20 minutes"
- "Processed 10,000 images in 3 minutes"
- "Integrated multimodal AI in 2 hours"

**Why it works**: Implies ease and speed → dwell + click + share

---

### 10. "The Math is Mathing" Hook
**Pattern**: Show clear ROI or cost-benefit

**Template:**
```
[Comparison] + "the math is mathing"
```

**Examples:**
- "40% cheaper, same quality, zero infra. The math is mathing."
- "10x faster, 1/3 the cost, better accuracy. The math is mathing."
- "Same benchmarks, lower price, no GPU management. The math is mathing."

**Why it works**: Clear value proposition → dwell + share + follow

---

## Hook Selection Guide

**By content type:**

| Content Type | Best Hook Types |
|--------------|-----------------|
| Demo Video | "I just...", Time-Bound, Before/After |
| Benchmark | Data/Number, Contrarian, "Most People..." |
| Use Case | Before/After, Time-Bound, "The Math is Mathing" |
| Open Source | "I just...", Question |
| Promo | Time-Bound, "Stop..." |
| Giveaway | "I just...", Question |
| Meme | POV:, Contrarian |
| Technical Thread | Contrarian, Question, "Most People..." |

**By target engagement:**

| Target Signal | Best Hook Types |
|--------------|-----------------|
| Reply | Question, Contrarian |
| Share | Data/Number, Before/After, Time-Bound |
| Follow | "I just...", "Most People..." |
| Dwell | All (any good hook works) |

## Hook Quality Checklist

A good hook:

- [ ] Is under 140 characters (fits in one line)
- [ ] Creates curiosity or tension
- [ ] Uses specific numbers when possible
- [ ] Avoids corporate buzzwords
- [ ] Sounds conversational (not marketing)
- [ ] Matches the content type
- [ ] Passes anti-slop check (humanized)

## Hook Testing Framework

When unsure which hook to use, generate 3-5 candidates and evaluate:

1. **Curiosity score** (1-5): How much does it make you want to read more?
2. **Specificity score** (1-5): How concrete/specific is it?
3. **Emotion score** (1-5): Does it trigger excitement, surprise, or FOMO?
4. **Anti-slop score** (1-5): Does it sound human vs corporate?

**Total score = Curiosity + Specificity + Emotion + Anti-slop**

Use the highest-scoring hook.

## Video Hooks (First 3 Seconds)

For video content, the hook must be visual + audio:

**Visual hook patterns:**
- Start with the end result (show what you built)
- Screen recording with cursor movement
- Quick cuts (0.5s each) showing multiple outputs
- Text overlay: "Watch me build X in 60s"
- Split screen: Before vs After

**Audio hook patterns:**
- "Watch this" (direct command)
- "This is insane" (excitement)
- "Okay so..." (conversational)
- "Let me show you something" (curiosity)
- No intro music (get straight to content)

**Video hook template:**
```
[0:00-0:03]
Visual: [Show end result or dramatic before/after]
Audio: "I just [action] in [time] and [result]"
Text overlay: "[Time] [Task] [Result]"
```

**Example:**
```
[0:00-0:03]
Visual: Screen recording showing generated video playing
Audio: "I just built a video summarizer in 90 seconds"
Text overlay: "90 seconds → Video summarizer"
```
