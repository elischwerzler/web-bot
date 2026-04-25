# 💎 Web Bot — Hidden Gems from Complaints

Complaints aren't just noise — many are blueprints in disguise. Here are the ones where the pain point teaches a clear lesson.

---

## 🎮 Doge Gun Game (Roblox PvP)

- **Complaint:** "Client-trusted ammo/hit counts get exploited immediately; missing server validation is the #1 cheat vector."
  **→ Gem:** Build server-side validation into the *first* weapon, not retrofitted later.

- **Complaint:** "Gunplay 'feels awful' when there's no hit feedback beyond the HP bar moving."
  **→ Gem:** Hit particles + surface sounds + knockback = perceived skill. Ship them day 1, even if weapons are prototype.

- **Complaint:** "Arsenal's skill floor is undermined by weapon RNG."
  **→ Gem:** Let players *pick* their loadout. Skill > roll luck.

- **Complaint:** "Single-mode gun-rotation formulas get stale fast."
  **→ Gem:** Plan TDM / KoTH / CTF from day 1 even if only one ships first — architecture accommodates them.

- **Complaint:** "Most players hate realism-for-realism's-sake."
  **→ Gem:** Kill any "jam/bullet-drop/reload-animation" feature before it enters design doc. Fun > sim.

---

## 🧠 Watcher World (AI NPCs)

- **Complaint:** "NPCs hallucinate — invent quests/items/locations that don't exist."
  **→ Gem:** Constrain the LLM with an action whitelist. Parse its output and drop anything not in the whitelist.

- **Complaint:** "DataStore throttle = 60 + 10*players req/min; per-key writes capped at 1 per 6s."
  **→ Gem:** Batch NPC memory saves. Save every 60-180s per player, not per interaction.

- **Complaint:** "Roblox's AI chatbot loops FAQ answers — players hate dead-end help desks."
  **→ Gem:** Every NPC needs an escape hatch ("ask me something else" / "I don't know, let's find out together") so conversation never stalls.

- **Complaint:** "Luau Assist doesn't understand game architecture."
  **→ Gem:** Hand-write core systems (memory, session-lock, WorldSpirit roller). AI can fill in leaf code only.

- **Complaint:** "47% of devs worry about 'soulless' AI NPC outputs."
  **→ Gem:** Strong persona prompts + memory curation > bigger model. Personality is your moat.

---

## 📈 Roblox Hit Games 2026

- **Complaint:** "Shipping a genre clone with no unique twist — #1 killer."
  **→ Gem:** Every project pitch must answer "what's the ONE weird thing only this game has?" before scope.

- **Complaint:** "Anime Worlds Sim: 20k CCU → 200 after updates stopped."
  **→ Gem:** Commit to a weekly/bi-weekly LiveOps cadence *before* launch, or don't launch.

- **Complaint:** "Ignoring mobile cuts off majority audience."
  **→ Gem:** Mobile-first sketching. If a menu doesn't work on a phone, redesign before building.

- **Complaint:** "Platform bandwidth spikes >10,000ms, random Studio auth failures."
  **→ Gem:** Design for graceful degradation — offline cache, retry logic, never hard-fail on network.

---

## 📱 HTML Phone Games

- **Complaint:** "iOS 300ms tap delay; multi-touch lost with mouse events."
  **→ Gem:** Wire `touchstart/touchmove/touchend` with `preventDefault()` from day 1. Never `onclick`.

- **Complaint:** "Drawing at sub-pixel float coords forces anti-aliasing — tanks perf."
  **→ Gem:** `Math.floor()` every position. Integer-only coords.

- **Complaint:** "Real fingers behave differently from devtools emulator."
  **→ Gem:** Test on actual phone on day 1. Not day 30.

- **Complaint:** "Scope creep on single-file games."
  **→ Gem:** 1 mechanic rule. Ship it before adding a second.

---

## 🐾 Desktop Pet App

- **Complaint:** "Pet keeps relaunching after close — users call it virus-like."
  **→ Gem:** Clean "goodbye" quit. No sneaky autostart. Respect user control.

- **Complaint:** "Desktop Goose cursor grabbing is disruptive."
  **→ Gem:** Never take control from user. Pets observe; they don't interfere.

- **Complaint:** "Loud honking startles — audio default on."
  **→ Gem:** Audio defaults to OFF. User opts in.

- **Complaint:** "Shimeji requires Java — users refuse to install."
  **→ Gem:** Native (no JVM) or web-based. Zero-install is the bar.

---

## ⚙ Claude Code Customization

- **Complaint:** "Skill content enters conversation once, NOT re-read on later turns."
  **→ Gem:** Structure skills as read-once instructions. Don't treat SKILL.md as rolling docs.

- **Complaint:** "Four MCP servers = 67,000 tokens before you write a prompt."
  **→ Gem:** Aggressive MCP pruning. Only enable what the current project uses.

- **Complaint:** "Long-session degradation real — 18 min vs 4.5 fresh."
  **→ Gem:** Restart session after 2-3 hours of heavy work. Fresh > patched.

