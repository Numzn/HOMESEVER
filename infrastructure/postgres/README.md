# Shared PostgreSQL (infra)

Single Postgres instance for homelab apps. Container name: **infra-postgres**. Docker network: **infra** (external for other stacks).

## Deploy (on the server)

```bash
cd /srv/infrastructure/postgres
cp .env.example .env
# Set a strong POSTGRES_PASSWORD in .env
docker compose up -d
docker compose ps
docker compose logs -f postgres
```

## Health checks

```bash
docker compose ps
docker exec infra-postgres pg_isready -U postgres -d homelab
docker inspect infra-postgres --format '{{.State.Health.Status}}'
docker network inspect infra --format '{{.Name}}'
```

## Connection (from other containers on `infra`)

Hostname: `infra-postgres`  
Port: `5432`

```
postgresql://USER:PASSWORD@infra-postgres:5432/DBNAME
```

Use credentials from this stack’s `.env` only in app `.env` files on the server — not in git.

## App stacks: join the network

In `/srv/projects/<app>/docker-compose.yml`:

```yaml
services:
  myapp:
    # ...
    networks:
      - infra

networks:
  infra:
    external: true
```

Do **not** add another `postgres` service in app compose files; use `infra-postgres` as the host.

## Sync from laptop

From the HOMESERVER repo root:

```bash
./scripts/sync-to-server.sh
```

Then deploy on the server as above.
