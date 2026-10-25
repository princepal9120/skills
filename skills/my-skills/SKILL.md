---
name: my-skills
description: "Prince Pal's skill-library index. Use when watching a video and wanting to convert it into a skill via video-to-skill, and when browsing Prince's skill library to pick, route to, or add a package."
---

# my-skills

Single entry point for this repository. Load this skill to discover every other skill, decide which one to apply, or add a new video-derived package with [video-to-skill](https://github.com/opentoolsorg/video-to-skill).

Do not implement product-workflow advice from this file. Route to the matching skill and read that package.

## Catalog

Scan `skills/*/SKILL.md` in this repo. The table below must list **every** package except this aggregator. When a new folder appears under `skills/`, add a row here in the same change.

| Skill | Path | When to use |
| --- | --- | --- |
| `vercel-ceo-skill` | `skills/vercel-ceo-skill/` | Agent-first product workflow from the AI Labs breakdown of Vercel CEO tips: `/direction` audits, breaker agents, must-not-trade-off rules, security/slop debt, first-time-user agents, feedback MCP loops. Source: https://www.youtube.com/watch?v=y2ifUC9_zuU |

## How to pick a skill

1. Match the user's job to the **When to use** column. Prefer the most specific package.
2. Read that package's `SKILL.md` first (frameworks + topic index).
3. Open only the `segments/`, cheatsheet, or patterns files the task needs. Do not dump the whole package into context.
4. If nothing matches, say so. Offer to convert a source video (below) rather than inventing a skill from memory.

Routing hints:

- Direction drift, token vanity metrics, `AGENTS.md` / `CLAUDE.md` invariants, adversarial QA, new-user sessions, or support/Sentry fix loops → `vercel-ceo-skill`.
- "I watched a talk / YouTube video and want a skill" → stay here and run the converter workflow.

## Convert a video with video-to-skill

Converter: https://github.com/opentoolsorg/video-to-skill

1. Confirm the user wants a **library skill** (frameworks, commands, anti-patterns), not a one-off summary.
2. In Hermes, Claude Code, or Codex (with the converter installed):

   ```text
   /video-to-skill <video-or-course-url> [custom-skill-name]
   ```

3. Expect a package with `SKILL.md` (YAML `name` + `description`, lean, <=4k tokens), `segments/segNN-*.md`, `cheatsheet.md`, `patterns.md`, `glossary.md`, `timestamps.md`, and `sources.md`.
4. Every claim must include `[mm:ss]` and `[seen|guessed|unknown]`. Omit sponsor segments.
5. Copy the generated folder to `skills/<skill-name>/` in this repo. Do not commit raw media, transcripts with secrets, or absolute home paths.
6. Update **this** catalog in the same change (see below).
7. Optionally symlink into the host skills directory:

   - Claude Code: `~/.claude/skills/<skill-name>`
   - Hermes: `~/.hermes/skills/<skill-name>`
   - Codex: `~/.codex/skills/<skill-name>`

If video-to-skill is not installed, point the user at the converter repo and the install notes in this library's root `README.md`. Do not hand-author a video skill unless they explicitly ask to draft one from provided notes.

## Update this index

When adding, renaming, or removing a skill:

1. Ensure `skills/<name>/SKILL.md` exists with `name` and `description` frontmatter.
2. Add, edit, or delete the matching row in **Catalog**.
3. Add a routing hint if the skill would otherwise be easy to miss.
4. Mention the new skill in the root `README.md` catalog.
5. Keep descriptions to one line: trigger + outcome, no essay.

Future skills belong in `skills/<name>/`. This file is the router; it is not a dump of their contents.
