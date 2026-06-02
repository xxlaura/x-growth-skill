# Anti-Slop Rules: Reducing AI-Generated Content Detection

## Voice Profile is the Source of Truth

Before applying any rules below, read `config/voice.md` (if it exists). It contains the account-specific voice profile, including:
- Account type (Personal / Brand / Hybrid)
- Tone attributes (always + never)
- Hook patterns (use + avoid)
- Off-limits words and phrases
- Signature elements

The rules below are **general guidelines**. The voice.md file has **account-specific overrides** that take priority.

## What is Slop Score?

GROX's `PlanInitialBanger` classifier includes a `slop_score` field that detects AI-generated content. High slop scores suppress content distribution.

## Slop Indicators (What to Avoid)

### Language Patterns That Trigger High Slop Score

**Overly Formal/Corporate:**
- ❌ "We are excited to announce..."
- ❌ "Introducing our latest innovation..."
- ❌ "Leveraging cutting-edge technology..."
- ❌ "Revolutionary solution for..."
- ❌ "Seamless integration..."
- ❌ "Unparalleled performance..."

**Template-Like Structure:**
- ❌ Perfect paragraph breaks
- ❌ Every sentence complete and grammatically perfect
- ❌ No contractions (using "do not" instead of "don't")
- ❌ Bullet points with parallel structure
- ❌ Marketing buzzwords

**Lack of Personal Voice:**
- ❌ No first-person perspective
- ❌ No personal anecdotes
- ❌ No opinions or hot takes
- ❌ No imperfections or typos
- ❌ No conversational asides

### Visual Slop Indicators

- ❌ Stock photos (detected via embedding similarity)
- ❌ Generic AI-generated images
- ❌ Perfect symmetry and composition
- ❌ No text overlays or annotations

## Anti-Slop Transformation Rules

### Rule 1: First-Person Voice

**Before:**
```
Model Studio now supports Qwen-7B with improved performance.
```

**After:**
```
We just shipped Qwen-7B to Model Studio and honestly the speed improvements are wild 🚀
```

### Rule 2: Imperfect Punctuation

**Before:**
```
The API is fast, reliable, and easy to integrate.
```

**After:**
```
API's fast... reliable... and honestly just works. No 3-day integration nightmare.
```

### Rule 3: Emoji Usage (Natural, Not Excessive)

**Before:**
```
Try our new multimodal capabilities today.
```

**After:**
```
Just dropped multimodal support 👀 you can literally send it a video and it understands what's happening
```

### Rule 4: Personal Anecdotes

**Before:**
```
Model Studio provides cost-effective API pricing.
```

**After:**
```
Switched our internal tools to Model Studio last month and the CFO actually stopped complaining about API costs for once lol
```

### Rule 5: Conversational Contractions

**Before:**
```
You do not need to manage infrastructure.
```

**After:**
```
You don't need to manage infra. Like, at all. It just works.
```

### Rule 6: Vary Sentence Length

**Before:**
```
Model Studio offers the full Qwen series. It provides OpenAI-compatible APIs. It supports multimodal inputs. It requires no infrastructure management.
```

**After:**
```
Full Qwen series? Check. OpenAI-compatible APIs? Obviously. Multimodal? Yep. And zero infra to manage — we handle that part.
```

### Rule 7: Add Opinions/Hot Takes

**Before:**
```
Qwen-72B is a large language model with strong performance.
```

**After:**
```
Hot take: Qwen-72B is lowkey underrated. People sleep on it because it's not from OpenAI but the benchmarks don't lie 👀
```

### Rule 8: Include Imperfections

**Before:**
```
Our platform supports text, image, and audio/video processing.
```

**After:**
```
Text, image, audio/video... yeah it does all that. And before you ask — yes it's actually good at all of them, not just "technically supports" good
```

### Rule 9: Use Informal Language

**Before:**
```
The system demonstrates exceptional efficiency.
```

**After:**
```
This thing is stupid fast. Like, embarrassingly fast compared to what we were using before.
```

### Rule 10: Add Context/Asides

**Before:**
```
Model Studio is available in multiple regions.
```

