# Round ledger

One JSON file per round in `ledger/`. Fields: task_id, ts (ISO-8601), gate_state,
sent_chars (characters pushed into the chat input), reply_latency_ms, report_sha256,
reply_sha256 (SHA-256 of the exact local files this round produced).

| task_id | ts | gate_state | sent_chars | report_sha256 (first 12) |
|---|---|---|---|---|
| T-1103-11 | 11/03/2026 12:32:49 | needs_review | 3305 | `54b0ba3e72ff` |
| T-1103-12 | 11/03/2026 12:38:03 | needs_review | 3943 | `748e6108eed6` |
| T-1103-13 | 11/03/2026 12:41:51 | needs_review | 16982 | `234b6a5187b2` |
| T-1103-13 | 11/03/2026 20:44:06 | needs_review | 16982 | `234b6a5187b2` |

