![CreativeGates Logo](../img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }

# Configuration

Configuring CreativeGates is **optional**. Defaults work for most servers.

The main file is:

```text
/mstore/creativegates_mconf/instance.json
```

Changes are detected and reloaded automatically after a few seconds - no restart or reload command required.

!!! warning "JSON only"
    Comments in the examples below are for explanation. **Do not** put `//` comments in the real file.

## Migration from older versions

On load, CreativeGates migrates legacy fields:

| Removed / legacy | Becomes |
|------------------|---------|
| `usingWater` | `allowedGateTypes` / `allowedHorizontalGateTypes` |
| `useLavaInNether` | `replaceWaterWithLavaInNether` |
| `materialMode` | `materialManage` |
| `materialSecret` | removed (Secret is a manage setting) |

`pigmanPortalSpawnAllowed` is obsolete: nether-portal **look** no longer places real portal blocks on the server.

## Gate fills

Fills are chosen from allow-lists. Block fills and particle fills are separate.

### Supported block fill ids

Common ids (also accept plain material names where applicable):

| Id | Notes |
|----|-------|
| `NETHER_PORTAL` | Portal look; vertical uses client overlay; horizontal uses rotated BlockDisplays |
| `END_GATEWAY` | Gateway look via BlockDisplay (client fallback on older MC) |
| `WATER` | Real water; drowning damage cancelled inside the gate |
| `LAVA` | Real lava; fire/lava damage cancelled inside the gate |
| Other materials | Other blocks (e.g. `POWDER_SNOW`, `ICE`, `SCULK`) |

Defaults also allow several decorative materials. Invalid ids are dropped on load.

### Particle fills

Particle ids use a `PARTICLE_` prefix (e.g. `PARTICLE_PORTAL`, `PARTICLE_FLAME`) so they never collide with materials like `LAVA`. Configure via:

- `allowedGateParticleTypes` (vertical)
- `allowedHorizontalGateParticleTypes` (horizontal)

Particle density uses `gateFillParticleAmountMin` / `Max` / `Default` (clamped to 1–128).

### Nether - Water to Lava

When `replaceWaterWithLavaInNether` is `true`, a **WATER** fill in the nether places lava instead. Explicit `LAVA` fill is separate and does not need to be in the allow-list for that replacement.

## Horizontal gates

| Option | Default | Purpose |
|--------|---------|---------|
| `horizontalGatesEnabled` | `true` | Allow floor/ceiling frames |
| `horizontalGatesPreserveVelocity` | `true` | Keep momentum when entering horizontal gates |

Horizontal nether-portal visuals use BlockDisplays; animation can freeze at some camera pitches (client limitation).

## Mobs and vehicles

| Option | Default | Purpose |
|--------|---------|---------|
| `gatesAllowMobs` | `true` | Global: living mobs may use gates (per-gate setting can still disable) |
| `gatesAllowVehicles` | `true` | Global: boats/minecarts/etc. (living mounts use mobs, not this) |
| `gatesAllowMobsScanTicks` | `10` | Spigot-only scan interval for wandering mobs; ignored on Paper |

## Example configuration

```javascript
{
    "version": 1,
    "enabled": true,

    "aliasesCg": ["cg", "creativegates", "creativegate"],

    "teleportationSoundActive": true,
    "teleportationSound": "ENTITY_GHAST_SHOOT",
    "teleportationSoundVolume": 1.0,
    "teleportationSoundPitch": 1.0,
    "teleportationMessageActive": true,

    // PermissionDefault: "TRUE", "FALSE", "OP", "NOT_OP"
    "permissionDefaultCreate": "TRUE",
    "permissionDefaultSetGateFill": "TRUE",
    "permissionDefaultSetFillParticleCount": "TRUE",
    "permissionDefaultUse": "TRUE",

    "verboseCreatePermission": true,
    "verboseSetGateFillPermission": false,
    "verboseSetFillParticleCountPermission": false,
    "verboseUsePermission": true,

    // Block fills (vertical / horizontal)
    "allowedGateTypes": [
        "NETHER_PORTAL",
        "END_GATEWAY",
        "WATER",
        "LAVA",
        "POWDER_SNOW",
        "ICE",
        "SCULK_VEIN",
        "SCULK"
    ],
    "allowedHorizontalGateTypes": [
        "NETHER_PORTAL",
        "END_GATEWAY",
        "WATER",
        "LAVA",
        "POWDER_SNOW",
        "ICE",
        "SCULK_VEIN",
        "SCULK"
    ],

    // Particle fills - ids are PARTICLE_<Bukkit Particle name>
    "allowedGateParticleTypes": ["PARTICLE_PORTAL", "PARTICLE_FLAME", "PARTICLE_ENCHANT"],
    "allowedHorizontalGateParticleTypes": ["PARTICLE_PORTAL", "PARTICLE_FLAME", "PARTICLE_ENCHANT"],

    "gateFillParticleAmountMin": 16,
    "gateFillParticleAmountMax": 32,
    "gateFillParticleAmountDefault": 16,

    // Blank = first selectable type for that orientation
    "defaultGateType": "",
    "defaultHorizontalGateType": "",

    "replaceWaterWithLavaInNether": true,
    "horizontalGatesEnabled": true,
    "horizontalGatesPreserveVelocity": true,

    "gatesAllowMobs": true,
    "gatesAllowVehicles": true,
    "gatesAllowMobsScanTicks": 10,

    "maxarea": 200,
    "blocksrequired": {
        "EMERALD_BLOCK": 2
    },

    "removingCreateToolName": true,
    "removingCreateToolItem": false,

    "materialCreate": "CLOCK",
    "materialInspect": "BLAZE_POWDER",
    "materialManage": "BLAZE_ROD",

    // Creation only - existing gates remain usable. Bypassed by
    // create.bypassdisabled, override mode, or cg.override.bypass.
    "gateCreationDisabledWorlds": []
}
```

## Portal conflicts with vanilla nether portals

Older docs recommended switching `usingWater` to avoid CreativeGates interfering with vanilla nether travel. Current **NETHER_PORTAL** fills are display/overlay based (not real portal blocks), so they should not create vanilla portal destinations or piglin spawns. Therefore, this is no longer a limitation.

If you still prefer fluid portals, allow `WATER` / `LAVA` and set them as defaults (or restrict `allowedGateTypes` accordingly).

## Troubleshooting

### Gates not working

- MassiveCore installed and up to date
- Permissions: `creativegates.create` / `creativegates.use` (and config permission defaults)
- Required frame blocks present (unless bypassed)
- World not in `gateCreationDisabledWorlds`
- At least one allowed fill type for that orientation

### Tools do nothing

- Player may have run `/cg tool` off - toggle it back on
- Need `creativegates.cg.inspect` / `creativegates.cg.manage` for item tools

### Cannot manage / inspect secret gates

- Only the creator, or staff with override / `cg.override.bypass`

### Configuration not applying

- Wait a few seconds for auto-reload
- Validate JSON (no comments, trailing commas, etc.)
- Check console for migrator / sanitize messages

### Getting help

1. Check the server console for errors
2. Confirm MassiveCore + CreativeGates versions match your release
3. Open an issue on [GitHub](https://github.com/JeremyFail/MassiveCraft) with versions, config snippets, and steps to reproduce
