# Segment 01 — Test ideas before committing

Chapter: [00:47]–[02:09]

## Framework

**Fresh-project verification** [00:47] [seen]: When an idea appears, create a new project and have an agent check from scratch whether it works. Do not adopt a workflow because a thread, vibe, or prompting guide said so.

**Anti-vibe example** [00:58] [seen]: Someone read a prompting guide claiming Astra performs better with a certain prompt style and started using it without ever measuring. The CEO's rule is personal verification over folklore.

**PRD-first, MVP-second** [01:19] [seen]: New work starts in a `specs/` folder that holds the PRD (main features). Jumping from that PRD into the full app discovers idea problems late and poisons early decisions — a wrong assumption is already load-bearing.

**Agent MVP prompt** [01:50] [seen]: Ask Claude Code (or whichever agent) to build an MVP of the basic features listed in the PRD. The MVP exists so you can see the idea as software and drop it cheaply if it is not worth building [02:09] [seen].

## Technique

1. Write the PRD into `specs/` before any app code [01:19] [seen].
2. Prompt: implement only the listed basic features as an MVP; no extra surface [01:50] [seen].
3. Evaluate the running MVP against the idea, not against token spend [02:09] [seen].
4. Kill or rewrite the idea here. Do not "just keep going" into the full app [01:50] [seen].

## Anti-patterns

- Trusting a prompting guide without a side-by-side check [01:19] [seen].
- Building the whole product off an untested PRD [01:19] [seen].
- Treating a pretty first-pass UI as validation of the idea [02:09] [guessed].

## Demo (what was described)

- Input: new idea + empty project + PRD in `specs/` [01:19] [seen].
- Action: agent implements basic features only [01:50] [seen].
- Observable: a first working version you can keep or discard [02:09] [seen].
