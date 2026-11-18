---
name: spec-first
description: Use before writing code for any new feature, command, script, automation or behaviour change requested in chat ("add a way to...", "make it...", "build...") when there is no ticket or approved spec. States goal, done-when and how to check in one line first, asks open choices, then reports each done-when item with evidence. Skip for a typo fix, a rename, a question, a lookup, or ticket work.
---

# Spec first (work without a ticket)

origin: a recurring miss, work started from chat without a ticket skipped planning. Distilled from ticket workflows, whose done-when lives in the ticket; chat work has none to inherit.

## 1. Size it by open decisions, not by diff size

- **Always, before you build:** one line in chat, `Goal: ... · Done when: ... · Check: ...`. Each done-when item is checkable (a command, a test, an observable behaviour).
- **One to three open product or technical choices:** read the repo first, so you ask about the choice and not about facts you could look up. Ask each choice one per prompt, with your recommendation (core Never Assume), then add the answers to the line.
- **Four or more, and the work is costly, or others will build from it:** core Never Assume proposes grilling; the spec that comes out of it has goal, constraints, approach (the pick, and one line on what you rejected), non-goals and done when. Save it to the vault only when it's long or shared.
- **A choice surfaces mid-build:** stop and ask; don't settle a design decision inside "just a fix". Headless runs and subagents pick their recommendation, note it as an assumption next to done-when, and continue.

## 2. Report against done-when

Before saying done, report each done-when item with its evidence. An item you couldn't check becomes verify debt (core Stay the Author).

## Don't

- A goal line for a typo fix, a rename, a question or a lookup.
- A spec file or review artifact for small work. The chat line is the spec.
