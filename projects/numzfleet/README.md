# numzfleet

Add `docker-compose.yml` and `.env` here. Join the external `infra` network to reach `infra-postgres`.

Example env (in app `.env`, not committed with real secrets):

```
DATABASE_URL=postgresql://postgres:YOUR_PASSWORD@infra-postgres:5432/homelab
```
