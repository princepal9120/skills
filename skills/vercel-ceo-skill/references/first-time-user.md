# Segment 06 — First-time user and error-free sessions

Chapter: [10:26]–[12:34]

## Framework

**Know your customer** [10:26] [seen]: Named as a Vercel value. Easy to build when you are the only customer (you check whether you like it). Different once other people pay.

**Error-free sessions** [10:26] [seen]: Favorite number: how many people get all the way through the app with nothing going wrong. Agents are how he measures and improves that. On anything new, an agent tries it and reports what could be better [10:58] [seen].

**You cannot be a first-time user of your own app** [10:58] [seen]: You know every button and page. A new customer does not. A confusing sign-up field is invisible to you and a drop-off for them [11:19] [seen].

## First-time-user agent

**Role** [11:19] [seen]: Uses the app as a new customer. Tests without knowing what the app does. Runs it in a browser and finds struggle points so you can lead people where you want them to go.

**Must not read the code** [11:49] [seen]: If it can read the repo it already knows how everything works and is no longer first-time. It is blocked from reading the app; it may only run it.

**Hook** [11:49] [seen]: A hook stops the agent from using its bash tool for anything other than running the app. Edit or delete attempts are blocked. That is what makes the feedback honest.

## Error-free session agent

**Role** [12:18] [seen]: Separate agent. Runs browser tests for every step every customer must complete. Finds slow steps, broken steps, flows that die halfway. Can write the fix. Walks each path start-to-finish and **saves results as JSON** [12:34] [seen]. Run before every ship [12:34] [seen].

## Technique

1. Create the first-time-user agent with read/edit/delete denied by hook; browser-only [11:49] [seen].
2. Create the path-coverage agent for critical customer journeys; persist JSON results [12:18] [seen].
3. Treat error-free session rate as a ship gate [10:26] [seen].
4. Hook implementation details (Claude Code PreToolUse vs others) were not specified [11:49] [unknown]; map to the host's equivalent deny list [11:49] [guessed].

## Anti-patterns

- Founder-as-QA on an app you designed [10:58] [seen].
- Allowing the "new user" agent to open source files "just to set up" [11:49] [seen].
- Shipping without the JSON path report [12:34] [seen].
