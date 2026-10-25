# Cheatsheet — Vercel CEO agent workflow

## Decision rules

| If you see… | Do this | Evidence |
| --- | --- | --- |
| Idea or prompting-guide claim | New project + agent check; do not trust vibes | [00:47] [seen] |
| PRD exists, no running product | Agent MVP of **basic** features only | [01:50] [seen] |
| Lots of tokens / PRs, unclear heading | Run `/direction` against `specs/` | [02:09] [seen] |
| `/direction` lists drift | Update the docs **or** delete the extra surface | [03:39] [seen] |
| Feature just landed | Security scan (DeepSec or equivalent) | [05:34] [seen] |
| Path is customer-critical | Quality gate ("good enough"), not tests-only | [06:30] [seen] |
| Path is throwaway / internal | Slop debt allowed if you named it | [06:30] [seen] |
| Agent choosing speed vs safety | Must-not-trade-off section + a test per rule | [07:56] [seen] |
| Happy-path tests all green | Run breaker on a **data copy** | [08:25] [seen] |
| You "already know" the UX | First-time-user agent; hooks block repo read | [10:58] [seen] |
| About to ship | Browser-path agent; persist JSON | [12:34] [seen] |
| Support ping or Sentry issue | Clear bug → fix now; confusion → human | [13:02] [seen] |

## Trade-off matrix

| Spend | Starve | Never starve |
| --- | --- | --- |
| Tokens, extra features [02:09] [seen] | Unplanned surfaces [02:37] [seen] | Direction vs plan [03:07] [seen] |
| Speed on non-critical slop [06:30] [seen] | Review time on toys [06:30] [guessed] | Security on trusted paths [05:09] [seen] |
| Agent autonomy on clear bugs [13:32] [seen] | Auto-code for fuzzy UX complaints [13:02] [seen] | Must-not-trade-off tests [07:56] [seen] |

## Tells (you're off course)

- Progress updates that quote token counts [02:09] [seen].
- Features the PRD cannot name [02:37] [seen].
- Invariant rules with zero failing tests possible [07:56] [seen].
- QA done by the builder agent on the intended path [08:44] [seen].
- "New user" agent with file-read tools enabled [11:49] [seen].
- Long gap from customer report to a fix [13:02] [seen].

## Command stubs

```text
/direction          # scorecard + drift vs specs/
/breaker            # isolated, copy-on-write, find-fix-rerun
/first-time-user    # browser only; hooks deny read/edit
/error-free         # critical paths → JSON before ship
/feedback-triage    # MCP inboxes: auto-fix vs escalate
```

Host names may differ [03:07] [guessed]; keep the jobs identical.
