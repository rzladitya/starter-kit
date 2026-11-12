# Engineering Constraints (Quality Contract)

**Status:** DRAFT  
**Owner:** [FILL]  
**Stack:** TBD until architecture approval

## Non-negotiable floor
- No secrets committed; use environment variables or approved secret store.
- No deliberate test skips/deletions to make a build green without explicit documented reason.
- No hidden suppression of lint/type/security errors merely to pass checks.
- No empty error handlers that hide failures; no knowingly incomplete production stubs.
- No weakening quality gates without human approval and an ADR/decision entry.
- No unreviewed destructive migrations, automatic production deploy, or PR merges.

## Measurable checks — fill after stack is selected
| Dimension | Enforced threshold | Actual command | When | Owner |
|---|---|---|---|---|
| Typecheck | [TBD] | [TBD] | edit/task | [FILL] |
| Lint/format | [TBD] | [TBD] | edit/CI | [FILL] |
| Unit tests | [TBD] | [TBD] | task/CI | [FILL] |
| Integration tests | [TBD] | [TBD] | PR/CI | [FILL] |
| Secret scanning | [TBD] | [TBD] | PR/CI | [FILL] |
| Dependency vulnerability scan | [TBD] | [TBD] | PR/CI | [FILL] |
| Security/static analysis | [TBD] | [TBD] | PR/CI | [FILL] |
| API/schema contract test | [TBD if relevant] | [TBD] | PR/CI | [FILL] |
| Performance/load | [TBD with baseline] | [TBD] | staging/release | [FILL] |
| Backup/restore drill | [TBD if relevant] | [TBD] | release | [FILL] |

> Never mark a check 'enforced' until a real command has been tested to fail on a known violation and pass on a clean control. Prefer diff-scoped fast checks and fuller CI gates.

## Exception register
| ID | Constraint | Scope | Reason | Owner | Expiration | Approval |
|---|---|---|---|---|---|---|
| [none] | | | | | | |

## Baseline and ratchets
- Existing baseline: N/A (new project). Capture the first real baseline rather than inventing a threshold.
- Ratchet: block regression on agreed dimensions, subject to recorded exceptions.
