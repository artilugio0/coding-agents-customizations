---
description: Write tests for all features in the current iteration before implementation
allowed-tools: Write, Read, Edit, Bash, Glob, Grep
argument-hint: (no arguments needed)
---

You are writing tests for all features in the current iteration. No application code will be written.

## Step 1 — Read iteration and specs

Read `specs/iterations/current.md`. If it doesn't exist, stop:
> "No active iteration. Run `/spec-iteration-start` first."

Read every spec file listed under `## To Implement` in `current.md`.

## Step 2 — Understand the testing landscape

Explore the project to determine:
- What test framework is in use (Jest, pytest, RSpec, Vitest, Go test, etc.)
- Where test files live (e.g. `tests/`, `__tests__/`, alongside source files)
- File naming conventions (e.g. `*.test.ts`, `*_test.go`, `test_*.py`)
- Any existing test files to use as examples of style and structure

If the project has no existing tests, note this — you may need to ask.

## Step 3 — Ask technical questions (only if needed)

If the test framework or conventions are unknown or ambiguous after exploring the codebase, ask the user.

If any spec's `## Interfaces` section is too vague to write meaningful tests against, ask for clarification.

Batch all questions into one message. Skip this step entirely if all answers are already clear from the codebase.

## Step 4 — Write tests

For each feature listed under `## To Implement`, create test file(s) covering:

- **Core Behavior** — the main success flow described in the spec
- **Rules** — one test per invariant listed in the spec's Rules section
- **Edge Cases** — one test per named edge case in the spec

Tests must reference the spec's `## Interfaces` section for what to call and assert against.

Tests are expected to fail at this point — no implementation exists yet. This is intentional and correct.

Do not write any application code.

## Step 5 — Update `specs/iterations/current.md`

Add or update a `## Tests Written` section listing each test file created:

```
## Tests Written
- `tests/auth.test.js` — covers 0001-auth (login flow, session rules, edge cases)
- `tests/payments.test.js` — covers 0002-payments (charge flow, webhook edge cases)
```

## Step 6 — Update spec status

In each feature spec's `## Status` section, mark `- [x] Tests written`.

## Step 7 — Confirm

- List all test files created with brief descriptions of what they cover.
- Suggest the user run the tests to confirm they fail as expected (no implementation yet).
- Tell the user their next step is `/spec-iteration-implement`.
