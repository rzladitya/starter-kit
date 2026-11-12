/pstack:poteto-mode

Review the current feature diff against the approved PRD, NFR, Architecture, ADRs, threat model, constraints and implementation plan.

1. First run real tests, typecheck, lint, build and scans that the project actually defines. Report exact command/output; if unavailable, state NOT RUN.
2. For consequential changes use Pstack's adversarial interrogate review where supported. Verify each claimed bug against code paths and rerun/reproduction; don't invent findings.
3. Look for security regressions, API contract breakage, missing validation, misleading tests, brittle abstraction and failure paths.
4. Fix only proven defects within the approved scope. Repeat checks after any fix.
5. Ask me to run `/plannotator-review` (or open a native review when plugin supports it) to annotate the uncommitted diff.
6. Give a GO / HOLD recommendation, with evidence and unresolved risks; do not merge or deploy.

Reply in Indonesian, link findings to concrete file paths and test results.
