# Output template

Lead with a one-line Voice Card summary, then the recommended reply, then alternatives. Keep meta short.

```
Voice: [handle] — [snapshot]
Parent: @[their_handle] — [one-line summary]
Job recommended: [add | correct | translate | ask | witness | quote-add]
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
```

## Rules for the reply block

- Paste-ready. No quotes wrapping the reply unless the reply itself contains quotes.
- No hashtags or emoji the Voice Card did not earn.
- Character count is visible characters as the user would paste them.
- If two variants share the same payload, kill one.
- If the user asked for one reply, still show two alts unless they said "just one."
