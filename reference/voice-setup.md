# Voice Setup: Account Identity & Style Co-Creation

Voice setup is the **foundation** of the x-growth toolkit. Every other command (write, thread, reply, etc.) reads `about.md` and `voice.md` before generating a single line.

## Architecture

```
voice-setup (interview + sample analysis)
      │
      ├──→ about.md    (who you are, what you stand for)
      └──→ voice.md    (how you sound, what you never say)
              │
              ▼
      ALL downstream commands
      (write, thread, reply, hook, rewrite...)
```

## When to Run

- **First time** using x-growth (mandatory)
- **Re-running** when pivoting account strategy
- **User says**: "setup my voice", "configure account", "voice setup", "set up my style"

## Interview Flow

The interview has **3 batches** of questions. Use structured options where possible to reduce friction.

---

### Batch 1: Account Identity (4 questions)

**Q1: Account Type**
```
This account is a:
A) Personal account (founder, developer, creator)
B) Brand/product account (company, product, team)
C) Hybrid (personal face representing a brand — e.g. "CEO of X")
```

**Q2: What is the account's name and role?**
```
Account name/handle: ___
Role:
A) Product/team account for a developer tool
B) Founder/CEO personal brand
C) Technical educator / content creator
D) Community / open source project
E) Other: ___
```

**Q3: Who are you writing for?**
```
Primary audience:
A) AI/ML developers and engineers
B) Enterprise decision makers (CTOs, VPs)
C) Startup founders building with AI
D) AI researchers
E) General tech audience
F) Other: ___
```

**Q4: What are the 3-5 topics you want to be known for?**
```
Topic pillars (select all that apply):
A) Model releases and benchmarks
B) Developer tutorials and how-tos
C) Industry analysis and hot takes
D) Open source and community
E) Product updates and features
F) Behind-the-scenes / building in public
G) Cost optimization and ROI
H) Other: ___
```

---

### Batch 2: Voice & Personality (4 questions)

**Q5: When someone sees a post from this account, what should they think?**
```
Brand impression (pick 1-2):
A) "This account knows things others don't"  → Insider/Expert voice
B) "This is the most practical AI account I follow" → Builder/Practitioner voice
C) "This account is ahead of the curve" → Visionary voice
D) "This account is honest and transparent" → Authentic voice
E) "This account is fun and doesn't take itself too seriously" → Playful voice
```

**Q6: What is your point of view on the AI industry?**
```
Core belief (pick the one that resonates most):
A) Most people are overpaying for AI and don't realize it
B) Open source will win — closed models are a temporary moat
C) The real value is in applications, not model benchmarks
D) AI infrastructure should be invisible — developers shouldn't think about it
E) The next wave is multimodal + agentic, and most people aren't ready
F) Other: ___
```

**Q7: What is one thing this account refuses to do?**
```
Off-limits (select all):
A) Trash-talk competitors
B) Share revenue or user numbers
C) Post about politics
D) Use engagement bait ("Like if you agree!")
E) Post memes / casual humor
F) Share personal/team stories
G) Make predictions about the future
H) Other: ___
```

**Q8: What existing accounts does this voice remind you of?**
```
Voice references (select all that apply, or add your own):
A) @linear — crisp, product-led, minimal
B) @vercel — technical, developer-first, benchmarks
C) @stripe — elegant, precise, lets the product speak
D) @supabase — playful + technical, developer humor
E) @raaboron / @railway — bold, opinionated, backed by product
F) @kaboroevich — personal founder voice, building in public
G) @swyx — technical depth, community builder
H) Other: ___
```

---

### Batch 3: Writing Samples (1 request)

