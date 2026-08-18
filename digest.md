# D2R Bible System Digest

_Snapshot generated: 2026-08-18 18:03:43 · pushed: 2026-08-18 18:03:43 IDT_

**System health**: 🟡 NEEDS ATTENTION
**Attention (red / warn / stale / overdue)**: I, L, T
**Fires today**: 194 (full-day 24/7 ideal 262 — the Mac sleeps, so a number below the ideal is EXPECTED and is NOT an underfire; judge health by per-routine staleness, not this ratio)

## Routines

_`⏰ stale` = interval job overdue vs its own interval; `⏰ overdue` = daily job past its time today with 0 fires. A low Today count with a recent Last Run and no ⏰ flag is HEALTHY (laptop sleep)._

| ID | Status | Schedule | Last Run | Today | Health | Summary |
|----|--------|----------|----------|-------|--------|---------|
| I | 🔴 red | daily 09:00 | 2026-08-18 10:37:25 | 1/1 | on-schedule | 4 REGRESSED (1985 passed) · Error: hovering the piece name raised no card — chec |
| L | 🔴 red | daily 10:30 | 2026-08-18 10:30:08 | 1/3 | on-schedule | 1 drift(s) detected · items=320 bosses=13 |
| P | 🟡 warn | every 30min | 2026-08-18 17:33:40 | 36/48 | on-schedule | attention: I, L · 11/14 green · 187 fires today |
| T | 🟡 warn | 15×/day (A-F LLM proxy) | 2026-08-18 17:55:40 | 11/15 | on-schedule | D fired · severity=red · 4140/219 tok |
| G | 🟢 green | every 6h | 2026-08-18 18:02:41 | 4/4 | on-schedule | 7/7 categories · 312/312 items · sim 3507ms · 0 errors |
| H | 🟢 green | every 12h | 2026-08-18 13:56:00 | 2/2 | on-schedule | 320/320 items click cleanly · 0 fails · 11311ms |
| J | 🟢 green | daily 10:00 | 2026-08-18 10:00:15 | 1/1 | on-schedule | 4 screenshots captured · 592K logs/J_20260818_100005/01_bosses.png 576K logs/J_2 |
| K | 🟢 green | every 6h | 2026-08-18 13:56:51 | 3/4 | on-schedule | skipped · system load 5.43 too high (>4) |
| M | 🟢 green | manual | 2026-05-26 22:36:56 | 0 | on-schedule | no patches needed |
| N | 🟢 green | daily 23:30 | 2026-08-17 23:30:05 | 0/1 | on-schedule | rollup written (15006 bytes, 14 routines) |
| O | 🟢 green | manual | 2026-05-27 13:13:21 | 0/3 | on-schedule | v42 shipped — command palette + runewords + recently-viewed + TZ countdown |
| Q | 🟢 green | every 1h | 2026-08-18 17:56:12 | 18/24 | on-schedule | 0 auto-fixes · 0 alerts |
| R | 🟢 green | every 2h | 2026-08-18 17:05:50 | 9/12 | on-schedule | all 7 smoke checks passed · live widget OK · screenshots saved |
| S | 🟢 green | every 10min | 2026-08-18 17:58:30 | 108/144 | on-schedule | polled issue #1 · processed 0 new comments · cursor (none) |

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
