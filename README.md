# voice-content-skills

Installable [Agent Skills](https://agentskills.io) for on-voice writing on X and long-form.

Voice first. Virality second. No invented facts. No 2020 thread costumes.

## Skills

| Skill | Version | Use when |
| --- | --- | --- |
| [`viral-tweets`](skills/viral-tweets) | 1.3 | Tweets, threads, quote-tweets, "write like me" |
| [`viral-articles`](skills/viral-articles) | 1.0 | X Articles, Substack, essays, teardowns, guides |

They are siblings. Tweets do not load article refs. Articles hand a launch thread back to tweet rules.

## Install

Grok skill-installer:

```bash
# tweets
bash <skill-installer>/scripts/install-skill.sh \
  --repo imsachinshah/voice-content-skills \
  --path skills/viral-tweets --ref main

# articles
bash <skill-installer>/scripts/install-skill.sh \
  --repo imsachinshah/voice-content-skills \
  --path skills/viral-articles --ref main
```

Or copy a skill folder into your agent's skills directory:

- Grok — `.grok/skills/<name>/`
- Claude Code — `.claude/skills/<name>/`
- Cursor — `.cursor/skills/<name>/`

Each folder must keep `SKILL.md` at its root.

## Repo layout

```
skills/
  viral-tweets/
    SKILL.md
    references/
    assets/
  viral-articles/
    SKILL.md
    references/
    assets/
```

Normalized Agent Skills folders. No app, no landing page, no shared `common/` package — agents load one skill directory.

## License

MIT
