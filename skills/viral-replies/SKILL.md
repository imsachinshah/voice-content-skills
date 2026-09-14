---
name: viral-replies
description: Write on-voice replies and quote-adds under other people's posts. Use when the user wants reply-guy copy, strategic replies, quote-tweet adds, "reply to this", or engagement under a KOL without sounding like a bot. Fetch the parent, load voice, pick a reply job, then write 3 short variants. Do not use for original tweets, threads, bios, or auto-posting unless the user explicitly asks to publish.
metadata:
  type: workflow
  version: "1.0"
---

# Viral Replies

Replies are how most accounts grow. They still have to sound like the account. Add one fact, one local angle, or one mechanism. Never "great point."

## Workflow

Run these steps in order. Skip a step only if the user already supplied its output (pasted parent, a saved voice card).

### 1. Lock the parent

Need the post being replied to. If the user pasted it, use that. If they gave a URL or ID, `x_thread_fetch`. If they named an account ("reply to @x on Y"), search first, then fetch the specific post.

Read:

- The parent text
- Who they are (handle, not just follower count)
- 2–3 existing high-quality replies (what is already said)
- Whether this is a reply, a quote-tweet, or a reply-to-a-reply

If the parent is a question the account cannot answer from known facts, say so. Do not invent.

### 2. Load voice (mandatory unless a Voice Card is already in this conversation)

Same Voice Card rule as `viral-tweets`. Fetch originals — do not guess from bio.

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

Fill the card from that skill's voice-analysis pattern — register, length, emoji, stance, what they never do. Replies on *their* feed teach warmth and brevity; they do not teach structure. Do not copy the parent author's voice.

### 3. Pick a reply job

Read [references/reply-jobs.md](references/reply-jobs.md). One job per reply.

Default jobs: **add**, **correct**, **translate**, **ask**, **witness**. Quote-tweets use **quote-add**.

If the job is "agree," stop. Agreement without payload is noise.

### 4. Draft in the account's voice

Write **3 variants**. Different jobs when the parent supports it. If only `add` is honest, write three different payloads, not three skins of the same compliment.

Rules from [references/reply-rules.md](references/reply-rules.md):

- One to three sentences. Default under 160 characters. Hard ceiling 280.
- First six words contain a name, number, mechanism, or a clause from the parent.
- Quote a specific clause, or add a fact they did not have. Generic praise fails both tests.
- No hashtags, no "this.", no "so true.", no emoji stacks unless the Voice Card is emoji-heavy.
- Do not thread a reply. If it needs sequence, it is an original — hand to `viral-tweets`.
- Never invent engagement, fake "I've been saying this," or unsourced numbers.

### 5. Score, then ship

For each variant, mentally score 1–5 on:

- Voice match
- Payload (new fact or angle)
- Fit to *this* parent (would it fail under a different viral tweet?)
- Screenshot-clean

Lead with the highest combined score. Output using [assets/output-template.md](assets/output-template.md). Ready to paste — no commentary inside the reply block.

## Tool map

| Need | Tool |
|------|------|
| Parent post + replies | `x_thread_fetch` |
| Find the post | `x_keyword_search` from:their_handle + keywords |
| Our voice | `x_keyword_search` from:<handle> -filter:replies |
| Verify a number we add | `web_search` / `browse_page` on primary sources |

Do not promise to publish. Draft only, unless the user has an X connector and explicitly says to post.

## Quality bar

A draft is done when:

1. It could pass as that account under a stranger's post.
2. Deleting it would lose a fact or a question — not just a vibe.
3. It does not work under a *different* viral tweet. If it does, it is generic.
4. Nothing needs a disclaimer like "written by AI."

If voice samples are too weak to imitate, say so and write a clean default (short, specific, no hype) instead of inventing a personality.
