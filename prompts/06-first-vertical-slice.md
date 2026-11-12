/pstack:poteto-mode

SCAFFOLD + FIRST SLICE (phases 4–5). First inspect docs/DECISION_LOG.md and docs/STATUS.md. If there is no explicit APPROVED authorization for this bounded first slice, STOP and report the missing approval.

After verifying approval:
1. Read approved PRD/NFR/architecture/ADRs/constraints/implementation plan.
2. Identify the smallest end-to-end first user journey and its acceptance test.
3. Scaffold ONLY what that slice needs, using the approved stack; use minimal dependencies.
4. Add real test, lint, typecheck, build and secret-scanning commands when appropriate for the stack. Update docs/CONSTRAINTS.md with actual runnable commands.
5. Implement in small steps: failing behavior test if feasible → implementation → verification → refactor.
6. Run commands and capture factual results. Stop on unexplained failures; do not silence checks.
7. Update docs/IMPLEMENTATION_PLAN.md and docs/STATUS.md; include changed files, commands, evidence, residual risks, and rollback.

Do not auto-merge, deploy to production, rotate secrets or run destructive migrations. Reply in Indonesian with verified evidence only.
