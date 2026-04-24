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
