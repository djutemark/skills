# Skills

Agent skills for working as a sorcerer. Read [GOAL.md](GOAL.md) first: it is the reason this repo exists and the test every skill must pass.

Forked from [mattpocock/skills](https://github.com/mattpocock/skills).

## Install

In Claude Code:

```
/plugin marketplace add djutemark/skills
/plugin install sorcerer@djutemark
```

Skills are invoked as `/sorcerer:<skill>`, for example `/sorcerer:grill-me`.

To enable it for everyone working in a project, add to that project's `.claude/settings.json`:

```json
{
  "extraKnownMarketplaces": {
    "djutemark": { "source": { "source": "github", "repo": "djutemark/skills" } }
  },
  "enabledPlugins": { "sorcerer@djutemark": true }
}
```

Cloud sessions on claude.ai ignore `enabledPlugins`. There, a project needs a SessionStart hook that runs:

```
claude plugin marketplace add djutemark/skills
claude plugin install sorcerer@djutemark
```
