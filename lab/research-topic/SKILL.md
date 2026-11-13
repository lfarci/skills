---
name: research-topic
description: Research a topic against official sources and file it.
version: 0.1.0
license: MIT
metadata:
  hermes:
    tags: [lab, web, github]
    category: lab
    related_skills: [create-lab-issue, save-resource, grill-idea]
    requires_toolsets: [web]
---

# Research topic

Investigate a question against official, primary sources, then file the findings as an issue or a comment in the lab repo (for example `lfarci/notes`). Write no files. Use `save-resource` when the user only wants a link kept. Follow `create-lab-issue` for titles, bodies, parents, tools, asking before writes, and the board-field reminder. Tools for this skill: `web_extract` and `web_search`, then the GitHub MCP tools `create-lab-issue` names. Terminal and `gh` stay unused.

Inspired by Matt Pocock's [research](https://github.com/mattpocock/skills/blob/main/skills/engineering/research/SKILL.md).

## Steps

1. Restate the question and the kind of answer that would settle it. Search the lab repo with `search_issues` for existing work on the same question.
   Done when the question is explicit, and any existing issue or comment is in hand.
2. Investigate against official or primary sources (vendor docs, the project's own repo or spec, first-party APIs), not a secondary write-up. Fetch each candidate with `web_extract`; use `web_search` only to locate a better canonical URL, then extract again. Follow every claim back to the source that owns it.
   Done when each finding has a primary-source URL, or it is marked unsupported.
3. Draft a short, cited write-up: the answer, the sources, what is still unknown, and whether this is a new issue or a comment on an existing one. One *concern* per issue; several concerns become several issues. Show the draft and wait for a yes.
   Done when the user has approved the draft and the target (new issue vs comment).
4. File with `create-lab-issue`, or post the approved write-up as a comment with `add_issue_comment`. Reply with one short line and the link, plus the board-field reminder when a new issue was created.
   Done when the findings live on the agreed issue or comment, with citations, and no file was written.
