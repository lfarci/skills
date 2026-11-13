---
name: grill-idea
description: Grill a lab Idea until it is scoped or not planned.
version: 0.1.0
license: MIT
metadata:
  hermes:
    tags: [lab, github, issues]
    category: lab
    related_skills: [create-lab-issue, split-lab-issue, research-topic]
---

# Grill idea

Interview the user relentlessly about an Idea in the lab repo (for example `lfarci/notes`) — or an Experiment they want scoped — until the **Idea scope** below is met, or the Idea is not worth pursuing. Then offer to file or update the issue with `create-lab-issue`, or to split concerns with `split-lab-issue`. Do not file, close, or otherwise write until the user confirms. Look up facts with `web_search` / `web_extract` or `issue_read` / `search_issues`; do not ask the user for anything those tools can answer. Terminal and `gh` stay unused.

This skill is the source of truth for **Idea scope**. `create-lab-issue` and `review-backlog` point here when they file or review an Idea.

Inspired by Matt Pocock's [grilling](https://github.com/mattpocock/skills/blob/main/skills/productivity/grilling/SKILL.md).

## Idea scope

An Idea is well scoped when all of the following are explicit:

- **Goal**: what to explore or improve, and why
- **Outcome**: the definition of done
- **Boundaries**: what is out of scope
- **Next step**: the smallest next step, or a first Experiment, to decide whether the Idea is worth pursuing

If the Idea is not worth pursuing, propose a comment that explains why and, on confirmation, close the issue as **not planned** (see **Closing issues** in `create-lab-issue`). Never delete issues.

## Steps

1. Name the Idea or Experiment, including any existing issue read with `issue_read`. Map it as a design tree: every decision branches into the decisions that hang off it.
   Done when the target is named and the first frontier (questions whose prerequisites are already settled) is listed.
2. Work the tree in rounds, aimed at filling **Idea scope** (or at deciding the Idea is not worth pursuing). In each round, ask the whole frontier: number each question, give a recommended answer, and word the question so "yes" accepts that recommendation. Wait for the user's answers before the next round. A question that depends on another still open in this round belongs to a later round.
   Format:

   ```
   ❓ **Q1** - **<title>**: <question>

   ➡️ <recommended answer>
   ```

   Done when the frontier is empty: every branch visited, nothing left silently assumed, and either the four scope fields are explicit or the user has said the Idea is not worth pursuing.
3. Summarize. If the Idea is not worth pursuing, show the proposed comment (why) and the close as **not planned**. Otherwise show the scoped Goal, Outcome, Boundaries, and Next step, and confirm a shared understanding. Stop here if the user is not ready to write.
   Done when the user has confirmed the summary, or has asked to stop without writing.
4. On confirmation, either close as **not planned** with the approved comment (`add_issue_comment`, then `issue_write`), or file or update the issue so its body meets **Idea scope**, using `create-lab-issue` (and `split-lab-issue` if there are several concerns). Use `research-topic` first if a settled point still needs primary-source legwork. Include the board-field reminder in `create-lab-issue` when an issue is created or left open.
   Done when the approved close or the scoped issue is in place, or the user declined to write.
