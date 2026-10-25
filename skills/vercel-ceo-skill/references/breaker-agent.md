# Segment 05 — Breaker agent

Chapter: [08:25]–[10:26]

## Framework

**Break it on purpose** [08:25] [seen]: At a Vercel product launch the CEO did not only check that it worked. He gave it to an agent and told it to break the product the way a busy site is stressed: concurrent actions that clash, slowdowns, comparison with other products [08:44] [seen].

**Happy-path blindness** [08:44] [seen]: Model-written code easily works when everything goes right and fails when someone skips a step or does two things at once. The same agent that built the app will re-use it the intended way and watch tests pass [08:44] [seen]. Customers will not.

**Live-scale surprises** [09:13] [seen]: Once many people use the product, failures appear that the builder agent never thought to test. Test the situations that are sure to happen in production.

## What to build

**Breaker agent** [09:13] [seen]: Ask your working agent to create a specialist whose job is to break the app on purpose and report every break. It attacks the way an outsider would so you find weak spots first [09:42] [seen]. Finding it yourself is a fix; someone else finding it first is expensive [09:42] [seen].

**Copy the data** [09:55] [seen]: The prompt must make the breaker operate on **copies** of app data so real data stays safe.

**Run + loop** [09:55] [seen]: Ask Claude to run the breaker; it starts a separate agent in its own context window, stress-tests, and reports back. Then: fix, re-run, confirm the breaks are gone. Optional: a review loop that keeps finding and fixing [10:26] [seen].

## Technique

1. Prompt: create a breaker agent; mission is adversarial breakage; never touch prod data — copy first [09:13] [seen].
2. Include concurrency, skipped steps, clashing writes, latency under load, comparison with peer products [08:44] [seen].
3. Run in an isolated context window [09:55] [seen].
4. Fix from the report; re-run until silent [09:55] [seen].
5. Keep the loop available as a recurring review [10:26] [seen].

## Anti-patterns

- Builder agent "QA" on the intended path only [08:44] [seen].
- Pointing the breaker at production databases [09:55] [seen].
- Filing breaks without a re-run to prove the fix [09:55] [seen].

## Unknowns

- Exact load sizes, chaos scripts, or Vercel-internal breaker prompts [08:44] [unknown].
