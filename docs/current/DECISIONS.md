# Decisions

Updated: 3 November 2026 (MYT)

| ID | Decision | Status | Reason |
| --- | --- | --- | --- |
| D-001 | Permit controlled recovery work but hold production and normal feature development. | Accepted | The inherited data and identity model is not an acceptable production boundary. |
| D-002 | Preserve the inherited source at tag `arqevo-inherited-baseline-20261103`. | Accepted | Recovery requires an exact, reviewable reference before sanitisation or refactoring. |
| D-003 | Use the controlled fork as `origin`; keep the original repository as push-disabled `upstream`. | Accepted | Prevents accidental upstream modification while retaining read-only comparison. |
| D-004 | Work only through short-lived branches and reviewed pull requests; never commit directly to `main`. | Accepted | Keeps recovery changes bounded and reviewable. |
| D-005 | Reuse the Nexus source/controller versus runtime/database operating pattern, but no Bayam-specific data, secrets, identities, routes or branding. | Accepted | Reuses proven infrastructure discipline without crossing programme boundaries. |
| D-006 | Use only synthetic fixtures and offline/read-only checks until containment gates pass. | Accepted | Prevents mutation or further exposure of inherited production records. |
| D-007 | Do not allocate or deploy runtime infrastructure until exact port, database, network, secret, backup and rollback boundaries pass preflight and receive explicit GO. | Accepted | Protects existing services from collision or interruption. |
| D-008 | Decide separately whether recovery requires a sanitized private repository. | Pending owner decision | A public fork cannot become a secure operational-data boundary. |
