# ADR-0001: Webhook Delivery Retry Strategy

- Status: Proposed

**TL;DR**: Failed webhook deliveries currently aren't retried at all — a downstream outage means a permanently lost event. This ADR picks a retry strategy.

## Questions

### QST: Should failed webhook deliveries retry with exponential backoff, or a fixed interval?
- Status: unanswered
- Why asking: a fixed interval is simple but can pile up retries during a sustained outage; backoff is more resilient but needs a cap so it doesn't retry forever.
- Need: pick an option

**Option A — Fixed interval** (retry every 30s, up to 5 times). Simple to reason about and debug.

**Option B — Exponential backoff** (1s, 2s, 4s, 8s, 16s, capped at 5 attempts). Backs off automatically during a real outage instead of hammering a downed endpoint.

**Recommendation**: (by Loftsman)

**B — exponential backoff.** Justification: a fixed interval retries at the same rate whether the downstream is down for a second or an hour, which is exactly the pattern that turns a brief outage into a thundering herd once it recovers. Consequence if wrong: if most failures are truly transient (a single dropped packet, not an outage), backoff adds needless latency to the first retry — a fixed short interval would recover faster in that specific case.

**ANS:** (by [name])
[Fill this in]

---

## Links
