---
name: ticket-authoring
description: Use whenever you write or rewrite a ticket or issue body (Linear, GitHub, a local ticket file), including sub-tickets cut from a plan. Owns what goes in the body so someone who was not in the room can pick the ticket up cold.
---

# Ticket authoring

A ticket body is read **cold**: by an assignee, a reviewer or an agent who was not in the meeting, the chat or the thread that produced it. Write for that reader. Every rule below serves one test: could they act on this ticket with nothing but the ticket and the links in it?

This skill owns ticket body content. Neighbours own the rest:

| Concern | Owner |
|---|---|
| Body content (this file) | `ticket-authoring` |
| Read the live body before replacing it, edit surgically | `shared-artifacts` |
| Slicing a plan into tickets, blocking edges | `blueprint`, or your own slicing skill |
| A project's ticket layout, grouping and create flow | that project's own rules |

## Rules

Apply every rule to every body you write or rewrite. Done means each rule checked against the final text, not the draft.

1. **Every reference stands alone.** Each label, codename, layer or region id, meeting, doc, design or thread the ticket mentions is a working link or gets a plain-words definition where it first appears. Prefer the link; when there is none, say what the thing is in a clause ("the A1 chat menu, the dropdown above the composer"). Check: list every proper noun, id, acronym, codename, numbered label ("L1-L4", "region 2c"), dated or "the X" reference ("the Oct 27 call", "the content matrix", "the proposal in the design thread"). Each item on the list has a link or a definition at its first use. You wrote the shorthand, so you can't trust your own sense of what reads clearly; the list is the check.
2. **Separate now from target.** Describe today in present tense under a "Now" heading. Describe the target under a "Target" heading, with "should" for behaviour and "must" for a hard constraint. Do not use "Should" as a heading. A bare present-tense sentence in a scope list reads as either, so "It does not select the card" becomes "It should not select the card". Check: outside "Now", no sentence describes behaviour in plain present tense.
3. **Design tickets show the target.** Put a capture of each target design frame (exported from Figma or the design tool) in the body next to its link, so the target reads at a glance without opening the file. Describe the current state in words; add a screenshot of it only when one is already at hand, since capturing it adds a stage. Check: every design link in the body has its capture beside it.
4. **Name the work by area.** Under a "Work by area" heading, say which area each piece of work belongs to: frontend, backend or agent, design. Write "none" for an area with no work, so nobody waits on a person who has nothing to do. Check: a reader can tell who does what without reading code.

## Lessons

Where each rule came from. Newest first. A rule without a lesson row doesn't belong above.

| Rule | Lesson |
|---|---|
| 4. Name the work by area | An assignee read a frontend-only ticket as blocked on the agent team, because the body did not say which area owned the work. |
| 2. Separate now from target (heading) | "Should" as a heading read oddly; the target section is now headed "Target". |
| 3. Design tickets show the target | A design ticket linked design frames without captures, so a reader had to open the file to see the target. Current-state screenshots were dropped as a required step because they add a capture stage. |
| 2. Separate now from target | A scope list said "It does not select the card": the reviewer could not tell whether that was today's behaviour or the target. |
| 1. Every reference stands alone | A parent's sub-tickets leaned on team shorthand (menu codes, layer ids, a dated call, a doc and a design thread) with no link or definition; the assignee could not act on them. |

### Adding a lesson

When your human corrects a ticket body:

1. Fix the ticket.
2. Draft the rule: one numbered entry under Rules, the target behaviour stated positively, with a check that tells done from not-done. If it sharpens an existing rule, draft the edit to that rule instead.
3. Show your human the rule text in one prompt, with their correction quoted. Their yes makes it their change; a no or a rewrite from them wins.
4. On their yes: add the Lessons row and ship the change. Without it, park the draft where your harness keeps proposals, and say so.
