# D2R Bible System Digest

_Snapshot generated: 2026-05-27 06:10:21 · pushed: 2026-05-27 06:10:21 IDT_

**Total fires today**: 14 / 14 expected
**All green**: True

## Routines

| ID | Status | Schedule | Last Run | Today | Summary |
|----|--------|----------|----------|-------|---------|
| G | 🟢 green | every 6h | 2026-05-27 01:53:57 | 3/4 | 7/7 categories · 312/312 items · sim 3506ms · 0 errors |
| H | 🟢 green | every 12h | 2026-05-26 23:03:36 | 0/2 | 312/312 items click cleanly · 0 fails · 13038ms |
| I | ⚪ inactive | daily 09:00 | (never) | 0/1 | no runs yet |
| J | 🟢 green | daily 10:00 | 2026-05-26 23:03:57 | 0/1 | 4 screenshots captured · 332K	logs/J_20260526_230353/01_bosses.png 456K	logs/J_2 |
| K | 🟢 green | every 6h | 2026-05-27 06:02:13 | 1/4 | load 1057ms · boss 63ms · sim2k 4512ms |
| L | 🟢 green | daily 10:30 | 2026-05-27 02:19:36 | 6/1 | no drift · items=312 bosses=11 |
| M | 🟢 green | manual | 2026-05-26 22:36:56 | 0 | no patches needed |
| N | ⚪ inactive | daily 23:30 | (never) | 0/1 | no runs yet |
| O | 🟢 green | manual | 2026-05-27 02:19:36 | 4 | shipped konyo_d2r_bible_v41.html -> FINAL.html |

## What each routine does

- **G** — End-to-end audit · runs Playwright, verifies 7 categories (tabs/bosses/items/sliders/wishlist/sim/TZ)
- **H** — Item sweep · opens every item card (312/312), confirms no broken renders
- **I** — Route audit · validates all internal navigation links
- **J** — Visual diff · 4 screenshots captured for regression spotting
- **K** — Perf · load time, boss-open latency, 2K-trial sim duration
- **L** — Integrity drift · checks data anchors (items=312, bosses=11, Hell Meph Shako=1:912, Countess Ist=1:850)
- **M** — Auto-patch · scans for apostrophe/regression, applies patches (manual trigger)
- **N** — Obsidian rollup · nightly digest of the day's routine fires
- **O** — Ship gate · promotes v##.html → FINAL.html (requires G+L green, manual trigger)
- **P** — Status injector · this file's source; writes routine_status.json every 30min
- **Q** — Self-heal watchdog · auto-fixes stale stderr, log bloat, missed fires, plist drift
- **R** — Chrome smoke · real Chrome via CDP, takes screenshots, verifies live widget renders

## Architecture

Local launchd routines (G-R, scheduled) → Routine P collects status → bridge_push.py commits to this repo every 30min → Claude.ai Routines A-F fetch this digest, think about it, write 1-line tracker entries.

Local handles mechanical work; Claude.ai handles pattern recognition + trend analysis.
