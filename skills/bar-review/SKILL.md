---
name: bar-review
description: Judge finished work against a named bar, "would the best team in the world ship this?", and answer SHIP, REJECT or ESCALATE with evidence. Use when you are the reviewer handed a diff, PR, plan, spec or design: a red team, a fresh review chat or subagent, or a review stage in a pipeline.
---

# Bar review

The bar: **would the best team in the world ship this?** Picture the strongest team you know of for this kind of work, reading the artifact cold. Reject until the answer is yes.

## What you judge

The artifacts (diff, PR, plan, spec, design, screenshots, test output) and the intent: what the work is for and what done looks like. Judge the work as it stands. If the brief carries the builder's reasoning ("I did X because Y"), set it aside: a reader of the shipped work never sees it, so it can't be what makes the work pass. The one exception is the builder's answers to earlier findings (Rounds).

Verify claims yourself, read-only: read the code the diff calls, open the page. Run tests and builds only when the brief names them. Deploys, pushes and writes to shared state stay with the caller.

Design and prose go through the same bar. For prose, apply the `unslop` checklist; for visuals, look for the generic AI look (default gradients, stock layouts, filler copy). These findings are low severity unless they change the meaning.

## Verdict

The first line of your reply is exactly one of `VERDICT: SHIP`, `VERDICT: REJECT` or `VERDICT: ESCALATE`; callers route on it. For a plan or spec, SHIP means build it as written and REJECT means revise it first.

**SHIP** when the best team would ship it as is. Under the verdict, list what you checked and how, one line each (tests run, files read, claims verified), and anything you couldn't check, so the SHIP can be proven wrong. Nits that wouldn't stop that team follow, marked optional.

**REJECT** when it falls short. Each finding carries:

- **Severity:** high (wrong, unsafe, breaks the intent or a hard constraint); medium (works, but a named reader would be misled or a named next change gets harder); low (optional). A REJECT needs at least one high or medium finding.
- **Evidence:** `file:line`, command output, a screenshot, a quoted spec line. Something the builder can open, not your impression.
- **The fix:** concrete enough that a builder in a fresh chat can act on it without asking you.

**ESCALATE** only in a review loop, as below.

## Rounds

The caller owns the loop: it counts rounds, keeps the reports and passes them in the brief. A brief with no round number is a single review: judge it once and leave rounds out of the reply.

From round 2, the brief also carries the builder's answer to each earlier finding: fixed, kept with a reason, or rejected with a reason. Rule on each against the evidence. A fix that holds, or a rejection whose reason checks out, closes the finding; the rest stay open and block. A new finding blocks only when it's high and you verified it in code or output you actually saw. Anything else new (a medium, a low, a worry about a file you couldn't open) goes under the verdict as an optional note or a question. This is how the loop converges instead of moving the goalposts each round.

Rounds 1 and 2 end in SHIP or REJECT. Round 3 is core's agent-to-agent cap: work that would still be rejected gets ESCALATE, which hands the human the choice core offers: step in, or approve 3 more rounds. List the findings still open and what each round changed. As a subagent or headless run, return the ESCALATE to your parent; the parent raises it with the human.

Single-round callers (core Red Team, the grilling skill's executive review) decide themselves whether a second round runs; this skill adds no rounds there.

## Trivial changes

Trivial means no behaviour change: prose, comments, formatting. A config value or dependency bump counts only when it touches no money, auth, permissions, persistent data, secrets or major version; otherwise review it normally. For a trivial change, check that it does what it says, then reply with `VERDICT: SHIP`, one line on what you checked, and one on anything you couldn't. The bar is the same; the review is as small as the change.
