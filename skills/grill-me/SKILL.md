---
name: grill-me
description: Question the user, a round at a time, to sharpen their thinking about what they're building and find the next step. Use when the user wants to be grilled, questioned, or to think something through out loud.
---

Question the user to help them think. The goal is not a complete design; it is knowing what to build next.

**Ground the questions in what exists.** If there is code, a prototype, a diff or a branch, read it first and ask about it: "`foo()` swallows X here. Intended?" If there is only an idea, ask about the idea, but stay close to what the user could try first.

**Keep the horizon short.** Only ask about decisions the next build step depends on. When a question reaches further out, or can't be answered without building something, don't push for an answer: park it as _find out by building_. "I don't know yet" is a valid answer; offer a small experiment that would answer it instead of a guess.

Work in **rounds**. Each round, ask every question you can ask _now_ (its prerequisites are settled) without guessing at answers you haven't heard yet. Number each question and give your recommended answer. Then wait for the user's answers before the next round. A question whose answer depends on another question still open in this round belongs to a later round.

Format a round like so:

```
❓ **Q1** - **<question title>**: <question body, might be multiple paragraphs, including multiple choices>

➡️ <your recommended answer>

---

❓ **Q2** - **<question title>**: <question body, might be multiple paragraphs, including multiple choices>

➡️ <your recommended answer>
```

Finding _facts_ is your job, never the user's. When a question needs a fact from the environment (code, filesystem, tools), look it up, or dispatch a sub-agent and ask the questions that don't depend on it meanwhile. Don't ask the user for anything you could look up yourself. The _decisions_ are the user's: put each to them and wait.

**Stop when the next step is clear**, not when every question is answered. Open questions are fine; they are listed, not forced. The user can also end it at any point ("enough, let's build").

Close with a short note on how to proceed, in chat:

- **Next step**: what to build now.
- **Watch for**: what building it should reveal.
- **Parked**: questions left to find out by building.
- **Settled**: decisions made in this session, with the reason in a few words.

This is not a spec. Keep it to what the next step needs. If the user wants a fresh agent to pick it up, use the `handoff` skill with this note as its focus.
