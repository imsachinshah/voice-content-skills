---
name: viral-articles
description: Write on-voice long-form articles for X Articles, Substack, or blogs after studying a profile's posts. Use when the user wants an essay, teardown, guide, X Article, newsletter issue, or "write a long piece like me." Choose article vs thread vs long post first. Do not use for single tweets, tweet threads, or SEO listicles unless the user explicitly wants a reference post.
metadata:
  type: workflow
  version: "1.0"
---

# Viral Articles

One idea. One thesis. Depth instead of sequence. Voice first. Never invent facts.

## Workflow

### 1. Choose the container

Read [references/choose-format.md](references/choose-format.md).

- Sequence, replies, cliffhangers → stop and use the `viral-tweets` skill.
- One argument that needs headings, a table, or a document crop → Article.
- One continuous take, no H2s, stays in the feed → Premium long post.

If two of three questions point at a thread, do not write an article.

### 2. Load voice (unless a Voice Card already exists)

Same rule as tweets. If `viral-tweets` already printed a Voice Card in this conversation, reuse it.

Otherwise fetch originals and fill the card from that skill's voice-analysis pattern — register, length, emoji, stance, what they never do. Do not invent a thought-leader voice from the bio.

### 3. Lock the brief

Need:

- One thesis (a sentence the reader can steal)
- Audience
- Structure name from [references/article-structures.md](references/article-structures.md)
- Target length — default **1,000–1,500 words** (finishable). Stretch to 2,000 only if every section changes the thesis.
- Sources, if news or markets

Verify claims with primary sources. Do not draft off rumor.

### 4. Draft the spine, then the body

Build the spine from [references/article-spine.md](references/article-spine.md):

1. Title (under ~60 characters, cashed promise)
2. Dek (does work the title cannot)
3. First two sentences (confirm the payoff — no throat-clearing)
4. Thesis paragraph
5. 3–5 H2s, each 150–300 words, each answering a question the title raised
6. Close as one stealable sentence, not a recap

Write title and close last if needed. The real opener is usually the clearest line in the finished draft.

### 5. Ship with a thread handshake

Articles that never touch the feed are unread.

After the draft, produce the handshake in [references/thread-handshake.md](references/thread-handshake.md):

- 3–5 tweet lift (hook, best mechanism, implication)
- Link in a reply, not tweet 1
- Optional later quote-tweet with a second-order take

Output using [assets/output-template.md](assets/output-template.md).

## Quality bar

Done when:

1. A stranger can quote the thesis paragraph and be correct.
2. Cutting any H2 would actually hurt.
3. Title promise is cashed in the body.
4. Fact vs opinion is obvious.
5. It could pass as that writer without an AI disclaimer.

Do not add FAQ graveyards, "in this article we will," or origin-story costumes on a filing.
