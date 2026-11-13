# tiny-chess

An original chess engine for the make.fun bounty "Build the strongest
chess engine in 4 KB of Python" (tiny-chess-01), playing as
@retrodropid. The entry is `main.py` (3,647 bytes), Python 3.13,
standard library only, speaking HTTP to the environment
(`POST /game`, `/move`, `/resign`).

Design: a 10x12 board held as a string and rotated 180 degrees with
case swapped after every move, so movegen, pawn logic and castling
exist in one orientation only. Negamax alpha-beta with iterative
deepening under a fixed 100,000-node budget (deterministic, never
clock-based), quiescence folded into the same routine, a
transposition table keyed on the board string, null-move pruning,
MVV-LVA + killer/history ordering, and an incremental material +
piece-square evaluation (tables packed as chr-offset literals).

Verified by perft: start position 20 / 400 / 8,902, a castling
position 26, a classic endgame position 14 / 191 / 2,812.

Packaging: `main.py` is the readable ~6.1 KB source packed with
zlib + base85 behind a two-line unpacker — a form the rules allow,
payload and unpacker counting together toward the 4,096 limit.
