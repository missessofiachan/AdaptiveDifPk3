# 📈 Adaptive Difficulty Engine for GZDoom

**Adaptive Difficulty** is an advanced, mod-agnostic "Director AI" for GZDoom. Instead of relying on static difficulty menus, this engine dynamically scales the game's intensity in real-time based on your active performance. It monitors your movement, ammunition reserves, and health pool every single second to ensure the game is always perfectly challenging.

## ✨ Key Features

### 🧠 The Director AI (Real-Time Scaling)
* **Performance Tracking:** The engine ramps up the difficulty when your health and armor are high, and initiates a rapid cool-down decay if you are pushed to the brink of death.
* **Master Bypass Switch:** A global toggle allows you to turn the entire Director AI on or off instantly mid-game.
* **Mod-Agnostic Design:** Safely tracks custom armor classes and automatically iterates through unknown weapon packs (like *Brutal Doom* or *Voxel Doom*) to accurately read your inventory.

### 👹 Relentless AI Aggression
* **Dynamic Pain Resistance:** Monsters become increasingly resistant to stagger and stun-locks as the difficulty climbs.
* **Overclocked Projectiles:** Enemy fireballs and rockets physically accelerate in mid-air to match your current stress profile.
* **Hair-Trigger Reflexes:** Vanilla targeting delays are slashed, forcing monsters to attack the millisecond they gain a line of sight.
* **Bloodlust Swarms:** When a monster is killed, nearby allies in its pack briefly enter an enraged speed-frenzy.

### 🗺️ Smart Map Density & Generation
* **Safe-Space Cloning:** Dynamically duplicates enemies using native geometry checks so monsters never spawn stuck in walls or voids.
* **Kill Chain Surges:** Going on a killing spree multiplies your duplication rates by 1.5x.
* **Ammo Starvation Protection:** Automatically halts all enemy cloning if your overall global ammunition reserves drop below 15%.
* **Distance Culling:** Prevents cloning monsters that are too far away to save system performance.

### ♻️ Dynamic World Recycling
* **Adaptive Item Respawning:** Health, armor, and ammo automatically respawn. **The twist:** If you are playing well, the Director starves you by making items take much longer to reappear. If you are dying, the Director takes pity and rushes items back into the map quickly.
* **Anti-Camp Proximity Safety:** Items will wait for you to step away from their spawn pads before materializing, preventing them from clipping into you while camping.
* **Reactive Enemy Respawning:** Aggressive enemy respawn logic that rewards high-skill play but freezes when you are in the "critical zone." Enemies will not respawn directly on top of you thanks to minimum-distance safety checks.

## 🎛️ Extreme Configuration & Presets
Press `ESC` -> `Options` -> `Adaptive Difficulty Options` to access the full menu. Every setting features native GZDoom tooltips to explain exactly what it does. 

Choose from 10 distinct profiles that instantly snap your sliders to curated experiences:
* **0-5:** *The Classics* (From *I'm Too Young To Die* to *Absolute Pandemonium*)
* **6:** *Turbo Overdrive* (Extremely fast enemies, instant reflexes, lower enemy health pools)
* **7:** *Meat Grinder* (Massive enemy cloning rates and extreme health pools, slower movement)
* **8:** *Bullet Hell* (Absolute chaos with overclocked projectiles filling the screen)
* **9:** *Custom Sandbox* (Unlocks all sliders completely, allowing for up to 10,000% multiplication)

## 🤝 The Perfect Pairing: HP Regeneration
This mod was engineered to be paired with **[HP Regen UZ](https://github.com/missessofiachan/hp-regenUZpk3)**.

In vanilla Doom, health pickups are finite, which can lead to a "death spiral." By adding an HP Regen mod, you create a seamless **Push and Pull** gameplay loop:
1. **The Push:** You play well and dominate a room -> The Adaptive Engine spikes the difficulty to Nightmare levels.
2. **The Pull:** A massive wave whittles your health down -> The Adaptive Engine detects your vulnerability and softens the incoming threat.
3. **The Recovery:** Your HP Regen kicks in while you take cover -> The Adaptive Engine detects your health rising and immediately ramps the intensity back up.

Together, they keep the game in a constant state of "flow," providing a high-octane experience that feels like a modern arena shooter.

## 🛠️ Installation
1. Download the latest `.pk3`.
2. Load it with GZDoom alongside your preferred WADs and weapon packs.
3. Turn on the Director AI in the options menu and let the chaos adapt to you.

---
*Engineered to make Doom feel alive.*