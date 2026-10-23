# Parked content from Clarify (not needed at the Clarify step)

Clarify only needs to explain *what the problem is*. The sections below were removed from Clarify.md; move them into Discover / Plan when needed.

## 5. Users and stakeholders

### 5.1 Users

| User type | What they need | How often |
|-----------|----------------|-----------|
| Members of the MAG project | Ask questions via chat/UI | Daily |
| KB authors (write / update `.md`) | To update the KB easily and know their change works with the RAG | End of day |
| KB maintainer / reviewer | Verifies AI-generated content | TBD |

**Real questions users ask.** Collect 5–10 real ones (plus a few the KB cannot answer) — they become the test set:
[Common questions](../Sub-init/Common-questions-newcomers-ask.md)

### 5.2 Stakeholder register

| Name | Role | Interest | Influence (H/M/L) | Responsibility |
|------|------|----------|-------------------|----------------|
| Nathan Tran | Developer (RAG tool, KB quality for RAG) | Deliver D1–D5 | TODO | TODO |
| TODO | Owner of the MAG project | Gets a working RAG for the MAG project | TODO | Defines what the RAG must provide |
| TODO | KB maintainer / reviewer | Correct KB | TODO | Verifies KB content |
| TODO | Security / management | No data leaks | TODO | Decides what data can go to external LLMs |
| TODO | KB authors | Easy updates | TODO | Update the KB following the agreed way of working |

---

### 6.3 Dependencies

| ID | Depends on | Needed for | Owner | Status |
|----|-----------|------------|-------|--------|
| DEP1 | Decision on whether KB content may go to an external LLM / embedding API | Choice of stack, O1 | Security / management (TODO) | Open |
| DEP2 | Clarification of the MAG project's needs (users, interface, deadline) | Scope, O1 | MAG project owner (TODO) | Open |
| DEP3 | A person who verifies the KB | O2, trust in answers | TODO | Open |
| DEP4 | Hosting for the service and the index update | O1, O3 | TODO | Open |

---

### 7.2 What success looks like

Four scenarios after v1 ships (fill in with real names/numbers). They are written from the user's point of view and do not assume how the KB or the index is implemented.

**Scenario 1 — A normal day: edit, then ask**

> A KB author fixes a wrong step in `build.md` and commits it. They are told the change is fine for the RAG.
> Within the agreed time the index reflects it. Later a member of the MAG project asks the chat
> *"How do I build and flash the firmware?"*. In a few seconds they get a short answer with the
> corrected step and a link to `build.md#flash`. They ask *"What is the deadline for X?"* — it is
> not in the KB, so the tool says *"I couldn't find this in the KB"*. Nobody is misled.

**Scenario 2 — Unverified or conflicting content is not presented as fact**

> A member of the MAG project asks *"Which baud rate does the sensor use?"*. The answer exists only in an
> AI-generated file that no human has verified, and a second file says something different.
> The tool does not pick one silently. It answers with what it found, shows **both sources**, and states that
> one is **unverified** and that the files **disagree**. The member checks the sources, finds the right value,
> and reports the wrong file. The KB owner fixes it, and the next time the question is asked the answer is consistent.
> *Success: wrong or conflicting KB content is visible and gets corrected, instead of becoming a confident wrong answer.*

**Scenario 3 — Something breaks and the team knows**

> Overnight the index update fails (e.g. the LLM/embedding service is down or a file is malformed).
> In the morning members can still ask questions and get answers from the last good index, and the tool shows
> *"Index last updated: 2 days ago"*. The person on duty was notified when the update failed, reads the log, sees which
> file or service caused it, fixes it, and the next update succeeds. Nobody discovers weeks later that answers are stale.
> *Success: failures are noticed quickly, never silent, and do not take the whole service down.*

**Scenario 4 — A change to the approach is judged by evidence** *(for the team that builds the RAG)*

> The team tries a new way of splitting or preparing the KB. Before releasing it they run the test questions.
> The report shows the retrieval hit rate rose from 62% to 78%, with two questions getting worse, and which ones.
> They keep the change and note the two regressions. Months later a different change lowers the score; the same
> report catches it before users do.
> *Success: quality changes are measured against the test set, not judged by feeling.*

### 7.3 Success by level

| Level | What success looks like | How to measure | Target |
|-------|-------------------------|----------------|--------|
| Answer quality | Correct answers, with the right source file + section | Test set, manual grade | TODO e.g. ≥ 80% correct |
| Trust | Says "I don't know" when the KB has no answer; no invented facts | Unanswerable questions in test set | TODO e.g. 100% refuse, 0 hallucinated |
| Freshness | Index reflects the latest KB | Time from merge to searchable | TODO e.g. ≤ 24 h |
| KB quality | KB is good input for RAG; AI-generated content is verified | Retrieval hit rate on the test set; % verified | TODO e.g. hit rate ≥ X%; verified Y% |
| Ease of update | A member can update the KB without help | Time / steps for a first edit | TODO e.g. < 10 min, no special tools |
| Speed | Answer fast enough to be used | Latency per question | TODO e.g. < 10 s |
| Adoption | Members of the MAG project actually use it | Queries per week, distinct users | TODO |
| Cost | Affordable to run | LLM/hosting cost per month | TODO e.g. < $X/month |

