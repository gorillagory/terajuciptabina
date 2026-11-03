# Decisions

Updated: 4 November 2026 (MYT)

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
| D-009 | Record production continuation as NO-GO while containment findings C-001 through C-009 remain unresolved. | Accepted | The static audit confirms critical identity, authorization, public-data and payment-boundary failures. |
| D-010 | Keep Nexus runtime infrastructure in discovery-only mode for this phase. | Accepted | Source governance and offline tests can proceed without allocating or changing containers, databases, ports, networks, secrets, DNS or routes. |
| D-011 | Make `nexus-pbund:/root/workspaces/arqevo` the canonical source/controller checkout. | Accepted | Matches the established one-writer server model and prevents divergent desktop source copies. |
| D-012 | Use `dev-task/<short-slug> -> staging -> main` as the only promotion path. | Accepted | Separates bounded development, test integration and production-source acceptance. |
| D-013 | Use the Windows checkout only as reference and authenticated GitHub-ref relay until a repository-scoped server credential is separately approved. | Accepted | Enables exact ref publication without copying personal credentials or making the desktop a second source writer. |
| D-014 | Treat branch promotion and deployment as separate gates. | Accepted | Neither a merge to `staging` nor a merge to `main` authorises a runtime change. |
