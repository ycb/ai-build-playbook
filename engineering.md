# Engineering principles

What I ask of code an agent writes. Short on purpose: these are the reminders that still change
outcomes, not a style guide.

- **Small diffs.** Make the smallest change that does the job. No full-file rewrites unless asked.
- **One job per unit.** A function does one thing; a module has one reason to change. If its
  description needs "and", split it.
- **Boundaries by concern.** Data access, domain logic and presentation stay apart, so each can be
  tested alone. Keep pure logic out of components.
- **Compose, don't inherit.** Small pieces passed in beat deep hierarchies.
- **Simple first.** Standard libraries and known patterns before clever ones. Correct before fast;
  optimize a measured bottleneck.
- **Rule of three.** Abstract only once something repeats three times.
- **Errors are features.** Validate inputs, handle failure paths, and say what went wrong.
- **Reuse before adding.** Look for existing code before creating a file, and say where you looked.
- **Say when you're unsure.** Don't guess at an API or a file you can't see.
- **Route by risk.** Use the most capable model where a wrong answer is costly, and a cheaper one for
  mechanical work.
