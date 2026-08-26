# ADR-0002: Changelog Bot's Posting Channel

- Status: Proposed

**TL;DR**: The changelog bot needs one Slack channel to post release notes to.

## Questions

### QST: Does the changelog bot post to #eng or #releases?
- Status: unanswered
- Why deferring: not blocking this ADR's acceptance — the bot ships either way and the channel is a one-line config change.
- Need: pick a channel

**Option A — #eng.** Everyone who'd care is already in this channel; no new channel to join.

**Option B — #releases.** A dedicated channel keeps release noise out of day-to-day engineering discussion, but requires people to opt in.

**Recommendation**: (by Loftsman)

**B — #releases.** Justification: a changelog bot posting on every merge is exactly the kind of ambient noise that trains people to mute a channel — better to give it its own home from day one than to retrofit that later once #eng habits have formed. Consequence if wrong: if #releases sits unread because nobody thought to join it, the bot's announcements become invisible, which is a worse failure than a bit of noise in #eng.

**ANS:** (by [name])
[Fill this in]

---

## Links
