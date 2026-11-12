# Security & Threat Model

**Status:** DRAFT  
**Reviewer:** [FILL]

## Assets & actors
- Critical assets: [data, credentials, money, business actions].
- Trusted users/services: [roles].
- Untrusted input sources: [browser, public API, files, prompts, plugins].

## Data flows / trust boundaries
Link threat model to `ARCHITECTURE.md` component/data-flow diagram.

| ID | Threat / abuse case | Entry point | Impact | Likelihood | Control | Verification | Owner |
|---|---|---|---|---|---|---|---|
| TH-001 | Unauthorized access | [FILL] | [FILL] | [FILL] | [FILL] | [Test] | [FILL] |
| TH-002 | Sensitive data leakage | [FILL] | [FILL] | [FILL] | [FILL] | [Test] | [FILL] |
| TH-003 | Dependency / supply chain risk | [FILL] | [FILL] | [FILL] | [FILL] | [Scan] | [FILL] |

## Core controls to decide
- Authentication, authorization, RBAC/ABAC, tenant isolation as applicable.
- Transport and storage encryption.
- Secrets management and rotation.
- Input validation and output encoding.
- CSRF/SSRF, injection and rate limiting where applicable.
- Audit events, incident response, retention.
- Backup, restore, disaster recovery.
- Data privacy, vendor AI and third-party exposure.

## Security approval
No production go-live with unresolved **critical** risks. Document exceptions with an owner, expiry and mitigation. Record approval ID in `DECISION_LOG.md`.
