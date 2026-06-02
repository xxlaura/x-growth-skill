# Video Scripts: VQV-Optimized Video Structure

Video content triggers multiple high-value signals simultaneously: `vqv_score` (high), `video_watch_time` (continuous), `dwell_score` (medium), `share_score` (high). The key is maximizing watch time.

## VQV Requirements

- **Minimum duration**: Must exceed `MinVideoDurationMs` (likely 5-10 seconds) to trigger VQV weight
- **Optimal range**: 30 seconds to 2 minutes
- **Sweet spot**: 60-90 seconds

## Video Structure Formulas

### Formula 1: Speed Demo (30-60 seconds)
**Best for**: Showing how fast something is

```
[0:00-0:03] HOOK
Visual: End result already showing
Audio: "I just [built/created/did] [thing] in [time]"
Text overlay: "[Time] → [Result]"

[0:03-0:08] CONTEXT
Visual: Show the starting point / problem
Audio: "Normally this takes [long time]. Watch:"

[0:08-0:45] DEMO
Visual: Screen recording of actual process
Audio: Minimal, let the speed speak for itself
Text overlay: Timestamps ("0:12 — API call sent", "0:25 — Response received")

[0:45-0:55] RESULT
Visual: Show the final output
Audio: "And... done. [Time]."

[0:55-1:00] CTA
Visual: End card with link
Audio: "Try it → link in bio"
Text overlay: "[handle] — link in bio"
```

**Caption template:**
```
Built [thing] in [time] using [product] 🤯

[One-line explanation]

No [pain point], no [pain point], just [simple solution].

Try it → link in bio
```

---

### Formula 2: Comparison Video (60-90 seconds)
**Best for**: Showing A vs B performance

```
[0:00-0:03] HOOK
Visual: Split screen — both tools side by side
Audio: "[Tool A] vs [Tool B]. Watch this."
Text overlay: "A vs B"

[0:03-0:10] SETUP
Visual: Show the same task/prompt for both
Audio: "Same task, same prompt. Let's see who wins."

[0:10-0:35] TEST 1 (Speed)
Visual: Side-by-side screen recordings
Audio: "First — speed..."
Text overlay: Timer for each side

[0:35-0:55] TEST 2 (Quality)
Visual: Show outputs side by side
Audio: "Now quality..."
Text overlay: Key metrics

[0:55-1:10] RESULTS
Visual: Comparison table / chart
Audio: "[Winner] is [X]% faster and [Y]% cheaper"

[1:10-1:20] CTA
Visual: End card
Audio: "Try [winner] → link in bio"
```

---

### Formula 3: Before/After Video (45-60 seconds)
**Best for**: Showing transformation / impact

```
[0:00-0:03] HOOK
Visual: Quick flash of "after" state
Audio: "This used to take [long time]. Now it takes [short time]."
Text overlay: "[Before] → [After]"

[0:03-0:15] BEFORE
Visual: Show the old workflow / pain point
Audio: "Before: [describe the problem]"
Text overlay: "Before: [pain point]"

[0:15-0:20] TRANSITION
Visual: Quick transition effect
Audio: "Then we switched to [product]"

[0:20-0:45] AFTER
Visual: Show the new workflow
Audio: "After: [describe the solution]"
Text overlay: Key metrics changing

[0:45-0:55] RESULT
Visual: Final numbers / dashboard
Audio: "The results speak for themselves"

[0:55-1:00] CTA
Audio: "Link in bio to try it"
```

---

### Formula 4: Tutorial Video (90-120 seconds)
**Best for**: Teaching something step by step

```
[0:00-0:03] HOOK
Visual: End result preview
Audio: "In 2 minutes, you'll know how to [task]"
Text overlay: "2 min → [skill]"

[0:03-0:10] PREREQUISITES
Visual: Quick text list
Audio: "All you need: [prerequisite 1], [prerequisite 2]"

[0:10-0:30] STEP 1
Visual: Screen recording
Audio: "Step 1: [action]"
Text overlay: "Step 1: [action]"

[0:30-0:50] STEP 2
Visual: Screen recording
Audio: "Step 2: [action]"
Text overlay: "Step 2: [action]"

[0:50-1:10] STEP 3
Visual: Screen recording
Audio: "Step 3: [action]"
Text overlay: "Step 3: [action]"

[1:10-1:20] RESULT
Visual: Show completed result
Audio: "And that's it. You now have [result]"

[1:20-1:30] CTA
Visual: End card
Audio: "Full docs → link in bio"
```

---

## Video Production Rules

### Rule 1: First 3 Seconds = Everything
- Show the end result immediately (don't build up to it)
- Use text overlay with the key message
- Start with energy — no intro music, no "hey guys"
- The algorithm measures `video_watch_time` from second 1

### Rule 2: Subtitles Are Mandatory
- 80%+ of X users browse with sound off
- Use large, readable text overlays
- Highlight key numbers and phrases
- Tools: CapCut, Descript, or built-in subtitle features

### Rule 3: Screen Recordings Must Be Clear
- Zoom in on the relevant area (don't show full desktop)
- Use cursor highlighting (yellow circle around cursor)
- Speed up slow parts (2-4x speed)
- Slow down important parts (0.5x speed)

### Rule 4: Visual Variety
- Change the visual every 5-10 seconds
- Alternate between: screen recording, text overlay, face cam, demo output
- Use quick cuts (0.3-0.5s) for transitions
- Add subtle zoom/pan to static screens

### Rule 5: Audio Energy
- Speak slightly faster than normal conversation
- Vary your tone (don't be monotone)
- Emphasize key numbers and results
- Keep it casual ("okay so..." not "ladies and gentlemen...")

### Rule 6: End Card
- Last 3-5 seconds: clear CTA
- Show handle + "link in bio"
- Don't add outro music (just end cleanly)

---

## Video Caption Templates

### Demo Video Caption
```
Built [thing] in [time] using [product] 🤯

[One-line description of what was built]

No [pain point 1], no [pain point 2], just [simple solution].

Try it yourself → link in bio
```

### Comparison Video Caption
```
[Tool A] vs [Tool B] — the results are wild

Same task, same prompt:
- Speed: [A] vs [B]
- Cost: [A] vs [B]
- Quality: [A] vs [B]

The math is mathing.

Try the winner → link in bio
```

### Before/After Caption
```
Before: [pain point]
After: [solution]

[Key metric]: [before] → [after]

Switched to [product] last month and... yeah.

Try it → link in bio
```

---

## Video Tools Recommendation

| Purpose | Tool |
|---------|------|
| Screen recording | Screen Studio, OBS |
| Video editing | CapCut, DaVinci Resolve |
| Subtitles | CapCut auto-subtitles, Descript |
| End cards | Canva video editor |
| Thumbnails | Canva, Figma |

---

## Video Analytics to Track

| Metric | Target | Why |
|--------|--------|-----|
| 3-second view rate | >80% | Hook effectiveness |
| Average watch time | >50% of duration | Content quality |
| Completion rate | >30% | Full video value |
| Share rate | >2% | Share signal strength |
| Profile visits | >1% | Follow funnel |