- **Complaint:** "Shell profiles with startup text break hook JSON parsing."
  **→ Gem:** Keep `.bashrc` silent on interactive-check. Print nothing unless asked.

---

## 🏗 Sandbox Retention (Watcher World directly)

- **Complaint:** "Pure sandboxes with no clear goals feel like 'empty worlds' — players need something to work toward."
  **→ Gem:** Watcher World needs visible objectives. The WorldSpirit event roller is the answer — it generates goals on a timer.

- **Complaint:** "Jack of all trades, master of none."
  **→ Gem:** Pick ONE hook for Watcher World (AI-memory NPCs? the WorldSpirit?). Go deep on one. Other features support it.

- **Complaint:** "<1% D90 retention even in top games."
  **→ Gem:** Assume churn is brutal. Every design decision prioritizes *re-entry* (visible progress on return, short loops, daily cycles).

- **Complaint:** "Players drop at 3 min if onboarding is unclear."
  **→ Gem:** Core gameplay must be obvious within 60 seconds. Tutorial in the first minute or cut it.

## Web Bot Run 2026-04-24 (+10 genre subtopics)

### Roblox fishing game design
- [devforum-fisch] Fisch suffers softlock after catching fish: can't move/unequip/open UIs
  - **Lesson:** Test full input cycle (catch->move->UI) every release - softlocks kill retention more than any single bug
- [devforum-fisch] Server-side boat mechanics worsen performance across regions
  - **Lesson:** Move physics to client when authority isn't critical; reserve server for damage/economy
- [rouniverse-fishit] Forgotten Tier fish at 1-in-25-million catch rate
  - **Lesson:** Cap your rarest tier above 0.001% - 'effectively never' is not a goal, it's just frustration
- [rouniverse-fishit] Streamer Luck Scandal - 310%+ luck boosts via paid passes
  - **Lesson:** Cap purchasable luck multipliers below 2x or expect P2W backlash and refund storms
- [endsights-fisch] Reaching level 100 takes 15-25 hours focused
  - **Lesson:** First 30 minutes must show meaningful power spike (new rod, new zone) or casuals churn

### Roblox Doors-like horror design
- [devforum-not-to-put] Default Roblox walk sound is terrible in horror games
  - **Lesson:** Replace default walk/jump/land sounds before any other polish - they break atmosphere instantly
- [devforum-not-to-put] Repetitive jumpscares reduce tension
  - **Lesson:** Budget at most 1 jumpscare per 3-5 minutes - quiet builds the scare, density kills it
- [endsights.com] Generic horror sound effects across entities
  - **Lesson:** Each entity needs a unique audio signature players can learn - never reuse stings between threats
- [devforum-not-to-put] Walking-simulator pacing kills horror
  - **Lesson:** Mix every quiet exploration segment with a forced action/decision moment within 60 seconds
- [doors-fandom] The Rooms subfloor has dull gameplay even per devs
  - **Lesson:** Procgen alone isn't enough - each floor needs a unique mechanic hook beyond layout shuffle

### Roblox anime fighter combat design
- [tryhardguides] DMCA risk severe - shutdowns over IP
  - **Lesson:** Use original characters with anime-inspired aesthetics; never copy named heroes/abilities verbatim - one C&D ends the game
- [search-summary] Combat criticized as NPC farming simulator
  - **Lesson:** Ship a PvP-tested combo system day 1, not a stat grind disguised as combat
- [search-summary] Update cadence is poor
  - **Lesson:** Anime-fighter players churn fast - schedule biweekly content drops or commit to a sunset
- [devforum-design] Marketing harder when source anime isn't popular
  - **Lesson:** Pick inspiration from top-tier anime properties or invest in original lore branding upfront

### Roblox dress-up fashion game design
- [thezillennialzine] Voting system abused - 1-star to mock others
  - **Lesson:** Use blind voting with score normalization and outlier rejection, not raw 1-5 averages
- [thezillennialzine] Hateful stereotypes slip through moderation
  - **Lesson:** Pre-screen submitted outfits with text/asset moderation pipelines - don't rely solely on Roblox filter
- [WebSearch] Clothes disappearing when entering games
  - **Lesson:** Validate inventory load with retry on join; missing-cosmetics tickets dominate fashion-game support
- [WebSearch] Farming servers - 5-star coordinated cheating
  - **Lesson:** Cap stars-per-player-per-day or weight votes by reviewer reputation
- [bloxquiz.gg] Panic styling when time runs low destroys good looks
  - **Lesson:** Include a 'lock outfit' button with 30s remaining and a final 5s 'are you sure' confirm

### Roblox roleplay Brookhaven-like design
- [esportsdriven] Generic Roleplay Gaem fails due to broken controls
  - **Lesson:** Polish core movement/controls before any RP feature - players judge in 30 seconds
- [devforum-1550069] Cluttered worlds with weird structures
  - **Lesson:** Map navigation must be readable from spawn - if players can't find school/store in 60s, they leave
- [devforum-1683798] Restricting players to pre-built houses
  - **Lesson:** Give genuine customization - canned houses lose to free-form RP competitors every time
