# GuaranteedCosmeticCrate

GuaranteedCosmeticCrate is a BepInEx mod for **REPO** that improves the vanilla cosmetic crate spawn system while keeping full compatibility with the game's original logic.

Instead of replacing REPO's spawning system, this mod extends it.

---

# Features

### Vanilla Compatible
The mod uses REPO's internal:

- `SetupHost()`
- `SpawnCosmeticWorldObject()`
- cosmetic spawn curves
- bad luck system

No manual Photon spawning.

---

# Guaranteed Cosmetic Crate

If vanilla fails to spawn a cosmetic crate:

- the mod detects it
- logs the result
- safely forces **1 cosmetic crate**

If vanilla already spawned one:

- nothing is modified
- no duplicate spawn

---

# Better Rarity Chances

Optional rarity multipliers allow better crates to appear more often.

Configurable:

- Rare chance multiplier
- UltraRare chance multiplier
- Global cosmetic spawn multiplier

---

# Multiplayer Safe

Uses REPO's own spawning system.

Compatible with:

- Host
- Multiplayer
- Photon sync
- Vanilla networking

---

# Console Logging

Detailed console logs included.

Examples:
[GuaranteedCrate] Vanilla already spawned crate(s): 1


[GuaranteedCrate] No vanilla cosmetic crate detected.
[GuaranteedCrate] Forcing cosmetic crate spawn...
[GuaranteedCrate] Selected rarity: UltraRare
[GuaranteedCrate] Cosmetic crate spawned successfully


Useful for:

* debugging
* testing spawn rates
* verifying compatibility

---

# Installation

## Requirements

* BepInEx 5
* REPO

---

## Install

1. Install BepInEx
2. Place:

```text
GuaranteedCosmeticCrate.dll
```

inside:

```text
REPO/BepInEx/plugins/
```

3. Launch the game once.

Config file will be generated automatically.

---

# Configuration

Config location:

```text
REPO/BepInEx/config/nzoow.repo.guaranteedcosmeticcrate.cfg
```

Example:

```ini
[General]
GuaranteedCrate = true
SpawnChanceMultiplier = 1.5

[Rarity]
RareMultiplier = 1.5
UltraRareMultiplier = 2.0

[Debug]
VerboseLogs = true
```

---

## Config Options

### GuaranteedCrate

Guarantees at least one cosmetic crate.

Default:

```ini
true
```

---

### SpawnChanceMultiplier

Boosts vanilla cosmetic spawn chance.

Default:

```ini
1.5
```

---

### RareMultiplier

Boosts Rare crate weight.

Default:

```ini
1.5
```

---

### UltraRareMultiplier

Boosts UltraRare crate weight.

Default:

```ini
2.0
```

---

### VerboseLogs

Enables detailed console logs.

Default:

```ini
true
```

---

# Technical Details

The mod:

* patches `ValuableDirector.SetupHost()`
* checks `cosmeticWorldObjectTargetAmount`
* rolls rarity using vanilla `chanceCurve`
* calls `SpawnCosmeticWorldObject()` through reflection
* preserves `cosmeticWorldObjectBadLuckCount`

No hardcoded crate prefabs.

No unsafe Photon spawning.

---

# Compatibility

Designed for:

* REPO
* BepInEx 5
* Multiplayer

Should work with most gameplay mods.

---

# Credits

Created by **nzoow**

Powered by:

* BepInEx
* Harmony
* Photon
* REPO reverse engineering

