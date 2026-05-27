# D2R Bible System Digest

_Snapshot generated: 2026-05-27 15:53:27 · pushed: 2026-05-27 15:53:27 IDT_

**Total fires today**: 130 / 262 expected
**All green**: True

## Routines

| ID | Status | Schedule | Last Run | Today | Summary |
|----|--------|----------|----------|-------|---------|
| G | 🟢 green | every 6h | 2026-05-27 14:28:23 | 6/4 | 7/7 categories · 312/312 items · sim 3508ms · 0 errors |
| H | 🟢 green | every 12h | 2026-05-27 14:28:10 | 2/2 | 312/312 items click cleanly · 0 fails · 20216ms |
| I | 🟢 green | daily 09:00 | 2026-05-27 14:04:21 | 3/1 | 134 passed · 0 failed · 1 skipped |
| J | 🟢 green | daily 10:00 | 2026-05-27 14:29:31 | 3/1 | 4 screenshots captured · 336K logs/J_20260527_142928/01_bosses.png 548K logs/J_2 |
| K | 🟢 green | every 6h | 2026-05-27 14:28:09 | 4/4 | load 1233ms · boss 58ms · sim2k 4513ms · best-of-3 |
| L | 🟢 green | daily 10:30 | 2026-05-27 14:27:50 | 8/3 | no drift · items=312 bosses=11 |
| M | 🟢 green | manual | 2026-05-26 22:36:56 | 0 | no patches needed |
| N | 🟢 green | daily 23:30 | 2026-05-27 14:27:48 | 2/1 | rollup written (13149 bytes, 13 routines) |
| O | 🟢 green | manual | 2026-05-27 13:13:21 | 5/3 | v42 shipped — command palette + runewords + recently-viewed + TZ countdown |
| P | 🟢 green | every 30min | 2026-05-27 15:33:29 | 45/48 | 113/247 fires today · 13/13 green |
| Q | 🟢 green | every 1h | 2026-05-27 15:27:48 | 16/24 | 0 auto-fixes · 0 alerts |
| R | 🟢 green | every 2h | 2026-05-27 14:27:59 | 8/12 | all 7 smoke checks passed · live widget OK · screenshots saved |
| S | 🟢 green | every 10min | 2026-05-27 15:47:57 | 14/144 | polled issue #1 · processed 0 new comments · cursor (none) |
| T | 🟢 green | 15×/day (A-F LLM proxy) | 2026-05-27 15:49:00 | 14/15 | F fired · severity=yellow · 3487/198 tok |

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
- **S** — Tracker poller · polls GitHub Issue #1 every 10min, relays Claude.ai routine status to Obsidian/Telegram
- **T** — _(reserved)_

## Architecture

Local launchd routines (G-S, 11 scheduled jobs covering audit/heal/poller pipelines) → Routine P collects status → bridge_push.py commits to this repo every 30min → Claude.ai Routines A-F (installed in desktop app Settings → Routines) fetch this digest, think about it, post 1-line tracker entries to Issue #1, which Routine S relays back to Obsidian + Telegram.

Local handles mechanical work; Claude.ai handles pattern recognition + trend analysis.
