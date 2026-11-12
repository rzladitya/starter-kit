# Non-Functional Requirements (NFR)

**Status:** DRAFT  
**Owner:** [FILL]

> Every number must come from a requirement or a measurement. Do not invent SLOs, load, RTO/RPO or cost. If unknown, write `TBD (owner: ..., decision date: ...)` and plan the measurement.

| Domain | Target / constraint | Cara ukur / bukti | Owner |
|---|---|---|---|
| Availability | [TBD] | uptime check, alert | [FILL] |
| Latency p50/p95/p99 | [TBD] | load test/trace | [FILL] |
| Peak concurrency / TPS | [TBD] | load test | [FILL] |
| Data volume & growth | [TBD] | sample/baseline | [FILL] |
| RPO / RTO | [TBD] | backup & restore drill | [FILL] |
| Security | [IAM, SSO, encryption, least privilege] | threat review + tests | [FILL] |
| Privacy & residency | [TBD + jurisdiction] | data classification & infra config | [FILL] |
| Auditability | [actors, actions, retention] | audit event tests | [FILL] |
| Observability | [logs, tracing, metrics] | failure exercise | [FILL] |
| Scalability | [TBD] | load test scenario | [FILL] |
| Accessibility | [TBD] | automated & manual audit | [FILL] |
| Cost ceiling | [TBD monthly/annual] | infra estimate | [FILL] |
| Deploy environment | [on-prem/cloud/hybrid/TBD] | deployment review | [FILL] |

## SLA vs SLO
- Internal SLOs: [FILL].
- External contractual SLA (if any): [FILL].

## Data classification
| Classification | Example | Storage / access restrictions |
|---|---|---|
| Public | [FILL] | [FILL] |
| Internal | [FILL] | [FILL] |
| Confidential / regulated | [FILL] | [FILL] |

## Performance budgets & capacity assumptions
- Real baseline: [TBD, test to obtain].
- Budget / pass threshold: [only after evidence].
- Failure mode / safe degradation: [FILL].