### 7.4 Acceptance gate for v1 (must all be true)

- [ ] Test-set accuracy meets the target above
- [ ] Every answer shows its source
- [ ] "I don't know" works on the unanswerable questions
- [ ] The chosen way to keep the KB good for RAG is in place and works (TBD in Discover)
- [ ] The index update runs unattended and its result can be seen (log / status)
- [ ] No confidential data sent to a disallowed provider
- [ ] At least N real users tried it and gave feedback (TODO: N)

### 7.5 Signs it is NOT working (stop and rethink)

- Answers are often wrong, or cite the wrong file
- Answers are wrong because the **KB itself is wrong** (unverified AI content)
- Members find updating the KB too hard (rules, tooling) and stop doing it
- The index update fails silently and nobody notices
- Users stop using it after the first weeks

### 7.6 Review

At 2 weeks and 2 months after launch (TODO: owner), compare against the targets above and decide: keep, improve, or stop.

---

## 8. Risks and open issues

### 8.1 Risk register

Scoring: probability and impact are High / Medium / Low (3 / 2 / 1); score = probability × impact.
Probabilities are initial estimates to confirm with the team.

| ID | Risk | Probability | Impact | Score | Mitigation | Owner | Status |
|----|------|-------------|--------|-------|------------|-------|--------|
| R1 | KB is AI-generated and unverified → RAG gives wrong answers with citations | H | H | 9 | TODO (see G1, DEP3) | TODO | Open |
| R2 | Sensitive info leaks to an external LLM API | M | H | 6 | TODO (see DEP1) | TODO | Open |
| R3 | No RAG experience in team → wrong design, wasted time | H | H | 9 | TODO (spike, baseline first) | TODO | Open |
| R4 | Whatever KB rules or tooling we choose are too strict or complex → members stop updating the KB | M | M | 4 | TODO | TODO | Open |
| R5 | Index update fails silently → stale answers | M | M | 4 | TODO | TODO | Open |
| R6 | MAG project's needs unclear or change (e.g. API instead of chat) | M | M | 4 | TODO (see DEP2) | TODO | Open |

### 8.2 Open questions

| ID | Question | Impact | Owner | Due | Status |
|----|----------|--------|-------|-----|--------|
| Q1 | Can KB content be sent to an external LLM / embedding API? (cloud vs local) | High | TODO | TODO | Open |
| Q2 | What is the "MAG project", and what does it require from the RAG (users, interface, deadline)? | High | TODO | TODO | Open |
| Q3 | Who verifies the AI-generated KB, and how? | High | TODO | TODO | Open |
| Q4 | Which interface for the chat/UI (web, Slack, Teams…)? | Medium | TODO | TODO | Open |
| Q5 | Is any technology / framework mandated by the client or project owner, or is the choice ours (and who approves it)? | High | TODO | TODO | Open |
| Q6 | How big is the KB (files, size)? | Medium | TODO | TODO | Open |
| Q7 | Budget and hosting for the index update and the service? | Medium | TODO | TODO | Open |
| Q8 | Who owns the KB (and any KB rules) after v1? | Medium | TODO | TODO | Open |
| Q9 | What is the best way to make the KB good for RAG: template, restructuring, indexing-time processing, other? | High | TODO | TODO | Open (Discover §4.4) |
| Q10 | Is daily enough, or must the index update on every change? | Medium | TODO | TODO | Open |

### 8.3 Things we may be missing or misunderstanding

Check each one with the team. They are the points most likely to break the project if wrong.

1. **RAG quality is capped by KB quality.** A perfect RAG over a wrong KB gives confident wrong answers. Verification is part of the project, not a side task.
2. **KB structure affects retrieval, but a template is only one way to fix it.** Good chunking depends on structure (clear headings, one topic per section, metadata). Options include authoring rules, AI-assisted restructuring, or processing at indexing time. D2 and D1 must be designed together, and the approach is chosen from evidence in Discover.
3. **A scheduled rebuild is cheap only if incremental.** Re-embedding the whole KB each day costs time and money as it grows; re-index only files whose content changed.
4. **Daily is not the same as "up to date".** Between an edit and the next run, answers are stale. Decide if ≤ 24 h is acceptable or if re-index on merge is needed.
5. **Scope changed from "onboarding" to "RAG for a MAG project".** Success metrics about onboarding time no longer apply; the MAG project's real needs must be confirmed.
6. **Privacy decides the stack.** Cloud vs local changes the choice of LLM, embedding model, cost, and hardware. This is the first question to answer.
7. **Needs a test set, even without RAG experience.** Without real questions + expected sources you cannot tell if changes help or hurt.
8. **Operations are part of delivery.** Someone must watch the index update, handle failures, and manage API keys / costs.
9. **Do not over-build.** With no RAG experience, start with the smallest end-to-end version and grow it based on test results.

