![FactionsChat3 Logo](../img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }

# Player Guide Overview

Welcome to the FactionsChat player guide! This guide will help you understand how to use chat channels and formatting on a FactionsChat server.

## What is FactionsChat?

FactionsChat is a plugin that adds multiple chat channels to Factions servers, allowing you to communicate with specific groups of players based on faction relationships. It also provides extensive chat formatting options to personalize your messages.

## Getting Started

### Basic Chat Usage

By default, your messages go to the Global chat channel where everyone on the server can see them. You can switch between different chat channels to communicate with specific groups of players.

### Switching Chat Channels

To switch your active chat channel, use:
```
:<channel>

# -- OR -- #

/f c <channel>
```

For example:
```
# Switch to Faction chat
:faction
:f
/f c faction
```

Once you switch channels, all your messages will go to that channel until you switch again.

### Sending One-Off Messages

To send a single message to a channel without switching to it, use:
```
:<channel> <message>
```

For example:
```
:a Need backup at base!
:f Anyone have extra diamonds?
```

This sends the message to the specified channel but keeps your active channel unchanged.

## Channel Persistence

FactionsChat remembers your last active channel, even if you log out and log back in. You'll automatically be in the same channel you were using before.

## Commands Quick Reference

| Command | Description | Example |
|---------|-------------|---------|
| `/f c help` | View help for the various FactionsChat features/commands you can access | `/f c help` |
| `/f c toggle <channel>` | Toggle (enable/disable) messages for a specific channel - this will show hide messages for that channel until you toggle it again | `/f c toggle faction` |
| `/f c ignore <player>` | Ignore messages from the specified player | `/f c ignore Steve` |
| `/f c unignore <player>` | Stop ignoring messages from the specified player | `/f c unignore Steve` |
| `/f c ignorelist [page]` | View the list of players you are currently ignoring (paginated) | `/f c ignorelist 1` |

## Next Steps

Learn more about FactionsChat features:

- **[Chat Channels](chat-channels.md)** - Detailed guide to all available chat channels
- **[Chat Formatting](chat-formatting.md)** - Learn how to format and style your messages
- **[Player Ignoring](player-ignoring.md)** - Learn how the ignore system works to ignore messages from other players
