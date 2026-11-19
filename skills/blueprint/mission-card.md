<!--
Mission card template, used by the blueprint skill (step 6). A mission is one parent ticket in your
tracker; this card is the parent's body: the agreement. The sub-tickets are the work.

- The agent drafts it. The human approves it once, with the blueprint. No sub-ticket starts before that.
- Only the orchestrating agent edits the body, with a fresh read and a surgical edit (skill shared-artifacts).
- Budget in absolute tokens for this mission only.
- Each success criterion is a statement a test, a script or a reviewer can check.
- Each amendment goes into the mission changelog in the same turn as the card edit.
Delete this comment before the card goes into the tracker.
-->
# Mission: {short title}

**Outcome:** {one sentence: what is true when the mission is done}

## Success criteria

Reviewers and CI check each one. A criterion a reviewer thinks is wrong is a `ruling` for the human. Nobody changes the code only to meet it.

- [ ] {checkable statement, with how it is checked}

## Scope

- **In:** {sub-tickets}
- **Out:** {what this mission does not touch}

## Budget

Soft {N} tokens, hard {M} tokens, for this mission only. At the soft cap the next update says so. At the hard cap the mission pauses until the human raises the cap or stops it.

## Run mode

{Who orchestrates (a desk session or a scheduled run), who may start tickets, and where its rules for reviews, merges and signals live.}

## Approval points

These wait for the human: any ADR change, any new hard constraint, any `ruling` finding, a weakened or deleted test, the hard budget cap, the final SHIP, {project-specific items}.

## Update cadence

{Daily | Weekly}, as an update comment on this ticket: progress per criterion, decisions waiting, spend so far.

## Boundaries

- **May touch:** {repo, tracker}
- **Never:** {live systems, people, channels}

## Exit and kill

- **Exit:** all success criteria pass, the update shows the evidence, the human gives the final SHIP. This ticket closes.
- **Kill:** no criterion moves for 3 working days, or the hard cap is hit twice. The mission pauses and the update asks the human: change the card, raise the cap, or stop.

## Changelog

{link to the mission changelog}
