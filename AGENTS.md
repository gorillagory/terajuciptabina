# AGENTS.md

## Project

This repository is developed under the independent Arqevo TerajuWorks Recovery & Development programme.

## Boundaries

- Never use Bayam systems, secrets, data or branding.
- `origin` is the controlled fork; `upstream` is read-only.
- The canonical source/controller checkout is `nexus-pbund:/root/workspaces/arqevo`.
- The Windows checkout is reference and authenticated GitHub-ref relay only. Do not edit application source there.
- `nexus-docker` is runtime/database infrastructure only. A runtime artifact is never canonical source.
- Do not deploy without an explicit GO from Iskandar.
- Do not contact or modify upstream without explicit authorisation.

## Safety first

- Do not expose, copy or re-commit inherited personal or project data.
- Do not create real users or exercise live write/payment/AI endpoints during testing.
- Use synthetic fixtures only.
- Stop and report if a change could alter production data, payment state, identity, calculation values or deployment routing.

## Development method

- Work in the canonical checkout on `nexus-pbund`.
- Inspect Git status and read all files in `docs/current/` before changing source.
- Read the active source before editing.
- Preserve BuildPlanner V2 and RenovationPlanner V2 calculations with golden tests.
- Prefer narrow diffs and root-cause fixes.
- Do not add another patch layer when a canonical source can be corrected.
- Keep domain logic independent from UI rendering and persistence.
- Create each bounded task branch as `dev-task/<short-slug>` from current `staging`.
- Promote reviewed and verified task branches into `staging`; do not commit directly to `staging`.
- Treat `staging` as the only source branch for the isolated test environment.
- Promote `staging` into `main` only after recorded test-environment acceptance and an explicit production GO.
- Treat `main` as the production source branch. A merge is not deployment authorisation.
- Never commit directly to `main`, force-push a protected branch or rewrite the inherited baseline.
- Run the relevant tests and record evidence before handoff.

## Project truth

Read and update `docs/current/` for state, decisions, risks, tests, deployment and handover. Chat history is supporting context, not canonical project state.

## Completion report

Return GO/HOLD/NO-GO, verified facts, files changed, tests, remaining risks, next action and the exact branch/commit.
