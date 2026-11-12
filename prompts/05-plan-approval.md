/pstack:poteto-mode

# Phase 3 — Risk & Plan (gate G3)

## Preconditions
- Read `CLAUDE.md`, `docs/STATUS.md` and `docs/DECISION_LOG.md`. G0, G1 and G2 must be **APPROVED**; otherwise STOP.
- Read `docs/PRD.md`, `docs/NFR.md`, `docs/CONSTRAINTS.md`, `docs/ARCHITECTURE.md`, `docs/DATA_MODEL.md`, `docs/adr/`, `docs/SECURITY_THREAT_MODEL.md` and `docs/IMPLEMENTATION_PLAN.md`.
- If the threat model has unresolved **critical** items, STOP and list them.

## Step 1 — Draft the plan (normal mode)
Write a small, dependency-ordered vertical-slice plan in `docs/IMPLEMENTATION_PLAN.md`:
- Slice 0 = minimal foundation (phase 4 scaffold); Slice 1 = the smallest end-to-end user behavior. Do not attempt the whole MVP.
- Per slice: user outcome, linked `FR-xxx`, components/files, verification to run once the stack exists, failure cases, rollback, stop-the-line risks.
- Break Slice 0 and Slice 1 into tasks in the Task decomposition table.
- List every new dependency and schema change the slices need; each needs explicit approval.

## Step 2 — Human review (Plan Mode + Plannotator)
- Tell me to switch to **Plan Mode** (Shift+Tab in Claude Code). In Plan Mode, present the plan without editing files; the Plannotator hook opens when you finish the plan.
- If the Plan Mode hook is unavailable, or only the Markdown file needs review, tell me to run `/plannotator-annotate docs/IMPLEMENTATION_PLAN.md`.
- Incorporate my annotations back into `docs/IMPLEMENTATION_PLAN.md` after leaving Plan Mode.

## Hard limits
Drafting a plan, opening Plannotator or exiting Plan Mode is **not** authorization to code. No scaffolding, installs or schema changes. Do not commit.

## Finish
1. Walk through the **G3 checklist** in `docs/WORKFLOW.md`.
2. Update `docs/STATUS.md`; propose a draft G3 entry for `docs/DECISION_LOG.md` using the "Required approval record format", including the exact authorized scope (slices, dependencies, schema changes).
3. Wait for my explicit APPROVED message; only then record it with my words, the date and the scope.
4. Reply using the Delivery format in `CLAUDE.md`, then stop.
