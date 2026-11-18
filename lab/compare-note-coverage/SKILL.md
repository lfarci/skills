---
name: compare-note-coverage
description: Map source notes to wiki concept notes and report coverage gaps.
version: 0.2.0
license: MIT
metadata:
  hermes:
    tags: [lab, github, notes]
    category: lab
    related_skills: [ingest-notes, clean-up-migration]
---

# Compare note coverage

When the user wants to know whether the wiki in the lab repo (for example `lfarci/notes`) captures everything in a set of source notes — after an ingestion, or before deleting a migration folder — build the coverage ledger. Tools: the GitHub MCP tools `get_file_contents` and `search_code`, then `create_branch`, `push_files`, and `create_pull_request` when the ledger changes. Terminal and `gh` stay unused.

**Source of truth:** `wiki/FILING.md` (section *Preserve sources and keep a coverage ledger*) for the ledger's location, statuses, and format. Read it every time. If it is missing, stop and ask. When recording destination paths, use the current filing tree (`me/learn/`, `me/home/cooking/`, `me/career/guides/`, `me/health/`, and so on), not the retired top-level `learning/`, `cooking/`, or `work/` folders.

The deliverable is the updated ledger file in a pull request (or in the ingestion PR that asked for it) plus a short comparison report. Never merge a notes PR. Never copy an omitted sensitive value into the ledger or the report: describe it by field.

## Steps

1. List every source file in the folders to compare, and every wiki note whose `## Sources` section links into them.
   Done when each source has its list of citing concept notes (possibly empty).
2. Check URLs: collect every URL in each source and confirm it appears somewhere in the wiki. Treat equivalent forms (a short link and its full form, a decoded and an encoded path) as found, and say so in the row.
   Done when each source has its missing-URL list.
3. Check content by reading each source against its citing notes: ideas, facts, names, dates, and list items. Note anything left out or condensed and why (sensitive, credential, condensed itinerary, unclear).
   Done when every source has a status: *Full*, *Partial* (with what is missing), or *Not captured*.
4. Write the ledger as `wiki/FILING.md` says: a summary with counts, then one row per source with its citing notes, status, and notes. Link sources and notes with relative paths.
   Done when the ledger lists every source and its counts add up.
5. Report: the counts, every *Partial* and *Not captured* source with its reason, and what the user should verify before any cleanup.
   Done when the report is in the PR body or the chat reply, with the PR link if one was opened.
