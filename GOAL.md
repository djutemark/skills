# Goal

A skill set for working as a **sorcerer**, in a world where both people and AI are drifting toward **wizardry**.

The terms come from [Wizards and Sorcerers](https://www.marginalia.nu/log/68-wizards-vs-sorcerers/) (marginalia.nu):

- **Wizards** design up front. They divide problems by reason, lean on patterns and algorithms, and work from explicit knowledge.
- **Sorcerers** grow software bottom-up. They build pieces before knowing how they fit, and come to understand the problem by writing the code. Their knowledge is tacit.

Both work. Neither is the other done badly.

## Why this repo exists

Agents run on explicit knowledge, so the default way of working with them is wizardry: spec, then plan, then execute. For a sorcerer that is not neutral. It moves the thinking out of the code and into documents written before the understanding exists.

These skills exist so I can work with agents **without becoming a wizard**.

## Principles

1. **Building is thinking.** Understanding comes from making. A skill must never require a design, spec, or plan before code exists.
2. **The agent is hands and memory, not architect.** It speeds up the loop of trying, running and looking. It does not decide the shape ahead of me.
3. **Explicit knowledge comes after, not before.** When something must be written down (for an agent, a colleague, or a future me), it is drawn out of what was built, not demanded up front.
4. **Borrow wizard discipline, on sorcerer terms.** The article's point is that the strongest programmers carry some of the other side. Wizard tools (review, design vocabulary, glossaries, decisions) are welcome here when they run on grown code, not on a blank page.
5. **Tests are essential, and they come once the code firms up.** After [grug](https://grugbrain.dev/): no first test before the domain is understood; that is wizardry. Test along the way while it helps, then invest in integration tests once stable cut points emerge. Unit tests are scaffolding, not treasure. Keep end-to-end tests few, curated, and green. Mock only coarsely, at system boundaries. The one exception is bugs: reproduce the bug in a regression test first, then fix it.

## Test for any skill in this repo

Does it let me think by building, and leave the explicit part for after? If a skill only works when the design comes first, it either gets adapted or it doesn't belong here.
