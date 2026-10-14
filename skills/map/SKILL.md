---
name: map
description: Draw a project's current architecture as a Mermaid diagram, read off the code. Use when the user asks how a repo, monorepo or project is structured, how its parts relate, or for an architecture overview.
argument-hint: "[path to a single project]"
allowed-tools: Bash(cat ${CLAUDE_PLUGIN_ROOT}/PRINCIPLES.md)
---

!`cat ${CLAUDE_PLUGIN_ROOT}/PRINCIPLES.md`

Draw how the parts of a codebase relate, as it is now. The output is a current view, not documentation.

## Scope

- **Path argument**: map that directory as a single project.
- **Monorepo**: the root declares several projects (workspaces in `package.json`, `pnpm-workspace.yaml`, `Cargo.toml`, `go.work`; Nx, Turborepo or Lerna config; `settings.gradle`; a `.sln`), or several sibling directories each carry their own manifest. Map the projects.
- **Otherwise**: map the root as a single project.

## Sources

Read the code and the manifests. Never take structure from READMEs, docs or existing diagrams: they may be stale.

**Monorepo.** One node per project. Edges:

- Solid: a dependency one project declares on another in its manifest.
- Dashed: a runtime link visible in the code (HTTP client, queue, shared database), labelled with what carries it.

**Single project.** One node per major module or package; a class instead of its module only when one class is most of that module. Edges are imports between them. Leave out tests, generated code and vendored code.

## Diagram

- Mermaid `flowchart`. Use `classDiagram` only when the user asks for classes.
- At most about 20 nodes. Fold smaller parts into their parent rather than dropping them.
- Name nodes as the code names them.
- Leave out any edge you could not trace to a manifest entry, an import or a call.

## Output

Write the diagram and a short legend to `<repo-name>-map.md` in the OS temporary directory (`$TMPDIR`, else `/tmp`; `%TEMP%` on Windows), never inside the repo. Give the path in chat, then list what was folded or left out, and any part whose role you could not tell from the code.
