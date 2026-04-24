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


## Roblox battlegrounds game design
- **Complaint:** Nearly all battlegrounds games feature identical scripts.
  **-> Gem:** Ship ONE truly novel mechanic (parry window, destructible stage) or do not release - the genre is 90% clones; differentiation IS survival.
- **Complaint:** The Strongest Battlegrounds has no real objective.
  **-> Gem:** Add at least one round-win state (KO count, last-standing timer) - infinite-brawl alone cannot retain players.
- **Complaint:** Seas Battlegrounds collapsed after a single terrible update.
  **-> Gem:** Never ship a game-altering update without a beta server; LiveOps mistakes kill battlegrounds games in a week, not a month.
- **Complaint:** Jujutsu Shenanigans has no built-in tutorial.
  **-> Gem:** Ship a 60-second in-match tutorial (parry, dodge, dash-cancel) on first join - genre fluency is the #1 retention blocker.
- **Complaint:** Solo devs underestimate difficulty.
  **-> Gem:** Budget 12+ months solo; if deadline is shorter, scope to 1 arena + 3 movesets, not 10.

## Roblox Rojo workflow
- **Complaint:** Live syncing often fails.
  **-> Gem:** 90% of sync failures are duplicate-plugin or stale port - check rojo serve port and plugin version on every fresh setup.
- **Complaint:** Non-script assets need separate handling.
  **-> Gem:** Treat Rojo as scripts-only; keep models/terrain/UI in a checked-in .rbxlx opened alongside in Studio.
- **Complaint:** Chaotic workflow when adding Instances.
  **-> Gem:** Scaffold folders/instances up front via project.json; do not fight Rojo by creating Instances in Studio mid-session.
- **Complaint:** Two-way sync experimental in Rojo 7+.
  **-> Gem:** Never rely on two-way - filesystem is source of truth, Studio is view-only for scripts.

## Roblox MessagingService cross-server
- **Complaint:** MessagingService is explicitly best-effort - can drop messages.
  **-> Gem:** Never use MessagingService as the ONLY channel for state - pair with periodic DataStore/MemoryStore reconciliation.
- **Complaint:** SubscribeAsync can yield indefinitely during Roblox outages.
  **-> Gem:** Wrap SubscribeAsync in task.spawn with a timeout; do not let a Roblox-side stall block your server boot sequence.
- **Complaint:** Publishes silently throttled when quota exceeded.
  **-> Gem:** Track publish count per minute yourself; warn in logs at 80% of the 600+240*players limit before throttle hits.
- **Complaint:** 1 KB message size is restrictive.
  **-> Gem:** Compress payloads with single-char keys - triples your effective bandwidth.

## Roblox Open Cloud API
- **Complaint:** Persistent 429 errors even when limits not exceeded.
  **-> Gem:** Build exponential backoff with jitter into every Open Cloud call - never assume published rate limits are the actual ceiling.
- **Complaint:** Rate limits shared across ALL API keys per owner.
  **-> Gem:** Multiple API keys will not multiply quota - use one key and design around the single bucket.
- **Complaint:** Legacy docs retiring March 31, 2026.
  **-> Gem:** Migrate to new unified OpenAPI-based endpoints this quarter; scripts calling legacy endpoints will silently break.
- **Complaint:** Messages published via Open Cloud do not arrive in Studio test.
  **-> Gem:** Test Messaging integration on a live published place; Studio cannot receive cross-server Open Cloud messages.

## Roblox rebirth prestige system
- **Complaint:** steepness^rebirth becomes unusable at millions of rebirths.
  **-> Gem:** Cap rebirth cost curve at a hard ceiling (e.g., 1e15); design for the player who rebirths 10,000 times.
- **Complaint:** Rebirth trades 100 for 1 feels unbalanced.
  **-> Gem:** First rebirth should pay for itself in half the original time - ramp difficulty only AFTER that first validation.
- **Complaint:** Over-farming tiers wastes time players do not realize.
  **-> Gem:** Show rebirth-now-to-save-X-minutes prompt when rebirthing would accelerate progress - teach the meta directly.
- **Complaint:** Players get wrong rebirth counts from poorly-guarded conditions.
  **-> Gem:** Validate rebirth with a single server-side atomic RemoteFunction: check threshold, decrement currency, increment count in one call.
- **Complaint:** Multiplier compounding bug applied multiple times per tick.
  **-> Gem:** Compute base income once per session and multiply at read time, never at accrual time.

