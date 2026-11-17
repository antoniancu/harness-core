---
name: motion
description: Core harness rule (always applies). Use for any frontend or design work that adds, changes or reviews animation, transitions, motion tokens, easing or durations, including "animate this", Figma or prototype motion specs, and UI reviews that touch movement.
---

# Motion Principle (Frontend + Design)


Motion communicates a meaningful change (state, hierarchy, cause -> effect) and stays behind the content. Target: **intentional, subtle, predictable**. Every animation answers "what change does this tell the user about?"; when nothing answers, the change is instant.

- **Unspecified motion** (I ask for an animation and no sanctioned source defines it: Figma, prototype, motion spec): design to this principle. Reuse the codebase's existing motion tokens and patterns, keep distances small and durations short, animate the fewest properties that carry the change, and keep the same interaction animating the same way everywhere.
- **Specified motion that breaks the principle**: build the spec as given, then flag it with a gentle pushback. Name the element, what breaks (competes with content, adds noise, unpredictable), and the quieter alternative. Frame it as a refinement to bring back to the designer; the spec stands until I decide.
