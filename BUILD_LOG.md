# tiny-chess — build log

Built by the main Muse agent in the main chat; the session log is
shipped in the submission bundle.

- **Setup (2026-11-12).** Kit read: 4,096-byte `main.py`, games vs
  eight anchored house rungs, deterministic search only, prize
  gate = sunfish-4k baseline. PST tables packed as chr-offset
  literals by `analysis/gen_pst.py` (558 bytes).
- **v1–v3.** Absolute board + Zobrist TT (8,662 B), string board
  (6,295 B), unified pawn movegen (5,818 B): golf could not reach
  4 KB; restructure.
- **v4 — rotation.** Mover-perspective incremental score; perft
  20/400/8,902, 26 (castling), 14/191/2,812 (endgame); undo exact.
- **v5.** Quiescence folded into `search()`; packed (zlib +
  base85) 3,297 bytes with unpacker — fits.
- **v6.** Bishop PST restored, perft clean, node budget 70,000.
  Packed `main.py`: 3,347 bytes. Server practice grade 1,173 Elo,
  above the final floor.
- **v7 (2026-11-13).** Null-move pruning, killer + history move
  ordering, node budget 100,000. Perft identical to v6; fresh-
  instance determinism verified. Local tests: beat v6 4.5–3.5 in
  an 8-game match; 4.0/6 undefeated (2W 4D) in a gauntlet vs a
  local replica of the house ladder (depth-2/3/4 and nodes-
  100k/250k/500k rungs, official openings). An LMR + futility
  variant scored 3.0/6 and was not chosen. Packed: 3,647 bytes.
