---
name: x-profile
description: Rewrite an X profile in the account's actual voice — display name, bio, location/link line, and pinned tweet. Use when the user wants a new bio, "fix my profile", pinned tweet options, or a profile that matches how they already write. Fetch real posts first. Do not use for feed tweets, threads, articles, or LinkedIn headlines.
metadata:
  type: workflow
  version: "1.0"
---

# X Profile

The profile is a landing page, not a slogan. It has to sound like the feed. Voice first. No invented credentials.

## Workflow

Run these steps in order. Skip a step only if the user already supplied its output (current bio paste, a saved voice card).

### 1. Lock the account and load voice

Default to the user's handle. If they name a different account, use that.

Fetch:

- Current display name, bio, location, website from `x_user_search`
- Pinned / recent originals via `x_keyword_search` from:<handle> -filter:replies (Latest + Top)

Build a **Voice Card** using the same pattern as `viral-tweets` (`references/voice-analysis.md` in that skill). Reuse a card already in this conversation.

If they have no originals, write a clean default (short, specific, no hype) and say the feed is too thin to imitate.

### 2. Name the job of the profile

One job. Pick with the user if unclear:

- **reporter** — they post news; bio says beat + why follow
- **builder** — they ship; bio says what they are building *this month*
- **operator** — they teach a craft; bio says who it is for
- **witness** — they are a person in a scene, not a brand

A bio that tries to be all four is a keyword dump. Match the feed, not the aspiration.

### 3. Rewrite the four fields

Read [references/bio-patterns.md](references/bio-patterns.md) and [references/pinned-jobs.md](references/pinned-jobs.md).

Output **3 variants** for each field.

Constraints:

- Display name: human name ± one signal. Not a slogan. Not ALL CAPS unless they already are.
- Bio: 160 characters. One beat + one proof. Line breaks only if the Voice Card uses them.
- Location / website: real or omit. Do not invent a city or a product URL.
- Pinned: a tweet they could actually post. Prefer a specific-result, short-claim, or the best existing original.

Never invent: follower counts, "ex-{FAANG}", advisor roles, revenue, "building the future of X."

If the pin should be a *new* tweet, write it in voice (hand internals to `viral-tweets` templates) and say it must be posted, then pinned.

### 4. Ship as a paste pack

Output using [assets/output-template.md](assets/output-template.md). Show character counts. Recommend one full set (name + bio + pin) that hangs together, then alts per field.

## Tool map

| Need | Tool |
|------|------|
| Bio, name, website | `x_user_search` |
| What the feed actually is | `x_keyword_search` from:handle -filter:replies |
| What already worked | `x_keyword_search` from:handle min_faves:N, Top |

## Quality bar

Done when:

1. Bio could only belong to this feed.
2. A stranger knows the beat in one glance.
3. Nothing in the bio is untrue.
4. Pinned tweet would still work as a normal post.
5. Nothing needs a disclaimer like "written by AI."
