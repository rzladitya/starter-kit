# Architecture-first Workflow (Greenfield)

## Principles
- Discovery comes before stack selection. Architecture is chosen from product needs and NFRs, not personal habit.
- Every phase must produce reviewable artifacts, acceptance criteria, and evidence for decisions.
- A phase may include exploration or prototypes, but never mix them with production implementation.

> This file is the single source of truth for phase numbering and gate checklists. README, `CLAUDE.md` and `STATUS.md` follow it.

| Stage | Agent tasks | Deliverable | Stop / approval gate |
|---|---|---|---|
| 0. Discover | Interview + challenge assumptions | Brief, PRD, MVP scope, user journeys | **G0** — owner signs off scope |
| 1. Constrain | Define SLO/security, RTO/RPO, operations & cost caps | NFR, CONSTRAINTS | **G1** — tech/security agree on targets or TBD + owner |
| 2. Design | Compare 2–3 architectures when there is a real trade-off; define domain, components, sequences, data shapes | Architecture, Data Model, ADR | **G2** — ADRs Accepted |
| 3. Risk & Plan | Threat modeling, data governance, vertical slices, rollback | Threat Model, Implementation Plan | **G3** — human approves plan via Plannotator / recorded decision |
| 4. Scaffold | Minimal initialization after explicit approval | Project files, test harness, CI foundation | Build & smoke test actually run |
| 5. First slice | Smallest end-to-end UI/API/persistence path | Working feature, tests, docs, evidence | **G4** — independent review + Plannotator + CI |

## Gate checklist (Definition of Ready)

### G0 — Product gate (phase 0)
Target user, top 3 problems, in/out scope, success metrics, acceptance criteria.
- [ ] Primary user and top jobs-to-be-done are concrete.
- [ ] MVP has verifiable acceptance criteria.
- [ ] Non-goals and dependencies are explicit.
- [ ] Open questions have owners.

### G1 — Quality gate (phase 1)
Non-functional requirements have targets or an owned TBD; data classes, security stance, deployment preference.
- [ ] Deployment constraints, sensitive data policy, auth/access model captured.
- [ ] Target performance, capacity and uptime are measured or assigned for discovery.
- [ ] RTO/RPO and data retention requirements decided or owned as TBD.
- [ ] Cost assumptions trace to source or marked provisional.

### G2 — Architecture gate (phase 2)
Diagrams, dependencies, deployment view, data model, alternatives, ADRs.
- [ ] At least one simpler design considered, not overengineered.
- [ ] Component responsibilities and trust boundaries documented.
- [ ] Contract + domain shapes + failure modes documented.
- [ ] Significant tech choice has ADR with rejected alternatives.
- [ ] Testability, operability, rollback and migration reviewed.

### G3 — Implementation authorization (phase 3)
Plan approved by a human, decision log contains a specific authorization; `docs/STATUS.md` updated.
- [ ] Threat model critical issues resolved or explicitly blocked.
- [ ] `IMPLEMENTATION_PLAN.md` has a single, bounded first vertical slice.
- [ ] Native Plan Mode review (if used) has finished; feedback incorporated.
- [ ] Plannotator annotation review or explicit human review recorded.
- [ ] `DECISION_LOG.md` contains clear human APPROVED record for coding.

### G4 — Release gate (phase 5)
Relevant test/lint/typecheck/secrets/security checks actually ran; results and failures recorded.
- [ ] Tests, static checks, integration checks and security scans executed and reported.
- [ ] Diff reviewed using human review / `/plannotator-review`.
- [ ] Critical issue disposition recorded; no fake green checks.
- [ ] No unapproved merge/deploy/destructive migration.

### Human review order
PRD → NFR → Architecture + ADR → Threat model → Plan → Code diff → CI → Release decision.

## Review in Claude Code + Plannotator
1. Use native Claude Code Plan Mode for implementation planning; the Plannotator hook opens the review when the agent finishes the plan through the host mechanism.
2. If the plan is written as Markdown, run `/plannotator-annotate docs/IMPLEMENTATION_PLAN.md`. This is a manual document review and does **not** automatically approve Plan Mode.
3. Record APPROVED / CHANGES REQUESTED decisions and artifact references in `DECISION_LOG.md`.
4. After coding, run `/plannotator-review` to review the diff (it does not replace tests).

## Multi-agent policy
- Use Pstack `arena` only when an architecture choice is truly consequential and 2+ alternatives are useful; it is not mandatory for every task.
- Use an independent reviewer for security, permissions, migrations, boundary changes and hard-to-reproduce bugs.
- When running in Claude Code, check actual support (Cursor-only features may be skipped) and record the fallback.
- Human approval is still required for production deploys, destructive data changes and auto-merge.