**After:**
```
Model Studio's live in multiple regions now (finally 🙃 took us long enough but hey, global coverage is here)
```

## Slop Score Assessment Checklist

After writing content, evaluate:

- [ ] Does it use first-person ("I", "we")?
- [ ] Does it have at least one imperfect sentence?
- [ ] Does it include emoji (naturally)?
- [ ] Does it have a personal anecdote or opinion?
- [ ] Does it use contractions?
- [ ] Does it vary sentence length?
- [ ] Does it avoid corporate buzzwords?
- [ ] Would a human write this in a casual conversation?
- [ ] Does it have any typos or informal grammar?
- [ ] Does it express a viewpoint (not just facts)?

**Scoring:**
- 8-10 checks: Low slop risk ✓
- 5-7 checks: Medium slop risk ⚠️
- 0-4 checks: High slop risk ✗ — Rewrite required

## Example Transformations

### Example 1: Product Announcement

**High Slop (AI-generated):**
```
We are thrilled to announce the launch of Model Studio's new video generation capabilities. This cutting-edge feature leverages advanced AI to create high-quality videos from text prompts.
```

**Low Slop (Humanized):**
```
ok so we just dropped video gen on Model Studio and... it's actually insane?? like you type a prompt and it just... makes a video. and not even a bad one. we've been testing it internally for weeks and I'm still not over it
```

### Example 2: Technical Comparison

**High Slop (AI-generated):**
```
Model Studio offers superior cost-efficiency compared to competitors. Our pricing model provides 40% savings on API calls while maintaining comparable performance metrics.
```

**Low Slop (Humanized):**
```
Did some quick math on our API costs... Model Studio is like 40% cheaper than [competitor] for basically the same quality. The finance team is happy which means I'm happy 😌
```

### Example 3: Feature Highlight

**High Slop (AI-generated):**
```
Experience seamless multimodal integration with support for text, image, and audio/video processing in a single unified API.
```

**Low Slop (Humanized):**
```
One API for text + image + video/audio. That's it. No juggling 3 different services, no "integration hell" — just one endpoint that does it all. We spent way too long making this simple lol
```

## Brand Account Voice (官方账号专用)

Personal accounts use casual tone. Brand accounts need a different anti-slop strategy. The key principle:

> **Brand anti-slop = Specificity + Insider Knowledge + Product Confidence**
> Not: casual tone + emoji + imperfection

### Brand vs Personal Account Comparison

| Dimension | Personal Account | Brand Account |
|-----------|-----------------|---------------|
| Voice | "I just shipped..." | "Now available." |
| Tone | Casual, imperfect | Confident, precise |
| Anti-slop method | Personality + imperfection | Specificity + insider data |
| Emoji | Natural, frequent | Minimal, strategic |
| Humor | Personal jokes | Product wit, industry insight |
| Credibility | Personal experience | Product data + benchmarks |
| CTA | "Follow me" | "Try it →" |

### Brand Anti-Slop: 8 Rules

**Rule 1: Replace adjectives with numbers**

The #1 anti-slop technique for brands. AI writes vague adjectives; humans who built the product know exact numbers.

- ❌ "High-performance model serving" → slop
- ✅ "23ms p99 latency on Qwen-72B" → not slop
- ❌ "Cost-effective solution" → slop
- ✅ "$0.018 per 1K tokens — 40% below market" → not slop

**Rule 2: Show insider knowledge only the team would have**

AI can't generate real internal data. Use this.

- ✅ "Tested on 12,000 real enterprise workloads before launch"
- ✅ "The engineering team spent 6 months on this specific edge case"
- ✅ "3 a.m. deploy count last month: 847. That's developer trust."
- ✅ "We rejected 14 routing strategies before shipping the current one"

**Rule 3: Confident statements, not hype**

- ❌ "We're thrilled to announce our revolutionary new feature!" → slop
- ❌ "This is going to change everything!" → slop
- ✅ "Qwen3.7-Plus is now available via API." → confident, not hype
- ✅ "20% less than last month. Same model, better price." → confident

**Rule 4: Let the product demo speak**

Show, don't tell. AI can't generate real product demos.

