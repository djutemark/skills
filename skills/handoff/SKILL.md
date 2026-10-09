---
name: handoff
description: Compact the current conversation into a handoff document for another agent to pick up.
argument-hint: "What will the next session be used for?"
disable-model-invocation: true
---

Write a handoff document summarising the current conversation so a fresh agent can continue the work. Save to the temporary directory of the user's OS (`$TMPDIR`, else `/tmp`; `%TEMP%` on Windows) - not the current workspace.

The code is the source of truth. Point at files, symbols and commits rather than describing the design in prose.

Describe the current state, not a plan:

- **What exists**: paths, commits, what runs.
- **What was tried**: and what happened, including what was dropped and why.
- **What was understood**: what the building revealed about the problem.
- **Open threads**: hunches, and where things feel wrong or unstable.
- **Next experiments**: things to try and what each would tell us. Not tasks to complete; the next session decides the shape by building.

Include a "suggested skills" section in the document, naming which skills the next agent should call the Skill tool for.

Do not duplicate content already captured in other artifacts (specs, plans, ADRs, issues, commits, diffs). Reference them by path or URL instead.

Redact any sensitive information, such as API keys, passwords, or personally identifiable information.

If the user passed arguments, treat them as a description of what the next session will focus on and tailor the doc accordingly.
