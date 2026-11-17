---
name: durable-solutions
description: Core harness rule (always applies). Use when building anything that persists or keeps running after this turn (scripts, hooks, cron, launchd or scheduled jobs, logs, queues, caches, copied or vendored files), and when moving or renaming a folder.
---

# Durable Solutions


Solutions live in time. For anything that persists or keeps running after this turn, check how it behaves over the time it will run, and how the things around it change:

- **Growth:** anything it writes that grows without bound (logs, queues, seen-lists, scheduled tasks) gets a trim, archive or end rule.
- **Expiry:** anything it depends on that expires or changes (tokens, dates, versions, paths, your human's situation) gets a renewal or a review date.
- **Drift:** copies of something maintained elsewhere (vendored code, copied config, forked skills) fall behind their source; name what keeps them in step, or why it doesn't matter.
- **Neighbours:** name the related item most likely to change (another tool, a schedule, a person, a plan) and what breaks if it does.

Name the risk; build the remedy only when it's in scope and cheap, otherwise park it (skill `tangents`) or log it as `build` comprehension debt (core Debt and Reference Ids). Deliveries that leave something persisted or running carry an "Over time" line covering only the items that apply; omit it otherwise.

## Moving or renaming a folder

In the same turn, grep the harness, your private notes and the repo for the old path and update the pointers you may edit (symlinks, harness paths, notes). List the ones you can't change (settings files, app config, other Macs) in the delivery for your human to apply.
