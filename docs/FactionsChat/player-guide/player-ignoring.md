![FactionsChat3 Logo](../img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }

# Player Ignoring

FactionsChat supports the ability to ignore messages from other players. This guide covers how to use this feature.

!!! info "Permissions Required"
    The player ignoring feature requires specific permissions. Check with your server admin if this feature doesn't work for you.

## What is Player Ignoring?

Player Ignoring allows you to block messages from specific players. When you ignore a player, you won't see their chat messages in any channel. This is useful for avoiding spam, harassment, or simply messages from players you prefer not to interact with.

## Managing Your Ignore List

### Ignoring a Player

To add a player to your ignore list:
```
/f c ignore <player>
```

**Example:**
```
/f c ignore Steve
```

Once a player is on your ignore list, you will no longer see their chat messages.

!!! info "Staff Members"
    Some players may not be able to be ignored, typically staff members. This ensures important server messages and moderation communications are always visible.

### Unignoring a Player

To remove a player from your ignore list:
```
/f c unignore <player>
```

**Example:**
```
/f c unignore Steve
```

After unignoring a player, you will start seeing their messages again.

### Viewing Your Ignore List

To see which players you are currently ignoring:
```
/f c ignorelist [page]
```

**Examples:**
```
/f c ignorelist       # View first page
/f c ignorelist 1     # View page 1
/f c ignorelist 2     # View page 2
```

The ignore list is paginated, so if you're ignoring many players, you can navigate through different pages.

## Server Admin Features

Server administrators have additional options to manage ignore lists:

### Managing Other Players' Ignore Lists

**Add a player to someone's ignore list:**
```
/f c ignore <playerToManage> <playerToIgnore>
```

**Example:**
```
/f c ignore Alice Bob
```
This makes Alice ignore Bob's messages.

**Remove a player from someone's ignore list:**
```
/f c unignore <playerToManage> <playerToIgnore>
```

**Example:**
```
/f c unignore Alice Bob
```
This makes Alice no longer ignore Bob's messages.

**View another player's ignore list:**
```
/f c ignorelist <playerToManage> [page]
```

**Example:**
```
/f c ignorelist Alice
```
This displays the current ignore list for Alice.

## Related Guides

- **[Player Guide Overview](index.md)** - Return to the main player guide
- **[Chat Channels](chat-channels.md)** - Learn about available chat channels
- **[Chat Formatting](chat-formatting.md)** - Learn how to format and style your messages