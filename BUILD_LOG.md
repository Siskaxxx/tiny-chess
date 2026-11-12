# tiny-chess — build log

2026-11-12, WIB (UTC+7). Built by the main Muse agent in the main
chat, one assistant message per turn, recorded in
`session-chess-1.jsonl` (shipped in the submission bundle).

- **Setup.** Connected as @retrodropid; kit read: 4,096-byte
  `main.py`, 16 games per trial vs eight anchored house rungs,
  deterministic search only, prize gate = sunfish-4k baseline.
- **PST packing.** `analysis/gen_pst.py` packs seven piece-square
  tables as chr-offset literals (558 bytes); re-verified before
  submission.
- **v1 — 8,662 bytes.** Absolute board, Zobrist TT, killers.
  Compiles; 2.1x over the limit.
- **v2 — 6,295 bytes.** String board, slice make / restore unmake,
  TT keyed on the board string, shared direction table, rook/queen
  PSTs zeroed.
- **v3 — 5,818 bytes.** Unified pawn movegen, root folded into
  `search()`. Recorded: style golf cannot reach 4 KB; restructure.
- **v4 — 5,725 bytes, rotation.** Mover-perspective incremental
  score. Proven: perft 20/400/8,902, 26 (castling), 14/191/2,812
  (endgame); undo exact.
- **v5 — 5,442 bytes.** Quiescence folded into `search()`; packed
  form (zlib + base85) measures 3,297 bytes with unpacker — fits.
- **v6 — final.** Bishop PST restored, perft clean, node budget
  45,000 → 70,000 after timing (0.8-1.35 s/move). Packed `main.py`:
  **3,347 bytes**. grade-local cannot grade Python bots here
  (no Docker); the server practice trial grades.
