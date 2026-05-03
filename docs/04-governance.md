# Governance (capture standards)

This repo emphasizes governance as a first-class deliverable.

Core principles:

1) **Standardized capture**
Sessions are recorded with consistent, BI-friendly fields (e.g., session_type, global_session_severity 1–5, N-level tier, cycle markers when applicable).

2) **Separation of layers**
Operational monitoring fields (severity 1–5, tier labels, timestamps, protocol links) are kept distinct from free-text narratives. This reduces ambiguity and prevents “drift” in interpretation.

3) **Controlled vocabulary**
Key dimensions use enumerations (e.g., session_type, global_session_severity, n_level) to prevent naming drift and to keep the dataset queryable.

4) **Traceability**
Protocols are linked to sessions explicitly (N:N), enabling auditability of what was applied and when.

5) **Privacy-first publication**
Public artifacts must not contain client-identifying information. This repository uses fictional data and/or anonymized screenshots.

Objective:
- queryable
- dashboard-friendly
- consistent over time
- safe to present publicly