**Q9: Share 3-5 examples of posts you like (yours or others')**

```
Paste 3-5 posts that represent the voice you want.
These can be:
- Your own past posts you're proud of
- Posts from accounts you admire
- Drafts you've written but haven't posted

If you don't have samples, we'll use defaults based on your answers above.
Type "skip" to use defaults.
```

---

## Analysis Process

After collecting all answers:

### Step 1: Generate about.md

Use the interview answers to fill the about.md template. See template below.

**about.md structure:**
```markdown
# Account Identity

## Name & Role
[From Q1 + Q2]

## Account Type
[Personal / Brand / Hybrid]
[From Q1 — determines which anti-slop rules apply]

## Audience
[From Q3 — expanded to 2-3 sentences describing who reads this account and why]

## Topic Pillars
[From Q4 — one line each]
- [Pillar 1]
- [Pillar 2]
- [Pillar 3]

## Point of View
[From Q6 — written as a clear, quotable statement]

## Brand Promise
[From Q5 — what people should think when they see this account]

## Off Limits
[From Q7 — things this account never does]
```

### Step 2: Analyze Writing Samples

If samples provided, extract:

**Voice signals:**
- Sentence length (short/medium/long, average)
- Paragraph rhythm (bullet-heavy vs prose vs mixed)
- Hook style (question, data, contrarian, story, command)
- Tone (confident, casual, playful, academic, urgent)
- Signature phrases or patterns
- Emoji usage (none, minimal, frequent)
- CTA style (direct, soft, question-based, absent)

**Structural signals:**
- Length range (short tweets vs threads vs mixed)
- Lists vs prose ratio
- Opening patterns
- Closing patterns
- Transition style

**Absence signals (CRITICAL — define what the voice NEVER does):**
- Words/phrases never used
- Punctuation never used
- Hook types never used
- Tones never hit
- Structures never used

If no samples, derive voice rules from Q5 (brand impression) + Q8 (voice references).

### Step 3: Generate voice.md

**voice.md structure:**
```markdown
# Voice Profile

## Who I Sound Like
[2-3 sentences describing the overall voice — derived from Q5 + Q8 + sample analysis]

## Account Type
[Personal / Brand / Hybrid]
This determines which anti-slop rules apply.
- Personal → casual tone, first-person, imperfect punctuation, personal anecdotes
- Brand → confident, precise, insider data, technical specificity, strategic restraint
- Hybrid → personal voice representing a brand — mix both rulesets

## Tone
### Always:
[3-5 consistent tone attributes]
### Never:
[1-2 tones this voice never hits]

## Sentence Rhythm
- Average length: [short/medium/long]
- Pacing: [punchy/measured/mixed]
- Paragraph style: [bullets/prose/mixed]
- Avoid: [patterns to never use]

## Hook Patterns
### Use:
[3-5 hook types with examples]
### Avoid:
[Hook types this voice never uses]

## How I Open
[1-2 sentences describing opening style]
Never open with: [list]

## How I Close
[1-2 sentences describing closing/CTA style]
Never close with: [list]

## Signature Elements
[Recurring words, phrases, formatting choices, emoji patterns]

## Off-Limits Words & Phrases
[Words/punctuation/constructions absent from every sample]
- "excited to announce"
- "thrilled to share"
- "revolutionary"
- "seamless"
- "cutting-edge"
- "leverage"
- [Add account-specific off-limits from sample analysis]

## What This Voice Never Does
[3-5 specific avoided behaviors drawn from samples + Q7]
```

### Step 4: Save Files

Save both files to the skill's config directory:
- `.agents/skills/x-growth/config/about.md`
- `.agents/skills/x-growth/config/voice.md`

### Step 5: Confirm with User

Show the generated files and ask:
```
Here's your voice profile. Does this feel right?

Anything you'd like to adjust:
- Tone (more/less casual, more/less technical)
- Off-limits (add/remove)
- Hook patterns (add/remove types)
- Anything else
```

---

## Voice Presets (Quick Start)

For users who want to skip the interview, offer presets:

### Preset A: "Product-Led Brand"
- Account type: Brand
- Voice: Confident, precise, minimal
- References: @linear, @stripe, @vercel
- Anti-slop: Specificity + insider data + technical precision
- Emoji: Minimal (arrows, links only)
- CTA: Clean, direct ("Available now →")

### Preset B: "Developer Builder"
- Account type: Hybrid (personal face + brand)
- Voice: Technical, opinionated, building in public
- References: @supabase, @railway
- Anti-slop: First-person + product data + developer humor
- Emoji: Natural
- CTA: Conversational ("Try it and tell me what breaks")

### Preset C: "Technical Educator"
- Account type: Personal
- Voice: Clear, generous, depth-first
- References: @swyx, @karpathy
- Anti-slop: Teaching voice + personal experience + imperfect
- Emoji: Moderate
- CTA: Question-based ("What would you add?")

### Preset D: "Founder Voice"
- Account type: Hybrid
- Voice: Bold, visionary, transparent
- References: @paboroevich, @pmarca
- Anti-slop: Strong opinions + real numbers + vulnerability
- Emoji: Minimal
- CTA: Aspirational ("Join us")

---

## Re-Running Voice Setup

If the user already has config files, the setup command should:
1. Read existing about.md and voice.md
2. Show current profile summary
3. Ask: "Update specific sections, or start fresh?"
4. If updating: walk through only the changed sections
5. If fresh: run full interview again

---

## Integration with Other Commands

Every command in x-growth must check for voice config before generating:

```
Before generating any content:
1. Read config/about.md (if exists)
2. Read config/voice.md (if exists)
3. Apply voice rules to all output
4. If config files don't exist, prompt: "Run /x-growth voice-setup first"
```
