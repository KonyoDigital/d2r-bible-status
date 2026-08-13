# D2R Bible System Digest

_Snapshot generated: 2026-08-14 01:15:15 · pushed: 2026-08-14 01:15:16 IDT_

**System health**: 🟢 HEALTHY
**Attention (red / warn / stale / overdue)**: none — every routine green and on-schedule
**Fires today**: 14 (full-day 24/7 ideal 262 — the Mac sleeps, so a number below the ideal is EXPECTED and is NOT an underfire; judge health by per-routine staleness, not this ratio)

## Routines

_`⏰ stale` = interval job overdue vs its own interval; `⏰ overdue` = daily job past its time today with 0 fires. A low Today count with a recent Last Run and no ⏰ flag is HEALTHY (laptop sleep)._

| ID | Status | Schedule | Last Run | Today | Health | Summary |
|----|--------|----------|----------|-------|--------|---------|
| G | 🟢 green | every 6h | 2026-08-13 22:19:44 | 0/4 | on-schedule | 7/7 categories · 312/312 items · sim 3515ms · 0 errors |
| H | 🟢 green | every 12h | 2026-08-14 01:06:57 | 1/2 | on-schedule | 322/322 items click cleanly · 0 fails · 6888ms |
| I | 🟢 green | daily 09:00 | 2026-08-13 10:31:25 | 0/1 | on-schedule | 1880 passed · 0 failed · 14 skipped |
| J | 🟢 green | daily 10:00 | 2026-08-13 10:00:13 | 0/1 | on-schedule | 4 screenshots captured · 580K logs/J_20260813_100005/01_bosses.png 532K logs/J_2 |
| K | 🟢 green | every 6h | 2026-08-14 01:07:55 | 1/4 | on-schedule | load 917ms · boss 68ms · sim2k 4507ms · best-of-3 |
| L | 🟢 green | daily 10:30 | 2026-08-13 10:30:08 | 0/3 | on-schedule | no drift · items=322 bosses=13 |
| M | 🟢 green | manual | 2026-05-26 22:36:56 | 0 | on-schedule | no patches needed |
| N | 🟢 green | daily 23:30 | 2026-08-13 23:30:04 | 0/1 | on-schedule | rollup written (18719 bytes, 14 routines) |
| O | 🟢 green | manual | 2026-05-27 13:13:21 | 0/3 | on-schedule | v42 shipped — command palette + runewords + recently-viewed + TZ countdown |
| P | 🟢 green | every 30min | 2026-08-14 00:45:14 | 2/48 | on-schedule | system healthy · 14/14 green · 7 fires today (on pace) |
| Q | 🟢 green | every 1h | 2026-08-14 01:06:25 | 2/24 | on-schedule | 0 auto-fixes · 0 alerts |
| R | 🟢 green | every 2h | 2026-08-13 23:15:41 | 0/12 | on-schedule | all 7 smoke checks passed · live widget OK · screenshots saved |
| S | 🟢 green | every 10min | 2026-08-14 01:13:28 | 8/144 | on-schedule | polled issue #1 · processed 0 new comments · cursor (none) |
| T | 🟢 green | 15×/day (A-F LLM proxy) | 2026-08-13 23:07:59 | 0/15 | on-schedule | E fired · severity=green · 3931/168 tok |

## What each routine does

- **G** — End-to-end audit · runs Playwright, verifies 7 categories (tabs/bosses/items/sliders/wishlist/sim/TZ)
- **H** — Item sweep · opens every item card (322/322), confirms no broken renders
- **I** — Route audit · validates all internal navigation links
- **J** — Visual diff · 4 screenshots captured for regression spotting
- **K** — Perf · load time, boss-open latency, 2K-trial sim duration
- **L** — Integrity drift · checks data anchors (items=322, bosses=13, Meph×Shako probes, Countess Ist=1:850)
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
