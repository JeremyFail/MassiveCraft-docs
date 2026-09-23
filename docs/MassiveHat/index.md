![MassiveHat Logo](img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }

# Welcome to MassiveHat

MassiveHat is a block-hat plugin for Minecraft Spigot/Paper servers. It lets players wear blocks (and optionally other items like banners) on their heads as hats, and you equip the block like a regular helmet.

## What is MassiveHat?

MassiveHat allows players to turn the block (or configured item) they are holding into a hat. The block is placed on the player’s head as if it were a helmet. What makes it different from some other hat plugins is that you **equip the block like a normal helmet**: hold the block and use the hat command (e.g. `/hat`), and that block is worn on your head.

## Key Features

- **Block as helmet** - Hold any allowed block (or item), run the hat command, and it is worn on your head.
- **Configurable** - Admins can restrict which blocks or items are allowed as hats (e.g. only certain blocks, or allow banners).
- **Simple commands** - Shortcuts like `/hat`, `/mhat`, or `/blockhat` (configurable) to wear the item in hand.
- **Lightweight** - Minimal overhead; no complex systems beyond wearing the block.
- **MassiveCore integration** - Uses MassiveCore for config and permissions; config changes are auto-loaded.

## Quick Start

=== "For players"
    1. Hold a block (or allowed item) in your hand.
    2. Use the hat command (e.g. `/hat`, `/mhat`, or `/blockhat` - check with your server administrator).
    3. The block is now on your head. You can also equip it like a normal helmet by placing it in the helmet slot if the server allows it.

=== "For admins"
    1. Install [MassiveCore](https://factions.wiki/MassiveCore/) (required).
    2. Install the MassiveHat plugin.
    3. Grant the **`massivehat.use`** permission so players can wear hats.
    4. (Optionally) Edit the configuration.

## Documentation Sections

Use the navigation menu to explore:

- **[Player Guide](player-guide.md)** - How to use the hat command and wear blocks as hats.
- **[Admin Guide](admin-guide.md)** - Commands, permissions, configuration, and troubleshooting.

## Requirements

- **Server software:** Spigot or Paper
- **Dependencies:** MassiveCore
- **Permissions:** Players need **`massivehat.use`** to wear a block as a hat (default is no permission; you must grant it).

## Credits

[![License: MIT](https://img.shields.io/badge/License-MIT-7c4dff.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

Continuation of [MassiveHat](https://www.spigotmc.org/resources/massivehat.1908/) by MassiveCraft, updated to support modern Minecraft versions.