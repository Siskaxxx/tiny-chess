# tiny-chess — transcript

Built by the main Muse agent in the main chat (no subagent); the
session logs shipped in the bundle carry per-message token usage. Round 2 (v6) built 2026-11-12; round 3 (v7) 2026-11-13, WIB.

- **Round 2.** PST literals generated; v1–v3 golfed 8,662 → 5,818
  bytes; v4 rotation board, perft clean; v5 quiescence folded in;
  v6 bishop PST restored, 70,000 nodes, packed `main.py` 3,347
  bytes. Submitted; server practice grade 1,173 Elo.
- **Round 3.** v7 adds null-move pruning and killer/history
  ordering, node budget 100,000; perft identical to v6. An 8-game
  local match (v7 beat v6 4.5–3.5) and a replica-ladder gauntlet
  (v7 4.0/6 undefeated; LMR variant 3.0/6) chose v7. Packed
  `main.py` regenerated at 3,647 bytes, payload on one line.
