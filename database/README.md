# Database (PostgreSQL)

## Agreed PostgreSQL port

This project’s PostgreSQL instance is configured to listen on **port 5000** (see `startup.sh` and runtime `pg_isready` checks).
All connection strings/env files in this repository should use **5000** consistently.

Connection (from `db_connection.txt`):

- `psql postgresql://appuser:dbuser123@localhost:5000/myapp`

## Schema

The backend creates tables automatically on startup using SQLAlchemy (`Base.metadata.create_all`).

If you need to create the table manually, run (one statement at a time):

```sql
CREATE TABLE IF NOT EXISTS tasks (
  id SERIAL PRIMARY KEY,
  title VARCHAR(255) NOT NULL,
  is_completed BOOLEAN NOT NULL DEFAULT FALSE,
  created_at TIMESTAMPTZ NOT NULL DEFAULT NOW(),
  updated_at TIMESTAMPTZ NOT NULL DEFAULT NOW()
);
```
