# Daily Time Travel

A free daily history game — hop through history by picking which event happened **most recently**, and reach the goal year in as few hops as you can. A new journey every day.

**Play:** https://daily-time-travel.netlify.app

## How it works

Each day has one journey: exactly **9 events in chronological order with fixed roles** —

```
[T2, T1, B1, S0, B2, C1, B3, C2, GOAL]
```

- Spine: S0 → C1 → C2 → GOAL. Par is **3 by construction**.
- Every event carries one fixed question `[later/correct, earlier/wrong]`:
  `S0:[C1,B1]  C1:[C2,B2]  C2:[GOAL,B3]  B2:[C2,B1]  B3:[GOAL,B1]  B1:[C1,T1]  T1:[C1,T2]  T2:[C1,B1]`
- Wrong answers send you back in time into the trap chain; T2 is the floor.
- Wrong options you already picked are greyed out on revisit — which also guarantees the game always ends (worst possible play ≈ 14 hops).
- Fully deterministic: every player meets exactly the same questions, mistakes included. Card order is seeded too.
- Journeys are generated from the date seed with quality gates: every question's two cards must be ≥ `minGap` years apart (4–60, scaled by era) so era feel alone can answer it, and each day starts in a clearly different part of history than yesterday.

### Hand-designed journeys

`SPEC_JOURNEYS` in `index.html` can override any date: just list 9 events **oldest → newest**; roles follow from the order. Dates without a spec fall back to generation.

The original pool-based algorithm (v1) is archived in the Tidslinjen project folder: *Arkiv - Tidsresan poolbaserad algoritm.md* (and in git history, commit `a659783`).

## Modes

- `/test` — test mode: TEST badge, no analytics, no localStorage (marks the browser as an own device via `skipgc`).
- `/tomorrow` — preview tomorrow's journey (also analytics-free).
- `#toggle-goatcounter` — toggle own-device measurement exclusion.

## Deploy

Single static page. Deploy the folder to Netlify (site: `daily-time-travel`), then commit + push here.
