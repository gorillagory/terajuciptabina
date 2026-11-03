# Risk Register

Updated: 3 November 2026 (MYT)

| ID | Severity | Risk | Current control | Status |
| --- | --- | --- | --- | --- |
| R-001 | Critical | Personal and project records are tracked in a public repository and history. | Do not print, copy, edit or recommit record contents; inventory metadata only. | Open |
| R-002 | Critical | Temporary ID-based identity can permit unauthorized record access. | No live use; static review and synthetic denial tests only. | Open |
| R-003 | Critical | Server-held GitHub credentials can write operational records without adequate per-user authorization. | Do not configure credentials or call live mutation endpoints. | Open |
| R-004 | High | An expired or unsafe payment bypass may remain reachable. | Treat payment paths as disabled until code and configuration are independently verified. | Open |
| R-005 | High | Planner changes could alter financially material calculations. | Freeze behavior with BuildPlanner V2 and RenovationPlanner V2 golden tests before change. | Open |
| R-006 | High | The `main` push workflow writes a development-log record back to the repository. | No direct `main` pushes; use branch/PR review and assess workflow behavior before merge. | Open |
| R-007 | High | Reusing existing infrastructure without collision checks could interrupt services. | No runtime action; require exact read-only port, database, network, capacity and backup preflight. | Controlled |
| R-008 | High | A public fork may be mistaken for a containment boundary. | Record it as inherited reference/contribution only; private recovery strategy remains an owner decision. | Open |
| R-009 | Medium | Existing tests cover country/currency integrity more than identity, authorization, data migration or calculations. | Expand synthetic unit, contract, migration and golden-master coverage before feature work. | Open |
