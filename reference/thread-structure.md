# Thread Structure: Multi-Tweet Thread Templates

Threads are powerful for dwell time and share signals, but remember: **DedupConversationFilter** keeps only the highest-scoring tweet per conversation. Concentrate quality, don't spread it thin.

## Thread Length Guide

| Length | Use Case | Estimated Dwell Time |
|--------|----------|---------------------|
| 3-5 tweets | Quick tutorial, announcement | 30-60 seconds |
| 5-8 tweets | Tutorial, comparison, case study | 1-2 minutes |
| 8-12 tweets | Deep dive, technical explanation | 2-4 minutes |
| 12+ tweets | Comprehensive guide (rare) | 4+ minutes |

**Recommendation**: 5-8 tweets is the sweet spot for most content.

---

## Thread Structure Templates

### Template 1: Tutorial Thread (5-8 tweets)

**Structure:**
```
1/X — Hook + what you'll learn
2/X — Step 1 (setup/problem)
3/X — Step 2 (solution part 1)
4/X — Step 3 (solution part 2)
5/X — Result + demo
6/X — Code/resources
7/X — CTA (reply + share + follow)
```

**Example: "Build a RAG system in 20 minutes"**
```
1/7
I built a production-ready RAG system in 20 minutes using Model Studio

No vector DB setup, no embedding pipelines, no infra management

Here's exactly how:

🧵 Thread

2/7
The problem:

Most RAG tutorials take hours. You need to:
- Set up a vector database
- Configure embeddings
- Build retrieval logic
- Deploy everything

That's a weekend project, not a 20-minute one.

3/7
The solution:

Model Studio's RAG API handles everything:
- Built-in vector storage
- Automatic embeddings
- Smart retrieval
- Zero infra

One endpoint. That's it.

4/7
Step 1: Upload your docs

POST /rag/documents
{
  "files": ["manual.pdf", "docs/"]
}

Model Studio chunks, embeds, and indexes automatically.

5/7
Step 2: Query

POST /rag/query
{
  "question": "How do I reset my password?"
}

Response includes:
- Answer
- Source citations
- Confidence score

6/7
The result:

20 minutes from zero to production RAG

Cost: $0.02 per 1K queries
Latency: ~200ms
Accuracy: 89% on our test set

7/7
Try it yourself:
→ [link to docs]

Full code: [GitHub link]

What would you build with this? 👇

Follow @[handle] for more AI tutorials
```

---

### Template 2: Comparison Thread (5-8 tweets)

**Structure:**
```
1/X — Hook + controversial claim
2/X — Methodology
3/X — Benchmark 1 (speed)
4/X — Benchmark 2 (cost)
5/X — Benchmark 3 (quality)
6/X — Winner + analysis
7/X — CTA (reply + share)
```

**Example: "Qwen-72B vs GPT-4o for coding"**
```
1/7
Hot take: Qwen-72B on Model Studio beats GPT-4o for coding tasks

I ran 100 real-world coding benchmarks. The results surprised me.

🧵 Full breakdown:

2/7
Methodology:

100 coding tasks across:
- Bug fixing (25 tasks)
- Refactoring (25 tasks)
- Code review (25 tasks)
- New features (25 tasks)

Both models, same prompts, human evaluation.

3/7
Speed:

Qwen-72B: 0.8s average
GPT-4o: 1.2s average

Qwen is 33% faster.

For high-volume applications, that's significant.

4/7
Cost:

Qwen-72B: $0.018 per 1K tokens
GPT-4o: $0.03 per 1K tokens

Qwen is 40% cheaper.

Same quality, lower price.

5/7
Quality:

| Task        | GPT-4o | Qwen-72B |
|-------------|--------|----------|
| Bug fixing  | 82%    | 87%      |
| Refactoring | 79%    | 84%      |
| Code review | 85%    | 88%      |
| New feature | 88%    | 86%      |

Qwen wins 3/4 categories.

6/7
The winner:

Qwen-72B on Model Studio

- Faster (33%)
- Cheaper (40%)
- Better quality (3/4 tasks)

The only place GPT-4o wins: new feature generation (barely).

7/7
What's your go-to for coding tasks? 👇

Save this comparison for your next model decision 🔖

Follow @[handle] for more benchmarks
```

---

### Template 3: Story Thread (8-12 tweets)

**Structure:**
```
1/X — Hook (dramatic moment)
2/X — Context (the problem)
3/X — Attempt 1 (failure)
4/X — Attempt 2 (failure)
5/X — The insight
6/X — The solution
7/X — Implementation
8/X — Results
9/X — Lessons learned
10/X — CTA (reply + share + follow)
```

