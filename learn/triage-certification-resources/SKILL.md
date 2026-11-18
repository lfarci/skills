---
name: triage-certification-resources
description: Find, evaluate, and recommend official and original certification-prep resources; exclude exam dumps.
version: 0.1.0
license: MIT
metadata:
  hermes:
    tags: [learn, certifications, web]
    category: learn
    related_skills: [quiz-certification-knowledge, write-certification-notes, walk-through-certification-module, research-topic, save-resource]
    requires_toolsets: [web]
---

# Triage certification resources

When the learner wants to find, compare, shortlist, buy, or revisit exam-prep resources (practice tests, labs, courses, question banks, study guides), pick resources that give real evidence of readiness. Do not collect the longest list of links. Never recommend an exam dump.

This skill is for any exam. Confirm the exam if it is not clear. For file locations in `lfarci/notes`, see the Learn section of this repository's [README](../../README.md#learn).

If the user wants a general question researched and filed as a lab issue, use `research-topic`. If they only want a link kept as a lab issue, use `save-resource`.

## Steps

1. Confirm the exam, the kind of resource (diagnostic, full mock, targeted drills, lab, course, or reference), the learner's stage (first exposure, repairing a weak area, or final readiness), and any limits (budget, language, time, privacy). Ask only when a missing detail would change the advice; otherwise state the assumption and continue. Read the official source list, the current official study guide, and — if the advice depends on known gaps — the study plan and review log. Recheck dates, prices, and exam status; an old check is not current evidence.
   Done when the exam, the decision, and the official baseline are known.

2. Record what the official pages actually offer. A **practice assessment** tests knowledge. An **exam sandbox** shows the delivery interface. A **study guide** defines scope; it does not measure readiness. A **course assessment** measures module learning, not necessarily mixed-exam readiness. If you cannot find an official practice assessment, say you could not find one on the current official pages — do not claim none exists anywhere.
   Done when official offerings are listed and labelled correctly.

3. Search for free and paid options (exam code plus terms such as `practice assessment`, `mock exam`, `labs`, and exclusions such as `-dumps`). Search results are leads, not evidence: open the pages. Look for independent reviews, not only the vendor's own testimonials. Classify each candidate **before** judging price or convenience:

   | Class | Signals | Treatment |
   | --- | --- | --- |
   | Official | Hosted or provided by the exam owner | Authority for scope, format, and current facts |
   | Original practice | Says questions are original and based on public objectives or docs | Eligible to evaluate |
   | Unclear origin | “Realistic” or “exam-like” with no source | Inspect carefully; trust it less |
   | Exam dump | “Real,” “actual,” “recalled,” “previous exam,” “100% verified,” guaranteed pass, or updates based on what candidates saw | Exclude |

   Do not reproduce, buy, save, or send the learner to recalled live-exam content. Say briefly that dumps undermine exam integrity and are often wrong.
   Done when every candidate is classified and dumps are excluded.

4. Judge eligible resources on: coverage of the official domains, the quality of visible samples (not the claimed question count), accuracy against current official facts, access and price, and independent reviews. Strong evidence looks like realistic scenarios, artifacts (logs, configs, traces), plausible wrong answers, and explanations for why those answers fail. Easy definition quizzes can help memory; they are not final readiness evidence. If a resource gets a basic official fact wrong, lower trust in it. Prefer a free sample before paying when quality is not independently confirmed.
   Done when each shortlisted resource has a clear judgment and a check date.

5. Lead with the decision: the official baseline; a shortlist with strengths, limits, and confidence; what to avoid (without amplifying dump sites); what to try first, when to pay, and what result should trigger the next step. Label third-party resources as unofficial. A high score on a bank the learner has already seen many times is not proof they will pass.
   Done when the learner has a clear sequence they can follow.

6. Save the research only if asked. Add a short, dated entry to the official source list, and keep official sources distinct from unofficial ones. Note access, quality, freshness, and integrity caveats — not just the URL. Update the review log only for a real misconception or learner evidence. Do not treat a commercial practice score as mastery without the learner's own reasoning.
   Done when nothing was saved unless the learner asked, and any saved entry is dated and caveated.
