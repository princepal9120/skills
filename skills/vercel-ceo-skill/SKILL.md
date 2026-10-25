---
name: vercel-ceo-skill
description: "Apply Vercel CEO agent-building workflow from the AI Labs breakdown (youtube.com/watch?v=y2ifUC9_zuU). Use when setting up a /direction audit, breaker agent, must-not-trade-off rules, security/slop-debt gates, first-time-user agent, or support/Sentry MCP feedback loop."
---

# Vercel CEO agent workflow

Production playbook from AI Labs' breakdown of Vercel CEO (Guillermo Rauch) interview tips. Direction over token vanity. Sponsor segments omitted.

Evidence: `[mm:ss]` + `[seen]` spoken in source, `[guessed]` inferred, `[unknown]` not stated.

## Core frameworks

1. **Spec-then-MVP, not vibes** [00:47] [seen]: Spin a fresh project; have an agent verify from scratch. Prompting-guide folklore (example: "Astra likes this prompt") is worthless until you check. Start from a `specs/` PRD, then ask the agent for an MVP of basic features before building the full app [01:19] [seen].

2. **Direction over volume** [02:09] [seen]: Tokens spent and diffs shipped measure activity, not heading. Agents make building cheap, so every side idea becomes a feature. Install a `/direction` (or `direction`) command that diffs the repo against the plan folder, emits a scorecard + drift list, then either update the docs or delete the drift [03:07] [seen].

3. **Security debt + slop debt** [05:09] [seen]: Agents write more code than humans can review; attackers have agents too. Scan after each feature (Vercel DeepSec or equivalent) [05:34] [seen]. Slop debt is mess you accept for speed on non-critical paths; critical paths need quality gates (review agent + "good enough", not just "works") [06:30] [seen].

4. **Must-not-trade-off rules** [07:12] [seen]: Agents always pick speed vs safety. Put non-negotiables in a must-not-trade-off section of `CLAUDE.md` / `AGENTS.md`. Every rule needs a test so the agent cannot silently skip it; pair with `/direction` [07:56] [seen]. Caption ASR said `claw.md` [07:56] [seen] — treat as `CLAUDE.md` [07:56] [guessed].

5. **Breaker agent** [08:25] [seen]: Adversarial agent that copies production-like pressure (concurrency, clashes, latency, skipped steps). Copy data so prod stays safe. Find → fix → re-run loop, optionally continuous [09:13] [seen].

6. **First-time-user + error-free sessions** [10:26] [seen]: Favorite metric: sessions that complete without error. An agent uses the app as a new customer without reading code; hooks block read/edit/delete except running the app [11:19] [seen]. Separate browser-path agent covers critical flows and writes JSON results before ship [12:18] [seen].

7. **Feedback MCP loop** [12:34] [seen]: Judge agent adoption by report → reply → root-cause → fix latency. Clear bugs (broken button, failed payment) auto-fix; ambiguous ("I'm confused") escalate to a human. Wire support/Sentry (and similar) via MCP [13:02] [seen].

## When to load a segment

| Topic | File |
| --- | --- |
| Fresh-project MVP / anti-vibe testing | `segments/seg01-test-ideas-mvp.md` |
| `/direction` command, scorecard, drift | `segments/seg02-direction-audit.md` |
| Security scans, slop debt, quality gates | `segments/seg03-security-slop-debt.md` |
| Must-not-trade-off + tests | `segments/seg04-must-not-trade-off.md` |
| Breaker agent + copy-on-write data | `segments/seg05-breaker-agent.md` |
| First-time-user hooks + error-free sessions | `segments/seg06-first-time-user.md` |
| Support/Sentry MCP triage | `segments/seg07-feedback-mcp.md` |

Also: `cheatsheet.md`, `patterns.md`, `glossary.md`, `timestamps.md`, `sources.md`.

## Agent defaults

- Prefer `/direction` after any non-trivial feature landing.
- Never skip must-not-trade-off tests to "save tokens" [07:56] [seen].
- Do not let a first-time-user agent read the repo [11:49] [seen].
- Do not run a breaker against live customer data [09:55] [seen].
- Auto-fix only unambiguous production defects; escalate product confusion [13:02] [seen].
