# Reply jobs

One job per reply. Name it in the output.

## Contents

- Jobs
- Do not
- Pick
- Three variants

## Jobs

| Job | Use when | Payload |
|---|---|---|
| add-mechanism | Parent is right but incomplete | Mechanism, local number, named entity they skipped |
| correct-artifact | Parent has one load-bearing error | The error + the artifact. No insult. |
| translate-local | Parent is US/global; audience is here | Same fact, this market / this stack |
| ask-unique | You actually need their answer | One question they are uniquely placed to answer |
| witness-scene | You have lived the thing | One scene + one number. Not "same." |
| concede-sharpen | They pushed back and are partly right | Concede the valid bit, then the missing piece |
| quote-add | Quote-tweet, not a reply | Second-order effect. Do not restate. |

Skeletons for each job live in [reply-templates.md](reply-templates.md). Container rules live in [parent-and-quote.md](parent-and-quote.md).

## Do not

- **agree** — "This." / "So true." / "Great point." / "This is the way."
- **promo** — drop a product link under a viral post unless the parent asked for tools *and* the user said to.
- **thread-the-reply** — if it needs sequence, write an original with `viral-tweets`.
- **dunk** — especially on a smaller account. Dunks go viral for the dunker once, then train mutes.
- **strawman** — reply to what they wrote, not a worse version of it.

## Pick

```
Parent missed a mechanism or number?     add-mechanism
Parent is wrong on one fact?             correct-artifact
Parent is true elsewhere, not here?      translate-local
You need them to answer?                 ask-unique
You have a scene they described?         witness-scene
They pushed back and are half-right?     concede-sharpen
You are quoting, not replying?           quote-add
You only want to be seen agreeing?       do not draft
```

Default for news-style accounts: **add-mechanism** (local number or how-it-works), then **translate-local**, then **quote-add**.

## Three variants

Three variants = three different jobs when the parent supports it.

If only `add-mechanism` is honest, write three different *payloads* (a number, a mechanism, a named entity) — not three skins of "great insight."

If two variants share a hook or a payload, kill one.
