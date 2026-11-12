---
name: sync-issue-progress
description: Sync lab issue progress from verified work.
version: 0.1.0
license: MIT
metadata:
  hermes:
    tags: [lab, github, issues]
    category: lab
    related_skills: [create-lab-issue, review-backlog, restructure-subissues]
---

# Sync issue progress

When work has landed (or is claimed to have landed), update the matching issues in the lab repo (for example `lfarci/notes`). Verify every claim independently before writing. Follow `create-lab-issue` for tools, asking before writes, and the board-field reminder. Extra read tool: `get_file_contents` for a path or file cited as evidence. Terminal and `gh` stay unused. Never merge. Never delete issues.

Inspired by Matt Pocock's [wayfinder](https://github.com/mattpocock/skills/blob/main/skills/engineering/wayfinder/SKILL.md) (resolution comment, then close, then a pointer on the parent).

## Steps

1. Identify the issues to update (named by the user, or found with `search_issues` / `list_issues`). Read each with `issue_read` (body, comments, parent, sub-issues).
   Done when the candidate issues and their claimed progress are listed.
2. Verify each claim independently. Re-read the issue and comments. If a file, path, or commit in the lab repo is cited, fetch it with `get_file_contents` and check that the evidence actually supports the claim. Treat unverified claims as still open.
   Done when every claim is verified, unsupported, or marked as needing more evidence.
3. Propose the writes: a short progress or resolution comment, which finished Tasks to close, and how the parent index will be updated (a short `add_issue_comment`, or `issue_write` only if the parent already has a checklist in its body). Wait for a yes. Close nothing that was not verified, and merge nothing.
   Done when the user has approved the comment, the closes, and the parent-index update.
4. Apply the approved writes with `add_issue_comment` and, for finished Tasks, `issue_write` to close them as **completed** (see **Closing issues** in `create-lab-issue`). Update the parent index. Reply with one short line and the issue links.
   Done when approved comments and closes are in place, the parent index points at the resolution, unverified work is unchanged, and nothing was merged or deleted.
