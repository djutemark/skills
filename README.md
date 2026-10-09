# Skills

Agent skills. Read [GOAL.md](GOAL.md) first: it is the reason this repo exists and the test every skill must pass.

Forked from [mattpocock/skills](https://github.com/mattpocock/skills).

## Install

In Claude Code:

```
/plugin marketplace add djutemark/skills
/plugin install dj@djutemark
```

Skills are invoked as `/dj:<skill>`, for example `/dj:grill-me`.

To enable it for everyone working in a project, add to that project's `.claude/settings.json`:

```json
{
  "extraKnownMarketplaces": {
    "djutemark": { "source": { "source": "github", "repo": "djutemark/skills" } }
  },
  "enabledPlugins": { "dj@djutemark": true }
}
```

Cloud sessions on claude.ai ignore `enabledPlugins`. There, a project needs a SessionStart hook that runs:

```
claude plugin marketplace add djutemark/skills
claude plugin install dj@djutemark
```
