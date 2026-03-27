---
url: "https://medium.com/@ScottSparkwave/building-self-improvement-into-ai-agents-4b345e3b27e6"
tweet_url: "https://x.com/ScottSparkwave/status/2034428229834990074"
crawled: 2026-03-27T15:44:00
author: Scott Johnson (@ScottSparkwave)
published: 2026-02-07
---

# Building Self-Improvement into AI Agents

**Author:** Scott Johnson

**Publication Date:** February 7, 2026

**Publication:** Medium

---

Clawdbot/OpenClaw represents an orders-of-magnitude increase in deployable AI capability. The gap between what AI can reason about and what it can actually do just collapsed.

Two weeks ago, building an agent that could act autonomously in the real world meant weeks of custom work — coding integrations, wiring up workflows, connecting APIs, and thoroughly testing all outputs.

Now it's possible to install one tool, talk to it, and it sets up its own integrations, writes its own code, and builds its own quality checks. And because the agent can use its own capabilities to expand its capabilities, this compounds.

That's a big shift. Not necessarily smarter AI, but rather AI with vastly improved access to tools that it can use to take action in the world.

But to actually trust what these agents produce, they need to be able to check their own work. That's what we've been building at Sparkwave — and here's what it looks like in production.

### The Automation Platform

Sparkwave is a central automation platform. It coordinates AI agents, manages tasks, handles content, contacts, bookings, email marketing — all in one place. The dashboard shows what agents are running, what tasks need attention, and what's queued up. Right now our primary agent Rico is managing over 360 active tasks across the system.

Mission Control is where everything connects. Agents report their activity. Tasks flow through a board — inbox, assigned, in progress, review. Blocking issues surface automatically. When something needs a human decision, it shows up in the user's To Do list with the right context already attached.

The platform gives agents a place to operate. But a platform is only as good as what the agents produce. That's where the self-improvement architecture comes in.

### What Makes It Work: Recursive Self-Improvement Loops

We built evaluation systems that sit between the AI's output and the customer. Every response runs through a set of task-specific criteria — each one a pass/fail gate. When something fails, the system diagnoses the specific failure mode, applies a targeted revision, and re-evaluates. This runs inside Supabase edge functions, autonomously, at scale.

But the evaluation system is a safety net, and a safety net that fires constantly is a sign of a deeper problem. The real goal is improving the quality of first-pass output so the safety net gets triggered less and less over time.

Here's how that works in practice.

We had a lead inquiry that said "I work until 6pm, so evening classes would be great." The AI responded: "Our 6:00 PM class would be perfect for you!"

The customer said they work until 6pm. The AI suggested a class at 6pm. That's the kind of response that loses you a customer.

The evaluation system caught it — the response failed the constraint-checking criteria. The system revised and produced something appropriate. But that's just the fix for one response.

The self-improvement part: Rico analyzed why the AI made that mistake in the first place. The generation layer — the system prompts, context, and instructions that shape how the AI produces output — had a gap. It wasn't adequately distinguishing between times a customer mentions and times that actually work for them. Rico fed that insight back into the generation layer itself. Updated the prompts, refined the instructions, improved the context the AI receives.

The result: the next time a lead mentions a time constraint, the AI handles it correctly on the first pass. The evaluation system is still there as a safety net, but it fires less because the upstream generation got better.

That's the cycle. Catch failures → understand root causes → improve the generation layer → first-pass quality goes up → the safety net triggers less. Over time, the system produces increasingly reliable output from the start.

### The Evaluation Criteria

For lead responses, we currently run 6 criteria on every AI-generated output:

- **Relevance** — Would this response work for any input, or is it specific to this one?
- **Question Answered** — Did we address what they actually asked?
- **Detail Echo** — Did we reference specifics they mentioned? If someone says "I travel Tuesdays," the response better not suggest Tuesday classes.
- **Context Aware** — Does it fit the conversation history?
- **Accuracy** — Are the facts right? Class times, pricing, availability.
- **CTA Appropriate** — Is the next step right for this stage? Don't push a sale on someone who asked a simple question.

Each one is pass/fail. The system loops until all six pass or it hits a revision limit and flags for human review.

These criteria are specific to lead response. For social media content, the criteria are different. For email campaigns, different again. The evaluation framework is always tailored to the task. And the criteria themselves evolve as the system learns — some get refined, some get retired as the generation layer improves enough to make them unnecessary.

In other words, these recursive self-improvement processes can be replicated across automation functions, such as:

- Communication with clients and prospects
- All forms of content creation
- Scheduling and booking management
- Workflows
- Technological performance
- Bug detection

### Rico: The Agent That Builds and Maintains It All

The evaluation systems run autonomously. When a lead texts in, the whole process handles itself. No one approves anything at runtime.

But someone has to design those evaluation systems, build them, deploy them, monitor them, feed the learnings back into the generation layer, and keep the whole thing improving. That's Rico — our Clawdbot agent.

We run Clawdbot as our orchestration layer inside the Sparkwave platform. Rico runs 24/7, connects through Telegram and Discord, and shows up in Mission Control alongside everything else. Here's what Rico actually does:

- **Analyzes failure patterns.** When the evaluation system catches errors, Rico looks at them in aggregate. One failure is a fix. A pattern of failures is a signal that the generation layer needs to improve.
- **Improves the generation layer.** Rico updates system prompts, refines instructions, and enriches the context the AI receives — so first-pass output quality keeps going up.
- **Deploys changes into production.** Rico writes the code, pushes it to our Supabase edge functions, and verifies it's running correctly.
- **Monitors quality continuously.** Twice-daily health checks across all active systems. When our pass rate dropped to 43% one morning from a config change, Rico caught it, diagnosed the root cause, and deployed a fix before we'd finished coffee.
- **Fixes what breaks.** When we spotted duplicate SMS messages and generic waiver responses going out, Rico investigated, found the root causes — a race condition in one case, a missing context injection in another — and deployed targeted fixes.

The evaluation systems run without Rico. But they exist because of Rico. Rico built them, Rico feeds learnings back into the generation layer, and Rico keeps the whole architecture improving.

That's the compounding effect. The agent improves the system that produces output. Better output means fewer failures. Fewer failures means the agent can focus on deeper improvements rather than firefighting. Each cycle makes the next cycle more productive.

### The Results

Before we built this architecture: about 40% of our AI responses needed manual editing.

After: 94% pass rate on first evaluation cycle. The other 6% almost always pass after one revision.

And the pass rate keeps climbing — because the system is continuously feeding learnings back into the generation layer. The 94% today is higher than it was a month ago, and it'll be higher next month.

### Why This Matters Right Now

The constraint on AI capability was never intelligence. The models have been able to reason, evaluate, and plan for a while. The constraint was deployment — getting that intelligence connected to real tools, real data, real actions, running it autonomously, and achieving consistent, reliable positive results.

Clawdbot collapsed that barrier. "It's open source, runs on a $5 server, and out of the box it has email, messaging, API access, shell access" and autonomous decision-making. Anyone can deploy a genuinely autonomous agent now. And because agents can use their own capabilities to build new capabilities, what's possible is expanding fast.

If you want to see what this looks like for your business, DM me or drop a comment.

Scott Johnson — Founder, Sparkwave AI
