/pstack:poteto-mode

# Phase 1 — Constrain (gate G1)

## Preconditions
- Read `CLAUDE.md`, `docs/STATUS.md` and `docs/DECISION_LOG.md`.
- `docs/DECISION_LOG.md` must contain an **APPROVED** G0 entry for the current PRD version. If it does not, STOP and report what is missing.
- Then read `docs/PRD.md`, `docs/NFR.md` and `docs/CONSTRAINTS.md`.

## Tasks
Define measurable non-functional requirements and engineering constraints:
1. **Load and performance:** users, latency, availability, capacity. Only use numbers grounded in real expectations or measurements; otherwise write `TBD (owner, date)` and propose how to measure.
2. **Identity and data:** authentication, authorization, multi-tenancy (if relevant), privacy, data classification, data residency.
3. **Operations:** on-prem / cloud / hybrid options, backup/restore, RPO/RTO, monitoring, operational ownership.
4. **Cost and dependencies:** cost ceilings, vendor/dependency constraints, security posture.
5. **Verification strategy:** which kinds of checks are required (tests, lint/typecheck, secret scan, dependency scan, CI). Leave the actual commands `TBD` until the stack is chosen.
6. Ask decisive questions in short rounds (at most 4) using the question tool where options are clear.

Update `docs/NFR.md` and `docs/CONSTRAINTS.md`. List unresolved high-impact questions and cheap experiments that would answer them.

## Hard limits
No implementation, no stack selection, no fictional lint/test commands. Do not commit.

## Finish
1. Walk through the **G1 checklist** in `docs/WORKFLOW.md`: Met / Not met / TBD with evidence.
2. Update `docs/STATUS.md`; propose a draft G1 entry for `docs/DECISION_LOG.md` (status `Draft`, approver `TBD`).
3. Suggest `/plannotator-annotate docs/NFR.md` (and `docs/CONSTRAINTS.md`) for my review.
4. Reply using the Delivery format in `CLAUDE.md`, then stop.
