---
name: claude-handoff
description: Hand the current conversation off to a fresh background agent that picks up the work immediately.
argument-hint: "What will the next session be used for?"
disable-model-invocation: true
---

Write the summary exactly as the `handoff` skill describes (`../handoff/SKILL.md`), then launch a background agent seeded with it as its prompt: `claude --bg --name "<descriptive name>" -- "$(cat <summary file>)"`. Passing the file keeps the shell from running backticks or expanding `$` in the summary. It starts in the current working directory and returns immediately; the user manages it with `claude agents`.

Always pass `-n`/`--name` with a descriptive name (e.g. `--name "Fix login bug"`); it sets the display name shown in the job list, session picker, and terminal title.

End the summary with instructions for the launched agent: work in small loops (build, run, look), and stop and report back at a natural checkpoint rather than finishing the whole thing alone.

The summary becomes the agent's prompt, so the redaction rule matters doubly here.
