# D2R Bible Status Feed

Public mirror of the D2R Bible routine ecosystem. Updated every 30min by Routine P on Konyo's Mac.

Read by **Claude.ai Routines A-F** (D2R Bible thinking layer) via raw.githubusercontent.com.

## Files
- `status.json` — current snapshot, all 10 local routines + fires counter
- `recent_obsidian.md` — last N entries from each routine_X_history.md
- `digest.md` — one-page Markdown summary (recommended for Claude routine fetch)

## Architecture

```
Local launchd routines (G H I J K L N P Q R)
        |
        v  Routine P (every 30min) writes routine_status.json
        |  + bridge.py pushes to this repo
        v
GitHub repo (this) <-- Claude.ai Routines A-F fetch via web_fetch
                              |
                              v Claude writes 1-line tracker entry per fire
```
