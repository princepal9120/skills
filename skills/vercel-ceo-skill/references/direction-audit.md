# Segment 02 — Direction over volume (`/direction`)

Chapter: [02:09]–[04:07] (sponsor after [04:07] omitted)

## Framework

**Tokens ≠ progress** [02:09] [seen]: People judge AI work by tokens spent or changes shipped. Those numbers report volume. You can ship continuously and still go nowhere.

**Cheap-build drift** [02:37] [seen]: With agents, building is the cheap part. A feature can exist in minutes. Every idea-while-building becomes a feature; the agent will not refuse because it does not know which features matter.

**Plan already exists** [02:37] [seen]: The `specs/` folder (requirements + PRD) is the heading. The failure mode is the running app slowly leaving that plan.

**`/direction` command** [03:07] [seen]: Ask the agent to create a command named `direction` that checks whether built work matches the plan. Tell it where the plan folder lives. On Claude Code it lands in the commands folder under the Claude folder; reload plugins so the session can run `/direction` [03:07] [seen].

## What the command does

1. Spawn a separate agent per requirements document in the plan folder [03:39] [seen].
2. Main agent independently looks for changes that appear in no plan [03:39] [seen].
3. Merge into a report: on-course or off-course, plus a **scorecard** and an action list [03:39] [seen].
4. Human (or follow-up agent) either:
   - keeps the drift and **updates the requirement docs**, or
   - **removes** the drifted changes [03:39] [seen].

## Implementation notes

- Name the slash command `/direction` or `direction` — both match the source wording [03:07] [seen].
- Point it at `specs/` (or whatever folder holds PRD + requirements) [03:07] [seen].
- Hermes/Codex hosts: implement the same audit as a named skill or prompt command if slash-commands differ [03:07] [guessed].
- Exact scorecard dimensions were not specified [03:39] [unknown]. Reasonable axes: % of PRD capabilities present, count of unplanned surfaces, must-not-trade-off violations [03:39] [guessed].

## Anti-patterns

- Celebrating token burn or PR count as "using AI well" [02:09] [seen].
- Letting the agent keep adding features because each one "works" [02:37] [seen].
- Running `/direction` and ignoring the drift list [03:39] [guessed].
