---
name: rag-eval
description: Add or improve test questions in eval/questions.md and evaluate Sagittarius RAG retrieval and answers against them. Use when asked to build the test set, measure quality, compare changes (chunking, prompts, models), or log an evaluation run.
---

# RAG evaluation

The test set is `eval/questions.md`. Success targets are in `Docs/Project-Management/Initiation-phase/Clarify/Clarify.md` §6; metrics are in `Docs/Project-Management/Initiation-phase/Discover/Discover.md` §6.3.

## Adding questions

1. Prefer **real questions** (`Docs/Project-Management/Initiation-phase/Sub-init/Common-questions-newcomers-ask.md`). Keep wording natural, as users would type it.
2. For each, fill: expected short answer, expected source `file#section` (from the KB, checked by reading it), type.
3. Include **unanswerable** questions (answer must be "I don't know") and some **multi-file** ones. Aim for 20+ total.
4. Never invent an expected answer; if the KB does not clearly contain it, mark `TODO` or make it an unanswerable question.

## Running an evaluation

Evaluate **retrieval first**, then generation.

1. **Retrieval:** for each question, is the expected source in the top-k chunks? Record hit rate @k.
2. **Generation:** grade each answer 0/1/2 (see grading in `eval/questions.md`); check the citation points to the right file and section.
3. **Safety:** for unanswerable questions, did the system say "I don't know" and avoid inventing?
4. Record latency and cost per question if available.
5. Append one row to the **Run log** (date, what changed, metrics, notes) and update "Last result" per question.

## Comparing changes

Change one thing at a time (chunk size, template, retrieval, prompt, model). Re-run the full set and compare with the previous run-log row. Report which questions got better or worse, not only averages. Do not claim an improvement without the numbers.

## Rules

- Only run against content the user allows to leave the machine; privacy status is **unknown** (see Clarify §5.1, privacy constraint). Ask before using any external LLM or embedding API.
- If the RAG does not exist yet, help with the question set only.
