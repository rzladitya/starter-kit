# Review Gates / Definition of Ready

## Product (G0)
- [ ] Primary user and top jobs-to-be-done are concrete.
- [ ] MVP has verifiable acceptance criteria.
- [ ] Non-goals and dependencies are explicit.
- [ ] Open questions have owners.

## Requirements & NFR (G1)
- [ ] Deployment constraints, sensitive data policy, auth/access model captured.
- [ ] Target performance, capacity and uptime are measured or assigned for discovery.
- [ ] RTO/RPO and data retention requirements decided or owned as TBD.
- [ ] Cost assumptions trace to source or marked provisional.

## Architecture (G2)
- [ ] At least one simpler design considered, not overengineered.
- [ ] Component responsibilities and trust boundaries documented.
- [ ] Contract + domain shapes + failure modes documented.
- [ ] Significant tech choice has ADR with rejected alternatives.
- [ ] Testability, operability, rollback and migration reviewed.
- [ ] Threat model critical issues resolved or explicitly blocked.

## Implementation permission (G3)
- [ ] `IMPLEMENTATION_PLAN.md` has a single, bounded first vertical slice.
- [ ] Native Plan Mode review (if used) has finished; feedback incorporated.
- [ ] Plannotator annotation review or explicit human review recorded.
- [ ] `DECISION_LOG.md` contains clear human APPROVED record for coding.

## Code / release (G4)
- [ ] Tests, static checks, integration checks and security scans executed and reported.
- [ ] Diff reviewed using human review / `/plannotator-review`.
- [ ] Critical issue disposition recorded; no fake green checks.
- [ ] No unapproved merge/deploy/destructive migration.

## Human review order
PRD → NFR → Architecture + ADR → Threat model → Plan → Code diff → CI → Release decision.
