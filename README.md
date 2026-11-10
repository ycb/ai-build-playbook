# AI Build Playbook

How I build products with AI coding agents: the working agreement, plan and handoff templates I use
with Codex and Claude, and what they've caught in practice.

The thinking behind it is in
[How I design AI systems](https://roadmaps.substack.com/p/how-i-design-ai-systems-a-complete):
the model is not the product, and the system around it is. This repo is the kit that puts the article's
workflow into practice.

## The loop

1. **Define, design, deliver.** Agree on the problem, explore a few concepts, mock up the one you pick.
   The human approves before any code.
2. **Phase the work.** Proof of concept, then the UX, then data quality. Don't polish a flow around
   something that doesn't work yet.
3. **Plan each task.** An exec plan states scope, success criteria and how it will be verified.
4. **Test first.** Watch the test fail, then make it pass.
5. **Verify on the real thing.** Say which check produced the evidence, and how strong it is.
6. **Hand off.** End every session with a log entry either agent can pick up from.
7. **Memorialize learnings.** Anything a successor would otherwise rediscover goes in `LEARNINGS.md`.

The human owns product decisions, design review and every production step. Agents implement.

## What's here

| File | Use |
| --- | --- |
| [`templates/AGENTS.md`](templates/AGENTS.md) | The working agreement. Codex, Cursor and most agents read `AGENTS.md` |
| [`templates/CLAUDE.md`](templates/CLAUDE.md) | Points Claude at `AGENTS.md`, so both agents follow one agreement |
| [`templates/EXECPLAN.md`](templates/EXECPLAN.md) | Plan, progress, decisions, evidence and the session log |
| [`templates/LEARNINGS.md`](templates/LEARNINGS.md) | Short, durable lessons the agents read every session |
| [`engineering.md`](engineering.md) | Code principles: small, clear, tested, minimal diffs |
| [`examples.md`](examples.md) | Where this came from, and what it caught |

## Use it

Copy `templates/` into a new repo's root, fill in the verification commands in `AGENTS.md`, and start
the first task from `EXECPLAN.md`. Keep `docs/plans/` out of Git if the plans are for the agents only.
