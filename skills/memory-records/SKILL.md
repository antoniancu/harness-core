---
name: memory-records
description: Core harness rule (always applies). Use whenever you write, edit, merge, supersede or retire a memory kept across sessions (auto-memory topic files and MEMORY.md, private notes, any "remember this" request). Covers the scope and origin fields, which store a record belongs to, superseding changed decisions into archive/ with a CHANGELOG, and never deleting.
---

# Memory Records
<!-- incidents: an inferred date stored as fact, a disputed memory, project memories written to the wrong store -->

Applies to memory kept across sessions (auto-memory topic files, private notes), not plans or other vault artifacts.

- Mark each record's `scope` (`personal` or `project:<name>`: whose subject it is) and `origin`: `stated` (I said or wrote it to you), `observed` (a tool result or file showed it; cite it) or `inferred` (name what it rests on; use this when unsure). Auto-memory: in frontmatter `metadata`. Notes: in the first line. If the record's owner isn't the store's, write it to the owner's store (personal facts go to private notes; a preference about how agents work everywhere becomes a proposed core rule). If you can't tell which store owns it, don't write; name it in the delivery.
- When I change a decision (a choice I made among options), supersede it: move the old record to the store's `archive/` with `superseded_by: <new>`, give the new record `supersedes: <old>`, and swap the index line. Fix wrong facts in place. Retire to `archive/`, never delete. Log each supersede, merge and retirement in `archive/CHANGELOG.md` (date, what, into what, why). Skip `archive/` when reading current state.
