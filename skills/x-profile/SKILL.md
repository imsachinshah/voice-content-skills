---
name: x-profile
description: Rewrite an X profile in the account's actual voice — display name, bio, location/link line, and pinned tweet. Use when the user wants a new bio, "fix my profile", pinned tweet options, a profile audit, or a profile that matches how they already write. Fetch real posts first. Do not use for feed tweets, threads, articles, replies, weekly calendars, or LinkedIn headlines.
metadata:
  type: workflow
  version: "1.1"
---

# X Profile

The profile is a landing page, not a slogan. It has to sound like the feed. Voice first. No invented credentials.

A stranger decides in about two seconds from **name + bio + pin**. That is what this skill rewrites.

## Workflow

Run these steps in order. Skip a step only if the user already supplied its output (current bio paste, a saved Voice Card, a locked profile job).

### 1. Lock the account and load voice

Default to the user's handle. If they name a different account, use that.

Fetch:

- Current display name, bio, location, website from `x_user_search`
- Pinned / recent originals via `x_keyword_search` from:<handle> -filter:replies (Latest + Top)

Build a **Voice Card** using the same pattern as `viral-tweets`. Reuse a card already in this conversation. Quote 2–4 fragments as evidence. Do not invent a thought-leader voice from the bio.

If they have no originals, write a clean default (short, specific, no hype) and say the feed is too thin to imitate.

### 2. Name the job of the profile

One job. Pick with the user if unclear. Read [references/bio-patterns.md](references/bio-patterns.md) when choosing the bio skeleton.

- **reporter** — they post news; bio says beat + why follow
- **builder** — they ship; bio says what they are building *this month*
- **operator** — they teach a craft; bio says who it is for
- **witness** — they are a person in a scene, not a brand

A bio that tries to be all four is a keyword dump. Match the feed, not the aspiration.

Also lock the conversion job (follow / visit the link / understand the beat). Pin and link change with this.

### 3. Score the live profile, then rewrite

Read [references/profile-tests.md](references/profile-tests.md) before rewriting. Score name, bio, pin, link, location, photo-note, header-note: pass / needs-work / fail.

Then rewrite the text fields. Output **3 variants** for name, bio, and pin.

Constraints from [references/name-header-link.md](references/name-header-link.md) and [references/pinned-jobs.md](references/pinned-jobs.md):

- Display name (50): human name ± one searchable signal. Not a slogan. Not ALL CAPS unless they already are.
- Bio (160): one beat + one proof. Line breaks only if the Voice Card uses them.
- Location / website: real or omit. Do not invent a city or a product URL.
- Pinned: a tweet they could actually post. Prefer proof, thesis, product, or welcome.
- Header / photo: notes only (this skill does not generate images). Flag if they contradict the bio.

Never invent: follower counts, "ex-{FAANG}", advisor roles, revenue, "building the future of X."

If the pin should be a *new* tweet, write it in voice (hand internals to `viral-tweets` templates) and say it must be posted, then pinned.

### 4. Ship as a paste pack

Output using [assets/output-template.md](assets/output-template.md). Show character counts. Recommend one full set (name + bio + pin) that hangs together, then alts per field.

Run the two-second test: name + bio + pin only. Would a stranger know the beat and want to follow?

If the user wants a worked pair, use [assets/example-profiles.md](assets/example-profiles.md) as a pattern — do not ship the example as their bio.

Avoid default model tells unless the Voice Card proves the account writes that way:

- `Entrepreneur | Web3 | AI | Investor`
- `Building the future of [noun]`
- `I help people unlock their potential`
- Emoji walls as section breaks
- "Tweets are my own" on a personal account

## Tool map

| Need | Tool |
|------|------|
| Bio, name, website | `x_user_search` |
| What the feed actually is | `x_keyword_search` from:handle -filter:replies |
| What already worked (pin) | `x_keyword_search` from:handle min_faves:N, Top |
| Verify a proof in the bio | `web_search` / `browse_page` |

## Quality bar

Done when:

1. Bio could only belong to this feed.
2. A stranger knows the beat in one glance (name + bio + pin).
3. Nothing in the bio is untrue.
4. Pinned tweet would still work as a normal post.
5. Nothing needs a disclaimer like "written by AI."

## When to break

- User said "just the bio" → skip name/pin alts.
- Feed is news-aggregator → do not write a founder bio.
- They asked for tweets or a week of posts → `viral-tweets` / `content-batch`.
- They asked for a header image → note the job of the header; do not fake a design file.
