---
description: Start a new iteration — create and update specs based on your intent
allowed-tools: Write, Read, Edit, Glob
argument-hint: [description of what you want to accomplish]
---

You are starting a new development iteration for: **$ARGUMENTS**

If `$ARGUMENTS` is empty, ask the user:
> "What do you want to accomplish in this iteration?"
Then wait for their response before continuing.

## Step 1 — Read project context

1. Read `specs/PROJECT.md`. If it doesn't exist, stop and tell the user to run `/spec-init` first.
2. Read all files in `specs/features/` to understand what's already been specced.

## Step 2 — Check for an active iteration

Check if `specs/iterations/current.md` exists. If it does, stop and warn:
> "An iteration is already in progress. Run `/spec-iteration-close` first, or continue that iteration."

## Step 3 — Analyze intent

Based on the user's description and the existing specs, identify:
- **New features** — things not covered by any existing spec
- **Existing specs to modify** — specs whose described behavior will change

## Step 4 — Ask clarifying questions

Ask only what's necessary — not a fixed interview. Focus on:
- Ambiguous intent where a wrong assumption would be hard to reverse
- Spec decisions with significant trade-offs

Batch all questions into one message. Skip questions where the intent is already clear.

## Step 5 — Create and update specs

**For new features:**
- Determine the next available XXXX number by listing `specs/features/`.
- Create `specs/features/XXXX-<name>.md` using this template:

```
# Feature: <name>

## Overview
[1-2 sentences: what this feature does, from the user's perspective]

## Why
[what problem it solves and for whom]

## Behavior

### Core Behavior
[step-by-step description of the main flow, from the user's perspective]

### Rules
- [invariant 1: something that must always be true]
- [invariant 2]

### Edge Cases
- **[edge case name]:** [how it's handled]

## Interfaces
[Key inputs/outputs, API shapes, or UI elements — described at the contract level, not implementation]

## Out of Scope
- [what this feature explicitly does NOT do]

## Open Questions
- [anything unresolved — remove this section if none]

## Status
- [ ] Spec complete
- [ ] Implemented
- [ ] Tested
```

**For existing specs being modified:**
- Edit the spec file in place to reflect the new behavior.
- Update only the sections that are actually changing.

## Step 6 — Update PROJECT.md Core Features (only if new specs were created)

If any **new** spec files were created in Step 5:
- Read `specs/PROJECT.md`'s `## Core Features` list
- For each new spec, check if the feature is already listed
- If any are missing, add them as `- [ ] <Feature name>` entries
- If no new specs were created, skip this step entirely — do not touch PROJECT.md

## Step 7 — Create `specs/iterations/current.md`

First ensure the `specs/iterations/` directory exists. Then write:

```
# Iteration: <derived name from user description>

## Goal
<user's intent in 1-3 sentences>

## New Specs
- [ ] XXXX-<feature-name> — <one-line description>

## Updated Specs
- [ ] XXXX-<feature-name> — <what changed and why>

## To Implement
- [ ] XXXX-<feature-name>
- [ ] XXXX-<feature-name>

## Notes
<anything unresolved or worth flagging>
```

Omit "New Specs" if there are none. Omit "Updated Specs" if there are none.
List every spec that needs implementation work under "To Implement".

## Step 8 — Confirm

Tell the user:
- Which spec files were created (with paths)
- Which spec files were updated (with paths)
- That `specs/iterations/current.md` was created
- Suggest running `/spec-review <feature>` for any new specs before implementing
