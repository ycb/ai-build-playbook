# Examples

## Ours: two agents, one codebase

[Ours](https://github.com/ycb/ours-public) is a private web app for couples to plan time together. It
was built by Codex and Claude taking turns under this repo's `AGENTS.md`, and went from first commit
to real use in a week. The human made every product call and ran every production step.

What the process caught:

- **The real stack beats the stand-in.** Database tests ran on a lightweight harness during the build,
  and every Verification Evidence entry said so. The first authoritative run on the real stack
  confirmed all 1,108 assertions before the database work was trusted.
- **End-to-end tests drift unless they run.** After a week of UI changes without a real-stack run, the
  browser tests no longer matched the screens. Running them caught the stale steps, and one real bug:
  hidden form controls 250 px wide, which scrolled the page sideways on phones.
- **Look at the product, not just the tests.** Reviewing screenshots exposed what passing tests
  didn't: a 44 px gap from an empty status line, button labels breaking onto two lines, an attribution
  link with nothing to attribute. Each fix got a test where one could catch it.
- **A rename isn't a rewrite.** Repositioning the product by swapping keywords left the old framing
  visible in every sentence. Copy for a new purpose gets drafted from scratch.
- **Handoffs need a written state.** Every session ended with a Session Log entry, so either agent
  could stop mid-task and the other could pick up without the conversation.

## Narrata: the AI-system layer

[Narrata](https://github.com/ycb/narrata-cover-letter-agent) is where the
[article's](https://roadmaps.substack.com/p/how-i-design-ai-systems-a-complete) other half applies:
primitives, orchestration, evals and guardrails. One example: running resume and cover letter analysis
in parallel cut the upload pipeline from about 108 seconds to about 27, with the same models and
prompts. Orchestration mattered more than prompting.