**Example: "How we reduced API costs by 40%"**
```
1/10
Last month our CFO walked in and said:

"We're spending $50k/month on AI APIs. Fix it."

Here's how we cut it to $30k without sacrificing quality:

🧵 Thread

2/10
The problem:

We were using GPT-4o for everything:
- Customer support (simple FAQs)
- Content generation
- Code review
- Data extraction

One expensive model for all tasks. Classic mistake.

3/10
Attempt 1: Use cheaper models

We tried GPT-3.5 for simple tasks.

Result: Quality dropped 30%. Customer complaints spiked.

Reverted in 2 days.

4/10
Attempt 2: Fine-tune a smaller model

Spent 2 weeks fine-tuning Llama-2.

Result: 3 weeks later, still not good enough. Team was frustrated.

Abandoned.

5/10
The insight:

We didn't need one model. We needed a smart router.

Simple tasks → cheap model
Complex tasks → expensive model

But building that router ourselves? Months of work.

6/10
The solution:

Model Studio's Model Router

It automatically:
- Analyzes each request
- Routes to optimal model
- Balances cost vs quality

Zero setup. One API endpoint.

7/10
Implementation:

Day 1: Sign up for Model Studio
Day 2: Replace our API endpoint
Day 3: Monitor results

That's it. No fine-tuning, no routing logic, no infra changes.

8/10
The results (after 30 days):

Before: $50k/month
After: $30k/month

Quality: Maintained (actually improved 2%)
Latency: Same
Setup time: 2 hours

40% savings. 2 hours of work.

9/10
Lessons learned:

1. Don't use one model for everything
2. Building your own router is a trap
3. Let the platform handle optimization
4. The CFO is happy now 😌

10/10
What's your monthly API spend? Could you cut it 40%? 👇

DM this to your engineering lead 👀

Follow @[handle] for more cost optimization tips
```

---

### Template 4: List Thread (5-8 tweets)

**Structure:**
```
1/X — Hook + list intro
2/X — Item 1
3/X — Item 2
4/X — Item 3
5/X — Item 4
6/X — Item 5
7/X — CTA (reply + share)
```

**Example: "5 AI tools you're not using (but should be)"**
```
1/7
5 AI tools you're probably not using in 2026 (but should be):

🧵 Thread with use cases for each:

2/7
1. Model Studio Video Understanding

Upload a video, get:
- Timestamps
- Summaries
- Key moments
- Q&A

Use case: Automate video content analysis

3/7
2. Model Studio RAG API

Production-ready RAG in 20 minutes

No vector DB, no embeddings, no infra

Use case: Customer support, knowledge bases

4/7
3. Model Studio Multimodal

One API for text + image + video + audio

Use case: Content moderation, accessibility

5/7
4. Model Studio Model Router

Automatic cost optimization

Routes requests to optimal model

Use case: High-volume applications

6/7
5. Model Studio Batch API

Process 10K requests in parallel

50% cheaper than real-time

Use case: Data processing, analytics

7/7
Which one are you trying first? 👇

Save this thread for your next project 🔖

Follow @[handle] for more AI tool recommendations
```

---

## Thread Best Practices

### Do:
- Number tweets (1/X, 2/X, etc.)
- Make each tweet standalone (in case someone sees only one)
- Add a "save this" CTA in the middle (tweet 3-4)
- End with a strong CTA (reply + share + follow)
- Use consistent formatting (bullet points, tables, etc.)
- Add visuals when possible (screenshots, diagrams)

### Don't:
- Make tweets too long (keep under 250 chars when possible)
- Spread quality thin (better to have 5 great tweets than 10 mediocre ones)
- Forget to thread them (reply to your own tweet to create the thread)
- Use the same CTA in every tweet (vary them)
- Post threads too frequently (1-2 per week max, due to author diversity penalty)

---

## Thread Hook Formulas

### For tutorials:
- "I built [X] in [time]. Here's how:"
- "[Task] used to take [long time]. Now it takes [short time]. Here's the workflow:"
- "Stop [bad practice]. Here's a better way:"

### For comparisons:
- "Hot take: [controversial claim]. I ran [N] benchmarks:"
- "[Model A] vs [Model B]. The winner might surprise you:"
- "Everyone uses [X]. Here's why [Y] is better:"

### For stories:
- "[Dramatic moment]. Here's what happened:"
- "Last [timeframe], [problem]. Here's how we fixed it:"
- "We spent [amount] on [thing]. Here's how we cut it by [percentage]:"

### For lists:
- "[N] [things] you're not using (but should be):"
- "[N] lessons from [experience]:"
- "[N] mistakes I made with [topic] (so you don't have to):"

---

## Thread Analytics Tracking

After posting a thread, track:

1. **Thread completion rate**: How many people read to the end?
2. **Per-tweet engagement**: Which tweet got the most likes/replies?
3. **Share triggers**: Which tweet got shared most?
4. **Drop-off points**: Where did people stop reading?

**Optimization loop:**
- Analyze 5-10 threads
- Identify patterns in high-performing tweets
- Adjust structure for future threads
- Test different hook formulas
