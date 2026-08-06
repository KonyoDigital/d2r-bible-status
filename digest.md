# D2R Bible System Digest

_Snapshot generated: 2026-08-06 13:33:12 · pushed: 2026-08-06 13:33:12 IDT_

**System health**: 🟡 NEEDS ATTENTION
**Attention (red / warn / stale / overdue)**: I
**Fires today**: 142 (full-day 24/7 ideal 262 — the Mac sleeps, so a number below the ideal is EXPECTED and is NOT an underfire; judge health by per-routine staleness, not this ratio)

## Routines

_`⏰ stale` = interval job overdue vs its own interval; `⏰ overdue` = daily job past its time today with 0 fires. A low Today count with a recent Last Run and no ⏰ flag is HEALTHY (laptop sleep)._

| ID | Status | Schedule | Last Run | Today | Health | Summary |
|----|--------|----------|----------|-------|--------|---------|
| I | 🔴 red | daily 09:00 | 2026-08-05 10:38:43 | 0/1 | ⏰ overdue | 1857 passed · 27 failed · 15 skipped |
| P | 🟡 warn | every 30min | 2026-08-06 12:33:09 | 26/48 | on-schedule | attention: I · 12/14 green · 135 fires today |
| G | 🟢 green | every 6h | 2026-08-06 11:25:13 | 2/4 | on-schedule | 7/7 categories · 312/312 items · sim 3524ms · 0 errors |
| H | 🟢 green | every 12h | 2026-08-06 09:19:39 | 1/2 | on-schedule | 322/322 items click cleanly · 0 fails · 18890ms |
| J | 🟢 green | daily 10:00 | 2026-08-06 10:00:13 | 1/1 | on-schedule | 4 screenshots captured · 604K logs/J_20260806_100005/01_bosses.png 568K logs/J_2 |
| K | 🟢 green | every 6h | 2026-08-06 11:19:24 | 2/4 | on-schedule | skipped · system load 11.78 too high (>4) |
| L | 🟢 green | daily 10:30 | 2026-08-06 10:30:09 | 1/3 | on-schedule | no drift · items=322 bosses=13 |
| M | 🟢 green | manual | 2026-05-26 22:36:56 | 0 | on-schedule | no patches needed |
| N | 🟢 green | daily 23:30 | 2026-08-05 23:30:00 | 0/1 | on-schedule | rollup written (17677 bytes, 14 routines) |
| O | 🟢 green | manual | 2026-05-27 13:13:21 | 0/3 | on-schedule | v42 shipped — command palette + runewords + recently-viewed + TZ countdown |
| Q | 🟢 green | every 1h | 2026-08-06 13:17:33 | 14/24 | on-schedule | 1 auto-fixes · 0 alerts · fixed: [FIXED] P stderr was 1253B → a |
| R | 🟢 green | every 2h | 2026-08-06 12:22:31 | 7/12 | on-schedule | all 7 smoke checks passed · live widget OK · screenshots saved |
| S | 🟢 green | every 10min | 2026-08-06 13:31:34 | 80/144 | on-schedule | polled issue #1 · processed 0 new comments · cursor (none) |
| T | 🟢 green | 15×/day (A-F LLM proxy) | 2026-08-06 10:15:11 | 8/15 | on-schedule | C fired · severity=green · 3862/286 tok |

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
