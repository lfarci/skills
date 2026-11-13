---
name: create-lab-issue
description: Create a lab issue when filing work in the lab repo.
version: 0.3.0
license: MIT
metadata:
  hermes:
    tags: [lab, github, issues]
    category: lab
    related_skills: [save-resource, split-lab-issue, research-topic, grill-idea, restructure-subissues, review-backlog, sync-issue-progress]
---

# Create lab issue

Open an issue in the lab repo (for example `lfarci/notes`) with the GitHub MCP tools only: `search_issues`, `list_issues`, `issue_read`, `issue_write`, `add_issue_comment`, `sub_issue_write`. Terminal and `gh` stay unused. Draft, then ask, before any write.

This skill is the source of truth for hierarchy, titles, bodies, closing reasons, and board-field reminders. Other lab skills follow it when they file or reshape issues. **Idea scope** (goal, outcome, boundaries, next step) lives in `grill-idea`; when filing an Idea, satisfy that section.

## Steps

1. Pick the **Work type**. Default is Task unless the user is clearly opening a new Idea or Experiment.
   Done when the Work type is Idea, Experiment, or Task, with a reason.
2. Search the lab repo with `search_issues` (title keywords and related numbers) for existing work and a parent. Prefer the most relevant existing Idea or Experiment.
   Done when the search has been run, the chosen parent is named (or it is justified that none fits), and every close match was considered.
3. Handle duplicates. If a close duplicate already exists, show it and stop, or offer a comment on that issue. If a newly identified issue is itself a duplicate, close it as **duplicate** with `issue_write` (see **Closing issues**). Never delete issues.
   Done when the user has been shown any close duplicate, and no duplicate remains open as new work.
4. Draft the title, Work type, parent, and body using **Hierarchy** and **Title and body**. If the Work type is Idea, the draft must also satisfy **Idea scope** in `grill-idea`; if the Idea is still fuzzy, offer `grill-idea` first. Show the draft and wait for a yes.
   Done when the user has approved a draft that follows those sections.
5. Create with `issue_write`. Attach the parent with `sub_issue_write`. Comment on the parent with a short link to the child (`add_issue_comment`).
   Done when the issue exists, is a sub-issue of that parent, and the parent has the comment.
6. Reply with one short line and the issue link, plus the reminder in **Board fields**.
   Done when the user has been given that one-line reply and the board-field reminder.

## Hierarchy

Shape is **Idea → Experiment → Task**, via native GitHub sub-issues, maximum depth three. Legal attachments: an Experiment under an Idea, a Task under an Experiment. Follow these attachments unless the user explicitly overrides.

Default: a Task under the most relevant *existing* Idea or Experiment. Reuse a parent that already fits. If the best match is an Idea, attach through a fitting Experiment (reuse one, or propose a new Experiment under that Idea). Open a new Idea only when nothing existing fits and one is really needed. An Idea may have no children until it is ready to explore.

Leave parent titles and issue bodies unchanged unless the user asks. A parent stays a short index: gist plus link; detail lives on the child.

## Title and body

One *concern* per issue, in English. If the request has several concerns, split them with `split-lab-issue`.

Title: action-oriented sentence case (first word and proper nouns only). Examples: `Explore X: what it is`, `Read …`. Keep titles free of type tags. Work type lives in the body as `**Work type:** Idea|Experiment|Task` and on the lab board's **Work type** field, not in the title and not as labels. Leave default labels unused unless the user asks to add some.

Body, in this order:

- Heading: `## Idea`, `## Experiment`, or `## Task`
- `**Work type:** …`
- What it is (for an Idea, the **Idea scope** fields in `grill-idea`)
- Source link and direct links (canonical / official URLs), or context and references
- Why it matters, including which parent it belongs under
- Out of scope
- Next step, when known
- `Parent: #N` (or `Parent idea: #N`) when there is a parent

Stick to facts the user and sources support.

## Closing issues

Never delete issues. Close with a GitHub state reason, not a label (the lab repo classifies work with **Work type**, not labels):

- **duplicate** — the same concern already exists
- **not planned** — not worth pursuing, superseded, or replaced by a split
- **completed** — the work is done (see `sync-issue-progress`)

Post a short comment that states the reason, then close with `issue_write`. Example: `Closed as not planned: <why>.`

## Board fields

The connected GitHub token cannot set Projects v2 fields. Remind the user to set them on the lab board in the GitHub UI.

- **Work type:** Idea, Experiment, Task
- **Status:** Backlog, Ready, In progress, In review, Done
- **Priority:** P0, P1, P2
- **Size:** XS, S, M, L, XL

Typical values for a new Task: Work type Task, Status Backlog, Priority P2.
