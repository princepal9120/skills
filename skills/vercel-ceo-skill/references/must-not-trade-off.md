# Segment 04 — Must-not-trade-off rules

Chapter: [07:12]–[08:25]

## Framework

**Trade-offs are constant** [07:12] [seen]: Features vs time, speed vs polish vs cost. Some properties cannot be traded away because they define the product.

**Agents must pick** [07:28] [seen]: Everything an agent builds has trade-offs (speed vs safety). It cannot spend unlimited effort, so it chooses. If you do not pre-agree the rules, the model takes you wherever it wants [07:28] [seen].

**Where your time goes** [07:28] [seen]: Spend human attention on whether the app does what it is supposed to do, and how fast it needs to be.

**Must-not-trade-off section** [07:56] [seen]: Dedicated section in the project instruction file listing invariants you will never give up. Caption text: `claw.md` in the project root [07:56] [seen]. Treat as `CLAUDE.md` (and/or `AGENTS.md`) [07:56] [guessed].

**Rules without tests are forgotten** [07:56] [seen]: The file is only written instructions. Agents hold a lot of context and drop rules. Every rule needs a check the agent can run. Commit those tests so the agent cannot skip them [08:25] [seen].

**Pair with `/direction`** [08:25] [seen]: The direction command from segment 02 is the plan-alignment counterpart. Use both: direction for "are we building the right thing", tests for "did we violate an invariant".

## Technique

1. Draft the must-not-trade-off list before feature work [07:56] [seen].
2. For each bullet, add an automated test or gate [07:56] [seen].
3. Commit the tests [08:25] [seen].
4. Run `/direction` after landings so silent drift does not bypass the list [08:25] [seen].

## Example rule shapes (inferred)

Source did not list Vercel's actual invariants [07:56] [unknown]. Typical entries that fit the framework [07:56] [guessed]:

- Auth and session checks stay on every mutating route.
- Customer data never written to logs.
- Payments cannot be marked success without a provider confirmation.
- Public pages meet the first-time-user critical path (see seg06).

## Anti-patterns

- Putting preferences ("use prettier") in the same bucket as invariants [07:12] [guessed].
- Rules with no test, relying on the model to "remember" [07:56] [seen].
- Letting the agent delete or skip failing invariant tests to ship [08:25] [seen].
