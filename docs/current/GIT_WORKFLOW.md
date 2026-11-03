# Git Workflow

Updated: 4 November 2026 (MYT)

## Promotion path

```text
dev-task/<short-slug> -> staging -> main
bounded development     test       production source
```

Promotion and deployment are separate operations. No merge authorises a runtime change.

## Start a task

Run in `nexus-pbund:/root/workspaces/arqevo`:

```bash
git status --short --branch
git switch staging
git fetch --prune origin
git merge --ff-only origin/staging
git switch --create dev-task/<short-slug>
```

Stop if the checkout is dirty, `staging` cannot fast-forward, the expected refs differ or an operation would require rewriting history.

## Develop and verify

1. Read `AGENTS.md` and every relevant file in `docs/current/`.
2. Make the smallest bounded change on the task branch.
3. Use synthetic fixtures and offline/read-only checks until containment gates pass.
4. Run relevant tests plus `git diff --check`.
5. Record outcome, tests, remaining risks and the exact commit.

## Publish and review

The preferred end state is a repository-scoped write credential on the canonical server. Until separately approved, use the clean Windows checkout only to relay the exact server-created task ref to `origin`; do not edit application source there. Open a pull request from the task branch into `staging`.

## Promote to test source

Prefer a reviewed pull-request merge into `staging`. If the GitHub review path is unavailable, an evidence-bound `--no-ff` merge may be made on the canonical server and its exact `staging` ref relayed to the controlled fork. Re-fetch and prove that local `staging`, `origin/staging` and the reviewed merge SHA agree.

Deployment to the isolated test environment is a later, separately authorised operation.

## Promote to production source

`staging` may merge into `main` only when all of the following are recorded:

1. Containment, identity, authorization, payment and provider-cost controls are accepted.
2. The isolated test environment has passed acceptance.
3. BuildPlanner V2 and RenovationPlanner V2 golden tests pass.
4. Backup, restore and rollback have been rehearsed.
5. The self-writing development-log workflow has been resolved.
6. Iskandar gives explicit production GO.

The resulting `main` commit is eligible source; it is not deployment authorisation.

## Prohibited actions

- No direct commits to `staging` or `main`.
- No force-push or protected-ref history rewrite.
- No changes to the inherited baseline tag.
- No application-source editing in the Windows relay checkout.
- No use of runtime copies as source.
- No copying personal credentials or SSH keys between hosts.
- No deployment, migration, restart, public routing or provider call as a side effect of Git promotion.
