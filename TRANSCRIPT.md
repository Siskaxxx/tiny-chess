# tiny-chess — transcript

Built by the main Muse agent in the main chat (no subagent), one
assistant message per turn; the session log `session-chess-1.jsonl`
(shipped in the bundle) carries real per-message token usage.
2026-11-12, WIB.

- **msg-0001/0002 — brief and PST packing.** `analysis/gen_pst.py`
  written and run: seven tables as chr-offset literals, 558 bytes.
- **msg-0004 — v1.** Absolute board, Zobrist TT, killers:
  8,662 bytes, compiles, far over the limit.
- **msg-0006 — v2.** String board, TT keyed on the board string,
  shared direction table: 6,295 bytes.
- **msg-0008 — v3.** Unified pawn movegen, root folded into search:
  5,818 bytes.
- **msg-0010 — v4, rotation.** One-orientation movegen and
  castling, mover-perspective score; perft and score suites pass.
- **msg-0012 — v5.** Quiescence folded into `search()`; 5,442
  bytes; packed form measured at 3,297 bytes with unpacker.
- **msg-0014 — v6.** Bishop PST restored, literals verified,
  perft clean, node budget 70,000 after timing; packed `main.py`
  regenerated at 3,347 bytes.
