# AGENTS.md

## Project

This repository is developed under the independent Arqevo TerajuWorks Recovery & Development programme.

## Boundaries

- Never use Bayam systems, secrets, data or branding.
- `origin` is the controlled fork; `upstream` is read-only.
- The server working clone is canonical. Avoid divergent local copies.
- Do not deploy without an explicit GO from Iskandar.
- Do not contact or modify upstream without explicit authorisation.

## Safety first

- Do not expose, copy or re-commit inherited personal or project data.
- Do not create real users or exercise live write/payment/AI endpoints during testing.
- Use synthetic fixtures only.
- Stop and report if a change could alter production data, payment state, identity, calculation values or deployment routing.

## Development method

- Read the active source before editing.
- Preserve BuildPlanner V2 and RenovationPlanner V2 calculations with golden tests.
- Prefer narrow diffs and root-cause fixes.
- Do not add another patch layer when a canonical source can be corrected.
- Keep domain logic independent from UI rendering and persistence.
- Use feature branches and PR review; never commit directly to `main`.
- Run the relevant tests and record evidence before handoff.

## Project truth

Read and update `docs/current/` for state, decisions, risks, tests, deployment and handover. Chat history is supporting context, not canonical project state.

## Completion report

Return GO/HOLD/NO-GO, verified facts, files changed, tests, remaining risks, next action and the exact branch/commit.
