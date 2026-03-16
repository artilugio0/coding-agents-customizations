# coding-agents-customizations

Custom slash commands for spec-driven development with Claude Code.

## Commands

| Command | Purpose |
|---|---|
| `/spec-init` | Initialize spec-driven development in a project |
| `/spec-iteration-start [description]` | Start an iteration — creates and updates feature specs |
| `/spec-review [feature-name?]` | Review spec(s) for gaps, ambiguity, and conflicts |
| `/spec-iteration-implement` | Implement all features in the current iteration |
| `/spec-iteration-close` | Archive the completed iteration |

## How it works

**Specs live in `specs/`:**
- `specs/PROJECT.md` — living project document: vision, features, constraints, and a codebase structure map that stays current as the project grows
- `specs/features/XXXX-<name>.md` — one file per feature, covering behavior, rules, edge cases, and interfaces
- `specs/iterations/current.md` — active iteration plan; archived to `specs/iterations/archive/` on close

**Typical workflow:**

```
/spec-init                          # one-time setup
/spec-iteration-start "add auth"    # plan the iteration, create/update specs
/spec-review auth                   # tighten the spec before coding
/spec-iteration-implement           # implement everything in the iteration
/spec-iteration-close               # archive and move on
```

## Installation

Copy the `commands/` directory into your project or into `~/.claude/commands/` to make the commands available globally.
