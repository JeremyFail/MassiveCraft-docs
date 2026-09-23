![FactionsChat3 Logo](../../img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }
![PlaceholderAPI Logo](img/placeholderapi.png){ style="display: block; margin: 10px auto; max-height: 115px;" }

# PlaceholderAPI Integration

FactionsChat provides support for [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/), allowing you to display faction information in chat. If you have PlaceholderAPI installed, FactionsChat will run all placeholders through PlaceholderAPI. You will be able to use any of the [Factions Placeholders](../../../Factions/admin-guide/integrations/placeholderapi.md) in your chat format string, as well as any placeholders registered by other plugins.

If you don't have PlaceholderAPI installed, we do still provide basic built-in placeholder support. Scroll down to the Built-in Placeholders section below for more details.

!!! info "Note"

    For more information about PlaceholderAPI, visit their plugin listing page or [Wiki](https://wiki.placeholderapi.com/).


## Installation

1. Install PlaceholderAPI on your server
2. Install FactionsChat3
3. Configure the chat format string with the placeholders you wish to use

No additional configuration is required - the integration is automatic.

## Setup Differences

!!! warning "Important"
    
    Depending on the version of Factions being used, the available placeholders may be slightly different. Please see the below to find the setup that applies to you.

### Factions3 Renewed Plugin

When integrating with [Factions3 Renewed](../../../Factions), all the Factions placeholders will be available, in addition to the following that can be used with PlaceholderAPI:

- `%factions_chat_prefix%` - The chat prefix of the current chat mode (as defined in the FactionsChat `config.yml` file)
- `%factions_chat_color%` - The chat color of the current chat mode (as defined in the FactionsChat `config.yml` file)

### Other Factions Plugins

When integrating with any other Factions plugin, the following placeholders can be used with PlaceholderAPI:

- `%factionschat_chat_prefix%` - The chat prefix of the current chat mode (as defined in the FactionsChat `config.yml` file)
- `%factionschat_chat_color%` - The chat color of the current chat mode (as defined in the FactionsChat `config.yml` file)
- `%factionschat_faction_name%` - The name of the faction the player is in (will be blank if they are not in a faction)
- `%factionschat_faction_nameforce%` - the name of the faction the player is in (even if they are not in a faction)
- `%factionschat_player_rank%` - The name of the rank the player holds (will be blank if they are not in a faction)
- `%factionschat_player_rankforce%` - The name of the rank the player holds (even if they are not in a faction)
- `%factionschat_player_rankprefix%` - The prefix of the rank the player holds (will be blank if they are not in a faction)
- `%factionschat_player_rankprefixforce%` - The prefix of the rank the player holds (even if they are not in a faction)
- `%factionschat_player_title%` - The title the player currently holds
- `%rel_factionschat_relation_name%` - The relationship name of the player compared to another player (example: if a player is an ally, will display the word "Ally")
- `%rel_factionschat_relation_color%` - The relationship color of the player compared to another player (example: if a player is an ally, will use the configured ally color from the Factions configuration)

### Built-in Placeholders (PlaceholderAPI not installed)

If you don't have PlaceholderAPI installed, don't worry! We have built-in placeholder support for basic compatibility with Factions. The list of placeholders available without PlaceholderAPI is limited to the list below, but does provide the main functionality that most servers need for usage in chat. Here is the list of supported built-in placeholders:

- `%factions_faction_name%` - The name of the faction the player is in (will be blank if they are not in a faction)
- `%factions_faction_nameforce%` - the name of the faction the player is in (even if they are not in a faction)
- `%factions_player_rank%` - The name of the rank the player holds (will be blank if they are not in a faction)
- `%factions_player_rankforce%` - The name of the rank the player holds (even if they are not in a faction)
- `%factions_player_rankprefix%` - The prefix of the rank the player holds (will be blank if they are not in a faction)
- `%factions_player_rankprefixforce%` - The prefix of the rank the player holds (even if they are not in a faction)
- `%factions_player_title%` - The title the player currently holds
- `%rel_factions_relation_name%` - The relationship name of the player compared to another player (example: if a player is an ally, will display the word "Ally")
- `%rel_factions_relation_color%` - The relationship color of the player compared to another player (example: if a player is an ally, will use the configured ally color from the Factions configuration)
- `%factions_chat_prefix%` - The chat prefix of the current chat mode (as defined in the FactionsChat `config.yml` file)
- `%factions_chat_color%` - The chat color of the current chat mode (as defined in the FactionsChat `config.yml` file)

### All Setups

We also have two special placeholders that are not part of PlaceholderAPI _or_ part of the built-in placeholders. These are used to refer to the player's displayname and the message they are sending. Although they cannot be used by other plugins, they will work in the chat format string regardless of if you have PlaceholderAPI installed or not.

- `%DISPLAYNAME%` - The display name of the player
- `%MESSAGE%` - The message the player sent

## Placeholder Modifiers

In addition to the placeholders themselves, we also support several conditional modifiers, which work both with any of the above supported placeholders (with one exception - they do not work with the display name or message). Modifiers will tweak the final output of a placeholder. These modifiers only apply if the placeholder it's attached to actually resolves to a value.

For example, if you wanted to add a space to the right or left of a placeholder, but you _only_ wanted to do that if the value that resolves for that placeholder actually contains text, you can add one of the padding placeholders listed below to do that. A common use-case for this is on the Faction name - the Faction name is typically blank if the player is not in a faction. So, if you wanted a space between the Faction name and some other text but you only want that space to be added **if** the player is in a Faction, you would want to use a modifier rather than a hard-coded space in your format.

To add a modifier to a placeholder, use the pipe delimiter `|` right before the closing percent sign, followed by your modifier (or modifiers - you can use more than one!).

| Modifier | Description | Example |
|----------|-------------|---------|
| `lp` | Left Padding (space) | `%factions_faction_name|lp%` |
| `rp` | Right Padding (space) | `%factions_faction_name|rp%` |
| `bp` | Both Padding (spaces) | `%factions_faction_name|bp%` |
| `trim` | Remove excess spaces | `%factions_faction_description|trim%` |
| `upper` | Convert to uppercase | `%factions_faction_name|upper%` |
| `lower` | Convert to lowercase | `%factions_faction_name|lower%` |

**Example with modifiers:**
```
%factions_faction_name|rp%
```
This adds right padding (a space) after the faction name, but only if the player is in a faction.

## Usage Examples

Below are a few simple examples you could configure in your chat string.

**Simple Format:**
```yaml
ChatFormat: '%factions_faction_name|rp|upper%%DISPLAYNAME%: %MESSAGE%'
```

**Complex Format:**
```yaml
ChatFormat: "%factions_chat_prefix|rp%&f<%rel_factions_relation_color%%factions_player_rankprefix%%factions_faction_name|rp%&f%DISPLAYNAME%&f> %factions_chat_color%%MESSAGE%"
```

## Troubleshooting

### Common Issues

**Placeholders showing as text:**

- Ensure PlaceholderAPI is installed and running
- Check placeholder spelling and syntax

**Blank placeholders:**

- Player may not be in a faction (use `force` variants if needed)
- Faction may not have the requested data

### Testing Placeholders

Use the PlaceholderAPI test command:
```
/papi parse <player> <placeholder>
```

Example:
```
/papi parse Steve %factions_faction_name%
```
