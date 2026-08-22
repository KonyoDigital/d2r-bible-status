# D2R Bible System Digest

_Snapshot generated: 2026-08-22 11:27:17 · pushed: 2026-08-22 11:27:17 IDT_

**System health**: 🟡 NEEDS ATTENTION
**Attention (red / warn / stale / overdue)**: I, L, Q
**Fires today**: 117 (full-day 24/7 ideal 262 — the Mac sleeps, so a number below the ideal is EXPECTED and is NOT an underfire; judge health by per-routine staleness, not this ratio)

## Routines

_`⏰ stale` = interval job overdue vs its own interval; `⏰ overdue` = daily job past its time today with 0 fires. A low Today count with a recent Last Run and no ⏰ flag is HEALTHY (laptop sleep)._

| ID | Status | Schedule | Last Run | Today | Health | Summary |
|----|--------|----------|----------|-------|--------|---------|
| L | 🔴 red | daily 10:30 | 2026-08-21 10:30:08 | 0/3 | on-schedule | 1 drift(s) detected · items=320 bosses=13 |
| Q | 🔴 red | every 1h | 2026-08-22 10:47:17 | 11/24 | on-schedule | 🔴 L Playwright timeout loading… · 1 auto-fixes · 1 alerts · fixed: [FIXED] L std |
| I | 🟡 warn | daily 09:00 | 2026-08-21 10:40:56 | 0/1 | ⏰ overdue | 2 flaked (2047 passed) · Error: hovering the piece name raised no card — check t |
| P | 🟡 warn | every 30min | 2026-08-22 10:57:13 | 22/48 | on-schedule | attention: I, L, Q · 10/14 green · 113 fires today |
| G | 🟢 green | every 6h | 2026-08-22 08:05:46 | 1/4 | on-schedule | 7/7 categories · 312/312 items · sim 4348ms · 0 errors |
| H | 🟢 green | every 12h | 2026-08-22 02:08:52 | 1/2 | on-schedule | 320/320 items click cleanly · 0 fails · 506011ms |
| J | 🟢 green | daily 10:00 | 2026-08-22 10:01:30 | 1/1 | on-schedule | 4 screenshots captured · 592K logs/J_20260822_100002/01_bosses.png 12K logs/J_20 |
| K | 🟢 green | every 6h | 2026-08-22 07:47:59 | 2/4 | on-schedule | skipped · system load 25.52 too high (>4) |
| M | 🟢 green | manual | 2026-05-26 22:36:56 | 0 | on-schedule | no patches needed |
| N | 🟢 green | daily 23:30 | 2026-08-21 23:30:05 | 0/1 | on-schedule | rollup written (19174 bytes, 14 routines) |
| O | 🟢 green | manual | 2026-05-27 13:13:21 | 0/3 | on-schedule | v42 shipped — command palette + runewords + recently-viewed + TZ countdown |
| R | 🟢 green | every 2h | 2026-08-22 08:51:15 | 3/12 | on-schedule | all 7 smoke checks passed · live widget OK · screenshots saved |
| S | 🟢 green | every 10min | 2026-08-22 11:23:08 | 68/144 | on-schedule | polled issue #1 · processed 0 new comments · cursor (none) |
| T | 🟢 green | 15×/day (A-F LLM proxy) | 2026-08-22 10:15:14 | 8/15 | on-schedule | C fired · severity=yellow · 4129/354 tok |

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
