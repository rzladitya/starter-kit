# Decision Log / Approval Ledger

> THIS FILE STARTS WITH **NO APPROVAL**. Agent drafts do not count as human approval. Only the owner or explicitly authorized reviewer may confirm a decision. Record the actual user confirmation, not an inferred one.

| ID | Date | Phase | Decision | Evidence/review link | Approver | Status |
|---|---|---|---|---|---|---|
| D-000 | [YYYY-MM-DD] | 0 | Starter kit initialized; no architecture or coding authorization yet | README | [owner TBD] | Draft |

## Required approval record format
```text
ID: D-001
Date: YYYY-MM-DD
Phase: 0 / 1 / 2 / 3 / 4
Decision: Approve PRD vX.Y (or architecture, implementation, explicit code change)
Scope authorized: [clear boundaries]
Artifacts reviewed: [file paths + versions/commit]
Review method: Plannotator / explicit message / meeting note
Approver: [human name or role]
Status: APPROVED / CHANGES REQUESTED / REJECTED
Open exceptions: [IDs or none]
```

## Rules
- Update `STATUS.md` when a phase is approved; do not move state on inferred approvals.
- A Plan Mode `ExitPlanMode` review is a review event, not a guarantee of approval. Record accepted decision explicitly.
- New budget, data residency, identity, security, or irreversible decisions require a new record.
- Architecture approval does not automatically authorize production deployment.
