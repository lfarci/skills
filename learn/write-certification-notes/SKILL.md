---
name: write-certification-notes
description: Create, update, or audit concise official-source module notes for any certification.
version: 0.1.0
license: MIT
metadata:
  hermes:
    tags: [learn, certifications]
    category: learn
    related_skills: [walk-through-certification-module, quiz-certification-knowledge, triage-certification-resources]
---

# Write certification notes

When the learner wants to add, update, correct, refresh, or audit module reference notes, keep them short, original, current, and useful for later retrieval. They help someone make a decision; they are not a transcript of the course and they do not prove mastery.

This skill is for any exam. Confirm the exam if it is not clear. For file locations in `lfarci/notes`, see the Learn section of this repository's [README](../../README.md#learn). To teach a module page by page, use `walk-through-certification-module`. To quiz the learner, use `quiz-certification-knowledge`.

Reference notes stay in the exam's subject-knowledge folder (in `lfarci/notes`, under `wiki/tech/certifications/<exam>/modules/`). Keep readiness evidence in the study plan and mistakes in the review log — never mix those into a reference note.

## Steps

1. Read the area `AGENTS.md`, the modules index, and the target note. For a new note, also look at two or three existing notes and follow their layout if it is already consistent. Confirm the operation (create, targeted update, source refresh, audit, or index update) and the filename pattern (`NN-short-topic.md`). Official course pages, the official study guide, and official product docs are the authority. Recheck them before changing product behaviour, page lists, domain mappings, URLs, or time-sensitive facts. If a claim has no official source, leave it out or mark it as an open question.
   Done when the target, the official sources, and the layout to follow are known.

2. Keep a hard line between reference and evidence. Reference notes describe concepts, decision rules, boundaries, failure modes, and official sources. Record scores, completion dates, and demonstrated strengths only when the learner gives evidence or asks to log the session — and put them in the study plan or review log, not in the module note. Move learner-authored recall prompts, worksheets, or personal experiments to the practice area; do not delete them. Use original wording. Never copy a lesson or an assessment. Keep secrets and account data out of the workspace.
   Done when it is clear what belongs in the note and what belongs in the study plan or review log.

3. For a new note, or when refreshing structure, use this layout unless the workspace already uses a different established one. Keep headings unnumbered; the filename and index provide the order. Do not add other level-two sections.

   ```md
   # <official module title>

   [Official module](<official module URL>)

   ## Overview

   <One short paragraph: the module's purpose, its setting, and the main decision model.>

   ## Study objectives

   **Primary study-guide domain:** *<domain>* (**<published weight>**).

   This module supports the following exam skills:

   - **<skill area>:** <short, paraphrased capability and boundary>.

   ## Pages

   ### [<official page title>](<official page URL>)

   - <Two to four short, original bullets: the core model, a distinction or enforcement point, and a boundary or failure mode.>

   ## References

   ### Official training

   - [<module title>](<module URL>)
   - [<official study guide>](<URL>)

   ### Official product docs linked by the module

   - [<official document>](<URL>)
   ```

   For each substantive page, use the official title and URL as a heading. Write two to four bullets on what the learner must be able to decide or distinguish: the central mechanism, a precise difference (authority, scope, timing, trust, or enforcement), what actually enforces the outcome, a realistic failure and recovery, or the vendor surface that expresses it. Use a shorter summary for intro and wrap-up pages. For a knowledge check or exercise, describe its purpose and include a result only when it is evidenced. Do not invent completion, scores, or dates.
   Done when the note matches the layout and every page bullet is original and source-backed.

4. For a small correction, change only the affected bullets and links, and keep nearby accurate text. For an audit, fix only real defects: title, link, and official URL agree; the four sections are present and in order; study objectives use a current official domain and weight; page headings use official URLs in the current order; bullets do not claim completion without evidence; the index lists every module once, in numeric order. Recheck the official study guide before changing domain names or weights. If a product claim may be stale and cannot be verified, remove or qualify it rather than guessing.
   Done when the requested create, update, or audit is finished and unofficial claims are gone or flagged.

5. Say which files changed, what kind of work was done, and whether official sources were rechecked. If learner evidence was involved, say exactly what was recorded and why. Mention remaining uncertainty; do not imply the module or exam domain is complete just because the note exists.
   Done when the completion report is delivered.
