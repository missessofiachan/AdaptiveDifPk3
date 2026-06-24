# 📖 Adaptive Difficulty Engine: The Core Design Bible

This document outlines the "Hows and Whys" of the Adaptive Difficulty Engine. It is intended for modders, power-users, and game designers who want to understand the mathematical principles and design philosophies driving the Director AI.

## I. Core Philosophy: The Flow State
Traditional difficulty settings are static. If you select "Ultra-Violence," the game expects you to play at an Ultra-Violence level 100% of the time. This inevitably leads to spikes of frustration (when you run out of resources) or valleys of boredom (when you are fully maxed out). 

The Adaptive Difficulty Engine aims to achieve the **Flow State**—the psychological sweet spot between anxiety and boredom. By constantly adjusting the game's mechanics to your current resources, the engine ensures you are always challenged but rarely unfairly punished. 

## II. The Director AI (How Scoring Works)
At the heart of the mod is the `currentDifficulty` variable. This is a floating-point multiplier (e.g., `1.0` = Base Game, `2.0` = Nightmare+). 

### The 35-Tic Cycle
The Director does not calculate every single frame, as that would ruin game performance. Instead, it runs on a 35-tic cycle (exactly once per second). Every second, it asks three questions:
1. **Are you heavily armored?** (Total Health + Armor > 160). If yes, the difficulty climbs rapidly (`ramp_up_speed * 1.5`).
2. **Are you surviving?** (Health >= 80). If yes, the difficulty climbs steadily (`ramp_up_speed`).
3. **Are you dying?** (Health < 35). If yes, the difficulty actively lowers itself to give you breathing room (`cool_down_speed`).

### The Ammo Starvation Hook
We weapons-agnostically iterate through the player's inventory to find anything inheriting from the `Ammo` class. If the player holds less than 15% of their total maximum capacity across all weapons combined, the engine triggers an **Ammo Starved** state. This acts as a hard override, halting all enemy cloning immediately so the player isn't overwhelmed while holding an empty gun.

## III. Event-Driven Chaos (Why it works the way it does)
A massive hurdle in dynamic difficulty is applying the changes without breaking the game. If a monster's max health suddenly doubles *while* you are shooting it, GZDoom's damage logic will break, and the monster's state machine might desync. 

**The Solution: Snapshot Execution**
While the *score* updates every second, the *effects* only apply via Event Handlers:
* **`WorldThingSpawned`:** The moment a monster spawns, it takes a "snapshot" of the current difficulty score. It permanently locks in its Health, Speed, Pain Resistance, and Reaction Time based on that exact millisecond. 
* **`WorldThingDied`:** The moment a monster dies, its respawn timer is calculated based on the difficulty score *at the time of its death*. 
* **Projectile Interception:** Enemy fireballs natively spawn as neutral objects. We intercept them the moment they leave the monster's hand, check the live difficulty, and overclock their `Speed` and `Vel` directly. 

## IV. The AI Aggression Matrix
Making enemies "harder" by just giving them more HP makes them bullet sponges. The Adaptive Engine aims to make them *smarter* and *more terrifying*.

1. **Dynamic Pain Resistance:** High-tier players often stun-lock enemies with rapid-fire weapons like the Plasma Rifle. As difficulty climbs past 1.0, the engine linearly slashes the `PainChance` of monsters. At max difficulty, they become unstaggerable terminators.
2. **Hair-Trigger Reflexes:** Vanilla Doom monsters have a `ReactionTime` delay before they start attacking upon seeing the player. The engine divides this delay by the difficulty multiplier, forcing enemies to fire the absolute millisecond they gain line of sight.
3. **Bloodlust Swarms:** Using `BlockThingsIterator`, when a monster dies, the engine searches a 512-unit radius for allies. It injects the `bALWAYSFAST` flag into them and multiplies their speed by 1.5x. This creates a "pack rage" effect where killing the front-line enemies enrages the back-line.

## V. Non-Destructive Mod Compatibility
The hardest part of Doom modding is ensuring your mod doesn't break someone else's. 

### The Item Recycling Engine
Instead of replacing vanilla Medkits, Armor, and Ammo with custom "Respawning" variants (which would completely break mods like *Voxel Doom* or *NashGore*), the Adaptive Engine uses an invisible **Map Item Registry**. 

When the level loads, it logs the X/Y/Z coordinates and Class Name of every item. When an item is destroyed (picked up), it tells the registry to start a timer. When the timer hits zero, the engine forces the map to simply `Actor.Spawn` a brand-new instance of that original class at the original coordinates. 

**The Adaptive Math:** The respawn timer is multiplied by your real-time difficulty. 
* Base Delay: 30 Seconds.
* Difficulty `2.0`: Items take 60 seconds to respawn (Starving you).
* Difficulty `0.5`: Items take 15 seconds to respawn (Saving you).

### The Anti-Camp Rule
To prevent a newly spawned item from instantly being picked up by a player camping on the spawn pad (which ruins the tension), the engine runs a proximity check. If the player is within 128 units of the item's spawn point, the timer pauses at 0 until the player steps away, forcing them to move to collect their reward.

## VI. Summary
The Adaptive Difficulty Engine is not just a randomizer; it is a mathematical arbiter. It uses non-destructive hooks, agnostic inventory tracking, and snapshot execution to seamlessly manipulate the battlefield without ever touching the core game files. It ensures that no matter what WAD or weapon mod you load, the game will push back exactly as hard as you push it.