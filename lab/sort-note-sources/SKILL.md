---
name: sort-note-sources
description: Triage source notes and group them into topics before ingestion.
version: 0.3.0
license: MIT
metadata:
  hermes:
    tags: [lab, github, notes]
    category: lab
    related_skills: [ingest-notes, compare-note-coverage]
---

# Sort note sources

When source notes in the lab repo (for example a migration folder or a batch of captures in `lfarci/notes`) need curating before they are written up, decide what to keep, what to drop, and which topic each kept source feeds. Tools: the GitHub MCP tools `get_file_contents` and `search_code`. Terminal and `gh` stay unused.

**Source of truth:** `wiki/FILING.md` (sections *Drop or keep?*, *Where does it go?*, *Synthesize into concept notes*, and *Flag borderline items*). Read it every time. If it is missing, stop and ask.

Placement rules that must match the current filing guide:

- Default to **split**: each note focuses on one topic. Mixed personal-and-general sources become two linked notes, not one combined note.
- `me/` holds things about the user and the working material of his practices. There is no top-level `work/`, `cooking/`, or `learning/`.
- Learning (goals, courses, languages, certification study plans and exam history) goes in `me/learn/` (not `me/learning/`). Cooking goes in `me/home/cooking/`. Health follow-ups go in `me/health/`. Employment guides go in `me/career/guides/`.
- `me/career/projects/` is a record of historical projects that prove experience (professional or personal). `tech/` holds discovered knowledge and personal technical notes.
- `finance/` is a top-level placeholder for general finance knowledge. Personal budgets would go under `me/` when they exist.

The deliverable is a sorting plan in the chat, or in the PR that `ingest-notes` opens. Write no wiki files and change no source files. Never put a credential or a sensitive value in the plan: name such sources by title and field only.

## Steps

1. List every source file with its title, date, and labels or page path. Count them per folder.
   Done when the list covers every file in the source folders named by the user.
2. Triage each source with *Drop or keep?*. Record each drop with its reason (credential, sensitive, one-off, empty, template).
   Done when every source is kept or dropped with a reason.
3. Group the kept sources by subject, not by tool, label, or workspace. For each group, search the wiki for an existing canonical note (by topic and by every URL) and choose merge or create; give each new note a descriptive title and path from *Where does it go?*. A source that adds only one link is never its own note: assign it to the closest broader note or the matching bookmarks list.
   Done when every kept source belongs to exactly one primary topic with a destination note, and secondary topics are noted as cross-links.
4. Collect flags: placement (two areas or none), sensitivity (third parties, personal data, omissions), unclear wording, and structure questions (a new folder, a split, a long list note, a note that would hold a single link).
   Done when every borderline case has a flag.
5. Return the plan: a tree of destination notes with their sources, the drop list, and the flags.
   Done when the plan is shown to the user or handed to `ingest-notes`.
