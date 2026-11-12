---
name: notes-hierarchy
description: Attach issues to the right parent, shallowly.
version: 0.1.0
license: MIT
metadata:
  hermes:
    tags: [notes, github, sub-issues]
    category: notes
    related_skills: [notes-issue, save-resource]
---

# Notes hierarchy

Use this when filing or moving an issue under the right parent in the notes repo (for example `lfarci/notes`). Use only the GitHub MCP tools (`issue_read`, `list_issues`, `search_issues`, `issue_write`, `sub_issue_write`, `add_issue_comment`). Do not use `gh` or the terminal. Ask before writing.

## Rules

- Shape is exactly **Idea → Experiment → Task**. That is the maximum depth.
- Experiments are children of an Idea. Tasks are children of an Experiment. Never attach a Task to an Idea, or an Experiment to an Experiment. Never nest a Task under a Task.
- An Idea may have no children until it is ready to explore. Do not invent empty placeholder children.
- Prefer an existing parent. Search before opening a new Idea or Experiment just to hang a Task on.

## Keep parents tidy

A parent body should stay a short index, not a copy of every child:

- A checklist of children (`- [ ] #N Title`) and done criteria.
- Update the checklist when attaching or closing a child (`issue_write` on the parent, or `add_issue_comment` if a full edit is unnecessary).
- Child details stay in the child issue.

## Steps

1. Read the child (`issue_read`) and decide its level from the `## Idea` / `## Experiment` / `## Task` heading (or the request, if it does not exist yet).
2. Find the parent: follow links already in the body, then `search_issues` / `list_issues`. Confirm the parent is the right level (Idea for an Experiment, Experiment for a Task).
3. Show the user: child, proposed parent, and current siblings from `issue_read` on the parent (or the sub-issue list if the tool returns it). Wait for a yes.
4. Attach with `sub_issue_write`. Add `Parent: #N` in the child body if it is missing (`issue_write`).
5. Add the child to the parent's checklist if it is not already there.

## Pitfalls

- Do not create a fourth level. If work is too big for a Task, open a new Experiment under the same Idea.
- If the only matching parent is the wrong level, say so and propose the correct one instead of forcing the attach.
- Do not retitle parents or rewrite their plans unless the user asks.

## Verification

The child is a native sub-issue of a parent one level above it, the parent checklist mentions it, and no chain is deeper than Idea → Experiment → Task.
