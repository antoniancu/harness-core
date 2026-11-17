# harness-core

A small set of rules and skills that make an AI coding agent (Claude Code, Codex, others) work the way a busy human needs: it protects your attention, surfaces the hard constraints behind its work, asks one question at a time, and keeps you the author of what ships.

## What's here

| Path | What it is |
|---|---|
| `AGENTS.md` | The core rules every session loads. Locked rules first, then defaults. |
| `PERSONAL.example.md` | Template for your own style layer. |
| `PRINCIPLES.md` | How to change the rules without bloating them. |
| `skills/` | Skills the rules call: `grilling`, `tangents`, `follow-ups`, `bar-review`, `unslop`, `durable-solutions` and more. |

## The ideas that do the most work

- **Protect my time.** Spend agent compute to save human attention.
- **Mental model + hard constraints on every delivery.** You learn how it works and what must stay true, not just "done".
- **Never Assume + grilling.** Count the open decisions; ask one at a time with a recommendation, or run an executive grilling where the agent drafts rulings, a fresh reviewer attacks them, and you approve in one reply.
- **Feet to the fire.** Prove it with production-like data, a preview and another agent driving it, instead of predicting how it will break.
- **Candor over agreement.** The agent holds its position unless you bring a better argument.
- **One thing at a time.** One decision per prompt, bad news first.
- **Stay the author.** Comprehension debt is listed and closed with evidence.
- **Tangents get parked, not chased.**

## Install (Claude Code)

```sh
git clone https://github.com/antoniancu/harness-core.git ~/Dev/harness-core
cd ~/Dev/harness-core
cp PERSONAL.example.md PERSONAL.md        # then edit it; it's gitignored

# Refuses to overwrite an existing global CLAUDE.md: merge by hand if you have one.
test -e ~/.claude/CLAUDE.md && echo "~/.claude/CLAUDE.md exists, merge by hand" || \
  printf '@~/Dev/harness-core/AGENTS.md\n@~/Dev/harness-core/PERSONAL.md\n' > ~/.claude/CLAUDE.md

mkdir -p ~/.claude/skills
for s in ~/Dev/harness-core/skills/*/; do ln -sn "${s%/}" ~/.claude/skills/; done
```

`git pull` updates the rules and skills in place; your `PERSONAL.md` stays untouched.

## Install (Codex and other agents)

Codex doesn't follow `@` imports, so build one file from both layers and rebuild it after each `git pull`:

```sh
mkdir -p ~/.codex
cat ~/Dev/harness-core/AGENTS.md ~/Dev/harness-core/PERSONAL.md > ~/.codex/AGENTS.md
```

Install the skills wherever your agent reads agentskills.io skills (for Codex, `~/.codex/skills/`, or `~/.agents/skills/` for agents that share that path).

## Credits

`grilling`, `prototype`, `domain-modeling`, `research`, `writing-for-agents` and part of `shared-artifacts` are adapted from [mattpocock/skills](https://github.com/mattpocock/skills) (MIT). The notice is in `skills/LICENSE-mattpocock-skills.md`.
