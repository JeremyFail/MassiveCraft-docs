![CreativeGates Logo](img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }

# Welcome to CreativeGates

CreativeGates is a simple, powerful portal plugin for Minecraft Spigot/Paper servers. Players build frames, activate them with simple tools or commands, and travel between linked gates - with optional fill styles, horizontal portals, and per-gate travel rules.

## What is CreativeGates?

CreativeGates lets players create teleportation portals between locations on your server. Gates that share a network name link automatically. Creators (and staff with override) can inspect and manage settings, choose how the portal looks, and control whether players, mobs, and vehicles may travel.

## Key Features

- **No Commands Required** - Tools can be used instead of traditional commands
- **Flexible Frames** - Any enclosed shape/size within the configured max area
- **Network System** - Same network name links gates together
- **Multiple Fills** - Nether Portal, End Gateway, Water, Lava, particles, and more (admin-configurable)
- **Horizontal Gates** - Floor/ceiling portals (optional; can preserve momentum)
- **Mob & Vehicle Travel** - Living mobs and non-living vehicles can use gates when allowed
- **Native Manage Dialog** - Dialog UI when available; chat/chest UI fallback on older servers
- **Admin Control** - Permissions, world restrictions, override mode, and rich configuration

## Quick Start

=== "For Players"
    1. Build a rectangular (or closed) frame with solid blocks
    2. Include the required frame blocks (default: 2 emerald blocks)
    3. Name a clock on an anvil, then click inside the frame
    4. Pick a gate fill if prompted (or accept the server default)
    5. Repeat at another location with the same network name
    6. Walk through to teleport!

=== "For Admins"
    1. Install [MassiveCore](../MassiveCore/) (required dependency)
    2. Install CreativeGates
    3. Review/configure permissions (defaults allow create/use for all players)
    4. Optionally customize fills, tools, and worlds in config (config command or direct file editing)

## Documentation Sections

Use the navigation menu to explore:

- **[Player Guide](player-guide.md)** - How to create, travel, inspect, and manage gates
- **[Admin Guide](admin-guide/index.md)** - Commands, permissions, and configuration

## Requirements

- **Server Software**: Spigot / Paper (`api-version` 1.21+)
- **Dependencies**: MassiveCore
- **Permissions**: Optional - create and use default to allowed for everyone unless you change them

## Credits

[![License: MIT](https://img.shields.io/badge/License-MIT-7c4dff.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

Continuation of [CreativeGates 3](https://github.com/magnusulf/CreativeGates) by Madus, which was a continuation of [MassiveCraft CreativeGates 2](https://github.com/MassiveCraft/CreativeGates) by Cayorion and Ulumulu1510.
