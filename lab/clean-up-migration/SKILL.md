---
name: clean-up-migration
description: Remove a reviewed migration folder from the lab repo without breaking links.
version: 0.1.0
license: MIT
metadata:
  hermes:
    tags: [lab, github, notes]
    category: lab
    related_skills: [compare-note-coverage, ingest-notes]
---

# Clean up migration

When the user says a migration folder in the lab repo (for example `google-keep-migration/` or `notion-migration/` in `lfarci/notes`) can go, remove it in its own pull request without leaving broken links. Only start after the user has reviewed the coverage ledger and said which folder to delete. Tools: the GitHub MCP tools `get_file_contents` and `search_code`, then `create_branch`, `push_files`, and `create_pull_request`. Terminal and `gh` stay unused.

**Source of truth:** `wiki/FILING.md` (section *Preserve sources and keep a coverage ledger*). Read it every time. If it is missing, stop and ask.

The deliverable is one pull request that deletes the folder. Never merge it, and never delete anything outside the folder the user named.

## Steps

1. Read the coverage ledger. Confirm with the user that every *Partial* and *Not captured* row is accepted, or capture the missing content first with `ingest-notes`.
   Done when the user has explicitly approved deleting the named folder.
2. Find every link into the folder across the repository: `## Sources` sections, folder READMEs, migration notes, the ledger, and agent guidance.
   Done when every referencing file is listed.
3. Rewrite those references so nothing breaks: turn each source link into plain text (tool, title or page path, date), keep the rest of the line, and mark the ledger as historical with the deletion date. Update notes that describe the migration status.
   Done when no file outside the folder links into it.
4. Delete the folder, re-scan for broken local links, and run the repository validation if the environment allows it (say so if it does not).
   Done when the link check reports no broken links.
5. Open the PR with the deleted folder, the rewritten files, the check results, and Merge Danger (the deletion is permanent on `main`, and the files stay only in Git history).
   Done when the PR is open and unmerged, and the reply is one short line plus the PR link.
