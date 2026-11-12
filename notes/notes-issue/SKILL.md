---
name: notes-issue
description: Create notes issues with the lab conventions.
version: 0.1.0
license: MIT
metadata:
  hermes:
    tags: [notes, github, issues]
    category: notes
    related_skills: [notes-hierarchy, save-resource]
---

# Notes issue

Use this when the user wants to capture, format, or open an issue in the notes repo (for example `lfarci/notes`). Use only the GitHub MCP tools (`search_issues`, `list_issues`, `issue_read`, `issue_write`, `add_issue_comment`). Do not use `gh` or the terminal. Ask before writing.

## Conventions

- Hierarchy is **Idea → Experiment → Task**, via native parent/sub-issues. A new standalone issue defaults to **Idea**. An Experiment needs a parent Idea. A Task needs a parent Experiment. Do not nest deeper.
- Titles are sentence case (first word and proper nouns only). No type tags (`[Task]`, `Task:`), no emoji, no ALL CAPS or Title Case.
- Do not use labels to classify type. Put `**Work type:** Idea|Experiment|Task` in the body. If the GitHub MCP cannot set project fields, remind the user to set Work type (and Status) on the notes project board in the GitHub UI.
- Start the body with `## Idea`, `## Experiment`, or `## Task`.
- Required content:
  - Idea: problem or desired outcome, value, boundaries; room for child experiments.
  - Experiment: question or approach, method, decision criteria (adopt / revise / stop).
  - Task: concrete deliverable and checkable acceptance criteria or a short checklist.
- Link the parent (`Parent: #N` or `Parent idea: #N`). Link related issues. Do not invent facts.

## Steps

1. Read the request and pick the level (Idea / Experiment / Task). If it is a Task or Experiment, identify the parent (use `notes-hierarchy`).
2. Search for duplicates with `search_issues` in the notes repo (title keywords and related numbers). If something close exists, show it and stop or offer to comment with `add_issue_comment` instead of opening a new issue.
3. Draft title, work type, parent, and body. Show the draft to the user and wait for a yes.
4. Create with `issue_write`. Then attach the parent with `sub_issue_write` (see `notes-hierarchy`).
5. Report the issue number and URL. Remind the user to set Work type (and Status) on the board if needed.

## Pitfalls

- Do not create a Task without an Experiment parent, or an Experiment without an Idea parent, unless the user explicitly overrides.
- Do not dump a long research note into the issue; link a file in `projects/` (or `career/`) instead.
- Empty or default labels are normal; do not add `enhancement` / `documentation` unless the user asks.

## Verification

The new issue has a sentence-case title, the correct heading, a parent link when required, and no close duplicate in search results.
