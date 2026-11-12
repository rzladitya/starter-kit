/pstack:poteto-mode

Before architecture selection, read approved docs/PRD.md, docs/STATUS.md, CLAUDE.md.

Design measurable non-functional requirements and engineering constraints:
- user load, latency, availability and capacity (only grounded in actual expectations; otherwise mark TBD with owner);
- identity, authorization, multi-tenancy (if relevant), privacy, sensitive data and data residency;
- infrastructure options (on-prem, cloud, hybrid), backup/restore, RPO/RTO, monitoring, operational ownership;
- cost ceilings, dependency constraints, and security posture;
- runtime verification strategy (tests, lint/typecheck, secrets scanning, CI) without inventing commands before stack selection.

Update docs/NFR.md and docs/CONSTRAINTS.md. State unresolved high-impact questions and recommended experiments. Do not begin implementation. End with the G1 approval checklist in Indonesian.
