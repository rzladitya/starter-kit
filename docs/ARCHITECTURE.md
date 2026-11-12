# System Architecture

**Status:** DRAFT  
**Architect:** [FILL]  
**Related PRD version:** [FILL]  
**Related ADRs:** [Links]

## 1. Design drivers
| Driver | Requirement ref | Consequence for design |
|---|---|---|
| [FILL] | [FR/NFR] | [FILL] |

## 2. Alternatives considered
| Option | Strengths | Costs/risks | Disqualifying constraints | Decision |
|---|---|---|---|---|
| A — minimal viable architecture | [FILL] | [FILL] | [FILL] | Pending |
| B — alternative if warranted | [FILL] | [FILL] | [FILL] | Pending |

## 3. C4 context diagram (Mermaid)
```mermaid
flowchart LR
  U[Target user] --> S[Proposed system]
  S --> D[(Owned data)]
  S -. if required .-> X[External dependency]
```
Replace placeholders before approval.

## 4. Container and component boundaries
| Component | Responsibility | Owns state? | Public contract | Failure mode |
|---|---|---|---|---|
| [FILL] | [FILL] | [Yes/No] | [FILL] | [FILL] |

## 5. Core flows and trust boundaries
- Flow A: `[actor] → [auth] → [domain] → [storage] → [response]`.
- Trust boundaries: [internal, public, provider, ops].
- Authorizations per flow: [FILL].
- Error paths: timeout, retries, idempotency, eventual consistency [if relevant].

## 6. Deployment architecture
- Environment: dev, staging, prod [as required].
- On-prem/cloud/hybrid decision: [FILL].
- Networking: ingress/egress, segmentation, TLS: [FILL].
- Secrets: vault / secret provider [TBD].
- Backup/recovery: [FILL].
- Scaling and availability: [FILL].

## 7. Persistence & integrations
- Entities and relationships: `DATA_MODEL.md`.
- Sync/async decision rationale: [FILL].
- Migration and rollback strategy: [FILL].

## 8. Security / privacy / observability
- Threat model: `SECURITY_THREAT_MODEL.md`.
- Logs/traces/metrics ownership: [FILL].
- Data encryption and retention: [FILL].

## 9. Decision history
Capture non-trivial decisions as `docs/adr/ADR-000N-*.md` with alternatives and reasoning. Avoid a tech stack decision without explicit constraints.

## 10. Risks and feasibility spikes
| Assumption | How to verify it cheaply | Stop condition | Owner |
|---|---|---|---|
| [FILL] | [prototype/test/doc] | [FILL] | [FILL] |

## Approval
- Reviewer: [FILL]
- Recorded decision: [link to DECISION_LOG]
