![CreativeGates Logo](../img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }

# Admin Guide Overview

Welcome to the CreativeGates administration guide. Use the links below for setup, day-to-day management, and configuration.

## Quick Navigation

- **[Commands](commands.md)** - Command reference
- **[Permissions](permissions.md)** - Permission nodes and kits
- **[Configuration](configuration.md)** - `mstore` settings, fills, tools, and migration notes

## Quick Start

1. Install **MassiveCore**, then CreativeGates
2. Confirm players can create/use (defaults are permissive unless you change them)
3. Optionally restrict worlds, allowed fills, or who may manage/inspect
4. Existing configs from older CreativeGates versions migrate automatically on load

## What Changed in Recent Releases

CreativeGates 3.4.x added fill picking, horizontal gates, mob/vehicle travel, inspect/manage UIs, and richer admin tooling. Notable replacements:

| Old | New |
|-----|-----|
| `usingWater` | `allowedGateTypes` / `allowedHorizontalGateTypes` (and particle allow-lists) |
| `materialMode` (blaze rod enter/exit toggle) | `materialManage` - opens full manage UI |
| `materialSecret` (magma cream) | **Secret** toggle inside manage |
| Real nether-portal fill blocks | Display / client-overlay fills (avoids vanilla portal side effects) |

See [Configuration](configuration.md) for the full option list.
