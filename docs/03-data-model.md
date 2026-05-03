# Data model

This project uses a simple, BI-friendly operational model for a service domain (TEIA), centered on three entities and one bridge table.

## Entities

### 1) Cases
Represents each client journey / follow-up unit.

Primary key:
- `case_id`

### 2) Sessions
Represents each session event (timestamped).

Primary key:
- `session_id`

Foreign key:
- `case_id` (links each session to exactly one case)

Core analytical fields (examples):
- `datetime` (when the session happened)
- `session_type` (e.g., Diagnostic / Intervention / Consolidation / Stress-test)
- `global_session_severity` (TEIA global severity, 1–5)
- `n_level` (N1 / N2 / N3 / Mixed / Unclear)
- optional cycle markers (`cycle`, `cycle_session`)

### 3) Protocols
Represents the catalog of available protocols (playbooks).

Primary key:
- `protocol_id`

### 4) Session_Protocols (bridge table)
Represents the many-to-many relationship between Sessions and Protocols.

Keys:
- `session_id`
- `protocol_id`

Why this exists:
- One Session can use multiple Protocols.
- One Protocol can be used across many Sessions.
- In relational/BI modeling, this is represented via a bridge (junction) table.

## Relationship summary

- Cases 1 — N Sessions
- Sessions N — N Protocols (via Session_Protocols)
