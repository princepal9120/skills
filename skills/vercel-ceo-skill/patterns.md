# Patterns — Vercel CEO agent workflow

Step-by-step techniques. Each step is cited.

## Pattern: Spec → MVP (do not skip)

1. Create `specs/` and write the PRD of main features [01:19] [seen].
2. Open a new project; do not bolt the idea onto an existing app [00:47] [seen].
3. Prompt the agent: MVP of those basic features only [01:50] [seen].
4. Use the running MVP to keep or kill the idea [02:09] [seen].

## Pattern: Install `/direction`

1. Tell the agent the plan folder path (`specs/` or equivalent) [03:07] [seen].
2. Ask it to create a `direction` command under the host commands directory (Claude Code: commands folder inside the Claude folder) [03:07] [seen].
3. Reload plugins / restart so the command is in-session [03:07] [seen].
4. Run it: one sub-agent per requirements doc; main agent hunts unplanned changes [03:39] [seen].
5. Consume the scorecard: update docs to match kept drift, or revert drift [03:39] [seen].

## Pattern: Security scan after a feature

1. Finish the feature [05:34] [seen].
2. DeepSec path: setup → `.deepsec/` → paste bootstrap prompt (app + sign-in) → ask Claude to scan → read the report [05:52] [seen].
3. Non-DeepSec path: same cadence with your scanner [05:52] [seen].

## Pattern: Quality gates for slop control

1. Label surfaces: slop-OK vs critical [06:30] [seen].
2. On critical paths, add a review agent that checks "good enough", not only "works" [06:58] [seen].
3. Block release until every gate is green [06:58] [seen].

## Pattern: Must-not-trade-off with teeth

1. Add a **must-not-trade-off** section to `CLAUDE.md` / `AGENTS.md` [07:56] [seen].
2. Write one automated test (or gate) per rule [07:56] [seen].
3. Commit the tests [08:25] [seen].
4. Re-run `/direction` so plan drift cannot hide an invariant break [08:25] [seen].

## Pattern: Breaker find-fix loop

1. Prompt a breaker whose job is to break the app; operate on data copies only [09:13] [seen].
2. Cover concurrency, clashing actions, skipped steps, latency, peer comparison [08:44] [seen].
3. Run in a separate context window [09:55] [seen].
4. Fix from the report; re-run until clean [09:55] [seen].
5. Optionally leave a continuous review loop [10:26] [seen].

## Pattern: First-time-user + path JSON

1. Create a browser-only agent that does not know the product [11:19] [seen].
2. Hook: deny bash except "run the app"; deny read/edit/delete of source [11:49] [seen].
3. Create a second agent that walks every required customer step and writes JSON [12:18] [seen].
4. Gate ship on that JSON [12:34] [seen].

## Pattern: Feedback MCP triage

1. Connect MCP to support mail and error stream (Gmail + Sentry in the video) [13:32] [seen].
2. Classify each item: clear defect vs needs a conversation [13:02] [seen].
3. Auto-fix payments/buttons that are objectively broken [13:32] [seen].
4. Escalate "I'm confused" to a human [13:02] [seen].
5. Record time from report to fix [13:02] [seen].
