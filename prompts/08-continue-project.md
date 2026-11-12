/pstack:poteto-mode

# Continue — next vertical slice (repeat phase 5)

Use this at the start of a new session to continue an approved project after earlier slices.

## Preconditions
- Read `CLAUDE.md`, `docs/STATUS.md`, `docs/DECISION_LOG.md`, then the current `docs/PRD.md`, `docs/NFR.md`, `docs/CONSTRAINTS.md`, `docs/ARCHITECTURE.md`, `docs/adr/` and `docs/IMPLEMENTATION_PLAN.md`.
- Check `git log` and `git status` for the actual state; do not assume missing history.

## Tasks
1. Summarize the current architecture, confirmed decisions and the baseline check results (run the checks in `docs/CONSTRAINTS.md` now; report `NOT RUN` where unavailable).
2. Identify the next slice in `docs/IMPLEMENTATION_PLAN.md` and check that `docs/DECISION_LOG.md` authorizes it.
   - **Not authorized:** STOP and propose a draft approval entry with its scope.
   - **Needs a new design choice** (new service, data store, public API, schema change, dependency): STOP and route back to `prompts/03-architecture.md` / `prompts/05-plan-approval.md`.
3. For the authorized slice: list blast radius, dependencies, acceptance tests (linked `FR-xxx`) and rollback.
4. Surface any conflict between the request, the PRD/NFR and the architecture; stop for a decision if it is material.
5. Implement only that slice on a feature branch, in small verified steps (same rules as `prompts/06-first-vertical-slice.md`, Part B).

## Hard limits
Human approval is required for new major design choices, destructive operations, merging and production deploys. Commit only when I ask.

## Finish
1. Keep `docs/IMPLEMENTATION_PLAN.md`, `docs/STATUS.md` and ADRs in sync.
2. Hand off with evidence and recommend `prompts/07-code-review.md`, plus whether to use Plannotator for plan review (Plan Mode / `/plannotator-annotate`) or diff review (`/plannotator-review`).
3. Reply using the Delivery format in `CLAUDE.md`, then stop.
