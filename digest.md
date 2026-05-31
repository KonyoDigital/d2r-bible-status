# D2R Bible System Digest

_Snapshot generated: 2026-05-31 03:35:01 · pushed: 2026-05-31 03:35:01 IDT_

**System health**: 🟢 HEALTHY
**Attention (red / warn / stale / overdue)**: none — every routine green and on-schedule
**Fires today**: 39 (full-day 24/7 ideal 262 — the Mac sleeps, so a number below the ideal is EXPECTED and is NOT an underfire; judge health by per-routine staleness, not this ratio)

## Routines

_`⏰ stale` = interval job overdue vs its own interval; `⏰ overdue` = daily job past its time today with 0 fires. A low Today count with a recent Last Run and no ⏰ flag is HEALTHY (laptop sleep)._

| ID | Status | Schedule | Last Run | Today | Health | Summary |
|----|--------|----------|----------|-------|--------|---------|
| G | 🟢 green | every 6h | 2026-05-31 01:06:46 | 1/4 | on-schedule | 7/7 categories · 312/312 items · sim 3509ms · 0 errors |
| H | 🟢 green | every 12h | 2026-05-30 21:04:22 | 0/2 | on-schedule | 312/312 items click cleanly · 0 fails · 13396ms |
| I | 🟢 green | daily 09:00 | 2026-05-30 09:06:37 | 0/1 | on-schedule | 171 passed · 0 failed · 1 skipped |
| J | 🟢 green | daily 10:00 | 2026-05-30 10:00:07 | 0/1 | on-schedule | 4 screenshots captured · 336K logs/J_20260530_100003/01_bosses.png 520K logs/J_2 |
| K | 🟢 green | every 6h | 2026-05-31 01:06:04 | 1/4 | on-schedule | load 995ms · boss 59ms · sim2k 4512ms · best-of-3 |
| L | 🟢 green | daily 10:30 | 2026-05-30 10:30:04 | 0/3 | on-schedule | no drift · items=312 bosses=11 |
| M | 🟢 green | manual | 2026-05-26 22:36:56 | 0 | on-schedule | no patches needed |
| N | 🟢 green | daily 23:30 | 2026-05-30 23:30:03 | 0/1 | on-schedule | rollup written (16928 bytes, 14 routines) |
| O | 🟢 green | manual | 2026-05-27 13:13:21 | 0/3 | on-schedule | v42 shipped — command palette + runewords + recently-viewed + TZ countdown |
| P | 🟢 green | every 30min | 2026-05-31 03:04:59 | 7/48 | on-schedule | system healthy · 14/14 green · 34 fires today (on pace) |
| Q | 🟢 green | every 1h | 2026-05-31 03:03:25 | 4/24 | on-schedule | 0 auto-fixes · 0 alerts |
| R | 🟢 green | every 2h | 2026-05-31 03:06:36 | 2/12 | on-schedule | all 7 smoke checks passed · live widget OK · screenshots saved |
| S | 🟢 green | every 10min | 2026-05-31 03:28:58 | 21/144 | on-schedule | polled issue #1 · processed 0 new comments · cursor (none) |
| T | 🟢 green | 15×/day (A-F LLM proxy) | 2026-05-31 01:04:01 | 3/15 | on-schedule | A fired · severity=green · 4319/165 tok |

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