- [esportsdriven] Boho Salon plagued by bot invasions
  - **Lesson:** Add private/VIP-server flow early; public RP servers will be bot-spammed at scale
- [fandom-roleplay] FRP (godmodding, random attacks) by inexperienced players
  - **Lesson:** Bake RP rules into mechanics (cooldowns, consent prompts) - text rules are ignored by 9-year-olds

### Roblox idle clicker game design
- [devforum-clicker-review-1827003] Players abandon after ~6 min if stuck in first area
  - **Lesson:** First rebirth/zone unlock must arrive within 10 minutes for new players or they bounce
- [devforum-popular-3924361] Genre is in decline / oversaturated
  - **Lesson:** Don't ship a pure clicker - add a hybrid hook (racing, combat, theme) or skip the genre entirely
- [devforum-clicker-review-1827003] Auto-clicker gamepasses ineffective vs free tools
  - **Lesson:** Don't sell auto-clickers - bake them in and monetize cosmetics/prestige instead
- [exitlag-search-snippet] Number-overflow at large multipliers
  - **Lesson:** Use BigNum library from day 1 - retrofitting after numbers break is brutal
- [devforum-prevent-autoclick] Randomized auto-clickers evade pattern detection
  - **Lesson:** Detect behavior shape (no mouse-move + no camera-change + sustained click) - don't chase timing patterns

### Roblox battle royale game design
- [pcgamesn] Roblox forces devs to choose between cheaters or laggy
  - **Lesson:** Server-authoritative combat is non-negotiable for BR; budget for the performance hit upfront
- [game-ace] Pay-to-win monetization disrupts competitive balance
  - **Lesson:** Keep paid items strictly cosmetic - any stat advantage destroys ranked credibility instantly
- [devforum-kit] Roblox's official BR kit has bugs
  - **Lesson:** Don't trust template kits for shipping - rewrite core combat from scratch
- [devforum-structure] Predictable 3-move boss patterns get memorized
  - **Lesson:** Add 1-2 random moves to every pattern - memorization shouldn't be a win condition
- [pcgamesn] Anti-cheat causes shots failing to register
  - **Lesson:** Build hit-validation latency budget into design - if anti-cheat adds 100ms, gunfeel must compensate visually

### Roblox egg hatch simulator design
- [chi-2025-children-monetization] Pet Sim 99 0.05% drops called 'child gambling'
  - **Lesson:** Publish drop rates clearly and cap legendary rates above 0.5% to avoid moderation/reputation risk
- [devforum-the-hatch] Egg textures feel AI-generated and boring
  - **Lesson:** Hand-craft hero assets (eggs, top-tier pets) - players judge rarity by visual polish, not just stats
- [devforum-egg-positioning] Eggs positioned weird across screen sizes
  - **Lesson:** Anchor egg viewport frames to UIAspectRatio and test on 9:16 phone and 16:9 desktop both
- [devforum-the-hatch] Per-player ten-egg biome cap forces trading
  - **Lesson:** Don't gate progression behind RNG-events that require trading - traders ruin solo experience
- [devforum-egg-hatching-bug] Repeated hatching erroneously hatches extra eggs
  - **Lesson:** Disconnect old click connections before binding new ones - leaked event handlers are the #1 hatch bug

### Roblox hide and seek game design
- [Hide and Seek Extreme/thebloxclub] Heavily favors hiders, seekers frustrated
  - **Lesson:** Playtest both roles separately - asymmetric games need 45-55% win rate per side or one role gets abandoned
- [Hide and Seek Extreme] Glitch hiding spots break fairness
  - **Lesson:** Run automated geometry checks for clip-through points; community will find every one within a week
- [Hide N' Seek devforum] Games stuck not progressing past round 1
  - **Lesson:** Round state machine needs explicit timeouts and recovery; 'stuck round' = server reset for everyone
- [Hide N' Seek devforum] Settings buried in scripts
  - **Lesson:** Surface tunable game settings as Attributes on a config Folder, not hardcoded constants
- [mygamedesk] Motionless hiders trivially boring
  - **Lesson:** Build incentives to move (rotating safe-zones, hider-only objectives) so optimal play isn't AFK

### Roblox card game TCG design
- [devforum-creating-complex-card-game] Client-server sync is hardest part
  - **Lesson:** Use server as authority for all card state; client renders only - never trust client card draws or effects
- [devforum-balanced-scriptable-cards] Free-form scriptable cards make balance impossible
  - **Lesson:** Constrain card effects to a curated DSL or block-based editor; full Lua = exploit speedrun
- [gacha-monetization-research] Lack of transparency on pull probabilities
  - **Lesson:** Display drop rates on every pack purchase screen - not buried in patch notes
- [gacha-monetization-research] Pity systems weaponize sunk-cost
  - **Lesson:** If you ship a pity timer, cap weekly Robux spend or expect refund tickets and bad press
- [devforum-card-legacies-devlog] Card art quality issues hurt presentation
  - **Lesson:** Card art is the #1 visible quality signal - hire/commission art before scripting effects, not after
