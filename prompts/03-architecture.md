/pstack:poteto-mode

# Phase 2 — Design (gate G2)

## Preconditions
- Read `CLAUDE.md`, `docs/STATUS.md` and `docs/DECISION_LOG.md`.
- `docs/DECISION_LOG.md` must contain **APPROVED** G0 and G1 entries. If not, STOP and report what is missing.
- Then read `docs/PRD.md`, `docs/NFR.md`, `docs/CONSTRAINTS.md`, `docs/ARCHITECTURE.md`, `docs/DATA_MODEL.md` and `docs/adr/`.

## Role
Act as principal architect designing a NEW system.

## Tasks
1. Identify design drivers (link each to an `FR-xxx` / NFR row) and domain invariants.
2. Propose the **simplest coherent architecture**. Add one credible alternative only when there is a meaningful trade-off. Explain why simpler options fail before adding services, queues, caches or extra databases.
3. Compare options on reliability, security, operability, latency, extensibility, staffing/cost and risk.
4. Document C4-style context/container diagrams (Mermaid), trust boundaries, data flows, typed interfaces, persistence, deployment topology and error handling.
5. Write `docs/ARCHITECTURE.md` and `docs/DATA_MODEL.md`. Record each consequential choice as a new ADR in `docs/adr/` (copy `ADR-0001-template.md`, status `Proposed`).
6. List assumptions, a reversible validation strategy, and anything needing a cheap prototype or an external documentation check.

## Claude Code / Pstack tooling
- Use Pstack's architect workflow when cross-boundary interfaces and data shapes need deeper design.
- Consider Pstack `arena` **only** for a consequential architectural fork, and only if this session can actually run independent candidates. Report which agents/models actually ran; never claim a run that did not happen.
- If a prototype is needed, ask first; it must be isolated (e.g. a scratch folder or git worktree) and disposable.

## Hard limits
No production code, dependency installs or cloud resources. Do not mark ADRs `Accepted` without my explicit approval. Do not commit.

## Finish
1. Walk through the **G2 checklist** in `docs/WORKFLOW.md`: Met / Not met / TBD with evidence.
2. Update `docs/STATUS.md`; propose a draft G2 entry for `docs/DECISION_LOG.md`.
3. Recommend running `prompts/04-architecture-challenge.md` before I approve G2, and `/plannotator-annotate docs/ARCHITECTURE.md` for my review.
4. Reply using the Delivery format in `CLAUDE.md`, then stop.
