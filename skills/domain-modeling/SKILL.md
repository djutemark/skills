---
name: domain-modeling
description: Harvest a project's domain model from code that has firmed up. Use when the user asks to write or edit GLOSSARY.md, record an ADR, or name things that have stabilised in the code.
---

# Domain Modeling

Draw the domain model out of what has been built. The code is the evidence; the glossary and ADRs are its written-down residue. They come after understanding, never before it.

Don't run this on a blank page or while the user is still finding the shape by building. If a term or decision hasn't settled in the code yet, leave it unwritten. (Merely *reading* `GLOSSARY.md` for vocabulary is not this skill: that's a one-line habit any skill can do. This skill is for when you're changing the model, not just consuming it.)

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

Create files lazily: only when you have something to write. If no `GLOSSARY.md` exists, create one when the first term is resolved. If no `docs/adr/` exists, create it when the first ADR is needed.

## Harvesting

### Read the code first

Before proposing a term or a decision, read the code that embodies it: type names, module boundaries, function names, tests. Propose glossary entries from what the code already says. When the code uses several words for one concept, name the split and offer a canonical term.

### Code is the source of truth

When what the user says and what the code does disagree, note it once and move on: "Your code cancels whole Orders, but you described partial cancellation." Don't block on it. The user may resolve it by changing the code, by changing their words, or by building more first.

### Let terms stay provisional

Fuzzy or overloaded words are normal while the shape is still forming. Don't challenge vocabulary mid-build. Only record a term once the user has settled it, or the code has.

### Answer boundaries by building

When the boundary between two concepts is unclear, don't interrogate the user with invented scenarios. Suggest a spike or a test that would show the answer, and let the code decide.

### Update GLOSSARY.md as terms settle

When a term is settled, update `GLOSSARY.md` right there. Don't batch these up. Use the format in [GLOSSARY-FORMAT.md](./GLOSSARY-FORMAT.md).

`GLOSSARY.md` should be totally devoid of implementation details. Do not treat `GLOSSARY.md` as a spec, a scratch pad, or a repository for implementation decisions. It is a glossary and nothing else.

### Offer ADRs sparingly, after the fact

ADRs record decisions already made and built, not decisions about what to build. Only offer one when all three are true:

1. **Hard to reverse**: the cost of changing your mind later is meaningful
2. **Surprising without context**: a future reader will wonder "why did they do it this way?"
3. **The result of a real trade-off**: there were genuine alternatives and you picked one for specific reasons

If any of the three is missing, skip the ADR. Use the format in [ADR-FORMAT.md](./ADR-FORMAT.md).
