/pstack:poteto-mode

# Phases 4–5 — Scaffold + first vertical slice

## Preconditions
- Read `CLAUDE.md`, `docs/STATUS.md` and `docs/DECISION_LOG.md`.
- There must be an **APPROVED** G3 entry that authorizes this slice, its dependencies and any schema change. If not, STOP and report exactly what approval is missing.
- Read the approved `docs/PRD.md`, `docs/NFR.md`, `docs/CONSTRAINTS.md`, `docs/ARCHITECTURE.md`, `docs/DATA_MODEL.md`, `docs/adr/` and `docs/IMPLEMENTATION_PLAN.md`.
- Use a feature branch (not `main`). Track the plan's tasks with the todo list.

## Part A — Phase 4: Scaffold (Slice 0)
1. Scaffold **only** what Slice 1 needs, with the approved stack and only approved dependencies.
2. Add real test, lint/format, typecheck, build and secret-scan commands for this stack.
3. Prove each check works: it fails on a known violation and passes on clean code. Then write the commands into the Measurable checks table in `docs/CONSTRAINTS.md`.
4. Run build + smoke test. Report commands and actual output.
5. **Checkpoint:** stop, report Part A evidence, and wait for me to say "continue".

## Part B — Phase 5: First slice (Slice 1)
1. Restate the slice's user journey and its acceptance test (linked `FR-xxx`).
2. Work in small steps: failing behavior test (if feasible) → implementation → run checks → refactor.
3. Cover success, validation, authorization and failure paths as relevant.
4. Stop on any failure you do not understand. Never skip, delete or suppress a check to get green.

## Hard limits
No auto-merge, production deploy, secret rotation, destructive migration or unapproved dependency/schema change. Commit only when I ask.

## Finish
1. Check the Per-slice Definition of Done in `docs/IMPLEMENTATION_PLAN.md`.
2. Update `docs/IMPLEMENTATION_PLAN.md` (task states) and `docs/STATUS.md`.
3. Report changed files, commands run with results, untested paths, residual risks and rollback.
4. Recommend `prompts/07-code-review.md` next.
5. Reply using the Delivery format in `CLAUDE.md`, with verified evidence only, then stop.
