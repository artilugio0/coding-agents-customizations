---
description: Implement all features in the current iteration
allowed-tools: Write, Read, Edit, Bash, Glob, Grep
argument-hint: (no arguments needed)
---

You are implementing all features in the current iteration.

## Step 1 — Read the iteration

Read `specs/iterations/current.md`. If it doesn't exist, stop:
> "No active iteration. Run `/spec-iteration-start` first."

## Step 1b — Verify tests exist

Check whether `current.md` contains a `## Tests Written` section with at least one entry.

If not, stop:
> "Tests have not been written for this iteration. Run `/spec-iteration-write-tests` first, then review the tests before implementing."

## Step 2 — Read all specs to implement

Read every spec file listed under `## To Implement` in `current.md`. Also read `specs/PROJECT.md`
for overall project context.

If any spec has unresolved Open Questions or `- [ ] Spec complete` is unchecked, warn the user
and ask if they want to proceed anyway.

## Step 3 — Understand the existing codebase

Before writing any code, explore the project:
- Understand file/directory conventions and patterns in use
- Find existing utilities or abstractions that should be reused
- Identify where each new feature will fit in the current structure

## Step 4 — Plan

Write a brief implementation plan in the chat (not a file) covering all features in the iteration:
- Where code will live for each feature
- Key design decisions and why
- Any spec gaps or ambiguities that need clarifying before writing code

Ask the user if they want to proceed before writing any code.

## Step 5 — Implement

Implement all features. For each:
- Follow the spec's Rules and Edge Cases strictly
- Match the Interfaces described in the spec
- Do not implement anything listed in Out of Scope
- Make your own decisions on code structure, naming, and patterns

After implementing each feature, run the tests for that feature. All pre-existing tests for that feature must pass before moving on to the next feature.

## Step 6 — Reconcile with specs

After all implementation, report for each spec:
- **Followed:** which spec sections were implemented as written
- **Deviated:** where implementation differed from the spec and why — update the affected spec to match reality
- **Discovered:** things the spec didn't cover that you had to decide — add to that spec's Open Questions, or resolve and update the spec if the answer is clear
- **Test changes:** if any test was modified during implementation (e.g. a spec ambiguity required a judgement call), list each change and why — update the affected spec's Open Questions or resolve the ambiguity inline

## Step 7 — Update PROJECT.md Structure

After implementation and spec reconciliation:
- Read `specs/PROJECT.md`
- Update the `## Structure` section with a brief entry for each feature implemented in this iteration.
  - **New features**: add a new entry.
  - **Modified features**: update the existing entry if the file structure changed.
  - Leave entries for unrelated features untouched.
- Keep entries concise — this is a navigation aid, not documentation.

Format:
```
**<Feature>** (`<path>`) — <what lives here>
**<Feature>** (`<path1>`, `<path2>`) — <what lives here>
```

## Step 8 — Update iteration and spec status

- Mark each implemented item as `- [x]` in `specs/iterations/current.md`
- In each implemented feature spec, mark `- [x] Implemented` in the Status section
