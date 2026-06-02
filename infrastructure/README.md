# Infrastructure stacks

One Docker Compose project per subdirectory. Shared services only — apps live under `/srv/projects/`.

| Stack    | Path       | Purpose              |
|----------|------------|----------------------|
| postgres | `postgres/`| Shared PostgreSQL 16 |

Deploy from the stack directory on the server: `docker compose up -d`.
