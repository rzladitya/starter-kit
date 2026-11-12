# Domain and Data Model

**Status:** DRAFT  
**Owner:** [ISI]  
**Related architecture:** `ARCHITECTURE.md`

## Domain glossary
| Domain term | Definition | Invariant | Owner |
|---|---|---|---|
| [ISI] | [ISI] | [ISI] | [ISI] |

## Entities and relationships
```mermaid
erDiagram
    ENTITY_A ||--o{ ENTITY_B : owns
    ENTITY_A {
        string id
    }
    ENTITY_B {
        string id
        string entity_a_id
    }
```
> Ilustrasi placeholder — replace with real entities before approval.

## Data ownership
| Data category | Source of truth | Writer | Reader | Classification |
|---|---|---|---|---|
| [ISI] | [ISI] | [ISI] | [ISI] | [ISI] |

## Interface contracts
- API/command/event examples: [Path or schema].
- Validation and typed errors: [ISI].
- Idempotency key/duplicate handling: [ISI].
- API evolution and compatibility: [ISI].

## Storage lifecycle
- Retention/deletion: [ISI].
- Index and access pattern assumptions: [ISI].
- Migration & rollback: [ISI].
- Personal data handling: [ISI].
