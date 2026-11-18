---
name: walk-through-certification-module
description: Teach an official certification module one page at a time, then check understanding with one question.
version: 0.1.0
license: MIT
metadata:
  hermes:
    tags: [learn, certifications]
    category: learn
    related_skills: [write-certification-notes, quiz-certification-knowledge, triage-certification-resources]
---

# Walk through a certification module

When the learner wants to study, revisit, or walk through an official module or page, teach it one page at a time. The main goal is that they understand and remember the page, not that they finish it. Explain first; then ask one focused question. A short paraphrase is not enough if they still cannot explain the mechanism or choose between two plausible controls.

This skill is for any exam. Confirm the exam and the module if they are not clear. If no module is named, start with the first one and say so. For file locations in `lfarci/notes`, see the Learn section of this repository's [README](../../README.md#learn). Recheck the official study guide before changing domain mappings or judging readiness. Prefer official vendor docs (Microsoft Learn MCP `microsoft_docs_search` / `microsoft_docs_fetch` when the official path is on Microsoft Learn).

For a quiz or mixed test, use `quiz-certification-knowledge`. To write or fix a module reference note, use `write-certification-notes` — do not repeat that layout here. Edit notes only when the learner asks to record the session.

## Steps

1. Read any area `AGENTS.md` and, when advice depends on progress, the study plan, review log, and personal context. Find the official module URL and the current study-guide mapping in the source list. Fetch the module overview and the current page from official docs. Read enough of the surrounding module to know why the page sits where it does; do not infer the point from the title alone. For product behaviour that may have changed, check current official product docs and keep that distinct from the course's conceptual model.
   Done when the exam, module, official page, and domain mapping are known.

2. At the start of a module, ask one short closed-notes question or a self-rating to see what they already know. Use the answer to calibrate terms and examples. Do not hold back the walkthrough unless they want a quiz-led session.
   Done when a baseline is taken, or skipped only if they already asked to start teaching.

3. Keep each turn on one page. Start with a compact **page map**: purpose, learning objective, place in the module, and the relevant exam domain (as context, not proof that the page covers the whole domain). Then teach, in your own words:

   - the central idea, in plain language, before new terms;
   - every concept needed to reason about the page: what it is, why it exists, and how it relates to the others;
   - how it works (sequence, rule, or cause and effect), with a small real example;
   - three to seven facts, rules, distinctions, or caveats to keep;
   - why it matters for a design choice, an operational outcome, or an exam objective.

   Start with the intuitive model, then the precise technical model, then the practical effect. Also make the decision-relevant details explicit: where the rule stops, what actually enforces it (not only a config file, warning, or prompt), a realistic failure and how to recover, and the vendor surface that expresses it. If the page has a diagram, workflow, or config, explain the moving parts. Usually develop four to six insights; for a dense page, continue on a later turn rather than hiding a key boundary to stay short. Do not reduce the page to “traps” only — first teach the positive design knowledge.
   Done when the learner has enough explanation to answer a question on this page without already knowing the lesson.

4. Give one realistic scenario with a real trade-off or risk, and enough facts to decide (who is trusted, who has authority, what is at stake). Ask one retrieval question on the page's hardest distinction, and wait. Do not reveal the answer in advance. Then critique the answer: sound reasoning, hidden assumptions, missing boundaries, leftover risk, and controls that do not actually enforce the stated policy. If they are wrong or incomplete, explain the right model and ask one short follow-up. Close the page with one or two sentences on what to reuse later and which mix-up to avoid. Only then go to the next page, in official order, including knowledge checks and the summary.

   Official knowledge-check items also go one at a time, after the relevant ideas have been taught, and need a reason, not just a letter. A high score right after teaching is short-term memory, not mastery.
   Done when the page ends with a carry-forward insight and the learner has answered the check.

5. After the module's summary and a last applied scenario, report strengths, remaining gaps, and what that means for the exam domain. Name two or three insights worth later retrieval. Do not call the module mastered because its pages were finished. If they asked to record the session, update only the relevant progress and review files with sources and precise evidence, and hand module-note structure to `write-certification-notes`. Otherwise leave files unchanged.
   Done when the close is delivered and files are unchanged unless recording was requested.
