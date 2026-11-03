# Environments

Updated: 4 November 2026 (MYT)

## Host roles

| Host or service | Role | Boundary |
| --- | --- | --- |
| `nexus-pbund` | Canonical source/controller | Git work, review evidence, promotion control |
| GitHub controlled fork | Review and ref exchange | Pull requests and exact controlled refs |
| `nexus-docker` | Runtime/database host | Approved artifacts only; never canonical source |
| Windows checkout | Reference and authenticated GitHub-ref relay | No application-source editing |

## Branch-to-environment mapping

| Stage | Branch | Runtime boundary | Current state |
| --- | --- | --- | --- |
| Task | `dev-task/<short-slug>` | None | Source and offline/synthetic verification only |
| Test | `staging` | Proposed `nexus-docker:/srv/docker/apps/arqevo-staging` | Absent |
| Production | `main` | Proposed `nexus-docker:/srv/docker/apps/arqevo` | Absent |

Proposed paths are not reservations. Before either path is created, repeat a read-only inventory for port, network, database, volume, secret, backup and route collisions.

## Promotion boundaries

- A task branch may merge into `staging` only after its diff and test evidence are reviewed.
- `staging` is the sole test-environment source branch.
- `staging` may merge into `main` only after recorded test acceptance, all production gates and explicit production GO.
- A branch merge does not deploy, restart, migrate, publish or route an application.
- Runtime deployment requires its own exact manifest, preflight, rollback evidence and explicit GO.

## Git transport

The canonical server checkout currently has read access but no GitHub write credential. Until a repository-scoped server credential is separately approved, the clean Windows checkout may relay an exact server-created ref to the controlled fork. It must not author application changes. Never copy a personal credential or SSH key to bridge this gap.
