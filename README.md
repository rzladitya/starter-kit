# Architecture-first Starter Kit

> **Claude Code + Pstack + Plannotator** for starting an enterprise *greenfield project*.

Document templates and prompts that take an idea through PRD, NFRs, architecture design, and human approval, then into incremental implementation.

**This is not an application or a framework skeleton.** The technology stack is chosen *after* discovery and approval.

---

## Table of contents

- [Repository contents](#repository-contents)
- [Quick start](#quick-start)
- [Phases and approval gates](#phases-and-approval-gates)
- [Prompt sequence](#prompt-sequence)
- [Source of truth](#source-of-truth)
- [Safety and operations](#safety-and-operations)
- [References](#references)

---

## Repository contents

```text
.
├── CLAUDE.md                  # Project agent instructions (concise, points to docs/)
├── README.md
├── docs/
│   │   # — Project control (used in every phase)
│   ├── STATUS.md              # Current phase & state — read first
│   ├── DECISION_LOG.md        # Decisions & human approvals
│   ├── WORKFLOW.md            # Phases 0–5 + gate checklists G0–G4
│   │   # — Phase 0: Discover
│   ├── PROJECT_BRIEF.md       # Idea summary (filled in by the owner)
│   ├── PRD.md                 # Product requirements (drafted with the agent)
│   │   # — Phase 1: Constrain
│   ├── NFR.md                 # Product quality targets (SLO, RTO/RPO, privacy)
│   ├── CONSTRAINTS.md         # Engineering quality contract & check commands
│   │   # — Phase 2: Design
│   ├── ARCHITECTURE.md        # Architecture design
│   ├── DATA_MODEL.md          # Domain, entities, data contracts
│   ├── adr/
│   │   └── ADR-0001-template.md
│   │   # — Phase 3: Risk & Plan
│   ├── SECURITY_THREAT_MODEL.md
│   └── IMPLEMENTATION_PLAN.md # Plan per vertical slice
└── prompts/                   # One prompt per phase (01–08)
```

---

## Quick start

**1. Set up the repository**

```bash
git clone https://github.com/rzladitya/starter-kit.git my-project
cd my-project
claude
```

> Alternatively, copy this kit into an empty repository and run `git init` if it is not a Git repo yet.

**2. Install Pstack** (run inside Claude Code)

```text
/plugin marketplace add cursor/plugins
/plugin install pstack@cursor-plugins
/pstack:setup-pstack
```

In Claude Code, Pstack runs through an *adapter*: some Cursor models and Cursor-only features are unavailable. During `setup-pstack`, select models that are actually available in Claude Code.

**3. Install Plannotator** (optional, recommended)

```text
/plugin marketplace add backnotprop/plannotator
/plugin install plannotator@plannotator
```

Restart Claude Code after installing plugins. Usage:

| Need | How |
|---|---|
| Review an implementation plan | Claude Code native **Plan Mode** (the Plannotator hook opens automatically) |
| Review a Markdown document | `/plannotator-annotate docs/PRD.md` |
| Review the uncommitted diff | `/plannotator-review` |

**4. Start discovery**

Fill in the idea summary in [`docs/PROJECT_BRIEF.md`](docs/PROJECT_BRIEF.md), then paste the contents of [`prompts/01-discovery.md`](prompts/01-discovery.md) into Claude Code.

> [!IMPORTANT]
> Do not run all prompts at once. Run one phase → review the artifacts → record the decision → then continue.
> The files in `prompts/` are **user** messages for Claude Code; do not move them into `CLAUDE.md`.

> [!NOTE]
> Documents are in English. The agent replies in Indonesian by default; change the *Delivery format* section in `CLAUDE.md` and the "Reply in Indonesian" lines in `prompts/` to switch.

---

## Phases and approval gates

| Phase | Main output | Exit criteria | Gate | Reviewer |
|---|---|---|---|---|
| **0. Discover** | `PROJECT_BRIEF.md`, `PRD.md` | Users, problem, MVP and acceptance criteria are clear; owner signs off scope | G0 | Product owner |
| **1. Constrain** | `NFR.md`, `CONSTRAINTS.md` | Security, performance, RTO/RPO, data and compliance filled in or TBD with an owner | G1 | Tech lead / security |
| **2. Design** | `ARCHITECTURE.md`, `DATA_MODEL.md`, `adr/*` | Alternatives, trade-offs, risks, deployment and diagrams are readable; ADRs Accepted | G2 | Architect |
| **3. Risk & Plan** | `SECURITY_THREAT_MODEL.md`, `IMPLEMENTATION_PLAN.md`, `DECISION_LOG.md` | High risks mitigated; vertical-slice plan reviewed via Plannotator; owner records written **APPROVED** | G3 | Security / engineering / owner |
| **4. Scaffold** | Project files, test harness, CI foundation | Minimal initialization after approval; build & smoke test actually run | — | Engineering |
| **5. First slice** | Code, tests, docs, CI report, PR | One slice works end-to-end; real checks executed; independent review + Plannotator | G4 | Engineering / reviewer |

Every document starts as **DRAFT**, not approved. Phase numbering and the G0–G4 checklists are defined in [`docs/WORKFLOW.md`](docs/WORKFLOW.md).

---

## Prompt sequence

| # | File | When to use |
|---|---|---|
| 01 | [`01-discovery.md`](prompts/01-discovery.md) | Start from the idea, no code |
| 02 | [`02-nfr-and-constraints.md`](prompts/02-nfr-and-constraints.md) | Lock quality standards and non-functional requirements |
| 03 | [`03-architecture.md`](prompts/03-architecture.md) | Explore options, architecture and ADRs |
| 04 | [`04-architecture-challenge.md`](prompts/04-architecture-challenge.md) | Adversarial design review and risk check |
| 05 | [`05-plan-approval.md`](prompts/05-plan-approval.md) | Write the plan and submit it for Plannotator review |
| 06 | [`06-first-vertical-slice.md`](prompts/06-first-vertical-slice.md) | Minimal scaffold and one slice, after approval |
| 07 | [`07-code-review.md`](prompts/07-code-review.md) | Verification, independent review and diff review |
| 08 | [`08-continue-project.md`](prompts/08-continue-project.md) | Continue with the next sprint/feature on stable context |

---

## Source of truth

| Topic | Document |
|---|---|
| Product requirements | [`docs/PRD.md`](docs/PRD.md) |
| Quality & deployment constraints | [`docs/NFR.md`](docs/NFR.md), [`docs/CONSTRAINTS.md`](docs/CONSTRAINTS.md) |
| Structural decisions | [`docs/ARCHITECTURE.md`](docs/ARCHITECTURE.md), [`docs/adr/`](docs/adr/) |
| Coding scope & dependencies | [`docs/IMPLEMENTATION_PLAN.md`](docs/IMPLEMENTATION_PLAN.md) |
| Approvals, scope changes, exceptions | [`docs/DECISION_LOG.md`](docs/DECISION_LOG.md) |
| Agent instructions | [`CLAUDE.md`](CLAUDE.md) — keep it short; do not paste every Pstack skill here |

---

## Safety and operations

- **No false claims.** Never write `PASS` for a check that was not run; write `NOT RUN` with the reason.
- **Approval ≠ verification.** Plannotator is *human review*, not proof that tests, security or CI passed.
- **No risky automation early on.** Do not enable `autopilot-full`, auto-merge, production deploys or destructive migrations during discovery and design.
- **Sensitive data.** For company projects, review the AI provider policy. Disable Plannotator sharing if needed: `PLANNOTATOR_SHARE=disabled`.
- **Real checks only.** Define lint/test commands after the language/framework is chosen; do not copy fictional commands.

---

## References

- [Pstack](https://github.com/cursor/plugins/tree/main/pstack)
- [Pstack in Claude Code](https://github.com/cursor/plugins/blob/main/pstack/docs/harness/claude-code.md)
- [Plannotator](https://github.com/backnotprop/plannotator)
