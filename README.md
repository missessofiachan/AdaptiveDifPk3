# 📈 Adaptive Difficulty Engine for GZDoom

**Adaptive Difficulty** is a dynamic, intelligent "Director AI" for GZDoom that scales the game's intensity in real-time based on your active performance. 

Instead of picking a static difficulty level from the main menu, this engine reads your momentum, ammo reserves, and health pool. Play perfectly, and the engine will unleash absolute Nightmare-speed hordes. Make a mistake, and the AI will momentarily back off to let you recover. 

## ✨ Key Features

* 🧠 **Performance-Based Scaling:** Monster health, movement speed, and projectile aggression dynamically ramp up and cool down based on your active Health and Armor pool.
* 🧟‍♂️ **The 10x Horde Multiplier:** If you are dominating the map, the engine intercepts map generation and dynamically clones monsters (up to 10x density) to swarm you. 
* ⏱️ **Reactive Respawning:** Classic Nightmare respawns, but modernized. The better you play, the faster monsters revive. If your health drops into the critical zone, the respawn timers freeze to give you a breather.
* 🎯 **Behavioral Tracking (Kill Chains):** Racking up rapid kills builds an invisible momentum tracker. Maintain the chain, and the engine triggers an "Enemy Density Surge," drastically boosting spawn multipliers.
* 🪫 **Anti-Softlock Ammo Protection:** If your heavy munitions (Shells, Rockets, Cells) are completely drained, the AI recognizes you are "Ammo Starved" and temporarily halts map duplication so you aren't overwhelmed while holding a pistol.
* 🖥️ **Dynamic UI Overlay:** A clean, customizable on-screen HUD tracks your current "Stress Profile," rank, and total session eliminations.

---

## 🤝 The Perfect Pairing: Why You Should Use an HP Regen Mod

While this mod is highly customizable, the absolute best way to experience the **Adaptive Engine** is alongside an **HP Regeneration Mod**. 

### Why do they synergize so well?
The Adaptive Engine scales *directly* off your health pool. In vanilla Doom, taking a massive hit means the difficulty drops, but because map health pickups are finite, you might get stuck at a low difficulty tier for the rest of the level. 

By adding an **HP Regen Mod**, you create a high-octane "Push and Pull" gameplay loop:
1. You enter a room and dominate -> **Difficulty spikes to Nightmare levels.**
2. A Revenant lands a lucky rocket -> **Difficulty instantly drops to give you a lifeline.**
3. You take cover, and your HP passively regenerates -> **The engine recognizes you are recovering and begins ramping the hordes back up.**

HP Regen ensures the Adaptive Engine is constantly moving, keeping you in the "sweet spot" of maximum chaos without permanently punishing you for a single mistake.

---

## ⚙️ Configuration & Presets

You don't need to know how to code to tune the engine. Press `ESC` -> `Options` -> `Adaptive Difficulty Options` to access the full menu. 

Don't want to mess with sliders? Use the **Active Engine Preset** dropdown to instantly load profiles ranging from classic Vanilla baselines to **Absolute Pandemonium** (a locked 2.0x Nightmare state with 3x guaranteed map density).

## 🛠️ Installation

1. Download the latest version of the mod folder or `.pk3`.
2. Load it with GZDoom (or UZDoom) alongside your preferred WADs and gameplay mods.
3. *Highly Recommended:* Load this alongside your favorite HP Regen mod.

**Compatibility Note:** This mod is built using modern ZScript with a `StaticEventHandler` and `bISMONSTER` flag checks. This means it is **100% compatible out-of-the-box** with almost any visual, gore, or custom monster mod (like Brutal Doom, Voxel Doom, or Nash's Gore). 

---
*Engineered to make Doom feel alive.*