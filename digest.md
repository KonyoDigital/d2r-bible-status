# D2R Bible System Digest

_Snapshot generated: 2026-06-19 17:41:23 · pushed: 2026-06-19 17:41:23 IDT_

**System health**: 🟡 NEEDS ATTENTION
**Attention (red / warn / stale / overdue)**: I, Q, R, S, T
**Fires today**: 42 (full-day 24/7 ideal 262 — the Mac sleeps, so a number below the ideal is EXPECTED and is NOT an underfire; judge health by per-routine staleness, not this ratio)

## Routines

_`⏰ stale` = interval job overdue vs its own interval; `⏰ overdue` = daily job past its time today with 0 fires. A low Today count with a recent Last Run and no ⏰ flag is HEALTHY (laptop sleep)._

| ID | Status | Schedule | Last Run | Today | Health | Summary |
|----|--------|----------|----------|-------|--------|---------|
| I | 🟡 warn | daily 09:00 | 2026-06-18 09:33:50 | 0/1 | ⏰ overdue | 940 passed · 1 failed · 5 skipped |
| P | 🟡 warn | every 30min | 2026-06-19 05:33:52 | 7/48 | ⏰ stale | attention: I, Q, R, S · 11/14 green · 32 fires today |
| Q | 🟡 warn | every 1h | 2026-06-19 17:41:23 | 4/24 | on-schedule | 6 auto-fixes · 2 alerts · fixed: [FIXED] G was stale (16h since, [FIXED] H was s |
| G | 🟢 green | every 6h | 2026-06-19 01:00:28 | 1/4 | on-schedule | 7/7 categories · 312/312 items · sim 3783ms · 0 errors |
| H | 🟢 green | every 12h | 2026-06-18 17:08:41 | 0/2 | on-schedule | 312/312 items click cleanly · 0 fails · 27471ms |
| J | 🟢 green | daily 10:00 | 2026-06-19 10:19:29 | 1/1 | on-schedule | 4 screenshots captured · 348K logs/J_20260619_100745/01_bosses.png 348K logs/J_2 |
| K | 🟢 green | every 6h | 2026-06-19 17:41:23 | 2/4 | on-schedule | skipped · system load 8.33 too high (>4) |
| L | 🟢 green | daily 10:30 | 2026-06-19 10:36:03 | 1/3 | on-schedule | no drift · items=312 bosses=11 |
| M | 🟢 green | manual | 2026-05-26 22:36:56 | 0 | on-schedule | no patches needed |
| N | 🟢 green | daily 23:30 | 2026-06-18 23:30:00 | 0/1 | on-schedule | rollup written (19463 bytes, 14 routines) |
| O | 🟢 green | manual | 2026-05-27 13:13:21 | 0/3 | on-schedule | v42 shipped — command palette + runewords + recently-viewed + TZ countdown |
| R | 🟢 green | every 2h | 2026-05-31 19:08:06 | 0/12 | ⏰ stale | all 7 smoke checks passed · live widget OK · screenshots saved |
| S | 🟢 green | every 10min | 2026-06-19 16:25:14 | 22/144 | ⏰ stale | polled issue #1 · processed 0 new comments · cursor (none) |
| T | 🟢 green | 15×/day (A-F LLM proxy) | 2026-06-19 10:19:31 | 4/15 | ⏰ stale | C fired · severity=yellow · 3935/244 tok |

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
