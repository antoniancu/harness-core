# Principles for changing the harness

Read this before changing the rules or skills. `AGENTS.md` holds the rules every session loads; this file governs how those rules evolve.

1. **Protect your human's time.** The core first principle applies here too: every rule must earn its read cost.
2. **Personal fit over generic advice.** Keep what a frontier model can't know or wouldn't choose on its own: facts about your world (people, projects, paths, tools), your preferences among valid options, and corrections to failures actually seen (cite the incident). Cut generic best practice the model already follows. Test by removing the line and checking whether behaviour changes.
3. **Model-agnostic.** The harness should work the same on Claude, GPT or whatever comes next. Write instructions as plain prose in `AGENTS.md` files, skills in the agentskills.io format, and keep vendor-specific parts (hook config, tool names, plugin settings) in clearly marked places. Lock-in comes through convenience: before relying on a vendor-hosted feature (memory, scheduler, connector, cloud state), note where its state lives and how to export it.
4. **Don't hamper the model.** Push back on any instruction that could make a capable model worse: rigid steps for judgment work, shouted emphasis, rules that fight the model's defaults without evidence. Tag lines that work around today's model behaviour.
5. **Tangent handling is the core capability.** It's what compounds across work and life. Judge every change by two tests: no tangent gets lost (each is parked where it can be revived at the right time), and the main thread still finishes on time and in scope.
6. **Compounding.** Every correction lands once in its right home (rule, skill, hook, memory) and pays off in every later session. Measure: repeat corrections trend to zero.
7. **Three costs.** Each change should lower one of being wrong, complexity, or the cost of change, without raising the others much.
8. **Contain the blast radius.** Per-project rules keep failures local. Nothing depends on a single model, machine or runner without a tested fallback.
9. **Sort a change by its flow.** Riverbed changes (core rules, protocols) need the strongest objections answered and a decision record. Skills and notes stay cheap to add. Anything that spends attention or money gets a budget. For riverbed changes that touch other people, run the veil test: would you accept this rule if you were on the receiving end?
10. **Circulate or retire.** A memory, rule or skill unused for 90 days gets promoted to where it fires, merged, or archived. Parked ideas too: a tangent with no next action after 90 days moves to a dated archive file (revivable, never deleted).
11. **Capability isn't adoption.** A rule counts once a test prompt shows it changes behaviour. Test both sides: one prompt for the failure the rule prevents, one for over-applying it where it doesn't fit (every principle fails when pushed too far).
12. **Reshape the landscape before adding a rule.** Make the right action the easiest path (a default, template, skill step or hook) instead of more prose. Adding a rule is the moment to look for one to remove.
13. **Two speeds.** Sessions are the fast engine; the harness is the slow engine. Changes you ask for ship right away. Agent-proposed changes are parked and batched (weekly works), with one red team on the batch's combined effect. Safety fixes ship immediately.
14. **Simplest technique first.** Add a technique only with data or a measurable hypothesis.

## Tags

HTML comments: greppable, invisible when rendered.

- `<!-- model-sensitive: <why> -->` compensates for today's model behaviour. Re-test at every model release.
- `<!-- vendor: <name> -->` only works on one vendor's tooling (e.g. `claude-code`). Needs an equivalent elsewhere.

## At each model release

1. `grep -rn "model-sensitive" .`
2. On the new model, run your test prompts with and without each tagged line.
3. Keep, rewrite or delete it, and record the result in the commit message.

This is the counterweight to overfitting: the harness is tuned to today's projects, tools and models.
