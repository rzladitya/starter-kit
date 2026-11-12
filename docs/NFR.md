# Non-Functional Requirements (NFR)

**Status:** DRAFT  
**Owner:** [ISI]

> Semua angka harus berasal dari requirement atau measurement. Jangan mengarang SLO, load, RTO/RPO, atau biaya. Jika tidak diketahui, isi `TBD (owner: ..., decision date: ...)` dan rencanakan pengukuran.

| Domain | Target / constraint | Cara ukur / bukti | Owner |
|---|---|---|---|
| Availability | [TBD] | uptime check, alert | [ISI] |
| Latency p50/p95/p99 | [TBD] | load test/trace | [ISI] |
| Peak concurrency / TPS | [TBD] | load test | [ISI] |
| Data volume & growth | [TBD] | sample/baseline | [ISI] |
| RPO / RTO | [TBD] | backup & restore drill | [ISI] |
| Security | [IAM, SSO, encryption, least privilege] | threat review + tests | [ISI] |
| Privacy & residency | [TBD + jurisdiction] | data classification & infra config | [ISI] |
| Auditability | [actors, actions, retention] | audit event tests | [ISI] |
| Observability | [logs, tracing, metrics] | failure exercise | [ISI] |
| Scalability | [TBD] | load test scenario | [ISI] |
| Accessibility | [TBD] | automated & manual audit | [ISI] |
| Cost ceiling | [TBD monthly/annual] | infra estimate | [ISI] |
| Deploy environment | [on-prem/cloud/hybrid/TBD] | deployment review | [ISI] |

## SLA vs SLO
- Internal SLOs: [ISI].
- External contractual SLA (if any): [ISI].

## Data classification
| Classification | Example | Storage / access restrictions |
|---|---|---|
| Public | [ISI] | [ISI] |
| Internal | [ISI] | [ISI] |
| Confidential / regulated | [ISI] | [ISI] |

## Performance budgets & capacity assumptions
- Real baseline: [TBD, test to obtain].
- Budget / pass threshold: [only after evidence].
- Failure mode / safe degradation: [ISI].
