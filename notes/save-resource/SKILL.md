---
name: save-resource
description: Save a link into notes or a watch issue.
version: 0.1.0
license: MIT
metadata:
  hermes:
    tags: [notes, web, github]
    category: notes
    related_skills: [notes-issue, notes-hierarchy]
    requires_toolsets: [web]
---

# Save resource

Use this when the user sends a link, article, repo, or similar resource to keep. Prefer a Markdown note in the notes repo (for example `lfarci/notes`). Open a watch issue only when they want to track follow-up work. Use `web_extract` / `web_search` plus the GitHub MCP (`get_file_contents`, `create_or_update_file`, `search_issues`, `issue_read`, `issue_write`, `sub_issue_write`). Do not use `gh` or the terminal. Ask before writing.

## Where it goes

- Default file location: `projects/`. Use `career/` only for professional profile, brand, or job-search material.
- Never create a note at the repo root (only `README.md` and `TODO.md` belong there). Do not leave named notes in `inbox/`.
- Nested folders only when one effort already has several files. Otherwise a single file at `projects/` (or an existing pile) is enough.
- For a saved link, keep the note short. Do not invent a project plan.
- If they want to "keep an eye on it" or try it later, also open a **Task** under the matching Experiment (see `notes-issue` and `notes-hierarchy`), and link the note.

## Note shape

1. Title in sentence case; no emoji.
2. Optional short TL;DR (2–3 bullets).
3. Brief summary of what it is and why it matters. Do not copy long passages.
4. End with **References** (or **Further reading**) and the canonical URL. Use relative Markdown links to other notes, never `[[wiki links]]`.

File names are sentence-case or short descriptive slugs, consistent with nearby files (for example `projects/topic-name.md`).

## Steps

1. Fetch the page with `web_extract`. If extract is thin, use `web_search` only to locate a better canonical URL, then extract again. Do not invent details the page does not support.
2. Search existing notes (`get_file_contents` / path guesses under `projects/` and `career/`) and issues (`search_issues`) so you append or cross-link instead of duplicating.
3. Decide: update an existing note, create a new note, and/or open a watch Task. Show the user the path, a short draft, and any proposed issue (title, parent, body). Wait for a yes.
4. Write the file with `create_or_update_file` on the notes repo's default branch (usually `main`). If the file already exists, call `get_file_contents` first and pass its `sha` on the update. Commit message like `Add note on <topic>.`
5. If a watch issue is wanted, follow `notes-issue` (draft, duplicate check, ask) and `notes-hierarchy` (attach to the right Experiment). Link the note in the issue and the issue in the note.
6. Report the file path and, if any, the issue number.

## Pitfalls

- Updating without the current `sha` will fail or clobber; always re-read before `create_or_update_file`.
- Do not paste the full article into the repo or the issue.
- Career facts and salary material belong under `career/` and must not be invented.

## Verification

The note exists at the agreed path, summarizes the source with a reference link, and any watch issue is a Task under the right Experiment and points at the note.
