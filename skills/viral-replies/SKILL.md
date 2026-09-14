---
name: viral-replies
description: Write on-voice replies and quote-adds under other people's posts. Use when the user wants reply drafts, quote-tweet adds, "reply to this", strategic replies, or engagement under a KOL without sounding like a bot. Fetch the parent, load voice, pick a named job, then produce 3 short variants. Do not use for original tweets, threads, bios, weekly calendars, or auto-posting unless the user explicitly asks to publish.
metadata:
  type: workflow
  version: "1.1"
---

# Viral Replies

Replies are how most accounts grow. They still have to sound like the account. Add one fact, one local angle, or one mechanism. Never "great point."

## Workflow

Run these steps in order. Skip a step only if the user already supplied its output (pasted parent, a saved Voice Card, a locked job).

### 1. Lock the parent

Need the post being replied to.

- Pasted text → use that.
- URL or status ID → `x_thread_fetch`.
- "Reply to @x on Y" → search, then fetch the specific post.

Read, before drafting:

- The parent text (and tweet 1 if it is a thread)
- Who they are (handle, not follower count)
- 2–3 existing high-quality replies — what is already said
- Reply vs quote-tweet vs reply-to-a-reply

Read [references/parent-and-quote.md](references/parent-and-quote.md) when choosing the container, when existing replies already cover the obvious add, or when the parent is a small account.

If the parent is a question the account cannot answer from known facts, say so. Do not invent. If the thread is days old and the point is strong, prefer a quote-add or a new original (`viral-tweets`) over a late reply.

### 2. Load the voice (mandatory unless a Voice Card is already in this conversation)

Fetch real originals. Do not guess from bio.

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

Build a **Voice Card** using the `viral-tweets` voice-analysis pattern — register, length, emoji, stance, what they never do. Quote 2–4 fragments as evidence. Replies on *their* feed teach warmth and brevity; they do not teach structure. Do not copy the parent author's voice.

If samples are weak (emoji, one-word replies), say so and write a clean default (short, specific, no hype).

### 3. Lock the brief

Before writing, know:

- Parent clause you are answering
- Job from [references/reply-jobs.md](references/reply-jobs.md)
- Container — reply or quote-tweet
- Constraint — max variants, include a source, no emoji, etc.

If the job would be "agree," stop. Agreement without payload is noise.

### 4. Draft in the account's voice

Write **3 variants**. Different jobs when the parent supports it. If only `add-mechanism` is honest, write three different *payloads*, not three skins of the same compliment.

Before writing, pick a job and a skeleton from [references/reply-templates.md](references/reply-templates.md). Name both in the output.

Rules from [references/reply-rules.md](references/reply-rules.md):

- One to three sentences. Default under 160 characters. Hard ceiling 280 (emoji counts as 2).
- First six words contain a name, number, mechanism, or a clause from the parent.
- Quote a specific clause, or add a fact they did not have. Generic praise fails both tests.
- No hashtags, no "this.", no "so true.", no emoji stacks unless the Voice Card is emoji-heavy.
- Do not thread a reply. If it needs sequence, it is an original — hand to `viral-tweets`.
- Never invent engagement, fake "I've been saying this," or unsourced numbers.

Avoid default model tells unless the Voice Card proves the account writes that way:

- "Came here to say this" / "Taking notes" / "The algorithm needs to push this"
- "Great point." / "This." / "So true." / "Let's gooo" / "W" / "Based"
- "Unpopular opinion:" glued on a reply
- "What do you think? 👇"
- Restating the parent in nicer words

### 5. Score, then ship

For each variant, mentally score 1–5 on:

- Voice match
- Payload (new fact, local number, or unique question)
- Fit to *this* parent (would it fail under a different viral tweet?)
- Screenshot-clean

Lead with the highest combined score. Label the others as alternatives.

Output using [assets/output-template.md](assets/output-template.md). Always include character counts. Ready to paste — no commentary inside the reply block.

If the user is unsure what "good" looks like, show one pair from [assets/example-replies.md](assets/example-replies.md) — do not ship the example as their copy.

## Tool map

| Need | Tool |
|------|------|
| Parent post + replies | `x_thread_fetch` |
| Find the post | `x_keyword_search` from:their_handle + keywords |
| Our voice | `x_keyword_search` from:<handle> -filter:replies |
| Verify a number we add | `web_search` / `browse_page` on primary sources |
| Quote-tweet target | Fetch the original first, then write the add |

Do not promise to publish. Draft only, unless the user has an X connector and explicitly says to post.

## Quality bar

A draft is done when:

1. It could pass as that account under a stranger's post.
2. Deleting it would lose a fact or a question — not just a vibe.
3. It does not work under a *different* viral tweet. If it does, it is generic.
4. Fact vs opinion is obvious.
5. Nothing needs a disclaimer like "written by AI."

## When to break

- User said "just one" → one draft, no alts.
- User pasted the parent and a locked job → skip fetch and job-pick.
- Parent is a question you cannot answer honestly → say so; do not perform expertise.
- Idea needs sequence → stop and use `viral-tweets`.
- They asked for a bio or a week of posts → `x-profile` / `content-batch`.
