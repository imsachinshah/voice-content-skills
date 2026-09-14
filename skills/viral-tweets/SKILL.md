---
name: viral-tweets
description: Write on-voice viral tweets and threads after studying a profile's older posts. Use when the user wants tweet drafts, X posts, threads, copywriting for Twitter/X, profile voice matching, crypto or indie news tweets, or "write tweets like me." Pull recent posts, extract voice, then produce informative high-engagement copy. Do not use for long-form blogs, LinkedIn essays, or auto-posting unless the user explicitly asks to publish.
metadata:
  type: workflow
  version: "1.3"
---

# Viral Tweets

Write tweets that sound like the account, not like a model. Voice first, virality second. Never invent facts.

## Workflow

Run these steps in order. Skip a step only if the user already supplied its output (pasted posts, a saved voice card, or a locked topic).

### 1. Lock the target account

- Default handle is the user's X handle from context if one exists.
- If the user names a different account, use that.
- If neither is available, ask for the handle before drafting.

### 2. Load the voice (mandatory unless a voice card is already in this conversation)

Fetch real posts. Do not guess voice from bio alone.

Use X tools:

```
x_keyword_search
  query: from:<handle> -filter:replies
  mode: Latest
  limit: 10

x_keyword_search
  query: from:<handle> min_faves:5 -filter:replies
  mode: Top
  limit: 10
```

If results are thin (mostly emoji replies, quote-RTs, or under 20 words), also fetch:

```
x_keyword_search
  query: from:<handle>
  mode: Latest
  limit: 10
```

Read the bio from any returned author block. Optionally run `x_user_search` on the handle for display name and bio.

Then build a **Voice Card** using [references/voice-analysis.md](references/voice-analysis.md). Keep it short. Reuse the same card for the rest of the conversation unless the user changes accounts.

### 3. Lock the brief

Before writing, know:

- Topic or news item (one idea, not five)
- Goal — inform, opinion, thread, reply-bait, launch, recap
- Format — single tweet, 2–6 tweet thread, or quote-tweet angle
- Constraint — max variants, include sources, no hashtags, etc.

If the topic is news or markets, verify with primary sources (official posts, filings, CoinDesk / The Block / WSJ / company blogs). Do not draft off rumor screenshots.

### 4. Draft in the account's voice

Write **3 variants** by default (or the count the user asked for).

Rules:

- Match the Voice Card. If they write short and concrete, do not ship a 240-word essay. If they rarely use hashtags, skip them. If they use light emoji, do not flood.
- First line must earn the expand. Most mobile previews cut around 70–90 characters.
- Before writing variants, pick a hook circuit from [references/hook-psychology.md](references/hook-psychology.md) and a skeleton from [references/tweet-templates.md](references/tweet-templates.md). Name both in the output.
- Give the three variants *different* circuits and templates when possible (e.g. fact-mechanism, explanatory-why, lived-scene).
- One claim per tweet. Specific numbers beat adjectives.
- Informative tweets need a fact, a why-it-matters line, and a point of view. News-only restates get ignored.
- Stay inside X limits — 280 characters for standard accounts. Count after writing. If a draft overflows, cut words, do not start a thread just to save a sentence.
- Threads only when the idea needs sequence. Build them from [references/thread-structures.md](references/thread-structures.md) — pick a named structure, assign each tweet a slot job, then run the autopsy before shipping.
- Never invent engagement ("this is blowing up"), fake metrics, or unsourced claims.

Avoid default model tells unless the Voice Card proves the account actually writes that way:

- "Unpopular opinion:" / "Here's the thing:" / "Let that sink in."
- "5 lessons I learned" / "7 mental models" openers
- Em-dash stacks and beige bullet threads
- "This changes everything" with no mechanism
- Hashtag soup and engagement-bait questions that could sit under any tweet

### 5. Score, then ship the copy

For each variant, mentally score 1–5 on:

- Voice match
- Hook (circuit is clear and the first line would stop a stranger)
- Information density (new fact or useful frame)
- Shareability (would someone RT this as their take?)

Lead with the highest combined score. Label the others as alternatives.

Output using [references/output-templates.md](references/output-templates.md). Always include character counts. Ready to paste — no commentary inside the tweet block.

## Tool map

| Need | Tool |
|------|------|
| Recent originals | `x_keyword_search` from:handle -filter:replies, Latest |
| What already worked | `x_keyword_search` from:handle min_faves:N, Top |
| A specific post + replies | `x_thread_fetch` |
| Live topic pulse | `x_keyword_search` or `x_semantic_search` on the topic |
| Verify a news claim | `web_search` / `browse_page` on primary sources |
| Quote-tweet target | Fetch the original first, then write the quote |

Do not promise to publish. Draft only, unless the user has an X connector and explicitly says to post.

## Quality bar

A draft is done when:

1. It could pass as that account at a glance.
2. The first line works without the rest.
3. A skeptical reader can tell what is fact vs opinion.
4. Nothing needs a disclaimer like "written by AI."

If voice samples are too weak to imitate, say so and write a clean default voice (short, specific, no hype) instead of inventing a personality.
