# TEIA — Analytics Engineering Portfolio (Data Ops + Governance)

This is a public portfolio repository documenting a BI-friendly operational data model for a service domain (TEIA), with an emphasis on:
- data modeling (Cases / Sessions / Protocols)
- governance (controlled vocabularies + capture standards)
- traceability (protocol usage tracked per session)
- dashboard-ready structure

> Privacy note: no real client data is published here. The dataset in `sample-data/` is fictional. See `docs/06-privacy.md`.

---

## What’s inside

### Documentation
- Context: `docs/01-context.md`
- Glossary (domain terms): `docs/02-glossary.md`
- Data model (entities + relationships): `docs/03-data-model.md`
- Governance (capture standards): `docs/04-governance.md`
- Dashboards (concept/spec): `docs/05-dashboards.md`
- Privacy: `docs/06-privacy.md`

### Demo dataset (fictional)
Folder: `sample-data/`

Tables:
- `cases.csv`  
  One row per case (client journey / follow-up unit). Primary key: `case_id`.

- `sessions.csv`  
  One row per session (timestamped event). Primary key: `session_id`.  
  Foreign key: `case_id` → links each session to one case.  
  Includes TEIA-aligned operational fields such as `session_type`, `global_session_severity (1–5)`, and `n_level`.

- `protocols.csv`  
  One row per protocol (catalog / playbook). Primary key: `protocol_id`.

- `session_protocols.csv`  
  Bridge table (junction) for the many-to-many relationship between sessions and protocols.  
  Keys: `session_id`, `protocol_id`.

Relationship summary:
- Cases 1 — N Sessions
- Sessions N — N Protocols (via Session_Protocols)

---

## How to explore (quick)
1) Open `sample-data/sessions.csv` and filter by `case_id`.
2) Join `sessions.csv` ↔ `session_protocols.csv` ↔ `protocols.csv` to see which protocols were used per session.
3) Aggregate `global_session_severity (1–5)` over time to simulate a stability monitoring view.

---

## Notes
- Domain terms (TEIA / N-level / protocols) are explained in `docs/02-glossary.md`.
- This repo focuses on the data model and governance, not on publishing client narratives or full methodology.
