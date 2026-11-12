---
name: review-backlog
description: Review the lab backlog for issues that need attention.
version: 0.1.0
license: MIT
metadata:
  hermes:
    tags: [lab, github, issues]
    category: lab
    related_skills: [create-lab-issue, split-lab-issue, restructure-subissues, sync-issue-progress, grill-idea]
---

# Review backlog

Survey open issues in the lab repo (for example `lfarci/notes`) and show what needs attention. Recommend fixes; draft and ask before any write. Follow `create-lab-issue` for hierarchy, tools, and the board-field reminder. Terminal and `gh` stay unused.

This skill is safe to run on a weekly cron: if nothing needs attention, stay quiet (no comments, no chat noise on a scheduled run). In a live session, one short "nothing needs attention" line is enough.

Inspired by Matt Pocock's [triage](https://github.com/mattpocock/skills/blob/main/skills/engineering/triage/SKILL.md) (show what needs attention, recommend, then wait).

## Steps

1. List open issues with `list_issues` / `search_issues`, and read anything that looks off with `issue_read`. Look for: no parent or a parent at the wrong level, a Task attached to an Idea, a packed issue (several concerns), a close duplicate, a thin body, stale work with no recent progress, or an Idea that does not yet meet **Idea scope** in `grill-idea`.
   Done when every open issue has been considered and the attention list is complete (or empty).
2. If the attention list is empty: on a scheduled run, write nothing and end silently; in a live session, reply with one short line. Stop.
   Done when a clean backlog has produced no writes and no scheduled noise.
3. Present the issues that need attention, oldest first, each with one line and a recommended next step (`split-lab-issue`, `restructure-subissues`, `sync-issue-progress`, `grill-idea`, comment, close as **duplicate**, or close as **not planned** if an Idea is not worth pursuing). Wait for the user to pick, or for approval of a proposed batch.
   Done when the user has chosen what to act on, or has declined.
4. Carry out only the approved actions, asking again before each write, using the skill named in the recommendation. Never delete issues.
   Done when approved actions are done, declined ones are untouched, and any new or changed issue comes with the board-field reminder.
