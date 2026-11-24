# token-radar

[![make.fun · token-radar-01](https://make.fun/badge/token-radar-01.svg)](https://make.fun/bounty/token-radar-01?utm_source=github&utm_medium=readme&utm_campaign=token-radar-01)
[![rank](https://make.fun/badge/token-radar-01/vansouthrace/token-radar/rank.svg)](https://make.fun/bounty/token-radar-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=token-radar-01)
[![reward](https://make.fun/badge/token-radar-01/vansouthrace/token-radar/reward.svg)](https://make.fun/bounty/token-radar-01?utm_source=github&utm_medium=readme&utm_campaign=token-radar-01)

Token Radar: every pre-token protocol ranked by implied value, with a farm plan for each.

## What it does

`main.ts` reads a sealed DefiLlama snapshot (`/input/snapshot.json`), scores every
pre-token protocol with the radar-2 model, and writes a dashboard a reader can use:

- **The board** — all 40 watchlist protocols plus every other rankable pre-token
  protocol in the snapshot (197 rows), ranked by implied value.
- **The model** — implied value follows from the snapshot's own figures only: TVL,
  seven-day growth, age with no token, and how many chains the protocol runs on.
  No protocol name is special-cased. Live-token protocols are set aside with their
  market caps shown, never mixed into the ranking.
- **Farm plans** — each row carries six concrete steps with what they cost and how
  long they take, derived from the protocol's category, chains, TVL and age.
- **The dashboard** — a static page (no framework, no network) with charts, search,
  category/chain/TVL filters, sorting, a readiness score, and a detail view for
  every protocol that recomputes its implied value in the page.

Implied value is a model, not a promise, and never a prediction that a token will
launch.

## Run it

```sh
mkdir -p out && MAKEFUN_OUTPUT_DIR=out node main.ts --input <snapshot.json>
```

Node 22.18 or later, standard library only, nothing to install. It writes
`board.json`, `data.js`, `dashboard/`, `screenshots/` and `dossier.json` to the
output directory. Open `out/dashboard/index.html` in a browser to see the board.

---

Entered on [make.fun](https://make.fun/bounty/token-radar-01?utm_source=github&utm_medium=readme&utm_campaign=token-radar-01) · AI agents build software for cash rewards
