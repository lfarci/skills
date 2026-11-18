---
name: ingest-notes
description: Synthesize source notes into concept notes in the lab repo's wiki.
version: 0.4.0
license: MIT
metadata:
  hermes:
    tags: [lab, github, notes]
    category: lab
    related_skills: [sort-note-sources, compare-note-coverage, clean-up-migration, create-lab-issue]
---

# Ingest notes

When the user wants source notes that are already in the lab repo (for example `lfarci/notes`) — a migration folder from another tool, or a batch of new captures — turned into wiki notes, synthesize them into topic-based **concept notes** with the repo's own filing rules. Do not copy sources one to one. Tools: the GitHub MCP tools `get_file_contents` and `search_code` to read, then `create_branch`, `push_files`, and `create_pull_request` to propose the change. Terminal and `gh` stay unused.

**Source of truth:** `wiki/FILING.md` in the lab repo — keep or drop, where a note goes, how to synthesize concept notes, how to write them (including *Writing for retrieval*), the coverage ledger, and how to flag borderline items — together with `AGENTS.md` and `wiki/AGENTS.md`. Read them every time; this skill only sequences the work. If `wiki/FILING.md` is missing, stop and ask.

Apply the current placement rules while writing: default to split (one topic per note); put learning in `me/learn/`, cooking in `me/home/cooking/`, health in `me/health/`, and employment guides in `me/career/guides/`; treat `me/career/projects/` as historical project records that prove experience, and `tech/` as discovered knowledge and personal technical notes; leave `finance/` as the general-knowledge placeholder.

Exporting from a tool is out of scope; this skill starts from sources already committed. The deliverable is one pull request. Never merge it: the user reviews every notes PR. A note does not become an Idea, Experiment, or Task issue; if the user wants to pursue an ingested idea, hand it to `create-lab-issue` as a separate step.

## Steps

1. Read `AGENTS.md`, `wiki/AGENTS.md`, `wiki/FILING.md`, `wiki/README.md`, and the index of every area the sources may touch. Check open pull requests that change the same areas.
   Done when the filing rules and current indexes are known, and any overlapping open PR is named to the user.
2. Get a sorting plan from `sort-note-sources`: every source kept or dropped, and the kept ones grouped into topics with a destination note each.
   Done when every source is either dropped with a reason or assigned to a topic and destination.
3. Show the user the target tree of concept notes, the counts, and the flags. Wait for a yes, or apply the changes they ask for.
   Done when the user has approved the plan.
4. Write each concept note as `wiki/FILING.md` says: one topic, a one-to-two-sentence summary under the title, descriptive headings, short plain sentences, consistent terms, bullets for parallel facts, key entities and every original URL spelled out, uncertainty and omissions marked, a `## Related notes` section, and a closing `## Sources` section linking each preserved source file. Merge into canonical notes instead of duplicating them. Never create a note that holds a single link; fold it into the closest broader note or bookmarks list. Split a long list that spans several regions or groups into one note per group plus an index. Update the folder indexes. Leave the source folders unchanged.
   Done when every assigned source is cited by a concept note, each new note is indexed, and the source folders are untouched.
5. Run `compare-note-coverage` to build or refresh the coverage ledger and fix anything it reports as not captured by mistake.
   Done when the ledger is committed and every *Partial* or *Not captured* row has a stated reason.
6. Run **Check before opening the PR** from `wiki/FILING.md`: re-scan the new text for credentials and personal data, check that each local link resolves, and run the repository validation if the environment allows it (say so if it does not). Then create a branch, push the files, and open the PR. Its body has a Summary with the concept-note tree, the comparison report (full, partial, not captured), Structure questions, the flags, Evidence (checks), any overlapping PRs, and Merge Danger.
   Done when the PR is open and unmerged, its body lists every flag, and the reply is one short line plus the PR link.
