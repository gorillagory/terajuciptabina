# Deployment State

Updated: 4 November 2026 (MYT)

## Status

**NO DEPLOYMENT.** Arqevo now has a controlled source promotion path, but no application runtime has been allocated, changed or contacted.

## Branch and environment contract

| Purpose | Source branch | Intended runtime boundary | Current state |
| --- | --- | --- | --- |
| Bounded development | `dev-task/<short-slug>` | None | Source work only on `nexus-pbund` |
| Isolated test | `staging` | Proposed `nexus-docker:/srv/docker/apps/arqevo-staging` | Not allocated or deployed |
| Production | `main` | Proposed `nexus-docker:/srv/docker/apps/arqevo` | Not allocated or deployed |

The proposed runtime paths are planning labels, not reservations. They require a fresh read-only collision and capacity preflight before use. Branch promotion never performs or authorises deployment.

## Confirmed non-actions

- No container was built, started, stopped or restarted.
- No Compose project or shared platform service was changed.
- No database, role, schema, volume, secret or runtime data directory was created.
- No port, shared network attachment, proxy, tunnel, DNS record or public hostname was allocated.
- No Vercel, payment, messaging, AI or production mutation endpoint was called.

## Required pre-deployment gates

1. Approved sanitized source and data strategy.
2. Static and synthetic security acceptance for identity and authorization.
3. Planner golden-master test acceptance.
4. Exact source manifest and reviewed runtime artifact boundary.
5. Read-only collision/capacity inventory for the intended Nexus runtime.
6. Dedicated least-privilege database identities and root-owned secret files.
7. Matched backup and isolated restore rehearsal.
8. Recorded image/config/migration/rollback plan.
9. Resolve the self-writing `.github/workflows/development-log.yml` behaviour before any promotion to `main`.
10. Explicit deployment GO from Iskandar.
