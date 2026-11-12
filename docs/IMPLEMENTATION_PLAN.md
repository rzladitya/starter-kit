# Implementation Plan — Vertical Slices

**Status:** DRAFT  
**Depends on:** Approved PRD, NFR, Architecture, ADRs and Threat Model  
**Implementation authorized:** NO (until decision log entry)

## Deliverables and sequencing
| Slice | User outcome | Depends on | Files/components | Automated proof | Manual proof | Rollback |
|---|---|---|---|---|---|---|
| 0. Foundation | App boots; health or minimal path works | Approved architecture | [TBD] | build/type/test | repeatable local run | revert setup |
| 1. First vertical slice | [one actual user outcome] | 0 | [TBD] | [behavior + integration test] | [demo step] | [TBD] |
| 2. Next slice | [TBD] | 1 | [TBD] | [TBD] | [TBD] | [TBD] |

## Per-slice Definition of Done
- [ ] Uses approved interfaces and data invariants.
- [ ] Acceptance test links to PRD ID.
- [ ] Tests for success, validation, authorization and failure paths as relevant.
- [ ] Lint/typecheck/build/unit/integration checks executed (or explicitly NOT RUN with reason).
- [ ] No unapproved secrets, dependencies, schema change or external infrastructure action.
- [ ] Documentation and ADR updated if decision changed.
- [ ] Diff reviewed, risks reported, human review completed where required.
- [ ] Rollback or safe revert specified.

## Task decomposition
| ID | Task | Scope/files | Acceptance criteria | Dependency | Risk | State |
|---|---|---|---|---|---|---|
| T-001 | [TBD] | [TBD] | [measurable] | None | [TBD] | Backlog |

## Stop-the-line conditions
- Requirement contradicts approved PRD/NFR or architecture.
- Unresolved critical security issue, destructive migration, unauthorized deployment, or changed public API with no ADR.
- Tests fail for reasons not yet understood, checker is silently bypassed, or verifiability is lost.

## Approval
- Owner: [TBD]
- Date: [TBD]
- Decision entry: [TBD]
