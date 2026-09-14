---
name: content-batch
description: Plan and draft a week of on-voice X content from one topic cluster. Use when the user wants a content calendar, "week of tweets", batch drafts, or a mix of singles, one thread, replies, and a quote-tweet. Load voice first, pick a mix, then draft paste-ready posts. Do not use for a single tweet, a single reply, an article, a profile rewrite, or a Product Hunt launch.
metadata:
  type: workflow
  version: "1.1"
---

# Content Batch

One cluster. One week. Mix of containers so the feed does not look like a newsletter dumped into 7 tweets.

Voice first. Never invent facts. Hand each item to the sibling skill's rules when those skills are loaded.

## Workflow

Run these steps in order. Skip a step only if the user already supplied its output (saved Voice Card, locked cluster, locked mix).

### 1. Load voice

Same Voice Card as `viral-tweets`. Reuse if present. Otherwise fetch originals (Latest + Top) and fill the card. Quote 2–4 fragments. Do not guess from bio.

If samples are weak, say so and write a clean default — still mix containers, do not invent a thought-leader week.

### 2. Lock the cluster

Need:

- One topic cluster (not five products) — [references/cluster-rules.md](references/cluster-rules.md)
- Window — default 5 posting days (thin-feed: 3)
- Goal — inform, ship-log, audience-build, launch-adjacent (not a Product Hunt launch — that is a different pack)
- Hard constraints — no weekends, no threads, news-only, etc.

If the cluster is breaking news or markets, verify with primary sources (official posts, filings, CoinDesk / The Block / WSJ / company blogs) before any draft.

If the idea wants headings, a table, or a document crop → stop and use `viral-articles`. Do not explode an article into a fake week.

### 3. Pick a mix

Read [references/week-mix.md](references/week-mix.md) and [references/slot-jobs.md](references/slot-jobs.md).

Default 5-day mix for a news/builder account:

| Slot | Container | Job |
|---|---|---|
| 1 | single | fact-mechanism (the week's fact) |
| 2 | reply | add-mechanism under a larger relevant post |
| 3 | single | explanatory-why or lived-scene |
| 4 | thread (3–5) or skip | sourced-explainer *or* short-claim if 280 holds it |
| 5 | quote-add | second-order take on someone else's post |

Do not ship 7 fact-mechanisms. Do not ship 7 goal-shares. If the account never threads, replace slot 4 with a short-claim + a witness reply.

Cadence follows the Voice Card, not a 2-posts-per-day costume. Do not pad.

### 4. Draft the pack

For each slot, name the template / reply job / thread structure, then write paste-ready copy with character counts and a source.

Use sibling output rules when those skills are loaded:

- originals → `viral-tweets` (circuits, templates, thread autopsy)
- replies / quotes → `viral-replies` (jobs, already-said, reply vs quote)
- a piece that wants headings → `viral-articles` instead of forcing a thread

Score the *week*, not each tweet in isolation: would a stranger scrolling Mon–Fri think this is one person with a beat?

Avoid default model tells unless the Voice Card proves the account writes that way: "Unpopular opinion," numbered-lesson openers, beige bullet threads, hashtag soup, GM filler.

### 5. Ship

Output using [assets/output-template.md](assets/output-template.md). Lead with the recommended week. One alt per slot, not a second full week, unless they asked for two plans.

If they need a worked pattern, [assets/example-week.md](assets/example-week.md) is the shape — do not ship the example cluster as their copy.

Do not promise to publish. Draft only.

## Tool map

| Need | Tool |
|------|------|
| Our voice | `x_keyword_search` from:handle -filter:replies |
| What already worked | `x_keyword_search` from:handle min_faves:N, Top |
| Parent for a reply slot | `x_thread_fetch` or search |
| Verify news claims | `web_search` / `browse_page` on primary sources |
| Topic pulse | `x_keyword_search` / `x_semantic_search` on the cluster |

## Quality bar

Done when:

1. Same Voice Card all week.
2. At least two containers (not all singles).
3. Every news claim has a source.
4. Removing any slot would leave a hole — no filler GM posts.
5. Nothing needs an AI disclaimer.

## When to break

- User asked for 3 posts → thin-feed mix, do not pad to 5.
- Account never threads → skip slot 4 thread.
- Cluster is a filing that needs depth → `viral-articles` + handshake, not five restatements.
- Single tweet / single reply / bio → the sibling skill, not this one.
