---
description: Close and archive the current iteration
allowed-tools: Write, Read, Bash, Glob
argument-hint: (no arguments needed)
---

You are closing the current iteration.

## Step 1 — Read the iteration

Read `specs/iterations/current.md`. If it doesn't exist, stop:
> "No active iteration to close."

## Step 2 — Check for unchecked items

Scan all sections of `current.md` for unchecked items (`- [ ]`). If any exist, warn the user
and list them explicitly. Ask the user to confirm they want to close anyway.

## Step 3 — Determine archive filename

List files in `specs/iterations/archive/` (create the directory if it doesn't exist).
Count existing files to determine the next number NNNN (zero-padded to 4 digits, starting at 0001).

Derive the iteration name from the `# Iteration: <name>` heading in `current.md`.
Slugify it: lowercase, spaces to hyphens, remove special characters.

The archive filename will be: `NNNN-<iteration-name>.md`

## Step 4 — Archive

Move `specs/iterations/current.md` to `specs/iterations/archive/NNNN-<iteration-name>.md`.

Since there is no `mv` shorthand, do this by:
1. Reading the full contents of `specs/iterations/current.md`
2. Writing those contents to `specs/iterations/archive/NNNN-<iteration-name>.md`
3. Deleting `specs/iterations/current.md` using `rm specs/iterations/current.md`

## Step 5 — Confirm

Tell the user:
> "Iteration closed and archived as `specs/iterations/archive/NNNN-<name>.md`."