- ✅ Screen recording of actual product in action
- ✅ Real code snippet with real output
- ✅ Before/after with real metrics
- ✅ Side-by-side comparison with real numbers

**Rule 5: Use the "Product Voice" — speak as the product**

- ❌ "Our team is excited to share..." → corporate slop
- ❌ "We are proud to announce..." → corporate slop
- ✅ "Qwen3.7-Plus. Live now on Model Studio." → product voice
- ✅ "New model. Same API. 20% off." → product voice

**Rule 6: Reference real users and real use cases**

- ✅ "A team in Tokyo shipped a real-time translation app on this last week"
- ✅ "3 enterprise customers migrated from [competitor] this month"
- ✅ "Most popular use case this week: video summarization (up 340%)"

**Rule 7: Technical precision IS anti-slop**

Brands can — and should — use precise technical language. That's not slop. Slop is vague marketing speak.

- ❌ "Our advanced AI-powered platform delivers seamless results" → slop
- ✅ "OpenAI-compatible /v1/chat/completions endpoint. Drop-in replacement." → precise, not slop
- ✅ "Supports 128K context window, structured output, and function calling" → precise

**Rule 8: Strategic restraint**

Brand accounts earn trust by NOT overselling.

- ❌ "The best AI platform in the world!" → slop
- ✅ "Try it and see." → confident restraint
- ❌ "Don't miss this incredible opportunity!" → slop
- ✅ "Available now." → restraint

### Brand Account Voice Examples (Good Reference Accounts)

| Account | Voice Style | What Works |
|---------|-------------|------------|
| @linear | Crisp, product-led | "Shipped." One word. Screenshot. Done. |
| @vercel | Technical, developer-first | Specific benchmarks, real deploy times |
| @stripe | Minimal, elegant | Lets the product and API speak |
| @supabase | Playful + technical | Developer humor + real product updates |
| @railway | Bold, opinionated | Strong takes on infra, backed by product |

### Brand Account Slop Score Checklist

- [ ] Does it contain at least one specific number/data point?
- [ ] Could only the product team have written this? (insider knowledge)
- [ ] Does it avoid "excited to announce" / "thrilled to share"?
- [ ] Does it avoid vague adjectives (revolutionary, seamless, cutting-edge)?
- [ ] Does it use confident statements instead of hype?
- [ ] If it makes a claim, is it backed by data or a demo?
- [ ] Does it have a recognizable "product voice" (not generic marketing)?
- [ ] Would a developer trust this post? (not just find it entertaining)

### Brand Post Formula

```
[Confident statement / specific data] — no hype

[1-2 lines of technical precision / what it actually does]

[Insider detail only the team would know]

[Clean CTA]
```

### Brand Rewrite Example

**High Slop (AI-generated marketing):**
```
🚀 We're thrilled to announce Qwen3.7-Plus! Our revolutionary multimodal agent model delivers seamless AI capabilities through a powerful, easy-to-use API. Experience the future of AI today!
```

**Low Slop (Brand voice):**
```
Qwen3.7-Plus is live on Model Studio.

Multimodal agent model — vision input, reasoning chain, code execution, tool use. Single API call.

Tested on 12,000 production workloads before launch.

Available now. 20% introductory pricing.
→ [link]
```

**Low Slop (Brand voice, variant B):**
```
New model on Model Studio: Qwen3.7-Plus

What it does in one API call:
→ Reads images and video frames
→ Reasons through multi-step problems
→ Writes and executes code
→ Calls external tools

23ms p99 latency. 128K context. OpenAI-compatible endpoint.

20% off this month.
```

## When Slop is Acceptable

Some content types can tolerate higher formality:

- **Official announcements**: Can be more formal but still add personal touch
- **Technical documentation**: Can be precise but avoid marketing speak
- **Legal/compliance**: Must be formal (but these aren't typical X posts)

**Rule of thumb**: If it sounds like it could be on a corporate blog, it's too slop for X.

## Final Anti-Slop Mantra

> **Personal accounts**: Write like you're explaining to a smart friend over coffee.
> **Brand accounts**: Write like the engineer who built the product is tweeting directly — specific, confident, no marketing department in between.
