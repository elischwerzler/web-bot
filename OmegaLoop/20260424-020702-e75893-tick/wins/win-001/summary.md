# Win-001: /web-bot auto mode — 10 fresh Roblox topics

**Session:** 20260424-020702-e75893-tick
**Task:** Run the /web-bot slash command in auto mode to research 10 fresh Roblox-focused topics not already in webbot-feed.json. Append new topic objects, update generated timestamp, commit, and push.

## Outcome
Appended 10 fresh Roblox-focused topics to `webbot-feed.json`. Topic count 98 → 108. Timestamp updated to `2026-04-24T02:07:02Z`. Gems appended to `webbot-gems.md`.

## New topics added
1. Roblox battlegrounds game design
2. Roblox Rojo workflow
3. Roblox MessagingService cross-server
4. Roblox Open Cloud API external integration
5. Roblox rebirth prestige system
6. Roblox live events and concerts design
7. Roblox anime fighting game design
8. Roblox Knit framework
9. Roblox Wally package manager
10. Roblox gacha lootbox system design

## Method
Launched 10 parallel `general-purpose` research agents, each running 4-6 WebSearch calls and 3+ WebFetches per topic. Compiled returned JSON into topic objects with good/bad/gems structure. Originally researched 10 topics but discovered mid-run that a concurrent web-bot run added 10 topics of its own, overlapping with 3 of mine (ProfileService session locking, Luau strict typechecking, Roblox daily login rewards). Replaced those 3 with fresh research on Knit, Wally, and gacha/lootbox design.

## Experiments run this tick
1. **Exp 1 — Batch-research 10 Roblox topics in parallel.** Implemented via 10 Agent calls. WIN — all returned valid JSON with target item counts.
2. **Exp 2 — Edit webbot-feed.json tail to append topics.** First attempt failed with "file has been modified" (concurrent write). Re-read file, re-checked overlap, DISCARDED 3 topics.
3. **Exp 3 — Research 3 replacement topics (Knit, Wally, gacha).** WIN — 3 more agents returned clean JSON.
4. **Exp 4 — Append 10 new topics + update timestamp via single Edit.** WIN — file validated by `python -c json.load`, topic count 108.
5. **Exp 5 — Append matching gem sections to `webbot-gems.md`.** WIN — 8,915 chars appended covering all 10 new topics.

## Highest-value gems discovered
- **Gacha/lootbox compliance:** Roblox ToS requires disclosing drop rates when Robux buys random items. Use `GetPolicyInfoForPlayerAsync().ArePaidRandomItemsRestricted` to auto-hide gacha UI in restricted regions — missing this is a ToS/legal violation risk.
- **MessagingService reliability:** It is explicitly "best-effort" — never use as sole channel for critical state; pair with DataStore/MemoryStore reconciliation. Sept 2025 outage caused SubscribeAsync to yield indefinitely with no errors.
- **Knit framework status:** No longer receiving updates. Community consensus: start new projects on Matter or plain ModuleScripts + RbxUtil Comm.
- **DMCA risk in anime fighting:** Gamefam/Crunchyroll strikes wiped Anime Adventures and Anime Fighting Simulator X entirely, destroying all player progress. Design "anime-inspired" originals only.
- **Open Cloud rate limits shared across all API keys per owner** — spinning up more keys does NOT multiply quota.

## Files touched
- `webbot-feed.json` — +1,864 lines (10 new topic objects, timestamp updated)
- `webbot-gems.md` — +112 lines (gems sections for all 10 topics)
- `OmegaLoop/20260424-020702-e75893-tick/` — new session artifacts
