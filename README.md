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
- **Candor over agreement.** The agent holds its position unless you bring a better argument.
- **One thing at a time.** One decision per prompt, bad news first.
- **Stay the author.** Comprehension debt is listed and closed with evidence.
- **Tangents get parked, not chased.**

## Install (Claude Code)

```sh
git clone <this repo> ~/Dev/harness-core
cp ~/Dev/harness-core/PERSONAL.example.md ~/Dev/harness-core/PERSONAL.md   # then edit it
ln -s ~/Dev/harness-core/AGENTS.md ~/.claude/CLAUDE.md                     # back up any existing file first
echo '@~/Dev/harness-core/PERSONAL.md' >> ~/.claude/CLAUDE.md
for s in ~/Dev/harness-core/skills/*/; do ln -s "$s" ~/.claude/skills/; done
```

For Codex or other agents, point their global `AGENTS.md` at the same file and install the skills where that agent reads them.

Some skills are adapted from others' work and say so in their own files (for example Matt Pocock's skills, MIT).
