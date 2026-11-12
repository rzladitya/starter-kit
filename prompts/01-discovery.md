/pstack:poteto-mode

# Phase 0 — Discover (gate G0)

We are starting a NEW enterprise software project. There is no approved architecture or technology stack.

## Preconditions
- Read `CLAUDE.md`, `docs/STATUS.md`, `docs/DECISION_LOG.md` and `docs/PROJECT_BRIEF.md`.
- If `docs/PROJECT_BRIEF.md` is still mostly `[FILL]`, interview me to fill it before touching the PRD.

## Role
Act as a product engineer and skeptical principal architect. Refine the product from the business problem, not from a framework choice.

## Tasks
1. Restate the product idea, target users and the problem in plain language.
2. List high-risk assumptions and missing requirements.
3. Ask only the most decisive questions, in short rounds of at most 4. Use Claude Code's question tool with concrete options when it helps me answer quickly. Do not ask me to pick technologies.
4. Update `docs/PROJECT_BRIEF.md`, then draft `docs/PRD.md`: personas, user journeys, MVP scope, non-goals, `FR-xxx` IDs and testable Given/When/Then acceptance criteria.
5. Mark every unknown as `TBD (owner: ..., target date: ...)`. Do not invent numbers, users or evidence.
6. Summarize the key trade-offs in the MVP scope.

## Hard limits
No framework init, package install, database choice, cloud resources, or application code. Do not commit.

## Finish
1. Check `docs/PRD.md` against the **G0 checklist** in `docs/WORKFLOW.md`; mark each item Met / Not met / TBD with the evidence location.
2. Update `docs/STATUS.md` (current state, next milestone, active blockers, last updated). Do not tick milestone boxes.
3. Propose a draft `docs/DECISION_LOG.md` entry for G0 with status `Draft` and approver `TBD`. Never mark it APPROVED yourself.
4. Tell me to review with `/plannotator-annotate docs/PRD.md` and to reply with an explicit approval or changes.
5. Reply using the Delivery format in `CLAUDE.md`, then stop.
