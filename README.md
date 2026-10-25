# Prince Pal's agent skills

Personal library of reusable agent skills for [Claude Code](https://docs.anthropic.com/en/docs/claude-code), [Hermes](https://github.com/nousresearch/hermes-agent), and [Codex](https://github.com/openai/codex).

Skills here are playbooks an agent can load on demand: frameworks, commands, and evidence-grounded notes from talks and videos. New video-derived skills are produced with [video-to-skill](https://github.com/opentoolsorg/video-to-skill).

## Catalog

| Skill | When to load |
| --- | --- |
| [`my-skills`](skills/my-skills/) | Browse this library, pick a skill, or convert a new video with video-to-skill. |
| [`vercel-ceo-skill`](skills/vercel-ceo-skill/) | Build or audit an agent-first product workflow (direction audits, breaker agents, must-not-trade-off rules, security/slop debt, first-time-user agents, feedback MCP loops). |

Load **`my-skills`** first when you are unsure which package applies. It indexes every skill in this repo, including ones added later.

## Install

Clone the library, then symlink (or copy) the skill folders your host expects.

```bash
git clone https://github.com/princepal9120/skills.git
```

### Claude Code (`~/.claude/skills/`)

```bash
mkdir -p ~/.claude/skills
ln -s "$(pwd)/skills/my-skills" ~/.claude/skills/my-skills
ln -s "$(pwd)/skills/vercel-ceo-skill" ~/.claude/skills/vercel-ceo-skill
```

### Hermes

```bash
mkdir -p ~/.hermes/skills
ln -s "$(pwd)/skills/my-skills" ~/.hermes/skills/my-skills
ln -s "$(pwd)/skills/vercel-ceo-skill" ~/.hermes/skills/vercel-ceo-skill
```

Some Hermes layouts nest by category (`~/.hermes/skills/<category>/<name>`). Either path works as long as the package folder (the one that contains `SKILL.md`) is discoverable.

### Codex

```bash
mkdir -p ~/.codex/skills
ln -s "$(pwd)/skills/my-skills" ~/.codex/skills/my-skills
ln -s "$(pwd)/skills/vercel-ceo-skill" ~/.codex/skills/vercel-ceo-skill
```

After linking, restart the host or reload skills so the new packages appear.

## Convert a video into a skill

Use [opentoolsorg/video-to-skill](https://github.com/opentoolsorg/video-to-skill) (not this repo) to extract a transcript, author a modular package, and validate evidence labels.

```text
/video-to-skill <video-or-course-url> [custom-skill-name]
```

Or follow the converter README for the standalone extract/validate CLI. Drop the generated folder under `skills/<name>/`, then add a one-line entry in [`skills/my-skills/SKILL.md`](skills/my-skills/SKILL.md).

Every video-derived package should include:

| File | Purpose |
| --- | --- |
| `SKILL.md` | YAML `name` + `description`; lean frameworks + topic index |
| `segments/segNN-*.md` | Chapter deep-dives, loaded on demand |
| `cheatsheet.md` | Fast decision rules |
| `patterns.md` | Step-by-step techniques |
| `glossary.md` | Terms with timestamp citations |
| `timestamps.md` | Jump list back into the source |
| `sources.md` | Source metadata and provenance |

Claims in those packages carry `[mm:ss]` plus `[seen]`, `[guessed]`, or `[unknown]`.

## Layout

```text
skills/
  my-skills/              # aggregator / router
    SKILL.md
  vercel-ceo-skill/       # video-to-skill package
    SKILL.md
    segments/
    cheatsheet.md
    patterns.md
    glossary.md
    timestamps.md
    sources.md
```

## License

MIT. See [LICENSE](LICENSE).
