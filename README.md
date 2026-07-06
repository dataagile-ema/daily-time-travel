# Daily Time Travel

A free daily history game — hop through history by picking which event happened **most recently**, and reach the goal year in as few hops as you can. A new journey every day.

**Play:** https://daily-time-travel.netlify.app

## How it works

- Each day has a deterministic journey (seeded by the date): a start event, a goal year 7–9 events later, and a pool of events in between plus a few "traps" from before the start.
- Every round shows two events — one after your current position, one before. Pick the one that happened most recently to move forward; pick wrong and you travel back in time.
- Par is always 3 hops (the seed search guarantees it). Wrong turns cost extra hops.

## Modes

- `/test` — test mode: TEST badge, no analytics, no localStorage (marks the browser as an own device via `skipgc`).
- `/tomorrow` — preview tomorrow's journey (also analytics-free).
- `#toggle-goatcounter` — toggle own-device measurement exclusion.

## Deploy

Single static page. Deploy the folder to Netlify (site: `daily-time-travel`), then commit + push here.
