---
name: replication-appendix
description: Ends every shared artifact whose conclusions rest on data (queries, API pulls, counts, rates, percentiles) with a Replication Appendix another person's agent can rebuild it from. Use when writing a report, memo, nice spec, PDF, research note, ticket or PR body that presents quantitative findings. Appended by default, without asking.
---

# Replication Appendix

Adapted from Garry Tan's `methodology-appendix` skill (x.com/garrytan/status/2122586989082059129, 2026-11-17). Readers of our artifacts hand them to their own agents; the appendix is what lets those agents check and extend the work.

## The test

A reader with an agent and equivalent data access regenerates every number and rebuilds the document from the appendix alone, without asking the author anything. If they would need to ask "which column?", "pulled when?" or "how do I rebuild this?", the appendix failed.

It is a recipe, not a citation list. The body keeps stating findings plainly; method lives here.

## When it fires

Fires on a **data spine**: any shared artifact where a headline number, table of counts, rate or percentile came from a query, API or script you ran. Nice specs, research notes, analysis memos, PDFs for others, tickets and PR bodies that argue from data.

Narrative, qualitative or decision-only writing has no data spine and gets no appendix: meeting notes, plans without numbers, ordinary PR bodies, chat answers.

## The six sections

Write them in this order under `## Replication Appendix` (in a nice spec, a collapsed section at the end).

1. **Header.** Access required (tool or CLI plus auth, internal APIs, database by name) and the snapshot date (ISO). Live data won't reproduce exactly after it; point to Drift.
2. **Signal choice and outcome sensitivity.** The analysis usually turns on one column, threshold or filter. Table it: field, what it is, chosen or rejected and why. Then one **Outcome sensitivity** line: what the headline becomes under the strongest defensible alternative ("switching to `score_b` moves the count from 412 to 268 and drops claim 2"). This is the most important section; never skip it, even when the answer is "no defensible alternative changes the conclusion".
3. **Verbatim queries.** Every query or command that produced a number, copy-pasteable, in document order, labelled with the finding it supports. Paste what ran, not a retyped version. Add the schema notes a replicator would get wrong: enum meanings, non-obvious joins, columns that look present but aren't.
4. **Derivation.** Pseudocode from raw counts to the figures in the body, with every assumption as a named constant the reader can swap (`YIELD_HAIRCUT = 0.10..0.15  # marginal cases convert below observed rate`). Constants that change the recommendation are flagged as such.
5. **Rebuild.** Exact commands from the source of record to the delivered artifact, plus the visual check (`nicespec push` and the page URL; `pdfinfo` page count and a rendered page or two for PDFs). Name the source of record: the rendered page or PDF is never the original.
6. **Drift and gaps.** What was mid-flight at snapshot, coverage gaps (fields only populated for part of the range, and how you restricted rather than shipped a misleading denominator), what the data cannot see, and any claim retracted between versions with why.

## Procedure

1. Log each query verbatim as you run it (a scratch file in the work's vault folder). Reconstructed SQL is how appendices go wrong.
2. Write the analysis.
3. Append the six sections before rendering or pushing.
4. On revision, update the appendix in the same change as the finding; an appendix describing a superseded method misleads.

## Scope guard

Verbatim queries carry table names, ids and sometimes rows. The appendix stays inside the project or organisation the data belongs to and never carries personal facts into a shared artifact (core rule Personal Stays Private). Redact values, never the query shape; say what was redacted.

## Done when

- [ ] Every headline number traces to a pasted query and the derivation.
- [ ] Signal choice is named, with alternatives and an Outcome sensitivity line.
- [ ] Assumptions are named constants, not prose.
- [ ] Rebuild commands ran and the visual check was looked at.
- [ ] Drift, gaps and retractions are stated.
