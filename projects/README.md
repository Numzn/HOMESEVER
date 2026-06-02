# Application projects

Each app gets its own directory with its own `docker-compose.yml` and `.env`. Apps connect to shared infra (e.g. Postgres) via the external **infra** network — they do not run their own database container.

| Project   | Path          | Notes                    |
|-----------|---------------|--------------------------|
| numzfleet | `numzfleet/`  | Placeholder — add compose |
| numz-ai   | `numz-ai/`    | Placeholder — add compose |

## Postgres from an app

```yaml
networks:
  infra:
    external: true
```

Connection host: `infra-postgres:5432` (see [infrastructure/postgres/README.md](../infrastructure/postgres/README.md)).
