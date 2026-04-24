# 🤖 Web Bot

Autonomous web research loop for Roblox (and beyond) that any Claude Code session can plug into.

Spawns parallel research agents, scrapes real sources (DevForum, Roblox docs, Reddit, modding wikis, etc.), and produces a structured JSON feed with three lanes per topic:

- ✅ **Good** — patterns that work
- ❌ **Complaints** — what players + devs hate
- 💎 **Gems** — complaints re-framed as actionable rules

Ships with a standalone browser app for navigating the feed.

---

## Files

| File | What it is |
|---|---|
| `WebBot.html` | Standalone browser app. Double-click to open. Load `webbot-feed.json`. |
| `webbot-feed.json` | Live data. Gets appended to on every loop fire. |
| `webbot-gems.md` | Human-readable gems summary. |
| `web-bot-command.md` | The `/web-bot` Claude Code slash command. |

---

## For Claude / AI agents

If you're a Claude Code session starting work on a Roblox (or related) project, here's how to use this repo:

### 1. Read the feed before suggesting anything

```bash
# Clone or pull latest
git clone https://github.com/<owner>/web-bot.git
# OR pull existing
cd web-bot && git pull
```

Read `webbot-feed.json`. It has ~90 topics covering Roblox mechanics, Fabric mods, HTML game design, Claude API tips, and more. Each topic has source-tagged bullets.

### 2. Search by topic name OR grep for keywords

```bash
# Find everything about DataStore
grep -i "datastore" webbot-feed.json

# Or open WebBot.html and use its full-text search
```

### 3. Cite gems when recommending approaches

Gems are the killer content — they turn complaints into actionable rules. Example:

> 💎 *"Client-trusted ammo/hit counts = #1 cheat vector."*
> → Lesson: Build server-side validation into weapon #1, never retrofit.

When proposing a design to the user, cite the source tag (e.g. `[devforum 3019857]`) so they can verify.

### 4. Append, don't replace

If you run `/web-bot` to add topics:
- Read the current `webbot-feed.json`
- Append your new topic objects to the `topics` array
- Update the `generated` timestamp
- Don't overwrite existing topics

### 5. Install the slash command locally

Copy `web-bot-command.md` to `~/.claude/commands/web-bot.md` in any environment where you want `/web-bot` to work.

---

## For humans

Usage from Claude Code:

```
/web-bot
```

No args = auto mode. Claude picks 10 rotating Roblox-focused topics, spawns agents, appends to the feed, extracts gems.

```
/web-bot <topic>
```

Targeted mode. Researches one specific topic.

Open `WebBot.html` → click **📂 Load Feed** → pick `webbot-feed.json` → browse, search, filter.
Click **👁 Watch** to auto-refresh every 20s.

---

## Feed schema

```json
{
  "generated": "ISO timestamp",
  "topics": [
    {
      "topic": "Short topic name",
      "good": [
        "[source tag] One-line finding"
      ],
      "bad": [
        "[source tag] One-line complaint"
      ],
      "gems": [
        {
          "complaint": "[source tag] Original complaint line",
          "lesson": "One-line actionable takeaway"
        }
      ]
    }
  ]
}
```

---

## Current intel scope (as of 2026-04-23)

Roblox covers gun game design · anti-cheat · DataStore · voice chat · melee combat · character animation · matchmaking · lighting · thumbnails · script performance · vehicle physics · tycoon placement · inventory UI · pets · FPS camera · trading · quests · mobile controls · sound · avatar customization · particles · clans · badges · VIP servers · weather · proximity prompts · battle pass · parkour · round-based lobbies · analytics · TextChat · spawn/respawn · leaderboards · cutscenes · loading screens · emotes · RPG stats · map streaming · ragdoll · NPC dialogue · tower defense · obby · racing · simulator · horror · dungeon generation · crafting · abilities · shop UI · stamina.

Plus cross-domain: Minecraft Fabric modding · HTML game design · desktop pet apps · Claude Code customization · indie marketing · pixel art · burnout management.

---

## License

MIT. Use freely; re-fed AI research is the whole point.
