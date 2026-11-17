---
name: shared-artifacts
description: Core harness rule (always applies). Use before writing or editing any PR body (gh pr create, gh pr edit), ticket or issue description, Linear or Notion doc, wiki page, shared spec, or review reply that replaces existing text. Covers PR template adherence (read .github/pull_request_template.md, same headings in the same order, fill every section), PR body content (smallest visual, before/after evidence, one-way or two-way door call) and read-before-replace on artifacts other agents and humans edit (re-fetch, edit surgically, recover from body history).
---

# Shared artifacts: PR bodies, tickets, docs


## PR Body Template Adherence (CRITICAL)

Every PR body follows the repo's own `.github/pull_request_template.md`, including PRs opened manually with `gh pr create`.

- **Read the template from disk first** (`cat <repo>/.github/pull_request_template.md`). It is the source of truth, not memory or a hardcoded copy: the team edits it and it varies per repo.
- **Match it perfectly:** exact same section headings, in the exact same order. No added sections, no reordering, no renaming. Don't prepend a `## Summary` or move a section out of its template position.
- **Fill EVERY section** the template defines. Never silently drop a heading. If a section genuinely doesn't apply, keep the heading with a one-line "N/A - <reason>" (e.g. `_N/A - docs-only PR, no UI._`).
- **Don't edit `.github/pull_request_template.md`** to fit a PR: it's shared team config.
- Check off all template todos by default (`[x]`).

## PR Body Content

What goes inside the template's sections. The template still decides the headings; these rules never add, rename or reorder one. Adapted from Matt Pocock's `pr` skill (mattpocock/skills@5863806, MIT; its visual menu credits Dex Horthy's `show-me`).

- **Smallest visual first.** In the section that summarises the change, lead with the smallest view that makes the point: pseudocode, a call tree, a component tree, a shallow file tree, a Mermaid diagram, or a `diff` sketch of one of those. Put it next to the sentence it supports, and keep only the parts that answer the reader's question.
- **Before and after evidence.** Show that it works: screenshots when the change is visual and the setup allows it, else test runs or command output (the test that failed before and passes now).
- **Door call.** Say whether merging is a one-way door (destructive, hard to reverse) or a two-way door (cheap to roll back), and name the blast radius: what else could break.
- **No template in the repo?** Use `## Summary`, `## Evidence` and `## Merge Danger`, in that order.

## Shared Artifacts Have Other Writers: Read Before You Replace (CRITICAL)

PR bodies, ticket descriptions, Linear/Notion docs, wiki pages and shared specs are mutable surfaces that agents and humans edit concurrently. A blind overwrite silently destroys someone else's work: screenshots, verification results, review notes.

- **Never push a full replacement from a local copy or from memory.** Re-fetch the live version immediately before writing (`gh pr view --json body`, `gh api .../pulls/N -q .body`, Linear `get_issue`), then apply your changes to THAT text.
- **Edit surgically.** Change the sections you mean to change; leave everything else byte-identical. Wholesale rewrites are only safe when nobody else has touched the artifact.
- **Assume a co-writer on any agent-delegated ticket.** If another agent is on the same ticket or stack, it is actively editing: the window between your read and your write is where the loss happens.
- **Media and verification results are the usual casualties.** Screenshots, browser-test findings and "I checked X" notes are exactly what an agent adds and what a rewrite drops.

**Recovery when it happens anyway.** GitHub keeps full body history and the `diff` field is the complete body at that revision, not a patch:

```bash
gh api graphql -f query='{ repository(owner:"OWNER", name:"REPO") {
  pullRequest(number: N) { userContentEdits(first: 20) {
    nodes { editedAt editor { login } diff } } } }'
```

Take the last good revision, re-apply your intended edits on top, push once. Then say plainly what was lost and restored.
