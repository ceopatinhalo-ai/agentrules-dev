# PostgreSQL & Supabase Database Security Guard Standards
# Targets: PostgreSQL 16+, Supabase, Prisma, Drizzle ORM, Row Level Security (RLS)

## 1. Zero-Downtime Migration Policy
- Never add `NOT NULL` columns to existing tables without a safe default value.
- Add indexes concurrently in production (`CREATE INDEX CONCURRENTLY idx_users_email ON users(email);`).
- Never delete or rename columns directly in production. Follow the Expand and Contract pattern:
  1. Expand: Add new column.
  2. Write to both old and new columns.
  3. Backfill existing records.
  4. Contract: Drop old column in a subsequent release.

## 2. Row Level Security (RLS) & Hard Guardrails
- Enable RLS on ALL public-facing Supabase tables (`ALTER TABLE profiles ENABLE ROW LEVEL SECURITY;`).
- Write granular policies for `SELECT`, `INSERT`, `UPDATE`, and `DELETE`.
- Always verify tenant isolation (`WHERE auth.uid() = user_id` or `WHERE org_id = (SELECT current_org_id())`).
- Restrict `service_role` keys strictly to backend microservices; never expose service keys to client-side code.

## 3. Query Performance & Connection Pooling
- Always use PgBouncer / Supabase Transaction Pooler for serverless or edge runtimes.
- Avoid `SELECT *`. Select only explicit columns needed by the schema.
- Log queries running longer than 100ms via `pg_stat_statements`.
