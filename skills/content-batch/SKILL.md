---
name: content-batch
description: Plan and draft a week of on-voice X content from one topic cluster. Use when the user wants a content calendar, "week of tweets", batch drafts, or a mix of singles, one thread, replies, and a quote-tweet. Load voice first, pick a mix, then draft paste-ready posts. Do not use for a single tweet, a single reply, an article, or a Product Hunt launch.
metadata:
  type: workflow
  version: "1.0"
---

# Content Batch

One cluster. One week. Mix of containers so the feed does not look like a newsletter dumped into 7 tweets.

Voice first. Never invent facts. Hand each item to the sibling skill's rules when those skills are loaded.

## Workflow

Run these steps in order.

### 1. Load voice

Same Voice Card as `viral-tweets`. Reuse if present. Otherwise fetch originals (Latest + Top) and fill the card. Do not guess from bio.

### 2. Lock the cluster

Need:

- One topic cluster (not five products)
- Window — default 5 posting days
- Goal — inform, ship-log, audience-build, launch-adjacent (not a Product Hunt launch — that is a different pack)
- Hard constraints — no weekends, no threads, news-only, etc.

If the cluster is breaking news or markets, verify with primary sources (official posts, filings, CoinDesk / The Block / WSJ / company blogs) before any draft.

### 3. Pick a mix

Read [references/week-mix.md](references/week-mix.md).

Default 5-day mix for a news/builder account:

| Slot | Container | Job |
|---|---|---|
| 1 | single | fact-mechanism (the week's fact) |
| 2 | reply | add under a larger relevant post |
| 3 | single | explanatory-why or lived-scene |
| 4 | thread (3–5) | sourced-explainer *or* skip if the idea fits in 280 |
| 5 | quote-add | second-order take on someone else's post |

Do not ship 7 fact-mechanisms. Do not ship 7 goal-shares. If the account never threads, replace slot 4 with a short-claim + a witness reply.

### 4. Draft the pack

For each slot, name the template / reply job / thread structure, then write paste-ready copy with character counts and a source.

Use sibling output rules when those skills are loaded:

- originals → `viral-tweets`
- replies / quotes → `viral-replies`
- a piece that wants headings → stop and use `viral-articles` instead of forcing a thread

Score the *week*, not each tweet in isolation: would a stranger scrolling Mon–Fri think this is one person with a beat?

Avoid default model tells unless the Voice Card proves the account writes that way: "Unpopular opinion," numbered-lesson openers, beige bullet threads, hashtag soup.

### 5. Ship

Output using [assets/output-template.md](assets/output-template.md). Lead with the recommended week. One alt per slot, not a second full week, unless they asked for two plans.

Do not promise to publish. Draft only.

## Quality bar

Done when:

1. Same Voice Card all week.
2. At least two containers (not all singles).
3. Every news claim has a source.
4. Removing any slot would leave a hole — no filler GM posts.
5. Nothing needs an AI disclaimer.
