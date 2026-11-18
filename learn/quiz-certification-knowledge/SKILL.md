---
name: quiz-certification-knowledge
description: Run original, exam-oriented knowledge checks and scenario quizzes for any certification.
version: 0.1.0
license: MIT
metadata:
  hermes:
    tags: [learn, certifications]
    category: learn
    related_skills: [walk-through-certification-module, write-certification-notes, triage-certification-resources]
---

# Quiz certification knowledge

When the learner wants a quiz, a self-test, practice questions, or a check of a weak area, run original retrieval practice. The aim is exam readiness, not memorizing answer letters or copying lessons.

This skill is for any exam. Confirm the exam if it is not clear. For file locations in `lfarci/notes`, see the Learn section of this repository's [README](../../README.md#learn). Recheck the current official study guide before changing domain mappings or judging readiness. Prefer official vendor docs (Microsoft Learn MCP `microsoft_docs_search` / `microsoft_docs_fetch` when the exam is a Microsoft or GitHub credential).

To teach a page and then ask one question, use `walk-through-certification-module`. To find external practice tests, use `triage-certification-resources`.

## Steps

1. Before any question, ask how many questions they want (short quiz, timed mixed test, or a custom number) and whether to focus on a module, exam domain, or weak area. For a mixed test, follow official domain weights as closely as the count allows. Wait for the answer. Ask one question at a time unless they want a full set on screen.

   If they ask for an exam-style, timed, or closed-notes test, use **exam simulation mode**: no hints, no feedback, and no answer key between items; grade only when they finish or stop. Otherwise use coaching mode: ask for reasoning and correct mistakes at once. If they later ask for feedback after each question, switch for the rest of the session.
   Done when count, focus, and mode are agreed.

2. Read the study plan, review log, personal context, and any area `AGENTS.md` that affect advice. Recheck the official study guide. Official docs are the authority; personal notes are context, not proof of current product behaviour. Use the review log to find weak spots, but write a **new** scenario that tests the same idea in a different setting. For a small set, rotate domains across sessions rather than pretending exact official weights.
   Done when the official blueprint, sources, and coverage plan are in hand.

3. Write **original** questions. Never use recalled exam questions, dumps, or copied lesson quizzes. Prefer realistic work scenarios with trade-offs, unclear information, or failure modes. Vary the form: best design, missing control, safe sequence, root cause, compare two designs, interpret evidence, smallest useful fix. Add vendor-specific detail when the exam needs it (for a GitHub exam: token scope, branch rules, MCP allowlists, routing a review versus requiring one).

   Shuffle question order and the position of the correct option. Avoid long runs of the same letter, and do not tell the learner the position plan. Keep options similar in length and tone. Every wrong option should be plausible and tied to a common mistake. Difficulty must come from a real boundary (trust, scope, timing, enforcement, leftover risk), not from missing facts, double negatives, or one option that lists more safeguards than the others. Use “select all that apply” only when each choice can be judged on its own, and explain the scoring first. Do not reveal the answer in the question.
   Done when the next item is original, fair, and answer-hidden.

4. In coaching mode, ask for a reason, not only a letter. After each answer: say if it is correct, incomplete, or wrong; point out sound reasoning and hidden assumptions; name the official source; explain why the tempting wrong options fail. If the answer is wrong or incomplete, correct it at once (what they assumed, why that option fails, the right model) and ask one short follow-up before the next scored question. If the answer is right, keep feedback short. In exam simulation mode, take the selected option with no comment and move on.
   Done when the agreed count is reached or the learner stops, with no answer shown early.

5. Give one short report for both short quizzes and full tests: score and how sound the reasoning was; results by official domain, marking untested domains as untested; strengths; remaining mistakes; a cautious label (`Developing`, `Strong for assessed topics`, or `Needs targeted review`) — a short quiz cannot prove full-exam readiness; one or two next steps. Do not invent a scaled exam score, and do not say a practice percentage predicts a pass.
   Done when the report is delivered.

6. Log a finished session (not an abandoned one with no answers) in the review log: one dated practice-history row, plus a row for each important miss (wrong assumption, corrected model, official source, how to recheck). If the same miss happens again, note the repeat; do not add a duplicate row. Update the study-plan readiness table only after a meaningful body of evidence (a closed-notes mixed test, or repeated improvement in a domain) — never after one short quiz. Do not paste full question text or every correct answer. Make the log after the report; do not change study records just because a quiz ran.
   Done when evidence is recorded precisely, or left alone when there is nothing to record.
