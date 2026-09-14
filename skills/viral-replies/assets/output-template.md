# Output template

Lead with a one-line Voice Card summary, then the recommended reply, then alternatives. Keep meta short.

```
Voice: [handle] — [snapshot]
Parent: @[their_handle] — [one-line summary]
Job recommended: [add-mechanism | correct-artifact | translate-local | ask-unique | witness-scene | concede-sharpen | quote-add]
Template: [same or short-claim]
Format: reply | quote-tweet

Recommended
[reply text]
[N] characters · [job]

Why this one: [job + payload + why it only works under this parent]

Alt A — [job]
[text]
[N] characters

Alt B — [job]
[text]
[N] characters

Source used: [name + URL or "parent text only"]
Already said in-thread: [none | one-line of what you avoided duplicating]
```

## Rules for the reply block

- Paste-ready. No quotes wrapping the reply unless the reply itself contains quotes.
- No hashtags or emoji the Voice Card did not earn.
- Character count is visible characters as the user would paste them, including line breaks. Emoji = 2.
- If two variants share the same payload, kill one.
- If the user asked for one reply, still show two alts unless they said "just one."

## After delivery

If the user picks a variant, tighten only that one. Do not regenerate the whole set unless they change the parent, job, or account.
