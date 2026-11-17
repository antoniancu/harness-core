---
name: grilling
description: Grill the user relentlessly about a plan, decision, or idea, interactively or executive style (you draft researched rulings, a fresh reviewer attacks them, the user approves in one reply). Use when the user wants to stress-test their thinking, uses any 'grill' trigger phrases, or when the core Never Assume rule calls for a grilling session.
---

Interview the user relentlessly until you reach a shared understanding. Map this as a **design tree**: every decision branches into the decisions that hang off it.

Work the tree **one question at a time**. The **frontier** is every decision whose prerequisites are already settled: the questions you can ask _now_ without guessing at answers you haven't heard yet. Pick the most important frontier question and ask only that one, then wait for the answer before the next.

Ask through the host's question tool so the user answers with a tap: AskUserQuestion in Claude Code, or the equivalent buttons in other hosts. Put your recommended answer first, marked "(Recommended)", and show progress as "Q2 of 5" (the total may grow as answers open new branches; say so when it does). Never print the frontier as a list in chat first. Only when no question tool exists, fall back to one question per message:

```
❓ **Q2 of 5 - <question title>**: <question body, including the choices>

➡️ <your recommended answer>
```

Word each question so one tap (or "yes" in plain text) accepts your recommended answer.

Each answer reshapes the tree: settled decisions push the frontier outward and unblock questions that depended on them. Recompute the frontier and ask the next question.

Finding _facts_ is your job, never the user's. When a frontier question needs a fact from the environment (filesystem, tools, etc.), dispatch a sub-agent with a fresh context window to find it; don't ask the user for anything you could look up yourself. Don't block on it: a running exploration is an unsettled prerequisite, so only the questions downstream of it wait for the sub-agent to report; keep asking the other frontier questions meanwhile. The _decisions_ are the user's: put each to them and wait.

The session is done when the frontier is empty: every branch of the design tree visited, nothing left silently assumed. Do not act on it until the user confirms you have reached a shared understanding.

## Executive style

When the user picks "Executive" (core Never Assume says when to recommend it), you draft the rulings and the user approves them in one reply. It needs a live user: headless runs follow Never Assume's headless line instead.

1. **Sort the decisions.** Fact decisions are judgement calls whose best answer needs research beyond a quick lookup (code, data, vendor behaviour). Preference decisions turn on the user's priorities, taste or risk appetite; a decision that mixes both counts as preference. Ask the preference ones first, one per prompt as above.
2. **Draft the fact ones.** Pick the recommended option for each, researching as deeply as it needs. Draft in the main session; use parallel drafting subagents only when the run spans separate topics, and tell the user how many before you start.
3. **One review round, always.** A fresh reviewer (core Red Team briefing, judging against skill `bar-review`) attacks the whole draft against the goal and the plan, with evidence. Revise from its findings. This is the Red Team round for these decisions; building them later still gets its own round when core Red Team calls for one, and an amendment that changes a hard constraint gets a second review. Write the draft and the review report to the work's notes folder.
4. **One summary, answerable in one reply.** The shape first (a diagram, or an indented outline where the channel can't render one), then:
   - **Needs your yes:** numbered, each with your recommendation: rulings that change or reopen an earlier decision, and every ruling that touches money, state, auth, or another person or team.
   - **Applied:** the rulings the facts settle on their own, one line each naming the fact and its source, and the review's fixes.
   - The review's high and medium findings you rejected, each with the reason; the hard constraints kept; the comprehension debt (core Delivery rule).

   Nothing is recorded as a ruling until the user approves. They approve, amend, or ask to dig into a point.
5. **Scenario check after the yes.** Picking Executive opts the user into this. Give 3 to 5 concrete scenarios (real-shaped data, anonymised) and ask the user to predict each outcome, one per prompt. Where their prediction differs from the ruling, amend it and put the amendment back as one "needs your yes" line before recording. Skip this step when no ruling has data-shaped behaviour to predict.
