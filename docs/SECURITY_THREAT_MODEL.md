# Security & Threat Model

**Status:** DRAFT  
**Reviewer:** [ISI]

## Assets & actors
- Critical assets: [data, credentials, money, business actions].
- Trusted users/services: [roles].
- Untrusted input sources: [browser, public API, files, prompts, plugins].

## Data flows / trust boundaries
Link threat model to `ARCHITECTURE.md` component/data-flow diagram.

| ID | Threat / abuse case | Entry point | Impact | Likelihood | Control | Verification | Owner |
|---|---|---|---|---|---|---|---|
| TH-001 | Unauthorized access | [ISI] | [ISI] | [ISI] | [ISI] | [Test] | [ISI] |
| TH-002 | Sensitive data leakage | [ISI] | [ISI] | [ISI] | [ISI] | [Test] | [ISI] |
| TH-003 | Dependency / supply chain risk | [ISI] | [ISI] | [ISI] | [ISI] | [Scan] | [ISI] |

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
