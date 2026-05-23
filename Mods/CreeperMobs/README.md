# CreeperMobs

> Adds a blocky explosive creeper-style enemy to CastleMiner Z using CastleForge ModLoader.  
> Spawn them with a command, let them appear naturally at night, and tune chase, fuse, explosion, rendering, and multiplayer behavior from config.

**Current mod version shown in source:** `1.0.0.0`

![Preview](preview.gif)

---

## Contents

- [Overview](#overview)
- [Why this mod stands out](#why-this-mod-stands-out)
- [Features at a glance](#features-at-a-glance)
- [Requirements](#requirements)
- [Installation](#installation)
- [Quick start](#quick-start)
- [Command reference](#command-reference)
- [Configuration](#configuration)
- [Behavior notes](#behavior-notes)
- [Explosion notes](#explosion-notes)
- [Multiplayer notes](#multiplayer-notes)
- [Technical overview](#technical-overview)
- [Known limitations](#known-limitations)
- [Credits](#credits)

---

## Overview

**CreeperMobs** is a CastleForge gameplay mod that adds a blocky explosive creeper-style enemy to CastleMiner Z.

The goal is to create a hostile mob that feels immediately different from normal CastleMiner Z zombies while still using the game's existing enemy systems. Creepers chase the target, stop when close enough, begin a timed fuse, then detonate with configurable damage and terrain destruction.

At its core, the mod:

- registers a configurable `EnemyTypeEnum` slot as the creeper mob,
- defaults to `TREASURE_ZOMBIE` for full custom/modded-session testing,
- can optionally use an existing vanilla enemy slot such as `ZOMBIE_0_0` for vanilla-safe multiplayer testing,
- draws the mob as a custom blocky creeper-style model,
- replaces normal zombie chasing with creeper chase/fuse behavior,
- hides the custom model immediately when the explosion fires,
- lets you spawn creepers directly with `/spawncreeper`,
- supports large square-ish command spawn batches,
- includes configurable enemy stats, fuse timing, explosion behavior, rendering scale, and hot-reload settings,
- enables rare natural aboveground spawns by default,
- defaults natural spawning to night-only.

This makes it useful as both a gameplay enemy mod and a working example for custom hostile mob behavior in CastleForge.

---

## Why this mod stands out

CreeperMobs demonstrates several important CastleForge modding ideas:

- **Custom enemy slot registration**  
  The mod can use `TREASURE_ZOMBIE` as a full custom enemy slot, or switch to an existing vanilla slot such as `ZOMBIE_0_0` for safer online testing with vanilla clients.

- **Custom rendering without a skinned model pipeline**  
  The creeper is rendered with simple cuboid parts instead of requiring a full CMZ skinned XNB model with animation clips.

- **Unique behavior from normal zombies**  
  The mob does not use normal zombie melee behavior. It walks toward the target, stops nearby, primes its fuse, and explodes.

- **Night-only natural spawns by default**  
  Natural spawning is enabled by default, but it is restricted to aboveground night spawns unless changed in the config.

- **Configurable explosion behavior**  
  Block breaking and entity damage can be toggled independently, making the mob usable as either a destructive threat or a visual/effect-only test enemy.

- **Runtime tuning**  
  Health, movement, fuse timing, trigger distance, explosion type, scale, and other values can be edited in the INI file and reloaded while in game.

- **Large group spawning**  
  The command spawner lays mobs out in a square-ish grid so spawning many creepers does not create a single long line.

---

## Features at a glance

| Feature                    | What it does                                                               |
|----------------------------|----------------------------------------------------------------------------|
| `/spawncreeper` command    | Spawns one or more creeper mobs in front of the local player               |
| `/creeper` alias           | Short alias for `/spawncreeper`                                            |
| Square-ish batch spawning  | Large spawn counts are arranged into a compact grid                        |
| Custom blocky renderer     | Draws a creeper-style cuboid model instead of a vanilla zombie model       |
| Chase behavior             | Creepers move toward the target instead of randomly wandering              |
| Fuse behavior              | Creepers stop nearby, prime, and detonate after a configurable delay       |
| Instant visual hide        | The model is hidden immediately when the explosion triggers                |
| Optional fuse cancel       | Creepers can optionally cancel the fuse if the target gets far enough away |
| Optional terrain damage    | Block destruction can be enabled or disabled from config                   |
| Optional entity damage     | Blast damage/effects can be enabled or disabled from config                |
| Night-only natural spawns  | Natural aboveground spawns are restricted to night by default              |
| Config hot-reload          | Reloads settings with `/creepermob reload` or the configured hotkey        |
| Runtime info command       | Shows current enabled/spawn/fuse/rendering state with `/creepermob info`   |

---

## Requirements

CreeperMobs is built for the CastleForge ecosystem and requires:

- **CastleMiner Z**
- **CastleForge ModLoader**
- **ModLoaderExtensions**

The mod declares `ModLoaderExtensions` as a required dependency because it uses the shared CastleForge command infrastructure.

Recommended target environment:

| Item         | Recommended value                                                                |
|--------------|----------------------------------------------------------------------------------|
| Game version | `1.9.9.8`                                                                        |
| Framework    | CastleForge / ModLoader setup                                                    |
| Dependency   | `ModLoaderExtensions`                                                            |
| Multiplayer  | All clients should install the mod before joining a world that spawns this enemy |

---

## Installation

1. Install and verify **CastleForge ModLoader**.
2. Install **ModLoaderExtensions**.
3. Place the CreeperMobs DLL in your CastleMiner Z `!Mods` folder.
4. Launch the game once.
5. The mod will create its config folder and extract/use its resources.
6. Enter a world and test with `/spawncreeper`.

### Expected mod folder

After first launch, the mod uses:

```text
!Mods\CreeperMobs\
```

Expected files include:

```text
!Mods\CreeperMobs\CreeperMobs.ini
!Mods\CreeperMobs\Textures\creeper.png
```

> Depending on your packaging flow, the main `CreeperMobs.dll` may sit directly in `!Mods`, while the config and texture files live under `!Mods\CreeperMobs\`.

---

## Quick start

Once you are in a world, spawn one creeper:

```text
/spawncreeper
```

Spawn a small group:

```text
/spawncreeper 10
```

Spawn a large test group:

```text
/spawncreeper 200
```

Reload the config after editing the INI file:

```text
/creepermob reload
```

Check runtime settings:

```text
/creepermob info
```

---

## Command reference

| Command                  | Usage                | What it does                                                               |
|--------------------------|----------------------|----------------------------------------------------------------------------|
| `/spawncreeper`          | `/spawncreeper`      | Spawns one creeper mob in front of you                                     |
| `/spawncreeper <amount>` | `/spawncreeper 25`   | Spawns multiple creeper mobs in a square-ish grid                          |
| `/creeper`               | `/creeper 10`        | Alias for `/spawncreeper`                                                  |
| `/creepermob reload`     | `/creepermob reload` | Reloads the CreeperMobs config file                                        |
| `/creepermob info`       | `/creepermob info`   | Shows current enabled, natural spawn, night-only, fuse, and enemy-slot info |

### Spawn count behavior

The source currently allows large command batches and clamps command spawns internally. Large values are useful for stress testing, but they can hurt FPS and create heavy enemy load.

Recommended test values:

```text
/spawncreeper 1
/spawncreeper 10
/spawncreeper 50
/spawncreeper 200
```

Very large values should be treated as stress tests, not normal gameplay.

---

## Configuration

CreeperMobs creates this config on first launch:

```text
!Mods\CreeperMobs\CreeperMobs.ini
```

### Default config

```ini
; CreeperMobs - classic creeper-style mob config
; Uses a configurable EnemyTypeEnum slot.
; Default custom slot: TREASURE_ZOMBIE.
; Optional vanilla-safe slot: ZOMBIE_0_0.

[CreeperMobs]
; Master toggle for patches, command spawning, and natural spawning.
Enabled              = true
; If true, some aboveground spawns become creeper mobs.
NaturalSpawns        = true
; 0.03 = 3% chance when NaturalSpawns is enabled.
NaturalSpawnChance   = 0.03
; If true, natural creepers only replace aboveground night spawns.
SpawnAtNightOnly     = true
; Minimum percentMidnight required when SpawnAtNightOnly is true. 0.05 avoids edge-of-day spawns.
MinNightPercent      = 0.05
; Distance in front of the local player for /spawncreeper.
CommandSpawnDistance = 5

[EnemyType]
; Main custom enemy slot used for full modded-session testing.
; TREASURE_ZOMBIE is the default because it exists but is normally unused.
CustomEnemyType      = TREASURE_ZOMBIE

; Vanilla-safe mode uses an existing vanilla enemy enum such as ZOMBIE.
; This prevents vanilla clients from receiving an unknown/unregistered enemy slot.
; Warning: using ZOMBIE_0_0 can make modded clients/host treat normal zombies as creeper mobs.
VanillaSafeMode      = false
VanillaSafeEnemyType = ZOMBIE_0_0

[EnemyStats]
; Low test health to match early-game/simple mob behavior.
Health          = 2
SpawnRadius     = 20
DistanceLimit   = 45
SlowSpeed       = 1.75
RandomSlowSpeed = 0.35
FastSpeed       = 2.5
HasRunFast      = false

[Behavior]
; Creeper values. The mob chases the target, stops nearby, then detonates after FuseSeconds.
TriggerRadius      = 2.75
; Vertical tolerance for starting the fuse when the player is above/below the creeper.
TriggerHeight      = 4.0
; If true, the fuse cancels and returns to chase when the target escapes.
CancelFuseWhenFar  = false
CancelFuseDistance = 6.0
FuseSeconds        = 1.5
; Vertical velocity added when the mob bumps a wall.
WallJumpSpeed      = 7.0

[Explosion]
; If false, the explosion does not remove terrain blocks.
BreakBlocks    = true
; If false, the blast only shows effects and removes blocks when BreakBlocks is true.
DamageEntities = true
; Block breaking uses this vanilla ExplosiveTypes value: HEGrenade, TNT, C4, Rocket, Laser, Harvest.
ExplosionType  = HEGrenade

[Rendering]
; Classic model height is 24 texture/model units. 0.065 makes it about CMZ-player sized.
ModelScale       = 0.065
; Creeper leg animation speed.
AnimationSpeed   = 8
; If the model faces backward in-game, try 180.
YawOffsetDegrees = 0

[Hotkeys]
; Reload this config while in-game:
ReloadConfig = Ctrl+Shift+R
```

### Config reference

| Section       | Key                    | Default           | What it controls                                                               |
|---------------|------------------------|------------------:|--------------------------------------------------------------------------------|
| `CreeperMobs` | `Enabled`              | `true`            | Master toggle for the mod                                                      |
| `CreeperMobs` | `NaturalSpawns`        | `true`            | Allows rare natural aboveground creeper spawns                                 |
| `CreeperMobs` | `NaturalSpawnChance`   | `0.03`            | Chance to replace an aboveground enemy spawn when natural spawning is enabled  |
| `CreeperMobs` | `SpawnAtNightOnly`     | `true`            | Restricts natural creeper spawns to night                                      |
| `CreeperMobs` | `MinNightPercent`      | `0.05`            | Minimum midnight percentage required for night-only natural spawns             |
| `CreeperMobs` | `CommandSpawnDistance` | `5`               | Distance in front of the player used by `/spawncreeper`                        |
| `EnemyStats`  | `Health`               | `2`               | Enemy health value                                                             |
| `EnemyStats`  | `SpawnRadius`          | `20`              | Enemy spawn radius setting applied to the custom enemy type                    |
| `EnemyStats`  | `DistanceLimit`        | `45`              | Distance limit before the enemy gives up/despawns                              |
| `EnemyStats`  | `SlowSpeed`            | `1.75`            | Base movement speed                                                            |
| `EnemyStats`  | `RandomSlowSpeed`      | `0.35`            | Extra randomized movement speed range                                          |
| `EnemyStats`  | `FastSpeed`            | `2.5`             | Fast speed value retained on the enemy type                                    |
| `EnemyStats`  | `HasRunFast`           | `false`           | Whether the enemy type reports fast-run support                                |
| `Behavior`    | `TriggerRadius`        | `2.75`            | Horizontal distance required to begin the fuse                                 |
| `Behavior`    | `TriggerHeight`        | `4.0`             | Vertical tolerance required to begin the fuse                                  |
| `Behavior`    | `CancelFuseWhenFar`    | `false`           | Allows the fuse to cancel if the target escapes                                |
| `Behavior`    | `CancelFuseDistance`   | `6.0`             | Distance required to cancel the fuse when cancellation is enabled              |
| `Behavior`    | `FuseSeconds`          | `1.5`             | Seconds between fuse start and detonation                                      |
| `Behavior`    | `WallJumpSpeed`        | `7.0`             | Upward velocity added when the creeper bumps terrain                           |
| `Explosion`   | `BreakBlocks`          | `true`            | Allows the explosion to remove terrain blocks                                  |
| `Explosion`   | `DamageEntities`       | `true`            | Allows the blast to damage entities/show full explosive effects                |
| `Explosion`   | `ExplosionType`        | `HEGrenade`       | Vanilla explosive type used for block-removal behavior                         |
| `Rendering`   | `ModelScale`           | `0.065`           | Visual scale of the blocky model                                               |
| `Rendering`   | `AnimationSpeed`       | `8`               | Leg swing animation speed                                                      |
| `Rendering`   | `YawOffsetDegrees`     | `0`               | Extra yaw correction if the model faces the wrong way                          |
| `EnemyType`   | `CustomEnemyType`      | `TREASURE_ZOMBIE` | Enemy enum slot used for full custom/modded-session testing                    |
| `EnemyType`   | `VanillaSafeMode`      | `false`           | Uses `VanillaSafeEnemyType` instead of `CustomEnemyType` when enabled          |
| `EnemyType`   | `VanillaSafeEnemyType` | `ZOMBIE_0_0`      | Existing vanilla enemy enum used for safer online testing with vanilla clients |
| `Hotkeys`     | `ReloadConfig`         | `Ctrl+Shift+R`    | Hotkey used to reload the INI while in game                                    |

### Enemy type modes

CreeperMobs supports two enemy-type modes.

#### Full custom mode

```ini
[EnemyType]
CustomEnemyType      = TREASURE_ZOMBIE
VanillaSafeMode      = false
VanillaSafeEnemyType = ZOMBIE_0_0
```

Full custom mode keeps creeper mobs separate from normal zombies and is recommended when every client in the session has the mod installed.

#### Vanilla-safe mode

```ini
[EnemyType]
VanillaSafeMode      = true
VanillaSafeEnemyType = ZOMBIE_0_0
```

Vanilla-safe mode uses an existing enemy enum slot. This can help avoid unknown custom enemy slots in mixed testing, but it also means normal enemies using that slot may be treated as creepers by modded clients.

### Hot-reload workflow

After editing the INI, use either:

```text
/creepermob reload
```

or press the configured hotkey:

```text
Ctrl + Shift + R
```

Hot-reload is intended for config/runtime values only. If you rebuild or change C# code, restart the game after replacing the DLL.

---

## Behavior notes

CreeperMobs does **not** use normal CMZ zombie melee behavior for the custom enemy.

Instead, the custom enemy type replaces the chase/attack/restart flow with creeper-style states:

1. The mob picks a target through normal CMZ enemy handling.
2. It walks toward the target at a randomized speed.
3. If the target is close enough horizontally and vertically, the creeper enters its fuse state.
4. While priming, the creeper stops moving and faces the target.
5. If `CancelFuseWhenFar` is enabled and the target escapes beyond `CancelFuseDistance`, the creeper returns to chase.
6. When `FuseSeconds` expires, the creeper detonates.
7. The custom model is hidden immediately so it does not linger during vanilla cleanup.

### More vanilla-like fuse behavior

The default fuse duration is:

```ini
FuseSeconds = 1.5
```

For a chase that can be escaped, enable fuse cancellation:

```ini
[Behavior]
CancelFuseWhenFar  = true
CancelFuseDistance = 6.0
```

For a more punishing creeper, keep cancellation disabled:

```ini
[Behavior]
CancelFuseWhenFar = false
```

### Trigger tuning

To make creepers start the fuse closer to the player:

```ini
[Behavior]
TriggerRadius = 2.0
TriggerHeight = 3.0
```

To make creepers start the fuse from farther away:

```ini
[Behavior]
TriggerRadius = 3.5
TriggerHeight = 5.0
```

### Natural spawning

Natural spawning is enabled by default:

```ini
NaturalSpawns = true
```

Natural spawns are night-only by default:

```ini
SpawnAtNightOnly = true
```

To disable natural spawning completely:

```ini
[CreeperMobs]
NaturalSpawns = false
```

To allow natural replacements at any time the patched aboveground spawn selector runs:

```ini
[CreeperMobs]
SpawnAtNightOnly = false
```

A value of `0.03` means roughly a 3% replacement chance when the patched aboveground spawn selection runs.

---

## Explosion notes

CreeperMobs separates visual/damage effects from terrain destruction as much as the vanilla explosive helpers allow.

### Disable terrain damage

```ini
[Explosion]
BreakBlocks = false
```

This prevents the creeper from removing terrain blocks.

### Disable entity damage

```ini
[Explosion]
DamageEntities = false
```

This keeps the explosion from using the full vanilla blast damage path. Effects and terrain removal may still occur depending on `BreakBlocks` and the configured explosion behavior.

### Non-destructive visual test mode

For a safer testing setup:

```ini
[Explosion]
BreakBlocks    = false
DamageEntities = false
```

### Explosion type

The default block-removal type is:

```ini
ExplosionType = HEGrenade
```

Supported values depend on the game's `ExplosiveTypes` enum. The default config comments list the expected names:

```text
HEGrenade, TNT, C4, Rocket, Laser, Harvest
```

---

## Multiplayer notes

CreeperMobs is safest when **every player has the mod installed**.

By default, the mod uses `TREASURE_ZOMBIE` as its custom test enemy slot. This is useful for clean modded-session testing, but vanilla clients may not know how to register, render, or update that custom slot.

For safer online testing with vanilla clients, enable vanilla-safe mode:

```ini
[EnemyType]
VanillaSafeMode      = true
VanillaSafeEnemyType = ZOMBIE_0_0
```

Recommended multiplayer usage:

* For fully modded sessions, use `CustomEnemyType = TREASURE_ZOMBIE`.
* For vanilla-safe testing, use `VanillaSafeMode = true`.
* Keep `NaturalSpawns = false` until everyone has confirmed the mod loads correctly.
* Use `/spawncreeper` for controlled testing before enabling natural spawns.
* Avoid very large spawn batches on public or lower-end sessions.
* Disable `BreakBlocks` for safer public testing if you do not want terrain damage.

---

## Technical overview

CreeperMobs works by patching a few focused points in the CMZ enemy/rendering flow.

### Enemy slot

The mod registers a configurable enemy enum slot as the creeper mob slot.

Default custom mode:

```text
EnemyTypeEnum.TREASURE_ZOMBIE
```

Optional vanilla-safe mode:

```text
EnemyTypeEnum.ZOMBIE_0_0
```

`TREASURE_ZOMBIE` is useful for clean custom enemy testing because it keeps creepers separate from normal zombies. `ZOMBIE_0_0` is useful for safer online testing because vanilla clients already understand that enemy type.

### Enemy type

The custom enemy type derives from CMZ's zombie enemy type so it can keep the normal enemy lifecycle:

- health,
- damage,
- hit detection,
- collision,
- death,
- despawn,
- enemy manager registration,
- spawn messaging.

The main behavior difference is that the chase/attack/restart state returns custom creeper states instead of the normal zombie behavior.

### Chase state

The chase state moves toward the current target, faces the target, and checks whether the target is within the configured trigger range.

Important config values:

```ini
TriggerRadius = 2.75
TriggerHeight = 4.0
WallJumpSpeed = 7.0
```

### Fuse state

The fuse state stops the creeper, keeps it facing the target, and counts up to `FuseSeconds`.

The custom renderer remains responsible for visuals, so the fuse state avoids forcing a missing vanilla animation clip. This prevents animation dictionary errors while the creeper is priming.

### Explosion helper

The explosion helper handles the detonation moment. It can:

- hide the custom model immediately,
- disable hittable/blocking state,
- trigger vanilla explosive effects/damage,
- trigger vanilla terrain removal,
- send the normal enemy kill path when possible.

### Rendering

The mod patches the skinned model draw path and checks whether the current enemy is the custom creeper mob.

If it is not the custom mob, vanilla rendering continues normally.

If it is the custom mob, the mod skips the vanilla zombie model and draws a cuboid creeper model instead.

If the creeper has detonated, the renderer skips both the custom model and the vanilla model so it disappears immediately.

### Spawning

Command spawning uses CMZ's normal `EnemyManager.SpawnEnemy(...)` path. This keeps enemy IDs and world ownership consistent with the rest of the game.

For multiple command spawns, the mod computes a square-ish grid using the total requested amount. For example:

```text
20 mobs  -> about 5 x 4
100 mobs -> about 10 x 10
200 mobs -> about 15 x 14
```

---

## Known limitations

- This is still an experimental custom enemy mod.
- Natural spawning is enabled by default but should be used carefully in multiplayer sessions.
- Very large spawn counts can reduce performance.
- Multiplayer sessions should require all clients to install the mod.
- The custom renderer is intentionally simple and does not use CMZ's skinned model animation system.
- If the model faces backward, set `YawOffsetDegrees = 180` in the config.
- `VanillaSafeMode = true` helps avoid unknown enemy-slot crashes, but using `ZOMBIE_0_0` may cause modded clients/hosts to treat normal zombies as creeper mobs.
- Full custom mode should only be used when all players have the mod installed.
- Vanilla-safe mode is a compatibility fallback, not a perfect per-enemy handshake system.
- Explosion behavior depends on CMZ's existing explosive helpers and may vary by host/client ownership flow.
- If terrain safety matters, set `BreakBlocks = false` before public testing.

---

## Credits

- **RussDev7** - CastleForge / CreeperMobs implementation
- **CastleForge ModLoader** - mod loading and runtime framework
- **ModLoaderExtensions** - shared command infrastructure
