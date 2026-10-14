---
name: harvest
description: After a stretch of building, draw out what the code now knows (concepts, names, invariants, implicit decisions) into the smallest explicit layer worth keeping: glossary, ADRs, tests. Use when the user wants to harvest, wrap up a stretch of work or a milestone, write or edit GLOSSARY.md, or record an ADR.
---

# Harvest

Building leaves understanding in the code before it exists anywhere else. Harvest draws it out into the smallest explicit layer worth keeping. The code is the evidence; the glossary, ADRs and tests are its residue. They come after understanding, never before it.

Don't run this on a blank page or while the user is still finding the shape. What hasn't settled in the code stays unwritten. (Merely *reading* `GLOSSARY.md` for vocabulary is not this skill.)

## Gather

**The stretch.** Find what was built since the last harvest: the commits since `GLOSSARY.md` or `docs/adr/` last changed, or since the open milestone was created. Read the diff and the code it touches: type and module names, boundaries, tests.

**The milestone.** If the repo has an open GitHub milestone, read it and its issues (`gh api repos/{owner}/{repo}/milestones`, `gh issue list --milestone <title> --state all`). The milestone says what the stretch was heading toward; the issues are notes taken on the way. Read them as evidence, not as a checklist.

## Draw out

Look for what the code now knows that nothing else records:

- **Concepts and names.** Terms the code has settled on. When it uses several words for one concept, name the split and offer a canonical term. → glossary.
- **Implicit decisions.** Choices the code embodies that a future reader would want to undo. → ADR, only when it passes the three tests below.
- **Invariants and discovered behaviour.** Rules the code relies on, edge cases found by building, bugs that shaped it. → a test that pins it, at a stable cut point. Prefer integration tests; mock only coarsely at system boundaries. Don't pin what is still moving.
- **The milestone against the code.** What of **Building** now exists, what was built that it doesn't mention, and whether **Not yet** still holds. An issue the code has answered can be closed, with the commit that answered it. An issue that became a decision may be an ADR.

When what the user said and what the code does disagree, name it once: "The milestone says partial cancellation; the code cancels whole Orders." Don't block on it. The user resolves it by changing the code, the words, or the milestone.

## Propose, then write

Show the harvest in chat as one short list, grouped by target: glossary terms, ADRs, tests, issues to close or comment on, milestone changes. Leave out anything that wouldn't change how someone reads or changes the code. Then wait for the user to pick.

Write only what the user picks:

- **Glossary**: update `GLOSSARY.md` in the format in [GLOSSARY-FORMAT.md](./GLOSSARY-FORMAT.md). It holds terms only: no implementation details, no spec, no scratch notes.
- **ADRs**: in the format in [ADR-FORMAT.md](./ADR-FORMAT.md). Offer one only when all three are true:
  1. **Hard to reverse**: changing your mind later costs something real.
  2. **Surprising without context**: a future reader will wonder why.
  3. **The result of a real trade-off**: there were genuine alternatives.
- **Tests**: run them; a pinned behaviour test is green when it lands.
- **Issues**: close or comment with `gh`.
- **Milestone**: if it needs editing or closing, hand over to the `milestone` skill with what the harvest found.

Create files lazily: no `GLOSSARY.md` until the first term, no `docs/adr/` until the first ADR.

## File structure

Most repos have a single context:

```
/
├── GLOSSARY.md
├── docs/
│   └── adr/
│       ├── 0001-event-sourced-orders.md
│       └── 0002-postgres-for-write-model.md
└── src/
```

If a `GLOSSARY-MAP.md` exists at the root, the repo has multiple contexts. The map points to where each one lives:

```
/
├── GLOSSARY-MAP.md
├── docs/
│   └── adr/                          ← system-wide decisions
├── src/
│   ├── ordering/
│   │   ├── GLOSSARY.md
│   │   └── docs/adr/                 ← context-specific decisions
│   └── billing/
│       ├── GLOSSARY.md
│       └── docs/adr/
```
