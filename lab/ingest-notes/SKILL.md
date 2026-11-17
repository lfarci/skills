---
name: ingest-notes
description: Ingest exported notes into the lab repo's wiki by subject.
version: 0.1.0
license: MIT
metadata:
  hermes:
    tags: [lab, github, notes]
    category: lab
    related_skills: [create-lab-issue, save-resource, grill-idea]
---

# Ingest notes

When the user wants notes from another tool (a Google Keep Takeout, a Notion export, or any future export or batch of captures) brought into the lab repo's wiki (for example `lfarci/notes`), file each note by subject with the repo's own filing rules. Tools: the GitHub MCP tools `get_file_contents` and `search_code` to read, then `create_branch`, `push_files`, and `create_pull_request` to propose the change. Terminal and `gh` stay unused.

**Source of truth:** `wiki/FILING.md` in the lab repo — the decision tree for keep or drop, where a note goes, merge or create, how to write it, and how to flag borderline items — together with `AGENTS.md` and `wiki/AGENTS.md`. Read them every time; this skill only sequences the work. If `wiki/FILING.md` is missing, stop and ask.

The deliverable is one pull request. Never merge it: the user reviews every notes PR. Ingestion is not backlog work — a note does not become an Idea, Experiment, or Task issue. If the user asks to pursue an ingested idea, hand it to `create-lab-issue` (or `grill-idea` to scope it) as a separate step.

## Steps

1. Read `AGENTS.md`, `wiki/AGENTS.md`, `wiki/FILING.md`, `wiki/README.md`, and the index of every area the sources may touch. Check open pull requests that change the same areas.
   Done when the filing rules and current indexes are known, and any overlapping open PR is named to the user.
2. Locate the sources. If they are not yet in the repo, propose a first PR that adds the curated export under its own source folder (for example `<tool>-migration/`) with a README listing counts and, by title only, everything dropped as a credential or sensitive. Never commit a credential.
   Done when the sources are in the repo (or in an approved PR), unchanged from the export apart from the curation recorded in their README.
3. Triage every source note with **Drop or keep?** in `wiki/FILING.md`. List drops by reason and, for sensitive or credential notes, by title only.
   Done when every source note is either kept or recorded as dropped with its reason.
4. Place every kept note with **Where does it go?** and **Merge into an existing note or create a new one?**: search the wiki for the topic and for each URL first, merge into canonical notes, consolidate short captures, and create notes only for distinct topics. Write the plan as a ledger (source → destination) and collect placement, sensitivity, and wording flags.
   Done when every kept source has a destination in the ledger and every borderline case has a flag.
5. Show the user the target tree, the counts, and the flags. Wait for a yes, or apply the changes they ask for.
   Done when the user has approved the plan.
6. Write the notes as **How to write it** says: in English, with no YAML frontmatter, source metadata in the body with a link back to the source, every original URL kept, uncertainty marked, and omissions stated. Update the indexes and commit the ledger where `wiki/FILING.md` says. Leave the source folder unchanged.
   Done when every ledger row exists in the wiki, each new note is indexed, and the source folder is untouched.
7. Run **Check before opening the PR**: re-scan the new text for credentials and personal data, check that each local link resolves, and run the repository validation if the environment allows it (say so if it does not). Then create a branch, push the files, and open the PR. Its body has a Summary with the tree, Evidence (before/after and checks), the flags, any overlapping PRs, and Merge Danger.
   Done when the PR is open and unmerged, its body lists every flag, and the reply is one short line plus the PR link.
