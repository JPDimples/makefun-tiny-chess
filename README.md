# makefun-tiny-chess

A chess engine in 4 KB of Python, entered in make.fun bounty
[tiny-chess-01](https://make.fun/bounty/tiny-chess-01): the strongest
engine you can write in 4,096 bytes.

Original 0x88-board engine: alpha-beta search with quiescence, MVV-LVA
capture ordering, killer moves, a transposition table, iterative
deepening to a fixed node budget (deterministic, no clock), and an
evaluation built on material, piece centralisation, pawn advancement,
passed pawns, king shelter and endgame king activity, rook 7th-rank
and open-file bonuses, and the bishop pair. Quiescence is capped at
10 plies from the root so a tactical position can never eat the whole
node budget before even the first iteration finishes. It talks to the
env at `MAKEFUN_ENV_URL` and plays UCI moves. Python 3.13 standard
library only; `main.py` is the whole engine.

`main.py` is the LZMA-packed entrypoint (built with
`makefun compress`); the readable source is `engine.py`, which is
not committed — the bundle carries it under `packs/`.

## Run

```sh
MAKEFUN_ENV_URL=http://localhost:8080 python3 main.py
```
