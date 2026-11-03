# Test Evidence

Updated: 3 November 2026 (MYT)

## Baseline

- Source: `4903807239d8b34cf665bb1a42d8383d11973124`.
- Command: `node --test tests/*.test.js`.
- Result: **PASS — 36 passed, 0 failed, 0 skipped**.
- Duration reported by Node: approximately 185 ms.
- Test mode: offline Node test runner with synthetic mocks; no live GitHub write, user, payment, messaging or AI endpoint was exercised.
- Governance-branch revalidation after the containment documentation update: **PASS — 36 passed, 0 failed, 0 skipped** in approximately 206 ms.

## Static containment audit

- Inventory scope: 229 tracked files under `data/`, totalling 22,468,319 bytes.
- Parse result: 227 JSON files parsed successfully; the other two tracked files are `data/rates/README.md` and `data/users/README.md`.
- Account/control counts: 80 homeowner account files, 90 contractor account files and 31 contractor project-control files.
- Static API review confirmed ID-selected account access, identifier-selected quotation/project-control mutation, server-held GitHub write paths and an active detailed-quotation payment bypass.
- A bounded common-prefix secret scan emitted no values. One AWS-style signature was classified by JSON path and type as an encoded image-data false positive; no credible common-prefix secret was found in the current checkout.
- No live endpoint, provider, credential, container, database, network, DNS route or deployed service was exercised.

## Coverage limits

- The suite is concentrated on country/currency integrity and legacy-market handling.
- It is not evidence of secure authentication or per-record authorization.
- It is not a golden-master suite for BuildPlanner V2 or RenovationPlanner V2.
- It does not prove production data migration, backup restore, deployment or rollback behavior.
- The secret-signature check did not scan Git history and is not history clearance.
- Synthetic authorization-denial, payment fail-closed and provider-abuse tests are still required.
