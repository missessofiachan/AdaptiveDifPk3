# 📈 Adaptive Difficulty Engine for GZDoom

**Adaptive Difficulty** is a dynamic "Director AI" for GZDoom that scales the game's intensity in real-time based on your active performance. Instead of static difficulty settings, this engine reads your movement, ammo reserves, and health pool to ensure the game is always perfectly challenging.

## ✨ Key Features

* 🧠 **Performance Scaling:** Monster health, speed, and aggression ramp up/down based on your current Health and Armor.
* 🧟‍♂️ **10x Horde Multiplier:** Dynamic monster cloning for high-aggression play.
* ⏱️ **Reactive Respawning:** Aggressive respawn logic that rewards high-skill play but freezes when you are in the "critical zone."
* 🎯 **Behavioral Tracking:** Tracks "Kill Chains" to surge enemy density and "Ammo Starvation" to protect you when you're low on supplies.
* 🖥️ **Dynamic HUD:** Real-time stress profiling and campaign statistics overlay.

---

![GZDoom Compatible](https://img.shields.io/badge/GZDoom-v4.10%2B-blue)

## 🤝 The Perfect Pairing: HP Regeneration
This mod is designed to pair perfectly with **[HP Regen UZ](https://github.com/missessofiachan/hp-regenUZpk3)**.

### Why use them together?
In vanilla Doom, health pickups are finite, which can lead to a "death spiral" if you take too much damage. By adding an HP Regen mod, you create a seamless "Push and Pull" gameplay loop:

1. **The Push:** You play well and dominate a room -> The **Adaptive Engine** spikes the difficulty to Nightmare levels.
2. **The Pull:** A massive wave eventually whittles your health down -> The **Adaptive Engine** detects your vulnerability and softens the incoming threat.
3. **The Recovery:** Your **HP Regen** kicks in while you take cover -> The **Adaptive Engine** detects your health pool rising and immediately begins ramping the intensity back up to challenge you again.

Together, they keep the game in a constant state of "flow," providing a high-octane experience that feels like a modern arena shooter.

---

## 🛠️ Installation

1. Download the latest version of the mod folder or `.pk3`.
2. Load it with GZDoom alongside your preferred WADs.
3. **Highly Recommended:** Load this alongside [HP Regen UZ](https://github.com/missessofiachan/hp-regenUZpk3) for the optimal experience.

## ⚙️ Configuration & Presets
Press `ESC` -> `Options` -> `Adaptive Difficulty Options` to access the full menu. You can tune every slider from spawn density to aggression curves or select from built-in presets ranging from *I'm Too Young To Die* to *Absolute Pandemonium*.

---
*Engineered to make Doom feel alive.*
