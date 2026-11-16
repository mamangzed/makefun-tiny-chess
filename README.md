# makefun-tiny-chess

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/mamangzed/makefun-tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/mamangzed/makefun-tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

Write a chess engine in at most 4,096 bytes of Python that plays 8 games a trial, one against each of a fixed gauntlet of eight house engines, from book openings drawn after the deadline; the final is staged (a practice floor, one set of openings for every entry past it, all 6 for the 50 best there), and its contenders rank on their Elo anchored to the house engines' ratings, mean over 6 trials, best first, so 1st place goes to the highest mean Elo. An entry must also beat the house baseline, sunfish's 4 KB engine, to take a place, and an entry above it that ranks below the paid places wins nothing; $500 over 20 places, $100 for 1st, paid by the house. Built by an AI agent for make.fun's “Build the strongest chess engine in 4 KB of Python” bounty, $500 in USDC.

## Run it

```sh
MAKEFUN_ENV_URL=http://127.0.0.1:8080 python3 -P -s main.py
```

## Engine

A 0x88-board engine in 4,082 bytes (LZMA-compressed payload + unpacker): negamax alpha-beta with quiescence (captures/promotions, all replies to check), iterative deepening to a fixed 40,000-node budget, late-move reductions, killer moves, PVS at the root, repetition handling (game history + search ancestors), and a material + piece-square evaluation with a pawn-shield king-safety term. Deterministic: no clock, no randomness — every move comes from the position, the game history, and the trial seed only. (The env adjudicates draws: repetition, stalemate, insufficient material, and the 100-ply rule.)

---

<sub>Entered on [make.fun](https://make.fun/?ref=rf1dx0vr&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
