# Project Agent Instructions — Architecture-first

## Mission
You are working on a greenfield, enterprise-ready software project. The product, stack, and architecture are **not assumed**. Help the owner move from a validated idea to a safe, documented, testable first vertical slice. Prefer clear reasoning, simple architecture, reproducible evidence, and small diffs.

## Source-of-truth priority
1. Explicit current user request and latest approved decision.
2. `docs/DECISION_LOG.md` (approved decisions only).
3. `docs/PRD.md` (product scope), `docs/NFR.md` and `docs/CONSTRAINTS.md` (quality/security).
4. `docs/ARCHITECTURE.md`, `docs/DATA_MODEL.md`, and `docs/adr/` (approved design).
5. `docs/IMPLEMENTATION_PLAN.md` (delivery sequencing).
If sources conflict, **surface the conflict**. Do not quietly invent requirements or treat DRAFT content as approved.

## Phase contract
- **Discovery (phase 0):** No application code, framework install, or infrastructure changes. Produce and refine brief/PRD.
- **Constraints (phase 1):** Define measurable NFRs, threat assumptions, quality gates, and unresolved owners.
- **Architecture (phase 2):** Compare viable options with trade-offs; produce boundaries, data flow, and ADRs. Prototype only if explicitly approved, isolated, and disposable.
- **Risk & Plan (phase 3):** Produce the threat model and implementation plan, then offer the plan for human review. Use native Claude Code Plan Mode when appropriate so Plannotator can review via its hook. For existing Markdown plans, ask the operator to run `/plannotator-annotate <path>` if needed. A saved document alone does **not** fire the native plan hook. Gate G3: human approval recorded in `docs/DECISION_LOG.md`.
- **Scaffold (phase 4):** Require explicit recorded authorization in `docs/DECISION_LOG.md` before scaffolding production app, adding dependencies, or changing data schemas. Keep initialization minimal (project files, test harness, CI foundation); build and smoke test must actually run.
- **First slice (phase 5):** Implement a single smallest end-to-end slice. Run relevant automated checks, inspect actual artifacts and diff, report evidence. For important changes use independent review, then Plannotator diff review before PR/merge.

Phase numbering follows `docs/WORKFLOW.md`; keep README, STATUS and this file aligned with it.

## Engineering rules
1. State assumptions, risks, and unknowns. Mark unknown items `TBD (owner: ..., target date: ...)`; no fabricated facts.
2. Prefer domain-oriented boundaries, type safety, inputs validated at boundaries, least privilege, secret management, idempotent operations, and observable failure paths.
3. Do not add services, queues, microservices, caching layers, or databases without explaining why simpler alternatives fail.
4. Define acceptance tests from user-observable behavior. Build one vertical slice at a time, keep changes small, and verify the outcome.
5. No disabled tests, bypassed checks, suppression comments, blanket error handling, or weakened quality thresholds just to produce green status.
6. Redact secrets, tokens, credentials, PII, internal endpoints and sensitive data from logs, outputs, PRs, and prompts.
7. Never automatically deploy to production, merge PRs, run destructive migrations, delete user data, or change external infrastructure without a task-specific human approval.
8. Avoid model-specific claims: only use subagents, tools, models, or MCP providers available in this Claude Code session; gracefully fall back and report limitations.
9. For any 'done' claim, show commands executed, exit/results, files touched, behavior verified, and untested paths. If no checks exist yet, say so.
10. Keep documentation updated when behavior or architecture changes; add an ADR for consequential architectural decisions.

## Pstack and Plannotator integration
- Pstack is an installed **plugin**, not a project-local file dependency. Use `/pstack:poteto-mode` as an optional operator entry point, with relevant playbooks for feature, architecture or review. Do not auto-invoke heavy swarm/arena for trivial tasks.
- In Claude Code, Pstack's adapter maps Cursor-specific capabilities; model routing depends on `/pstack:setup-pstack`. A feature unavailable in Claude Code is not a blocker if a supported equivalent exists; record the gap.
- Plannotator is an **approval UI**. Native Plan Mode review and `/plannotator-annotate` are distinct; `/plannotator-review` examines uncommitted diff. User approval does not replace runtime verification.
- Do not duplicate entire plugin skill instructions inside this file.

## Start-of-session behavior
1. Read `docs/STATUS.md`, then the documents relevant to the active phase.
2. Summarize objective, current stage, decisions, missing information, and the next smallest deliverable.
3. If stage is DRAFT, work only within it. Ask the smallest set of decisive product questions; use explicit defaults only when clearly marked provisional.
4. Before changing code, confirm that the implementation gate is approved in `docs/DECISION_LOG.md` and scope is bounded by `docs/IMPLEMENTATION_PLAN.md`.

## Delivery format
Return: **Objective**, **Work completed**, **Evidence**, **Risks/unknowns**, **Decision needed or next slice**. Keep explanation clear and concise; respond in Indonesian unless user requests another language.
