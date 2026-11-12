/pstack:poteto-mode

Perform a skeptical architecture review BEFORE implementation. Read the PRD, NFR, constraints, architecture, domain model, ADRs and status.

Challenge the design as if it will handle real enterprise users:
- look for security and trust boundary failures, privilege escalation and data leakage;
- examine failure behavior, retries, idempotency, observability and recovery;
- identify wrong assumptions, overengineering, unowned data and untestable interfaces;
- consider a smaller design and quantify tradeoffs only when grounded in evidence;
- separate verified findings, plausible risks and questions that require an experiment.

Use independent subagent review when supported and proportionate; do not claim a second model ran unless one actually did.

Update docs/SECURITY_THREAT_MODEL.md and record review findings in docs/ARCHITECTURE.md or an ADR. Do not edit app code. Produce a prioritized BLOCK / FIX BEFORE SCALE / ACCEPT list and G2-G3 review status in Indonesian.
