# Segment 03 — Security debt and slop debt

Chapter: [05:09]–[07:12]

## Framework

**Security debt** [05:09] [seen]: Security problems that accumulate while working with agents. Agents write more code than was previously possible, so no human can personally review all of it.

**Attackers have agents too** [05:10] [seen]: Models are good and cheap at finding holes. Anyone who wants to cause harm can point an agent at your app. Advice: get ahead — protect as you go, not after a pile-up [05:34] [seen].

**Rule 1 — scan after each feature** [05:34] [seen]: Run security scans once a feature is built. Vercel shipped **DeepSec** to find gaps in agent-written code [05:34] [seen]. You may use your own scanners; DeepSec is one path.

**DeepSec loop (if used)** [05:52] [seen]:

1. Run DeepSec setup → creates a `.deepsec` folder.
2. Paste the provided prompt into Claude Code so it writes a short file about the app and how people sign in.
3. Ask Claude to run the scan.
4. Read the report.

**Rule 2 — budget slop debt** [06:30] [seen]: Slop debt is messy code you **choose** to accept in order to move fast. Fine on a small / non-critical app. Dangerous on the parts customers trust (data safety, core quality).

**Quality gates ≠ tests** [06:30] [seen]: Tests answer "does it work?". A quality gate answers "is it good enough?". Typical gate: a review agent that holds every change to your standards. Nothing goes live until every gate passes [06:58] [seen].

## Technique

- After each merged feature: security scan (DeepSec or equivalent) [05:34] [seen].
- Before building: decide which surfaces may carry slop and which may not [06:30] [seen].
- Install a review agent as a blocking gate on critical paths [06:58] [seen].
- Pair gates with `/direction` so "good enough" still matches the plan [06:58] [guessed].

## Anti-patterns

- Human-only review of agent-scale diffs [05:09] [seen].
- Treating green unit tests as a quality bar [06:30] [seen].
- Accepting slop on auth, payments, or customer data "because it's an MVP" [06:30] [guessed].

## Unknowns

- DeepSec product internals and current CLI flags [05:52] [unknown].
- Which scan classes the CEO runs at Vercel beyond DeepSec [05:34] [unknown].
