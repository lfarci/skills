---
name: create-notes-issue
description: Create and attach a notes issue under a parent.
version: 0.1.0
license: MIT
metadata:
  hermes:
    tags: [notes, github, issues]
    category: notes
    related_skills: [save-resource]
---

# Create notes issue

Use this when the user wants to capture something as an issue in the notes repo (for example `lfarci/notes`). Use only the GitHub MCP tools (`search_issues`, `list_issues`, `issue_read`, `issue_write`, `add_issue_comment`, `sub_issue_write`). Do not use `gh` or the terminal. Draft and ask before writing. After success, reply with one short line and the issue link (plus the board-field reminder below).

## Conventions

- Hierarchy is **Idea → Experiment → Task**, via native GitHub sub-issues. Maximum depth is three. Never attach a Task to an Idea, an Experiment to an Experiment, or a Task to a Task.
- Default level is **Task**, under the most relevant existing Idea or Experiment. Prefer an existing parent. Do not open a new Idea unless nothing existing fits and one is really needed. If the best match is an Idea, attach via a fitting Experiment (reuse one, or propose a new Experiment under that Idea) — never hang a Task directly on an Idea.
- One concern per issue. Write the issue in English.
- Titles are action-oriented and sentence case (first word and proper nouns only). Examples: `Explore X: what it is`, `Read …`. No type tags (`[Task]`, `Task:`), no emoji, no ALL CAPS or Title Case.
- Do not use labels to classify type. Put `**Work type:** Idea|Experiment|Task` in the body.
- The connected GitHub token cannot set Projects v2 fields (Work type, Status, Priority, Size). After creating an issue, remind the user to set them in the GitHub UI. Typical values: Work type Task, Status Backlog, Priority P2.
- Body shape:
  - Start with `## Task`, `## Experiment`, or `## Idea`.
  - `**Work type:** …`
  - What it is.
  - Source link and any direct links (canonical / official URLs, not a dump of every URL seen).
  - Why it matters, including which parent it belongs under.
  - Out of scope.
  - `Parent: #N` (or `Parent idea: #N`) when there is a parent. Do not invent facts.

## Steps

1. Read the request and pick the level. Default to Task unless the user is clearly opening a new Idea or Experiment.
2. Search for existing work and parents with `search_issues` (title keywords and related numbers) in the notes repo. Prefer the most relevant existing Idea/Experiment.
3. Check for duplicates. If a close duplicate already exists, show it and stop, or offer a comment on the existing issue. If a newly identified issue is itself a duplicate, close it as **not planned** with `issue_write`. Never delete issues.
4. Draft title, work type, parent, and body. Show the draft to the user and wait for a yes.
5. Create with `issue_write`. Attach the parent with `sub_issue_write`. Post a short comment on the parent that links the new child (`add_issue_comment`).
6. Reply with one short line and the issue link. Remind the user to set Work type, Status, Priority, and Size on the board (typical: Task, Backlog, P2).

## Pitfalls

- Do not create a Task without an Experiment parent, or an Experiment without an Idea parent, unless the user explicitly overrides.
- Do not invent an Idea just to have a place to hang work. Search first.
- Do not pack several concerns into one issue; split them.
- Empty or default labels are normal; do not add `enhancement` / `documentation` unless the user asks.
- Do not retitle parents or rewrite their plans unless the user asks.

## Verification

The issue has an action-oriented sentence-case title, the correct heading and Work type line, one concern, a parent one level above it (when required), no close unaddressed duplicate, and a short parent comment linking it. The reply to the user is one short line plus the link and the board-field reminder.
