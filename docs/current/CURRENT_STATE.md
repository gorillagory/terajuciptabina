# Current State

Updated: 4 November 2026 (MYT)

## Outcome

**NO-GO FOR PRODUCTION; HOLD FOR CONTAINMENT.** Read-only recovery, baseline protection, governance setup and synthetic testing may continue. Production continuation, normal feature expansion, live data mutation and deployment remain prohibited.

## Verified repository state

- Canonical source/controller checkout: `nexus-pbund:/root/workspaces/arqevo`.
- Controlled fork: `https://github.com/gorillagory/terajuciptabina` (`origin`).
- Original repository: `https://github.com/terajuciptabina-eng/terajuciptabina` (`upstream`, push-disabled locally).
- Active integration branch: `staging`, tracking `origin/staging` at `16feebfd59aa65463e1d74d4c2674ba3559f22bd` before the repository-workflow task.
- Approved promotion path: `dev-task/<short-slug> -> staging -> main`.
- The Windows checkout is reference and authenticated GitHub-ref relay only; application-source edits occur on the canonical server checkout.
- `origin/main` and `upstream/main`: `4903807239d8b34cf665bb1a42d8383d11973124`.
- `upstream/latest-working`: `3b6c108220dcde95ab5b91b83b89aab4198b6a3e`.
- Protected inherited reference: tag `arqevo-inherited-baseline-20261103` at `4903807239d8b34cf665bb1a42d8383d11973124`.
- The inherited snapshot has 389 tracked files, including 229 files under `data/`, 13 API files and 8 test files.
- The current tree contains 80 homeowner accounts, 90 contractor accounts and 31 contractor project-control files; an earlier 81-homeowner count does not match this SHA.
- Static inspection confirms repository-backed account and project persistence and a temporary GitHub-token API bridge.
- Static inspection confirms ID-only account access, identifier-selected quotation/project-control mutation and an active detailed-quotation payment bypass.
- The existing country/market integrity suite passes 36 of 36 tests using synthetic mocks on the canonical checkout.
- No application service, database, container, network, port, DNS route or production endpoint was changed or exercised during bootstrap.

## Infrastructure boundary

- `nexus-pbund` owns source, review evidence and release control; `nexus-docker` may hold only explicitly approved runtime/database artifacts.
- Do not copy a working checkout into a runtime path or treat a runtime copy as canonical source.
- Do not allocate a port, database, secret path, shared network attachment or public route until a read-only collision/capacity preflight and an explicit deployment GO.
- Reuse only generic infrastructure patterns. Do not reuse Bayam data, credentials, routes, application identities or branding.

## Active blockers

1. Authority, IP/licensing and data-retention instructions are not yet recorded as accepted decisions.
2. Inherited personal/project records remain in a public Git repository and history.
3. Authentication and per-record authorization are not adequate for production use.
4. Repository-backed operational writes use a server-held GitHub token.
5. Payment, messaging and AI paths have confirmed unsafe trust boundaries and no accepted containment control.
6. BuildPlanner V2 and RenovationPlanner V2 do not yet have a complete golden-master safety net.
7. A sanitized private recovery repository has not been approved or created.

## Next safe sequence

1. Start `dev-task/security-denial-tests` from current `staging` and add synthetic denial tests for account, quotation, project-control, payment and provider-cost abuse paths.
2. Create golden fixtures for both V2 planner calculation engines before refactoring.
3. Obtain owner decisions on authority, licensing, data retention, incident response and sanitized private-repository strategy.
4. Design containment and migration with counts, hashes, reconciliation and rollback before removing or relocating any inherited data.
5. Plan an approved history and credential assessment without printing values or contacting providers.
