# Containment Audit

Updated: 3 November 2026 (MYT)

## Scope and safety

This is a static audit of source commit `4903807239d8b34cf665bb1a42d8383d11973124`. It did not call a live API, configure a credential, create a user, send a message, initiate or verify a payment, invoke an AI provider, modify data, or touch a runtime service. Record values were not copied into this report.

## Tracked data inventory

- `data/` contains 229 tracked files totalling 22,468,319 bytes.
- 227 JSON files parse successfully; the other two files are documentation (`data/rates/README.md` and `data/users/README.md`).
- Account records: 80 homeowner JSON files and 90 contractor JSON files.
- Project-control records: 31 contractor JSON files.
- Other tracked data includes class registration/slot files, calculation rules, rate sets, analytics, a contractor database and a development log.
- The earlier bootstrap note stated 81 homeowner account files; the current inherited SHA contains 80. Treat the current Git tree as verified and the earlier count as historical until reconciled.

### Field-name classification

This classification counts files containing matching JSON keys; it does not inspect or reproduce the values.

| Field class | Files |
| --- | ---: |
| Email | 171 |
| Phone | 171 |
| Person/company name | 200 |
| Address | 35 |
| Account identity (`homeownerId` / `contractorId`) | 200 |
| Authentication/password metadata | 170 |
| Payment | 1 |
| Project/quotation/estimate/contract/progress | 165 |

The authentication/password classification is produced by `auth` and `passwordStored` keys. It is not evidence that plaintext passwords are stored in those records.

## Confirmed application exposure

| ID | Severity | Evidence | Finding |
| --- | --- | --- | --- |
| C-001 | Critical | `api/auth.js:194-206` | `GET` accepts only role and ID, then returns the account record. No user authentication or record authorization is enforced. |
| C-002 | Critical | `api/auth.js:210-244` | Contractor profile `PATCH` accepts role and ID and writes the record without authenticating the account owner. |
| C-003 | Critical | `api/quotations.js:8,93-165` | Quotation `GET`, `POST`, `PUT` and `DELETE` are selected by role/account ID; the server GitHub token is the effective write authority. |
| C-004 | Critical | `api/project-control.js:7,138-180` | Project-control `GET`, `PUT` and `DELETE` use supplied account/project identifiers without per-user authorization. |
| C-005 | Critical | `api/payment.js:43-59,124-131` | The detailed-quotation promotion bypass is hard-coded `true`; verification accepts any bill code beginning `BYPASS-` as paid. |
| C-006 | High | `api/admin.js:90-97` and related admin APIs | Administrative authority is a shared header password/key, not a named identity with scoped roles and durable actor audit. |
| C-007 | High | `api/floor-plan-ai.js:520-525` | The AI endpoint accepts `POST` without user authentication. Browser CORS is not an authorization boundary and does not prevent direct requests or provider-cost abuse. |
| C-008 | High | `api/auth.js:247-313` | Public signup writes a GitHub account record and can send Resend email and WhatsApp messages when providers are configured. |
| C-009 | High | `.github/workflows/development-log.yml` | Every normal push to `main` can cause a second workflow-authored commit to repository data. |

## External trust boundaries

The API source references 23 environment-variable names spanning GitHub, admin credentials, Vercel Blob, ToyyibPay, Resend, WhatsApp, Groq, OpenAI and OpenRouter. Hard-coded provider hosts also include GitHub, Vercel, Meta, Resend, ToyyibPay and AI-provider endpoints. None was contacted during this audit.

## Secret-signature check

- The current checkout was checked for common GitHub, OpenAI-style, AWS and private-key signatures without emitting matches.
- One case-insensitive AWS-style signature occurred inside a 95,739-character `profile.logoDataUrl` image data URI. It is classified as an encoded-image false positive, not a credential finding.
- No credible common-prefix secret was identified in the current checkout by this bounded scan.
- Git history and provider-side credential validity have not been scanned. Credential rotation and history rewriting require separate authority and planning.

## Containment conclusion

The inherited application is **NO-GO for production continuation** in its current identity, authorization and payment state. The repository remains **GO only for controlled read-only recovery, synthetic tests and owner-approved containment work**.

## Required next controls

1. Fence or disable inherited live mutation, payment, messaging and AI routes before any user-facing continuation.
2. Introduce named authentication, session/token lifecycle and server-side per-record authorization.
3. Remove operational data from Git through an owner-approved, reconciled migration to dedicated storage.
4. Rotate exposed or inherited provider credentials after ownership is confirmed; do not print them during verification.
5. Replace payment bypass logic with fail-closed entitlement verified against authoritative provider state.
6. Add synthetic denial tests for cross-account reads/writes, admin boundaries, payment forgery and provider-cost abuse.
7. Preserve planner behavior with golden fixtures before structural refactoring.
