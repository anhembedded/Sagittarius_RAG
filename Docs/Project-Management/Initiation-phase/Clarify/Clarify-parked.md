# Parked content from Clarify (not needed at the Clarify step)

Removed from Clarify.md because Clarify only needs to explain *what the problem is*. Move these into Discover / Plan when needed.
G* and DEP* IDs still exist in Clarify; R* and Q* only live here now.

## (was 5. Users and stakeholders

### (was 5.1 Users

| User type | What they need | How often |
|-----------|----------------|-----------|
| Members of the MAG project | Ask questions via chat/UI | Daily |
| KB authors (write / update `.md`) | To update the KB easily and know their change works with the RAG | End of day |
| KB maintainer / reviewer | Verifies AI-generated content | TBD |

**Real questions users ask.** Collect 5–10 real ones (plus a few the KB cannot answer) — they become the test set:
[Common questions](../Sub-init/Common-questions-newcomers-ask.md)

### (was 5.2 Stakeholder register

| Name | Role | Interest | Influence (H/M/L) | Responsibility |
|------|------|----------|-------------------|----------------|
| Nathan Tran | Developer (RAG tool, KB quality for RAG) | Deliver D1–D5 | TODO | TODO |
| TODO | Owner of the MAG project | Gets a working RAG for the MAG project | TODO | Defines what the RAG must provide |
| TODO | KB maintainer / reviewer | Correct KB | TODO | Verifies KB content |
| TODO | Security / management | No data leaks | TODO | Decides what data can go to external LLMs |
| TODO | KB authors | Easy updates | TODO | Update the KB following the agreed way of working |

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

