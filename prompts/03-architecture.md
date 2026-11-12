/pstack:poteto-mode

Act as principal architect designing a NEW project. Read CLAUDE.md plus approved PRD, NFR and CONSTRAINTS, and the decision log.

Before any code:
1. Identify design drivers and domain invariants.
2. Propose a minimal coherent architecture plus one credible alternative only if there is a meaningful trade-off.
3. Use Pstack's bundled architect workflow when cross-boundary interfaces and data shapes need deeper design. Consider its arena workflow ONLY for consequential architectural forks and only if session tools support independent candidates.
4. Compare reliability, security, operability, latency, extensibility, staffing/cost, and risks.
5. Define C4-style context/container diagrams (Mermaid), trust boundaries, data flows, typed interfaces, persistence choices, deployment topology and error handling.
6. Document docs/ARCHITECTURE.md, docs/DATA_MODEL.md and proposed ADR(s) in docs/adr/. Include assumptions and a reversible validation strategy.
7. Flag unknowns and what needs a cheap prototype or external documentation check.

No production code, no dependency installation, no cloud resource creation. Do not mark ADRs Accepted without explicit owner approval. Respond in Indonesian and stop at G2 review.
