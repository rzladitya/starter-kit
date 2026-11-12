/pstack:poteto-mode

# Phase 5 — Verify & review (gate G4)

## Preconditions
- Read `CLAUDE.md`, `docs/STATUS.md`, `docs/DECISION_LOG.md` and `docs/IMPLEMENTATION_PLAN.md` to identify the slice and its approved scope.
- Read the approved `docs/PRD.md`, `docs/NFR.md`, `docs/CONSTRAINTS.md`, `docs/ARCHITECTURE.md`, `docs/adr/` and `docs/SECURITY_THREAT_MODEL.md`.
- Inspect the actual diff (`git status`, `git diff` against the base branch).

## Tasks
1. **Run real checks first.** Run every command in the Measurable checks table of `docs/CONSTRAINTS.md`. Report the exact command and result; anything unavailable is `NOT RUN` with the reason.
2. **Scope check.** Flag any change outside the approved scope, any unapproved dependency or schema change, and any public API change without an ADR.
3. **Review the diff** for security regressions, broken contracts, missing validation, misleading tests, brittle abstractions and unhandled failure paths.
4. **Independent review** for consequential changes: spawn a reviewer subagent with the diff and the docs (not your conclusions), or use Pstack interrogate if supported. Report which agent/model actually ran.
5. **Verify every finding** against the code path and with a reproduction or test. Drop findings you cannot prove.
6. **Fix only proven defects** within the approved scope, then rerun the checks.

## Operator review steps (ask me to run these)
- `/code-review` and `/security-review` — Claude Code's built-in review commands, if I want a second pass.
- `/plannotator-review` — annotate the uncommitted diff.

## Hard limits
Do not merge, deploy, or push without my explicit request.

## Finish
1. Walk through the **G4 checklist** in `docs/WORKFLOW.md`.
2. Update `docs/STATUS.md`; propose a draft G4 entry for `docs/DECISION_LOG.md`.
3. Give a **GO / HOLD** recommendation with evidence, linked to file paths and check results, plus unresolved risks.
4. Reply using the Delivery format in `CLAUDE.md`, then stop.
