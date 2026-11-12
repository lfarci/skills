---
name: restructure-subissues
description: Restructure lab sub-issues under the right parent.
version: 0.1.0
license: MIT
metadata:
  hermes:
    tags: [lab, github, issues]
    category: lab
    related_skills: [create-lab-issue, split-lab-issue, review-backlog]
---

# Restructure sub-issues

Reshape existing sub-issues in the lab repo (for example `lfarci/notes`): reparent a child, fix a Task hung on an Idea, or close a duplicate. Follow `create-lab-issue` for legal attachments, depth, tools, asking before writes, and the board-field reminder. A parent stays a short index (gist plus link); detail lives on the child. Terminal and `gh` stay unused.

Inspired by Matt Pocock's [wayfinder](https://github.com/mattpocock/skills/blob/main/skills/engineering/wayfinder/SKILL.md) (the parent as an index, not a store).

## Steps

1. Read the named issue and its current parent and siblings with `issue_read` (and `search_issues` / `list_issues` as needed). State the current shape and what is wrong (wrong parent, wrong depth, duplicate, packed — if packed, hand off to `split-lab-issue`).
   Done when the current parent, level, and the proposed fix are explicit.
2. Search for a better parent and for close duplicates. Prefer an existing Idea or Experiment that already fits.
   Done when the proposed parent is named, or it is justified that a new Experiment under an existing Idea is needed, and any duplicate is identified.
3. Show the plan: what will be reattached, what will be commented, and any duplicate to close as **not planned**. Wait for a yes.
   Done when the user has approved the plan.
4. Attach with `sub_issue_write`. Update `Parent: #N` on the child with `issue_write` if it is stale. Comment on the new parent (and the old one, if it changed) with a short link. Close a confirmed duplicate as **not planned**. Never delete issues. Leave parent titles and plans unchanged unless the user asks; only the short index comment (or an existing checklist in the parent body) is updated.
   Done when attachments match `create-lab-issue`, duplicates are closed as not planned, parents have the index comments, and the user has the links plus the board-field reminder if a new issue was created.
