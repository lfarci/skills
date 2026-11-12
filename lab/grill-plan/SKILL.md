---
name: grill-plan
description: Grill a lab plan, Idea, or Experiment until it is settled.
version: 0.1.0
license: MIT
metadata:
  hermes:
    tags: [lab, github, issues]
    category: lab
    related_skills: [create-lab-issue, split-lab-issue, research-topic]
---

# Grill plan

Interview the user relentlessly about a plan, Idea, or Experiment in the lab repo (for example `lfarci/notes`) until every branch of the design tree is resolved. Then offer to file the outcome with `create-lab-issue` or `split-lab-issue`. Do not file, and do not otherwise act, until the user confirms a shared understanding. Look up facts with `web_search` / `web_extract` or `issue_read` / `search_issues`; do not ask the user for anything those tools can answer. Terminal and `gh` stay unused.

Inspired by Matt Pocock's [grilling](https://github.com/mattpocock/skills/blob/main/skills/productivity/grilling/SKILL.md).

## Steps

1. Name the target: the plan, Idea, or Experiment being settled, including any existing issue read with `issue_read`. Map it as a design tree: every decision branches into the decisions that hang off it.
   Done when the target is named and the first frontier (questions whose prerequisites are already settled) is listed.
2. Work the tree in rounds. In each round, ask the whole frontier: number each question, give a recommended answer, and word the question so "yes" accepts that recommendation. Wait for the user's answers before the next round. A question that depends on another still open in this round belongs to a later round.
   Format:

   ```
   ❓ **Q1** - **<title>**: <question>

   ➡️ <recommended answer>
   ```

   Done when the frontier is empty: every branch visited, nothing left silently assumed.
3. Summarize the settled decisions and confirm that you have reached a shared understanding. Stop here if the user is not ready to file.
   Done when the user has confirmed the summary, or has asked to stop without filing.
4. Offer to file: one issue via `create-lab-issue`, or several concerns via `split-lab-issue`. Follow that skill (draft, ask, tools, board-field reminder). Use `research-topic` first if a settled point still needs primary-source legwork.
   Done when the user has declined, or the approved issues exist and the user has the links.