## Roblox live events and concerts design
- **Complaint:** Grow-a-Garden scale events caused website-wide Roblox problems.
  **-> Gem:** If expecting 500K+ CCU, coordinate with Roblox partner support WEEKS ahead; surprise virality crashes more than your game.
- **Complaint:** Event Sequencer uses event-based polling instead of signals.
  **-> Gem:** Benchmark replicator perf at 70+ players BEFORE dress rehearsal - polling bottlenecks compound at scale.
- **Complaint:** Editing after submission affects eligibility.
  **-> Gem:** Lock all content 72h before event submission deadline; last-minute tweaks drop you from Roblox marketing feed.
- **Complaint:** Animation-audio sync is a persistent challenge.
  **-> Gem:** Rehearse concert audio-animation sync on LIVE servers (not Studio); ping-induced drift only shows at real latency.

## Roblox anime fighting game design
- **Complaint:** DMCA strikes wiped Anime Adventures, Anime Fighting Simulator X.
  **-> Gem:** Never use unlicensed IP names/assets - design anime-inspired originals; DMCA strikes wipe 100% of progress in a week.
- **Complaint:** High ping dependency undermines competitive play.
  **-> Gem:** Use lag compensation (client-side hit prediction with server reconciliation) for M1 combos - server-authoritative-only feels terrible at 150ms+.
- **Complaint:** Mobile controls disadvantage vs PC.
  **-> Gem:** Split mobile and PC matchmaking pools, or give mobile 10% auto-aim assistance - mixed queues toxify fast.
- **Complaint:** Button-mashing M1 spam is a common complaint.
  **-> Gem:** Build parry + perfect-block windows into core loop from day 1 - M1-spam games die in weeks, timing-based games retain.
- **Complaint:** Without fresh events games get stale quickly.
  **-> Gem:** Schedule monthly content drops (new moveset OR new arena) on a public calendar BEFORE launch.

## Roblox Knit framework
- **Complaint:** Knit has stopped receiving updates.
  **-> Gem:** Start new projects on Matter or plain ModuleScripts with RbxUtil Comm - Knit is in maintenance mode and the community has moved on.
- **Complaint:** Intellisense limitations: services load into generic tables without typing.
  **-> Gem:** If you must use Knit, write type-annotated wrapper modules for every GetService() call.
- **Complaint:** Single-script structure does not support Parallel Luau.
  **-> Gem:** For high-performance systems (physics sims, procgen), use Actor-based Parallel Luau outside Knit.
- **Complaint:** Services become unmanaged global state singletons.
  **-> Gem:** Treat each Knit service as a module with explicit dependencies - do not let services reach across into each other state.

## Roblox Wally package manager
- **Complaint:** Caret semver confusion: ^1.4.3 installs 1.7.0.
  **-> Gem:** Pin production deps with =1.4.3 exact operator, not ^1.4.3; reserve caret for intentionally-flexible dev deps.
- **Complaint:** wally init fails with os error 3 on Windows/PowerShell.
  **-> Gem:** Run wally init in a project directory that already exists - do not let Wally create the dir; fixes 90% of Windows init errors.
- **Complaint:** Packages installed outside DataModel, path not configurable.
  **-> Gem:** Map Packages/ServerPackages/DevPackages folders explicitly in default.project.json to the intended DataModel locations.
- **Complaint:** Not all packages available on Wally.
  **-> Gem:** For packages missing from Wally, fork + publish under your own scope to your private registry; do not embed source copies.

## Roblox gacha lootbox system design
- **Complaint:** Roblox ToS requires disclosing drop rates when Robux buys random items.
  **-> Gem:** Publish your drop-rate table in-game BEFORE any Robux gacha ships - not disclosing is both a legal and ToS violation.
- **Complaint:** Countries increasingly ban lootboxes - regional compliance risk.
  **-> Gem:** Detect GetPolicyInfoForPlayerAsync().ArePaidRandomItemsRestricted and auto-hide gacha UI for restricted regions.
- **Complaint:** Roblox random-item mechanics described as gambling for children.
  **-> Gem:** For under-13 games, never gate progression behind Robux-only pulls; always provide a free-currency path to every item.
- **Complaint:** Floating-point precision causes missed outcomes.
  **-> Gem:** Use integer weights (e.g., 100/1000 parts) with math.random(1, totalWeight) instead of decimals.
- **Complaint:** Converting duplicates to dust reduces engagement.
  **-> Gem:** Build a shards-of-featured-unit exchange so every unwanted dupe counts toward the featured unit over time.
