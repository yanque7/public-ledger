# handoff-ledger

An **append-only evidence ledger** for an automated DSH ↔ ChatGPT handoff loop.

Every round, a script (on a Windows machine) generates a structured report, sends it into a
ChatGPT conversation, reads the reply back, and records the round here. This repository holds
only the **metadata and fingerprints** of those rounds — it deliberately contains:

- no conversation text,
- no source code,
- no absolute local paths.

## Why it exists

The loop's executor (DSH) validates its own work, so any "we passed" claim it makes is
self-attestation. A reviewer (the ChatGPT side) asked for an anchor it can check independently.
This repository is that anchor, with one honest caveat stated up front: **it is still pushed by
the same machine that executes the loop.** It can show that a record existed at a point in time
and that its content hash matches; it cannot prove the GUI action behind it. That last step
requires a human spot-check.

## Layout

```
ledger/T-XXXXXX-YY.json   one file per round
LEDGER.md                 index table
```

Each round file:

| field | meaning |
|---|---|
| `task_id` | round identifier |
| `ts` | ISO-8601 timestamp of the round |
| `gate_state` | `blocked` / `needs_review` / `done` from the acceptance gate |
| `sent_chars` | characters written into the chat input box |
| `reply_latency_ms` | time between send and the reply being detected |
| `report_sha256` | SHA-256 of the exact report text that was sent |
| `reply_sha256` | SHA-256 of the exact reply text that was captured |
| `note` | free-form, e.g. capture caveats |

## How to verify a claim

1. Open `ledger/<task_id>.json` and note `report_sha256`.
2. Ask the executor to produce the report file whose hash matches. A mismatch means the report
   was altered after the round.
3. Ask for the commit history of this file: the hash of the commit that introduced the entry
   fixes when it first appeared.

What this cannot do: prove that the chat UI actually transmitted the text. That is why the
policy is `needs_review` rather than `done` unless a human has separately confirmed.
