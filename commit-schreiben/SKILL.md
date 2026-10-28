---
name: commit-schreiben
description: Write git commit messages in Jonas' style - conventional-commit prefix, everyday language in the "we" form, at most three short sentences, no co-author lines. Invoke this automatically, without being asked, whenever you create a commit or propose a commit message.
---

Load the `jonas-writing-style` skill first and follow it for wording and sentences. This skill adds the commit format on top and wins where the two differ.

A commit tells a teammate in a few seconds what changed and why, without opening the diff.

## Language

Write in the language of the project. If it isn't obvious, the existing commit messages decide.

## Subject line

- Conventional-commit prefix: `feat:`, `fix:`, `refactor:`, `perf:`, `docs:`, `test:`, `chore:`, `build:`. Add a scope only when the project already uses scopes.
- After the prefix, a short lowercase phrase in the imperative that says what the commit does ("feat: move windows between desktops without dock injection"). At most about 60 characters, no full stop.

## Description

- Optional, and at most three sentences. Leave it out when the subject says everything.
- From the point of view of someone using the software: what works differently now and, if it isn't obvious, why.
- Write it in the "we" form ("we now remember…"), not with the app's or project's name ("Floe now remembers…").
- No file lists and no test counts.

## Never

- No `Co-Authored-By` lines, no "Generated with Claude Code", no agent markers.
- One logical change per commit. If a diff mixes topics, split it into several commits instead of describing everything in one.

## Example

```
feat: move windows to other desktops with SIP enabled

We now move windows through the Dock, so it works on Tahoe with SIP on and you stay on your current desktop. We also remember which windows we just moved, so we don't mistake our own moves for the user's.
```
