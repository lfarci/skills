---
name: create-notes-issue
description: Create a notes issue when filing work in the notes repo.
version: 0.1.1
license: MIT
metadata:
  hermes:
    tags: [notes, github, issues]
    category: notes
    related_skills: [save-resource]
---

# Create notes issue

Open an issue in the notes repo (for example `lfarci/notes`) with the GitHub MCP tools only: `search_issues`, `list_issues`, `issue_read`, `issue_write`, `add_issue_comment`, `sub_issue_write`. Terminal and `gh` stay unused. Draft, then ask, before any write.

## Steps

1. Pick the level. Default is Task unless the user is clearly opening a new Idea or Experiment.
   Done when the level is Task, Experiment, or Idea, with a reason.
2. Search the notes repo with `search_issues` (title keywords and related numbers) for existing work and a parent. Prefer the most relevant existing Idea or Experiment.
   Done when the search has been run, the chosen parent is named (or it is justified that none fits), and every close match was considered.
3. Handle duplicates. If a close duplicate already exists, show it and stop, or offer a comment on that issue. If a newly identified issue is itself a duplicate, close it as **not planned** with `issue_write`. Never delete issues.
   Done when the user has been shown any close duplicate, and no duplicate remains open as new work.
4. Draft the title, work type, parent, and body using **Hierarchy** and **Title and body**. Show the draft and wait for a yes.
   Done when the user has approved a draft that follows those sections.
5. Create with `issue_write`. Attach the parent with `sub_issue_write`. Comment on the parent with a short link to the child (`add_issue_comment`).
   Done when the issue exists, is a sub-issue of that parent, and the parent has the comment.
6. Reply with one short line and the issue link, plus the reminder in **Board fields**.
   Done when the user has been given that one-line reply and the board-field reminder.

## Hierarchy

Shape is **Idea → Experiment → Task**, via native GitHub sub-issues, maximum depth three. Legal attachments: an Experiment under an Idea, a Task under an Experiment. Follow these attachments unless the user explicitly overrides.

Default: a Task under the most relevant *existing* Idea or Experiment. Reuse a parent that already fits. If the best match is an Idea, attach through a fitting Experiment (reuse one, or propose a new Experiment under that Idea). Open a new Idea only when nothing existing fits and one is really needed.

Leave parent titles and plans unchanged unless the user asks.

## Title and body

One *concern* per issue, in English. If the request has several concerns, split into several issues.

Title: action-oriented sentence case (first word and proper nouns only). Examples: `Explore X: what it is`, `Read …`. Work type lives in the body as `**Work type:** Idea|Experiment|Task`, not in the title and not as labels. Leave default labels as they are unless the user asks to add some.

Body, in this order:

- Heading: `## Task`, `## Experiment`, or `## Idea`
- `**Work type:** …`
- What it is
- Source link and direct links (canonical / official URLs)
- Why it matters, including which parent it belongs under
- Out of scope
- `Parent: #N` (or `Parent idea: #N`) when there is a parent

Stick to facts the user and sources support.

## Board fields

The connected GitHub token cannot set Projects v2 fields (Work type, Status, Priority, Size). Remind the user to set them in the GitHub UI. Typical values: Work type Task, Status Backlog, Priority P2.
