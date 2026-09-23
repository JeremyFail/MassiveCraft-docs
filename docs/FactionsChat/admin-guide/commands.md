![FactionsChat3 Logo](../img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }


# Commands

Below is a list of all the currently available FactionsChat3 commands and some simple usage examples.

!!! info "Note"

    The instructions below use `/f c <command>` syntax. If you are running FactionsChat3 in standalone mode, the command will instead be `/chat` or `/c` for short.

## Player Commands

| Command | Description | Example |
|---------|-------------|---------|
| `/f c help` | View help for the various FactionsChat features/commands you can access | `/f c help` |
| `/f c <channel>` | Command to switch your active chat channel (alternative syntax available - see [Chat Channels](../player-guide/chat-channels.md) for more details) | `/f c ally` |
| `/f c toggle <channel>` | Toggle (enable/disable) messages for a specific channel - this will show hide messages for that channel until you toggle it again | `/f c toggle faction` |
| `/f c ignore <player>` | Ignore messages from the specified player | `/f c ignore Steve` |
| `/f c unignore <player>` | Stop ignoring messages from the specified player | `/f c unignore Steve` |
| `/f c ignorelist [page]` | View the list of players you are currently ignoring (paginated) | `/f c ignorelist 1` |

## Operator/Admin Commands

| Command | Description |
|---------|-------------|
| `/f c reload` | Reloads the plugin configuration (requires permission) |
| `/f c toggle <playerToManage> <channelToToggle>` | Toggle (enable/disable) a channel for another player |
| `/f c ignore <playerToManage> <playerToIgnore>` | Adds a player to another player's ignore list |
| `/f c unignore <playerToManage> <playerToIgnore>` | Removes a player from another player's ignore list |
| `/f c ignorelist <playerToManage> [page]` | View the list of players the specified player is currently ignoring |
