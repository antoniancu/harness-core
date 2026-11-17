---
name: database-safety
description: Core harness rule (always applies, CRITICAL). Use before ANY database CLI operation (supabase db push, db reset, migration up, db dump, link; psql or any migration tool against a shared database). Confirms which database the CLI is pointed at and states the target out loud.
---

# Database Safety (CRITICAL)


- **Always confirm which database the Supabase CLI is linked to before ANY `db` operation** (`supabase db push` / `db reset` / `migration up` / `db dump`). The link is sticky and silent: after working a preview branch the CLI stays linked to that branch, so the next `db push` can silently hit the wrong DB.
- Before operating: run `supabase projects list` (the linked row is flagged) or read `supabase/.temp/project-ref`, and state the target out loud.
- Any other database CLI (psql, prisma, a migration runner): print the connection target it will use (host and database name, never the password) and state it out loud before running a write.
