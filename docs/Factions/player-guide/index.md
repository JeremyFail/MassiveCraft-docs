![Factions3 Logo](../img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }

# Player Guide Overview

Welcome to the Factions player guide! This guide will help you understand how to play on a Factions server, from creating your first faction to becoming a dominant force on the server.

## What is Factions?

Factions is a plugin that transforms Minecraft into a strategic game of territorial control, diplomacy, and warfare. Players form groups (called factions), claim land to protect their builds, forge alliances or declare war, and compete for dominance on the server.

## Getting Started

### Creating or Joining a Faction

Before you can claim land or use most Factions features, you need to be part of a faction.

**To create a new faction:**
```
/f create <name>
```

**To join an existing faction:**

You'll need an invitation from that faction. Once invited, use:
```
/f join <faction>
```

**To leave a faction:**
```
/f leave
```

### Understanding the Basics

Once you're in a faction, you can:

- View your faction's information with `/f f`
- See other factions with `/f list`
- Check any player's faction status with `/f player <name>`
- View your faction's members and their status with `/f status`

## Core Concepts

### Power System

Power is the foundation of the Factions system. Here's how it works:

- **Each player has power** that increases over time when you're online
- **Power decreases when you die** - this is the main penalty for death
- **Your faction's power** is the sum of all members' power
- **Power limits land claims** - you can only claim as much land as you have power
- **Enemies can claim your land** if your power drops too low

**Check your power:**
```
/f player
```

### Territory and Claims

Territory is claimed in chunks (16x16 block sections). Protected territory prevents enemies from building, breaking blocks, or using containers.

**To claim land:**
```
/f claim
```

**To unclaim land:**
```
/f unclaim
```

**To see the territory map:**
```
/f map
```

**To see chunk boundaries:**
```
/f seechunk
```

**Territory title notifications:**
```
/f territorytitles
```
This toggles on/off messages when entering/leaving faction territory.

### Faction Relationships

Factions can have different relationships with each other:

- **Ally** - Full cooperation, can't harm each other, can build in each other's land (if permitted)
- **Truce** - Non-aggression pact, reduced restrictions
- **Neutral** - Default relationship, standard restrictions apply
- **Enemy** - Open hostility, can claim enemy land if their power is low enough

**To manage relationships:**
```
/f relation
```

## Common Commands Quick Reference

| Command | Description |
|---------|-------------|
| `/f create <name>` | Create a new faction |
| `/f join <faction>` | Join a faction |
| `/f leave` | Leave your faction |
| `/f claim` | Claim the chunk you're standing in |
| `/f unclaim` | Unclaim the chunk you're standing in |
| `/f map` | View the territory map |
| `/f home` | Teleport to faction home |
| `/f sethome` | Set faction home location |
| `/f invite add <player>` | Invite a player to your faction |
| `/f f` | View your faction info |
| `/f list` | List all factions |
| `/f player <name>` | View player information |
| `/f relation` | Manage faction relationships |
| `/f money` | Access faction bank |

## Getting Help

If you're stuck or have questions:

1. **Use `/f help`** to see available commands
2. **Ask faction members** for guidance
3. **Check faction MOTD** with `/f motd` for faction-specific rules
4. **Contact server staff** if you encounter issues

## Next Steps

Now that you understand the basics, explore more advanced features:

- **[Faction Management](faction-management.md)** - Learn how to manage your faction, claim territory, set permissions, and use the economy system
- **[Strategy & Tips](strategy-tips.md)** - Master raiding, defending, and get tips for becoming a dominant faction
