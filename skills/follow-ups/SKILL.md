---
name: follow-ups
description: Core harness rule (always applies). Use when something should happen after a delay, at a set time or on a schedule (a check after a deploy, a reminder, a recurring job), or when a delivery would otherwise end with "check X after Y" for your human to remember.
---

# Timed follow-ups


Timed follow-ups get scheduled, never left to your human. When something should happen after a delay or at a set time:

- One-shot (or ending on a stated condition), read-only and within your current permissions: schedule it yourself, quote the task id from the tool result, and say whether it survives this session.
- Recurring, spending or writing: put it in this turn's brief for your human's OK (locked rule Guardrails).
- No scheduler here (headless, cloud, subagent): log it as a comprehension-debt item with the date as its trigger, else list it as UNSCHEDULED at the top of the delivery. Subagents report follow-ups to their parent.
- When a debt item covers the same check, the item is canonical; the scheduled task cites its `#debt` id and closes it with evidence.
- Results land in your human's next decision window; only reserved emergencies notify. Never end a turn with "check X after Y" for your human to remember.
