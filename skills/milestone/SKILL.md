---
name: milestone
description: Question the user, a round at a time, about what they're building toward, and record it as a GitHub milestone. Use when the user wants to set, revisit or sharpen a milestone, or talks about where the work is heading.
---

Question the user to find out what they are building toward, then record it as a GitHub milestone. A milestone is a destination, not a plan: what exists when we get there, not how we get there.

**Start from what exists.** Read the repo's open milestones (`gh api repos/{owner}/{repo}/milestones`) and the code. If a milestone is open, question it against what has been built since: is it still the destination, or has it been reached? If several are open, ask which one this is about.

**Ask about the destination, never the route.** Ask what the user can run or show at the milestone that they can't now, who or what uses it, what is deliberately left out, and how they will know they are there. Questions about how to build it are parked: building answers them, or `grill-me` does. "I don't know yet" is a valid answer; that part is not in the milestone yet.

Work in **rounds**. Each round, ask every question you can ask _now_ without guessing at answers you haven't heard yet. Number each question and give your recommended answer. Then wait for the user's answers before the next round.

```
❓ **Q1** - **<question title>**: <question body>

➡️ <your recommended answer>
```

Finding _facts_ is your job: look them up in the code, issues and history. The _decisions_ are the user's.

**Stop when the user can say in a few lines what they are building** and what is not part of it. The user can also end it at any point.

Show the milestone in chat and wait for the user's OK before writing it to GitHub:

- **Title**: a short name for what gets built.
- **Description**:
  - **Building**: what exists at the milestone, as something the user can run or show.
  - **Not yet**: what is left out on purpose.
- **Due date**: only if the user gives one.

Then create it, or update the open one, with `gh api`.

**Issues are notes, not a breakdown.** Ideas and reminders come up while questioning. Offer to file them as issues under the milestone, and create only the ones the user agrees to. Never split the milestone into tasks: it must make sense without any issues under it.

When the milestone is reached, close it. When the direction changes, edit it rather than opening a second one.
