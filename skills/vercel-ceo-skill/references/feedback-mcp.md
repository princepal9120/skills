# Segment 07 — Fast customer feedback loop (MCP)

Chapter: [12:34]–[13:32] (AI Labs Pro / CTA after that omitted)

## Framework

**Adoption tell** [12:34] [seen]: One of the best ways to judge how well a company uses agents is what happens when a customer reports a problem: does someone reply properly, check what went wrong, and — if it is a clear bug — actually fix it? Measure elapsed time from report to fix [13:02] [seen].

**Two kinds of feedback** [13:02] [seen]:

| Kind | Example | Action |
| --- | --- | --- |
| Clear / mechanical | Screenshot of a dead button; payment failing | Fix as fast as possible; no product debate [13:02] [seen] |
| Ambiguous / human | "I'm confused by the app" | Cannot become a prompt yet; talk to the customer first [13:02] [seen] |

## MCP wiring

**Connect the inboxes** [13:02] [seen]: Attach Claude to where feedback already arrives via MCP servers.

- **Gmail MCP** — read support email [13:32] [seen].
- **Sentry MCP** — errors the app hits even when no customer wrote in [13:32] [seen].

**Triage** [13:32] [seen]: Claude reads each new report and sorts it. Broken (payment failing) → fix immediately. Needs judgment → escalate to a human.

## Technique

1. Wire support + error MCPs (Gmail/Sentry or the project's equivalents) [13:32] [seen].
2. Classify: clear defect vs ambiguous product signal [13:02] [seen].
3. Auto-fix only the clear bucket; open a human thread for the rest [13:32] [seen].
4. Track time from report-in to fix-out as the health metric [13:02] [seen].
5. Slack/Linear/other support MCPs are reasonable stand-ins when Gmail is not the inbox [13:32] [guessed].

## Anti-patterns

- Turning "I'm confused" into an unattended code change [13:02] [seen].
- Measuring agent quality by tokens while this loop is slow [12:34] [guessed].
- Ignoring Sentry because "nobody filed a ticket" [13:32] [seen].

## Unknowns

- Exact SLA Vercel uses for report-to-fix [13:02] [unknown].
- Whether the auto-fix path requires a human merge gate [13:32] [unknown].
