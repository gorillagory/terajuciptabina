# Risk Register

Updated: 3 November 2026 (MYT)

| ID | Severity | Risk | Current control | Status |
| --- | --- | --- | --- | --- |
| R-001 | Critical | Personal and project records are tracked in a public repository and history. | Do not print, copy, edit or recommit record contents; inventory metadata only. | Confirmed |
| R-002 | Critical | Temporary ID-based identity can permit unauthorized record access. | No live use; static review and synthetic denial tests only. | Confirmed |
| R-003 | Critical | Server-held GitHub credentials can write operational records without adequate per-user authorization. | Do not configure credentials or call live mutation endpoints. | Confirmed |
| R-004 | Critical | The detailed-quotation bypass is hard-coded active and accepts any `BYPASS-` bill code as paid. | Treat payment paths as disabled; replace with fail-closed provider-backed entitlement before any continuation. | Confirmed |
| R-005 | High | Planner changes could alter financially material calculations. | Freeze behavior with BuildPlanner V2 and RenovationPlanner V2 golden tests before change. | Open |
| R-006 | High | The `main` push workflow writes a development-log record back to the repository. | No direct `main` pushes; use branch/PR review and assess workflow behavior before merge. | Confirmed |
| R-007 | High | Reusing existing infrastructure without collision checks could interrupt services. | No runtime action; require exact read-only port, database, network, capacity and backup preflight. | Controlled |
| R-008 | High | A public fork may be mistaken for a containment boundary. | Record it as inherited reference/contribution only; private recovery strategy remains an owner decision. | Open |
| R-009 | Medium | Existing tests cover country/currency integrity more than identity, authorization, data migration or calculations. | Expand synthetic unit, contract, migration and golden-master coverage before feature work. | Open |
| R-010 | High | Administrative authority is a shared header secret rather than a named, scoped actor identity. | No live admin use; design named roles, durable audit and synthetic denial tests. | Confirmed |
| R-011 | High | The AI endpoint lacks user authentication and can expose provider cost to direct-request abuse. | Do not configure provider credentials or call the endpoint; add identity, rate and cost controls. | Confirmed |
| R-012 | High | Public signup can write repository data and trigger email/WhatsApp side effects when providers are configured. | No live signup; replace with contained identity workflow and mocked provider tests. | Confirmed |
