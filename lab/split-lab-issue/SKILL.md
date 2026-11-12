---
name: split-lab-issue
description: Split a packed lab issue into one-concern children.
version: 0.1.0
license: MIT
metadata:
  hermes:
    tags: [lab, github, issues]
    category: lab
    related_skills: [create-lab-issue, restructure-subissues, grill-plan]
---

# Split lab issue

Split an existing issue in the lab repo (for example `lfarci/notes`) that packs several *concerns* into one-concern children. Follow `create-lab-issue` for hierarchy, titles, bodies, tools, asking before writes, and the board-field reminder. Terminal and `gh` stay unused.

Inspired by Matt Pocock's [to-tickets](https://github.com/mattpocock/skills/blob/main/skills/engineering/to-tickets/SKILL.md).

## Steps

1. Read the source issue with `issue_read` (body, comments, parent, sub-issues). List each distinct concern.
   Done when every concern is named, and packed vs already-one-concern is decided.
2. Search the lab repo with `search_issues` for existing work that already covers a concern. Reuse a match instead of creating a duplicate.
   Done when each concern is either a proposed new child or a pointer to an existing issue.
3. Propose the breakdown: for each child, the title, level, parent, and what it delivers. Legal attachments and depth follow `create-lab-issue`. Children of a packed Task are sibling Tasks under that Task's Experiment, not a fourth level. Ask whether the granularity is right, and wait for a yes.
   Done when the user has approved the child list and parents.
4. Create each new child with `create-lab-issue` (draft already approved, so create, attach, and comment on the parent). If the source issue is the right-level parent (Idea or Experiment), keep it as a short index and comment with links to the children. If the source was itself a packed Task, offer to close it as **not planned** once the children exist. Never delete issues.
   Done when every approved child exists under the right parent, the source issue is an index or is closed as not planned as agreed, and the user has the links plus the board-field reminder.
