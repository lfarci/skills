---
name: save-resource
description: Save a link or resource list to keep as lab issues.
version: 0.2.0
license: MIT
metadata:
  hermes:
    tags: [lab, web, github]
    category: lab
    related_skills: [create-lab-issue, research-topic, split-lab-issue]
    requires_toolsets: [web]
---

# Save resource

When the user sends a link to keep (article, post, repo, short link, or a page that lists resources), resolve it first, then file issues with `create-lab-issue`. Tools for this skill: `web_extract` and `web_search`, then the GitHub MCP tools that skill names. Terminal and `gh` stay unused.

The deliverable is issues in the lab repo (for example `lfarci/notes`). Write no files. The chat reply is one short line and the issue link (one line per issue if several concerns were filed), not a list of links. Use `research-topic` when the user wants a question investigated, not only a link kept.

## Steps

1. Fetch the URL with `web_extract`. Expand short links (for example `lnkd.in`) to the canonical destination before deciding what to file.
   Done when the canonical URL is known and its content has been extracted.
2. Prefer the official vendor source (docs, repo, or product page) over a secondary write-up or aggregator. If the page is a mirror or recap, extract again from the official URL.
   Done when the filed source is the official page, or no official page exists.
3. If the page lists several resources, extract each direct URL, resolve those the same way, and split by *concern* — one issue per concern.
   Done when every distinct concern has its own canonical URL and a short account of what it is.
4. If extract is thin, use `web_search` only to find a better canonical URL, then extract again. Stick to facts the page supports.
   Done when the extract is enough to draft the issue, or a better official URL has been extracted.
5. File each concern with `create-lab-issue`.
   Done when every concern has a filed issue, and the reply is one short line plus link per issue.
