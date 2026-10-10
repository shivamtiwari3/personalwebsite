---
title: "The gap between an agent demo and production"
date: 2026-09-15
draft: false
summary: "Most agent projects die somewhere between the demo and the first real customer. Here is what actually closes that gap."
tags: ["agentic-ai", "evals", "product"]
ShowToc: true
---

Every company I talk to is building an agent. Very few have one in production.

The demo is easy now. You wire an LLM to a few tools, add a system prompt, and it looks magical in a screen recording. The production version is a different sport. The gap between the two is where most agent projects quietly die, and it is almost never the model that kills them.

## What actually breaks

**Memory on channels that have no memory.** We built an AI gut-health coach on WhatsApp, a channel with no session concept. A user asks about bloating on Monday and says "is it better now" on Thursday. The agent needs to know what *it* means. Stuffing the last N messages into the prompt works until users have been chatting daily for weeks, at which point context bloats, costs spike, and the model starts confusing its own instructions with the user's history.

**Model choice as a margin decision.** Migrating from GPT-4o to Llama 3.2 was not an infra call. It was a cost-per-resolution call. That only works if you have been running faithfulness and relevancy evals religiously, otherwise you are guessing and shipping a regression.

**The autonomy boundary.** The hardest conversation is never architecture. It is deciding where the AI should stop and a human should start. That line moves every month as models improve, and someone has to own it.

## What closes the gap

Three things, in order of impact:

1. **Evals before launch, not after the first bad answer.** A test set of real multi-turn scenarios, run on every change to the logic that matters.
2. **Escalation paths designed up front.** Design the human-in-the-loop before someone is angry, not in response to it.
3. **Treat the whole thing as a P&L object.** Latency, cost per resolution, and headcount saved belong in the same spreadsheet.

None of this is glamorous. The model was fine way earlier than you think. The product questions around it are the actual work.
