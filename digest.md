# D2R Bible System Digest

_Snapshot generated: 2026-06-04 10:14:45 · pushed: 2026-06-04 10:14:45 IDT_

**System health**: 🟡 NEEDS ATTENTION
**Attention (red / warn / stale / overdue)**: Q, R
**Fires today**: 105 (full-day 24/7 ideal 262 — the Mac sleeps, so a number below the ideal is EXPECTED and is NOT an underfire; judge health by per-routine staleness, not this ratio)

## Routines

_`⏰ stale` = interval job overdue vs its own interval; `⏰ overdue` = daily job past its time today with 0 fires. A low Today count with a recent Last Run and no ⏰ flag is HEALTHY (laptop sleep)._

| ID | Status | Schedule | Last Run | Today | Health | Summary |
|----|--------|----------|----------|-------|--------|---------|
| P | 🟡 warn | every 30min | 2026-06-04 09:44:44 | 20/48 | on-schedule | attention: Q, R · 12/14 green · 99 fires today |
| Q | 🟡 warn | every 1h | 2026-06-04 10:08:06 | 11/24 | on-schedule | 0 auto-fixes · 1 alerts |
| G | 🟢 green | every 6h | 2026-06-04 09:24:23 | 2/4 | on-schedule | 7/7 categories · 312/312 items · sim 3513ms · 0 errors |
| H | 🟢 green | every 12h | 2026-06-03 23:14:38 | 0/2 | on-schedule | 312/312 items click cleanly · 0 fails · 111365ms |
| I | 🟢 green | daily 09:00 | 2026-06-04 09:19:41 | 1/1 | on-schedule | 347 passed · 0 failed · 1 skipped |
| J | 🟢 green | daily 10:00 | 2026-06-04 10:00:09 | 1/1 | on-schedule | 4 screenshots captured · 336K logs/J_20260604_100005/01_bosses.png 544K logs/J_2 |
| K | 🟢 green | every 6h | 2026-06-04 09:14:59 | 2/4 | on-schedule | skipped · system load 7.08 too high (>4) |
| L | 🟢 green | daily 10:30 | 2026-06-03 10:30:07 | 0/3 | on-schedule | no drift · items=312 bosses=11 |
| M | 🟢 green | manual | 2026-05-26 22:36:56 | 0 | on-schedule | no patches needed |
| N | 🟢 green | daily 23:30 | 2026-06-03 23:30:04 | 0/1 | on-schedule | rollup written (18299 bytes, 14 routines) |
| O | 🟢 green | manual | 2026-05-27 13:13:21 | 0/3 | on-schedule | v42 shipped — command palette + runewords + recently-viewed + TZ countdown |
| R | 🟢 green | every 2h | 2026-05-31 19:08:06 | 0/12 | ⏰ stale | all 7 smoke checks passed · live widget OK · screenshots saved |
| S | 🟢 green | every 10min | 2026-06-04 10:14:11 | 62/144 | on-schedule | polled issue #1 · processed 0 new comments · cursor (none) |
| T | 🟢 green | 15×/day (A-F LLM proxy) | 2026-06-04 09:10:04 | 6/15 | on-schedule | A fired · severity=yellow · 4337/243 tok |

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
