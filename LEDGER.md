# Round ledger

One JSON file per round in `ledger/`. Fields: task_id, ts (ISO-8601), gate_state,
sent_chars (characters pushed into the chat input), reply_latency_ms, report_sha256,
reply_sha256 (SHA-256 of the exact local files this round produced).

| task_id | ts (UTC) | gate_state | sent_chars | report_sha256 (first 12) | reply_sha256 (first 12) | note |
|---|---|---|---|---|---|---|
| T-1103-11 | 2026-11-03T12:32:49.773Z | needs_review | 3305 | `54b0ba3e72ff` | `c53d6d048df0` |  |
| T-1103-12 | 2026-11-03T12:38:03.055Z | needs_review | 3943 | `748e6108eed6` | `7b5392a0575d` |  |
| T-1103-13 | 2026-11-03T20:44:06.0546843+08:00 | done | 16982 | `234b6a5187b2` | `432c45c385d7` | 人工独立核对通过：用户于 2026-11-04T01:19+08:00 在桌面端比对原始发送内容与完整回复，结果一致（verification/T-1103-13.md） |
| T-1103-14 | 2026-11-03T17:00:29.594Z | needs_review | 4303 | `d2e35bc9caa2` | `b4c35c614986` |  |
| T-1103-15 | 2026-11-03T17:10:17.888Z | needs_review | 4955 | `38241d86b65e` | `97ec0d50644a` |  |
| T-1103-16 | 2026-11-03T17:22:17.772Z | needs_review | 4374 | `7e6027b29a96` | `97d892d2065a` |  |
| T-1103-17 | 2026-11-03T17:24:15.762Z | needs_review | 3376 | `b437eb6316e5` | `2ef3cf64573d` |  |

