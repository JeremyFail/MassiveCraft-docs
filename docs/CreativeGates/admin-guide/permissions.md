![CreativeGates Logo](../img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }

# Permissions

Assign nodes with your permissions plugin (e.g. LuckPerms). Several important nodes also have **config defaults** (`permissionDefaultCreate`, `permissionDefaultUse`, etc.) that CreativeGates applies at runtime - see [Configuration](configuration.md).

## Player permissions

| Node | Description |
|------|-------------|
| `creativegates.create` | Create a gate |
| `creativegates.use` | Travel through a gate |
| `creativegates.setgatefill` | Choose fill type when creating or managing |
| `creativegates.setfillparticlecount` | Choose particle density for particle fills |

## Bypass / staff helpers

| Node | Description |
|------|-------------|
| `creativegates.create.bypassdisabled` | Always create in worlds listed in `gateCreationDisabledWorlds` |
| `creativegates.create.bypassframe` | Always skip `blocksrequired` frame materials |
| `creativegates.cg.override` | Use `/cg override` |
| `creativegates.cg.override.bypass` | Always manage any gate / apply override bypasses without toggling override mode |

Override mode (`/cg override`) also grants the world-creation and frame bypasses while enabled.

## Command permissions

| Node | Description |
|------|-------------|
| `creativegates.cg` | Base `/cg` command |
| `creativegates.cg.inspect` | `/cg inspect` and blaze-powder inspect tool |
| `creativegates.cg.manage` | `/cg manage` and blaze-rod manage tool |
| `creativegates.cg.tool` | `/cg tool` |
| `creativegates.cg.world` | World management parent |
| `creativegates.cg.world.list` | `/cg world list` |
| `creativegates.cg.world.delete` | `/cg world delete` |
| `creativegates.cg.version` | `/cg version` |
| `creativegates.cg.config` | `/cg config` |

## Bundles

| Node | Includes (summary) |
|------|--------------------|
| `creativegates.*` | create, setgatefill, setfillparticlecount, use, cg, version, inspect, manage, tool |
| `creativegates.admin.*` | `creativegates.*` plus override, config, and world list/delete (admin-related functions) |

!!! tip "Inspect / manage for players"
    Give `creativegates.cg.inspect` and `creativegates.cg.manage` (or `creativegates.*`) to players who should use blaze powder / blaze rod. Those command nodes are **not** implied by create/use alone.
