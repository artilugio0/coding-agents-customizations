---
description: Review spec(s) for gaps, ambiguity, and conflicts
allowed-tools: Write, Read, Glob
argument-hint: [feature-name] (optional — omit to review all specs)
---

You are reviewing feature spec(s) for quality and completeness.

Target: **$ARGUMENTS** (if blank, review all specs in `specs/features/`)

## Step 1 — Read the specs

If `$ARGUMENTS` is provided:
- Read `specs/features/$ARGUMENTS.md`

If `$ARGUMENTS` is empty:
- Read `specs/PROJECT.md`
- Read all files in `specs/features/`

## Step 2 — Analyze each spec against these criteria

For each spec, check:

**Completeness**
- [ ] Overview clearly describes what the feature does from the user's perspective
- [ ] Why section explains the motivation (not just what, but why it matters)
- [ ] Core Behavior covers the full main flow step by step
- [ ] At least 2-3 rules/invariants are defined (or explicitly noted as "none")
- [ ] Edge cases are named and handled (not just "handle errors gracefully")
- [ ] Interfaces are described at contract level (inputs, outputs, shapes)
- [ ] Out of Scope is explicit — what's intentionally excluded

**Clarity**
- [ ] No ambiguous language ("should", "might", "usually") in the Rules section
- [ ] Edge cases are specific — each one is named and resolved, not open-ended
- [ ] Interfaces don't leak implementation details (no class names, library specifics)

**Consistency**
- [ ] Feature doesn't contradict anything in `specs/PROJECT.md`
- [ ] Feature doesn't overlap or conflict with other feature specs

## Step 3 — Identify issues

List every issue found, grouped by severity:

**Must fix** — ambiguity or missing info that would block implementation
**Should fix** — gaps that could lead to misaligned implementation
**Consider** — suggestions to improve clarity or coverage

## Step 4 — Ask targeted questions

For each "Must fix" issue, ask the user one focused question to resolve it.
Ask all questions at once so they can answer in one message.

## Step 5 — Update the spec

Incorporate the user's answers into the spec file(s).
Mark `- [x] Spec complete` in the Status section if all "Must fix" issues are resolved.

## Step 6 — Confirm

Summarize what was changed and flag any "Should fix" items the user chose to defer.
