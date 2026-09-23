![Factions3 Logo](img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }

# Welcome to Factions

Factions is a comprehensive land claiming and faction warfare plugin for Minecraft Spigot/Paper servers. It provides players with the ability to create factions, claim territory, manage relationships with other factions, and engage in strategic gameplay.

## What is Factions?

Factions transforms your Minecraft server into a dynamic world of territorial control, diplomacy, and warfare. Players can band together to form factions, claim chunks of land to protect their builds, forge alliances or declare enemies, and compete for dominance on your server.

## Key Features

- **Territory Management**: Claim and protect chunks of land for your faction
- **Faction Relationships**: Form alliances, truces, or declare enemies with other factions
- **Economic Integration**: Built-in faction banks and economy support via Vault
- **Flexible Permissions**: Granular control over what faction members can do
- **Power System**: Dynamic faction strength based on member activity and deaths
- **Warfare Mechanics**: Territorial conquest through power imbalances
- **Rich Customization**: Extensive configuration options for server admins
- **Integration Support**: Works with Dynmap, WorldGuard, PlaceholderAPI, and more

## Core Concepts

### Factions
Groups of players working together with shared territory and resources. Each faction has a unique name, description, and internal hierarchy with customizable ranks.

### Territory Claims
Factions can claim chunks of land to protect them from other players. The amount of land a faction can claim is limited by their collective power.

### Power System
Each player contributes power to their faction. Power increases over time when online and decreases when players die. This creates strategic depth around territorial control.

### Relationships
Factions can have different relationships with each other:

- **Allies**: Full cooperation and shared protection
- **Truces**: Non-aggression pacts
- **Neutral**: Default relationship with no special benefits or restrictions
- **Enemies**: Open hostility with the ability to conquer territory

## Quick Start

=== "For Players"
    1. Join or create a faction with `/f create <name>`
    2. Claim territory with `/f claim`
    3. Invite friends with `/f invite <player>`
    4. Set faction relationships with `/f relation`
    5. Build and protect your base!

=== "For Admins"
    1. Install [MassiveCore](../MassiveCore) (required dependency)
    2. Install Factions
    3. Configure settings if needed
    4. Set up permissions for your server
    5. Optionally integrate with other plugins

## Documentation Sections

Use the navigation menu to explore:

- **[Commands](admin-guide/commands.md)** - Complete command reference and permissions
- **[Permissions](admin-guide/permissions.md)** - Detailed permission system documentation
- **[Configuration](admin-guide/configuration.md)** - Server configuration options and settings
- **[Integrations](admin-guide/integrations)** - Built-in integrations with third-party plugins

## Requirements

- **Server Software**: Spigot/Paper
- **Dependencies**: MassiveCore plugin (required)
- **Optional Integrations**: Vault (economy), Dynmap (mapping), WorldGuard (region protection), PlaceholderAPI (placeholders)

## Credits

[![License: LGPL v3](https://img.shields.io/badge/License-LGPL_v3-7c4dff.svg?style=for-the-badge)](https://www.gnu.org/licenses/lgpl-3.0)

Continuation of [Factions 3](https://github.com/magnusulf/Factions) by Madus, which was a continuation of [MassiveCraft Factions 2](https://github.com/MassiveCraft/Factions) by Cayorion, Ulumulu1510, MarkehMe, and Brettflan.