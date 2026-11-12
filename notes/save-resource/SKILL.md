---
name: save-resource
description: Resolve a link and file it as a notes issue.
version: 0.1.0
license: MIT
metadata:
  hermes:
    tags: [notes, web, github]
    category: notes
    related_skills: [create-notes-issue]
    requires_toolsets: [web]
---

# Save resource

Use this when the user sends a link (article, post, repo, or similar) to keep. Do not write files. Open one focused issue per concern in the notes repo (for example `lfarci/notes`) by following `create-notes-issue`. Use `web_extract` / `web_search` plus the GitHub MCP tools named in that skill. Do not use `gh` or the terminal. Do not dump links in chat.

## Resolve the link first

1. Fetch the URL with `web_extract`. Expand short links (for example `lnkd.in`) to the canonical destination before deciding what to file.
2. Prefer official vendor sources (docs, repo, or product page) over a secondary write-up or aggregator. If the page is a mirror or recap, extract again from the official URL.
3. If the page lists several resources, extract each direct URL, resolve those too, and treat each distinct concern separately — one issue per concern, not one issue that lists everything.
4. If extract is thin, use `web_search` only to find a better canonical URL, then extract again. Do not invent details the page does not support.

## Then file it

Follow `create-notes-issue`: search for duplicates and a parent, default to a Task under the most relevant existing Idea or Experiment, draft the issue (what it is, source and direct links, why it matters, out of scope), ask before writing, then create, attach, and comment on the parent as that skill describes.

Reply with one short line and the issue link (or one line per issue if several concerns were filed). Remind the user to set Projects v2 fields, as in `create-notes-issue`. No files, and no link-dumping in the reply.

## Pitfalls

- Do not write Markdown (or any other) files into the notes repo.
- Do not paste a list of unresolved or raw short links into chat or into a single catch-all issue.
- Do not skip extract and file from the URL alone.
- Career, profile, or job-search material still belongs under the matching existing parent, not a new Idea by default.
