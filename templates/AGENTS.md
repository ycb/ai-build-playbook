# Agent working agreement

More than one agent builds this repository, taking turns. Either must be able to stop at any commit and
let the other continue without the conversation that produced it. Git, the ExecPlan and
`LEARNINGS.md` are the only shared memory.

## Read first, every session

1. `README.md`: what the product is and why.
2. The current ExecPlan (`docs/plans/`): **Progress**, the newest **Session Log** entry, and the task
   you're about to start.
3. `LEARNINGS.md`.
4. `git log --oneline -15` and `git status`. A dirty tree means the last session stopped mid-task:
   read its Session Log entry before touching anything.

Don't redo work whose Progress box is checked and whose evidence is recorded. If the evidence is
missing, re-run the verification instead of re-implementing.

## Who decides

- The human owns the problem, the concepts, design review, product decisions and every production step.
- Agents propose and implement. Before building anything visible, align on the problem, then
  concepts, then a mockup.
- Ask before anything that can't be undone.

## Unit of work

One ExecPlan task per commit series. A task is done only when:

1. Its tests were written first and seen failing, then passing.
2. Its verification commands pass.
3. The ExecPlan is updated in the same commit or the next one:
   - tick the Progress box;
   - add a dated **Verification Evidence** line naming the agent, the commands and what they showed;
   - add **Decision Log** or **Surprises** entries for anything a successor would rediscover.

## Verification

| Check | Command | Needs |
| --- | --- | --- |
| Lint, unit, build | `<command>` | |
| Database or integration | `<command>` | |
| End to end, real stack | `<command>` | |

Evidence names the check that produced it. A stand-in (a mock, a local harness) is weaker than the real
stack: say which ran, and re-run the authoritative check before anything ships.

## Ending a session (required, even when stopping early)

Leave the tree committed, then add an entry at the top of the ExecPlan's Session Log:

```markdown
### YYYY-MM-DD HH:MM — <agent>
- Done: <tasks or steps, with commit hashes>
- State: <clean | wip commit <hash>: what's half-finished>
- Verified with: <which checks>
- Next: <the exact next step, and anything to re-check>
```

Unfinished work is committed as `wip: <task> — <what remains>`, never left uncommitted.

## Commits

- Conventional prefixes: `feat:`, `fix:`, `docs:`, `chore:`, `test:`, `wip:`.
- A trailer naming the agent: `Agent: <name>`.

## Hard boundaries

- Synthetic data only in code, fixtures, tests and screenshots.
- Never commit or paste credentials, keys, `.env` files or exports. The human handles secrets.
- No remote or production changes without an explicit checkpoint with the human.
- Migrations are append-only once committed; fix forward.
