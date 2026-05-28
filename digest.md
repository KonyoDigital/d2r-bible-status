# D2R Bible System Digest

_Snapshot generated: 2026-05-28 21:29:47 · pushed: 2026-05-28 21:29:47 IDT_

**Total fires today**: 224 / 262 expected
**All green**: False

## Routines

| ID | Status | Schedule | Last Run | Today | Summary |
|----|--------|----------|----------|-------|---------|
| I | 🟡 warn | daily 09:00 | 2026-05-28 09:09:22 | 1/1 | 151 passed · 3 failed · 1 skipped |
| P | 🟡 warn | every 30min | 2026-05-28 20:59:45 | 43/48 | 219/262 fires today · 12/14 green |
| G | 🟢 green | every 6h | 2026-05-28 20:00:44 | 3/4 | 7/7 categories · 312/312 items · sim 3508ms · 0 errors |
| H | 🟢 green | every 12h | 2026-05-28 19:59:01 | 2/2 | 312/312 items click cleanly · 0 fails · 15463ms |
| J | 🟢 green | daily 10:00 | 2026-05-28 10:00:10 | 1/1 | 4 screenshots captured · 336K logs/J_20260528_100006/01_bosses.png 548K logs/J_2 |
| K | 🟢 green | every 6h | 2026-05-28 19:59:04 | 3/4 | load 1064ms · boss 57ms · sim2k 4510ms · best-of-3 |
| L | 🟢 green | daily 10:30 | 2026-05-28 10:30:02 | 1/3 | no drift · items=312 bosses=11 |
| M | 🟢 green | manual | 2026-05-26 22:36:56 | 0 | no patches needed |
| N | 🟢 green | daily 23:30 | 2026-05-27 23:30:05 | 0/1 | rollup written (16021 bytes, 14 routines) |
| O | 🟢 green | manual | 2026-05-27 13:13:21 | 0/3 | v42 shipped — command palette + runewords + recently-viewed + TZ countdown |
| Q | 🟢 green | every 1h | 2026-05-28 20:58:45 | 21/24 | 0 auto-fixes · 0 alerts |
| R | 🟢 green | every 2h | 2026-05-28 20:00:07 | 10/12 | all 7 smoke checks passed · live widget OK · screenshots saved |
| S | 🟢 green | every 10min | 2026-05-28 21:20:14 | 127/144 | polled issue #1 · processed 0 new comments · cursor (none) |
| T | 🟢 green | 15×/day (A-F LLM proxy) | 2026-05-28 21:00:09 | 12/15 | B-PM fired · severity=green · 3568/101 tok |

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
- **S** — Tracker poller · polls GitHub Issue #1 every 10min, relays Claude.ai routine status to Obsidian/Telegram (legacy — claude.ai routines never wired due to missing GitHub connector)
- **T** — Claude.ai routine proxy · runs the A-F prompts (System Pulse, Content Health am/pm, Daily Rollup, Drift Watch, Heal Insights, Meta-Health) via Anthropic API directly. 15×/day, writes to 90-ClaudeTracker/, Telegram on red

## Architecture

Local launchd routines (G-T, 18 scheduled jobs covering audit/heal/poller/proxy pipelines) → Routine P collects status → bridge_push.py commits to this repo every 30min. Routine T runs the A-F observation prompts via Anthropic API directly, writing observations to obsidian_data/D2R-Bible/90-ClaudeTracker/ and sending Telegram alerts on severity=red. Routines G-R handle mechanical audits/health-checks; T handles LLM-driven pattern recognition + blind-spot analysis.

Local handles mechanical work; Claude.ai handles pattern recognition + trend analysis.
