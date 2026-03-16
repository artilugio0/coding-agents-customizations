---
description: Initialize spec-driven development in this project
allowed-tools: Write, Read, Bash, Glob
argument-hint: (no arguments needed)
---

You are setting up spec-driven development for this project.
Follow these steps in order.

## Step 1 — Gather project info

Ask the user the following questions. Ask them all at once so they can answer in one message:

- What is the **project name**?
- In one sentence, what does this project **do**? (Vision)
- What **problem** does it solve, and for whom?
- Who are the **users** of this project?
- What are the **core features** you plan to build? (a rough list is fine)
- Are there any explicit **non-goals** — things this project will NOT do?
- Any **key constraints** (technical, business, time)?

## Step 2 — Create the spec directory

Run: `mkdir -p specs/features`

## Step 3 — Write `specs/PROJECT.md`

Use the answers from Step 1 to fill in this template:

```
# [Project Name]

## Vision
[one sentence: what this project is]

## Problem
[what problem it solves, for whom]

## Users
[who uses this and what they need from it]

## Core Features
- [ ] [Feature 1]
- [ ] [Feature 2]
(one line per feature)

## Non-Goals
- [what this explicitly does NOT do]

## Key Constraints
[technical or business constraints that must be respected]

## Structure
[Populated after first implementation — maps each feature to where it lives in the codebase]

## Open Questions
[anything unresolved — leave blank if none]
```

## Step 4 — Write `CLAUDE.md`

Write the following content exactly to `CLAUDE.md` in the project root:

```
# Spec-Driven Development

This project uses spec-driven development. Every feature must have a spec before
implementation begins.

## Before Implementing Any Feature

1. Read `specs/PROJECT.md` for overall project context. This is a living document — it is updated as the project evolves.
2. Read `specs/features/[feature-name].md` for the feature's constraints.
3. If no spec exists for the feature, stop and tell the user to run `/spec-iteration-start` first.
4. If the spec is ambiguous or incomplete, ask — do not assume.

## During Implementation

- Respect all Rules and Edge Cases defined in the spec.
- Implementation decisions (code structure, libraries, patterns) are yours to make —
  the spec defines *what* and *why*, not *how*.
- Do not add behavior not described in the spec without flagging it first.

## After Implementation

- Note any deviations from the spec.
- If the implementation revealed a better approach, suggest updating the spec.

## Available Commands

| Command | Purpose |
|---|---|
| `/spec-iteration-start [description]` | Start an iteration — creates and updates specs |
| `/spec-review [name?]` | Review and improve spec(s) |
| `/spec-iteration-implement` | Implement all features in the current iteration |
| `/spec-iteration-close` | Archive the completed iteration |
```

## Step 5 — Confirm

Tell the user:
- Setup is complete
- Their next step is `/spec-iteration-start [description]` to plan and spec their first iteration
- They should run `/spec-review` on any new specs before running `/spec-iteration-implement`
