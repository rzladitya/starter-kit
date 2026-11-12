/pstack:poteto-mode

# Phase 2 → 3 — Architecture challenge & threat model (input for G2, start of phase 3)

Run this after `03-architecture.md` has drafted the design, **before** I approve G2.

## Preconditions
- Read `CLAUDE.md`, `docs/STATUS.md` and `docs/DECISION_LOG.md`. G0 and G1 must be **APPROVED**; otherwise STOP.
- `docs/ARCHITECTURE.md` must contain a real draft (not only `[FILL]`); otherwise STOP and tell me to run prompt 03.
- Read `docs/PRD.md`, `docs/NFR.md`, `docs/CONSTRAINTS.md`, `docs/ARCHITECTURE.md`, `docs/DATA_MODEL.md`, `docs/adr/` and `docs/SECURITY_THREAT_MODEL.md`.

## Tasks
Challenge the design as if real enterprise users depend on it:
1. Security and trust-boundary failures, privilege escalation, data leakage, supply-chain exposure.
2. Failure behavior: retries, idempotency, timeouts, observability, backup and recovery.
3. Wrong assumptions, overengineering, unowned data, untestable interfaces.
4. A smaller design: would it meet the PRD/NFR? Quantify trade-offs only from evidence.
5. Separate **verified findings**, **plausible risks** and **questions that need an experiment**.

## Independent review
When proportionate, spawn an independent reviewer subagent (Claude Code Agent tool, or Pstack interrogate if supported). Give it the documents, not your conclusions. Report which agent/model actually ran; if none did, say so.

## Outputs
- Update `docs/SECURITY_THREAT_MODEL.md` (threat table with controls, verification and owner).
- Record review findings in `docs/ARCHITECTURE.md` (section 10, Risks) or in the relevant ADR.
- Produce a prioritized list: **BLOCK** / **FIX BEFORE SCALE** / **ACCEPT**.

## Hard limits
No application code. Do not mark ADRs Accepted or approve gates yourself. Do not commit.

## Finish
1. Give the G2 status (checklist in `docs/WORKFLOW.md`) and the threat-model part of G3 (critical issues resolved or blocked).
2. Update `docs/STATUS.md`.
3. Reply using the Delivery format in `CLAUDE.md`, then stop and wait for my G2 decision.
