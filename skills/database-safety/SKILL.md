---
name: database-safety
description: Core harness rule (always applies, CRITICAL). Use before ANY database CLI operation, especially Supabase (supabase db push, db reset, migration up, db dump, link), psql against a shared database, or applying migrations. Confirms which database the CLI is linked to and states the target out loud.
---

# Database Safety (CRITICAL)


- **Always confirm which database the Supabase CLI is linked to before ANY `db` operation** (`supabase db push` / `db reset` / `migration up` / `db dump`). The link is sticky and silent: after working a preview branch the CLI stays linked to that branch, so the next `db push` can silently hit the wrong DB.
- Before operating: run `supabase projects list` (the linked row is flagged) or read `supabase/.temp/project-ref`, and state the target out loud. The project's `AGENTS.md` lists known refs.
