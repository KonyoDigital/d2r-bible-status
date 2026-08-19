# D2R Bible System Digest

_Snapshot generated: 2026-08-19 23:36:16 · pushed: 2026-08-19 23:36:16 IDT_

**System health**: 🟡 NEEDS ATTENTION
**Attention (red / warn / stale / overdue)**: I, L
**Fires today**: 196 (full-day 24/7 ideal 262 — the Mac sleeps, so a number below the ideal is EXPECTED and is NOT an underfire; judge health by per-routine staleness, not this ratio)

## Routines

_`⏰ stale` = interval job overdue vs its own interval; `⏰ overdue` = daily job past its time today with 0 fires. A low Today count with a recent Last Run and no ⏰ flag is HEALTHY (laptop sleep)._

| ID | Status | Schedule | Last Run | Today | Health | Summary |
|----|--------|----------|----------|-------|--------|---------|
| I | 🔴 red | daily 09:00 | 2026-08-19 11:48:16 | 1/1 | on-schedule | 20 REGRESSED (1999 passed) · Error: .tools-legend-fab never became visible withi |
| L | 🔴 red | daily 10:30 | 2026-08-19 10:30:10 | 1/3 | on-schedule | 1 drift(s) detected · items=320 bosses=13 |
| P | 🟡 warn | every 30min | 2026-08-19 23:06:14 | 36/48 | on-schedule | attention: I, L · 11/14 green · 189 fires today |
| G | 🟢 green | every 6h | 2026-08-19 19:37:06 | 3/4 | on-schedule | 7/7 categories · 312/312 items · sim 3510ms · 0 errors |
| H | 🟢 green | every 12h | 2026-08-19 13:35:25 | 1/2 | on-schedule | 320/320 items click cleanly · 0 fails · 78022ms |
| J | 🟢 green | daily 10:00 | 2026-08-19 10:00:09 | 1/1 | on-schedule | 4 screenshots captured · 588K logs/J_20260819_100002/01_bosses.png 512K logs/J_2 |
| K | 🟢 green | every 6h | 2026-08-19 19:34:08 | 3/4 | on-schedule | load 1008ms · boss 68ms · sim2k 4507ms · best-of-3 |
| M | 🟢 green | manual | 2026-05-26 22:36:56 | 0 | on-schedule | no patches needed |
| N | 🟢 green | daily 23:30 | 2026-08-19 23:30:06 | 1/1 | on-schedule | rollup written (17106 bytes, 14 routines) |
| O | 🟢 green | manual | 2026-05-27 13:13:21 | 0/3 | on-schedule | v42 shipped — command palette + runewords + recently-viewed + TZ countdown |
| Q | 🟢 green | every 1h | 2026-08-19 23:33:52 | 19/24 | on-schedule | 0 auto-fixes · 0 alerts |
| R | 🟢 green | every 2h | 2026-08-19 23:35:49 | 9/12 | on-schedule | all 7 smoke checks passed · live widget OK · screenshots saved |
| S | 🟢 green | every 10min | 2026-08-19 23:26:45 | 110/144 | on-schedule | polled issue #1 · processed 0 new comments · cursor (none) |
| T | 🟢 green | 15×/day (A-F LLM proxy) | 2026-08-19 21:00:07 | 11/15 | on-schedule | B-PM fired · severity=yellow · 4086/138 tok |

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
