![FactionsChat3 Logo](../img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }

# Chat Channels

FactionsChat provides multiple chat channels (sometimes referred to as "modes") based on faction relationships and scope. This guide explains each channel and how to use them effectively.

## Available Channels

All channels can be acessed through either their full name or abbreviation (first letter).

### Faction-Based Channels

| Channel | Description | Who Can See |
|---------|-------------|-------------|
| **Faction** | Private faction communication | Only members of your faction |
| **Ally** | Allied faction communication | Members of your faction and allied factions |
| **Truce** | Truce faction communication | Members of your faction and factions you have truces with |
| **Enemy** | Enemy faction communication | Members of your faction and enemy factions |
| **Neutral** | Neutral faction communication | Members of your faction and neutral factions |

### General Channels

| Channel | Description | Who Can See |
|---------|-------------|-------------|
| **Global** | Server-wide communication | Everyone on the server |
| **Local** | Proximity-based chat | Players within a certain range of you (range is configured by server staff) |
| **World** | World-specific chat | Players in the same world as you |

### Special Channels

| Channel | Description | Who Can See |
|---------|-------------|-------------|
| **Staff** | Staff communication | Only server staff/moderators (requires special permission) |

## Using Channels

### Switching Channels

#### Quick Syntax:

To quickly switch to a channel, simply type a colon, followed by the channel name or letter.
```
:faction

# -- OR -- #

:f
```

Please note - the colon prefix is configurable. Check with your server admin if the colon prefix doesn't work on your server.

#### Command Syntax:

Alternatively, you can us the `/f c <channel>` command syntax:
```
/f c <channel>
```

Examples:
```
/f c faction    # Switch to Faction chat
/f c ally       # Switch to Ally chat
/f c global     # Switch to Global chat
/f c local      # Switch to Local chat
```

### Sending Quick Messages

Send a one-off message without switching channels:
```
:f <message here>
```

Examples:
```
:a We're being raided, need help!
:f Anyone have extra diamonds?
:g Selling enchanted armor at spawn!
```

Please note - the colon prefix is configurable. Check with your server admin if the colon prefix doesn't work on your server.

## Toggling Channels

If your chat is very active and you only want to see messages for certain channels, you can turn messages for a specific channel off by toggling that channel:
```
/f c toggle <channel>
```

Run the same command again to turn messages for that channel back on.

## Troubleshooting

### My messages aren't showing up

- Check that you're in the right channel
- Verify you have permission to use that channel
- Validate the channel in question is not currently toggled off with `/f c toggle <channel>`
- Make sure you're in a faction (required for some channels)
- Ensure you have the correct faction relationships established

### I can't switch to a channel

- You may not have permission for that channel
- You may need to be in a faction first
- Some channels require specific faction relationships
- Staff chat requires special permissions

### No one is responding in a channel

- Confirm the channel you're in
- Check if anyone else is online with access to that channel
- Validate the channel in question is not currently toggled off with `/f c toggle <channel>`
- Faction channels are only useful if you have faction members online
- Try switching to global to see if chat is working

## Related Guides

- **[Player Guide Overview](index.md)** - Return to the main player guide
- **[Chat Formatting](chat-formatting.md)** - Learn how to format and style your messages
- **[Player Ignoring](player-ignoring.md)** - Learn how the ignore system works to ignore messages from other players
