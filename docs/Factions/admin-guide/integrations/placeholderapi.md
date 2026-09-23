![Factions3 Logo](../../img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }
![PlaceholderAPI Logo](img/placeholderapi.png){ style="display: block; margin: 10px auto; max-height: 115px;" }

# PlaceholderAPI Integration

Factions provides comprehensive support for [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/), allowing you to display faction information in chat plugins, scoreboards, tab lists, and any other plugin that supports PlaceholderAPI placeholders.

!!! info "Note"

    For more information about PlaceholderAPI, visit their plugin listing page or [Wiki](https://wiki.placeholderapi.com/).


## Installation

1. Install PlaceholderAPI on your server
2. Install Factions (PlaceholderAPI support is built-in)
3. Use placeholders in your supported plugins

No additional configuration is required - the integration is automatic.

## Available Placeholders

### Player Placeholders

| Placeholder | Description |
|-------------|-------------|
| `%factions_player_name%` | Player's name |
| `%factions_player_power%` | Player's current power |
| `%factions_player_powermax%` | Player's maximum power |
| `%factions_player_rank%` | Player's faction rank name |
| `%factions_player_rankforce%` | Player's faction rank (even if not in faction) |
| `%factions_player_rankprefix%` | Player's rank prefix |
| `%factions_player_rankprefixforce%` | Player's rank prefix (even if not in faction) |
| `%factions_player_title%` | Player's custom title |

### Faction Placeholders

These placeholders show information about the faction the player is currently a member of:

| Placeholder | Description |
|-------------|-------------|
| `%factions_faction_internal_id%` | Internal unique ID of the player's faction |
| `%factions_faction_name%` | Name of the player's faction |
| `%factions_faction_nameforce%` | Name of the player's faction (even if not in a faction) |
| `%factions_faction_description%` | Description of the player's faction |
| `%factions_faction_power%` | Current power of the player's faction |
| `%factions_faction_powermax%` | Maximum power the player's faction can have |
| `%factions_faction_powerboost%` | Current power boost of the player's faction |
| `%factions_faction_money_balance%` | Faction bank balance - formatted with a dollar sign and two decimal places |
| `%factions_faction_money_balance_raw%` | Faction bank balance - unformatted (no dollar sign, no specific decimal places) |
| `%factions_faction_leader%` | Name of the faction leader |
| `%factions_faction_founded%` | Founded date (format configurable) |
| `%factions_faction_peaceful%` | Whether the faction is peaceful (true/false) |
| `%factions_faction_claims%` | Number of claims the faction has |
| `%factions_faction_onlinemembers%` | Number of online faction members |
| `%factions_faction_offlinemembers%` | Number of offline faction members |
| `%factions_faction_allmembers%` | Total number of faction members |

### Faction Home Placeholders

| Placeholder | Description |
|-------------|-------------|
| `%factions_faction_home_formatted%` | Home location as "World (x, y, z)" |
| `%factions_faction_home_world%` | World name of faction home |
| `%factions_faction_home_x%` | X coordinate of faction home |
| `%factions_faction_home_y%` | Y coordinate of faction home |
| `%factions_faction_home_z%` | Z coordinate of faction home |

### Faction Relationship Placeholders

| Placeholder | Description |
|-------------|-------------|
| `%factions_faction_allies%` | Number of allied factions |
| `%factions_faction_allies_players%` | Number of allied players |
| `%factions_faction_allies_players_online%` | Number of online allied players |
| `%factions_faction_allies_players_offline%` | Number of offline allied players |
| `%factions_faction_enemies%` | Number of enemy factions |
| `%factions_faction_enemies_players%` | Number of enemy players |
| `%factions_faction_enemies_players_online%` | Number of online enemy players |
| `%factions_faction_enemies_players_offline%` | Number of offline enemy players |
| `%factions_faction_truces%` | Number of truce factions |
| `%factions_faction_truces_players%` | Number of truce players |
| `%factions_faction_truces_players_online%` | Number of online truce players |
| `%factions_faction_truces_players_offline%` | Number of offline truce players |

### Relational Placeholders

These placeholders work between two players and show their relationship (in other words, what relationship one player has to another):

| Placeholder | Description |
|-------------|-------------|
| `%rel_factions_relation%` | Relationship name (Ally, Enemy, etc.) |
| `%rel_factions_relation_color%` | Relationship color code |

### Territory Placeholders

These placeholders show information about the faction that owns the territory the player is currently standing in:

| Placeholder | Description |
|-------------|-------------|
| `%factions_faction_territory_internal_id%` | The internal unique ID of faction owning current territory |
| `%factions_faction_territory_name%` | Name of faction owning current territory |
| `%factions_faction_territory_description%` | Description of faction owning current territory |
| `%factions_faction_territory_leader%` | Leader of faction owning current territory |
| `%factions_faction_territory_relation_color%` | Relationship color compared to player's faction |
| `%factions_faction_territory_power%` | Power of faction owning current territory |
| `%factions_faction_territory_claims%` | Claims of faction owning current territory |
| etc. | *Most faction placeholders have territory equivalents - just replace `faction_` with `faction_territory_`* |

### Map Placeholders

These placeholders display a visual map in rows, based on the `placeholderMap` configuration settings.
This is designed for use with scoreboards where the scoreboard can be configured to update at a regular interval and show a live
territory map in-game as you walk, without having to run the `/f map` command.

| Placeholder | Description |
|-------------|-------------|
| `%factions_faction_map_row_N%` | The faction map row to display (with `N` being a number, starting with 1, and going up to the maximum number of rows set in the configuration) |

### Legacy Placeholders
Please note that some legacy placeholders do still work/exist and are not documented in the lists above - they are not officially supported and are subject to removal in future versions. We recommend using the above placeholders and only officially support those in the lists above.

## Placeholder Modifiers

In addition to the placeholders themselves, we also support several conditional modifiers. These modifiers only apply if the placeholder it's attached to actually resolves to a value.

For example, if you wanted to add a space to the right or left of a placeholder, but you only wanted to do that if the value that resolves for that placeholder actually contains text, you can add one of the padding placeholders listed below to do that. A common use-case for this is on the Faction name - the Faction name is blank if the player is not in a faction. So, if you wanted a space between the Faction name and some other text but you only want that space to be added **if** the player is in a Faction, you would want to use a modifier rather than a hard-coded space in your format.

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
%factions_faction_name|rp%Player joined the server!
```
This adds a space after the faction name, but only if the player is in a faction.

## Usage Examples

Below are a few simple example of how placeholders with Factions can be used. 

!!! info "Note"
    Actual configuration settings may vary based on the plugins being configured.

### Chat Formatting

**Simple Format:**
```yaml
format: '%factions_faction_name|rp|upper%{DISPLAYNAME}: {MESSAGE}'
```

**Complex Format:**
```yaml
format: "&7[%factions_player_rankprefix|rp%%factions_faction_name|rp%&7]&f{DISPLAYNAME}&7: &r{MESSAGE}"
```

### Scoreboard Examples

**Generic Scoreboard:**
```yaml
lines:
  - "&7Faction: &f%factions_faction_name%"
  - "&7Power: &f%factions_faction_power%&7/&f%factions_faction_powermax%"
  - "&7Claims: &f%factions_faction_claims%"
  - "&7Members: &f%factions_faction_onlinemembers%&7/&f%factions_faction_allmembers%"
  - "&7Territory: &f%factions_faction_territory_name%"
```

**Scoreboard with Map:**
This is an example of a scoreboard that shows the Faction Map. The map size and refresh duration is configurable using the `placeholderMap` settings in the config.
```yaml
lines:
  - "&b&lFaction Info and Map"
  - "&e&lPower: &r&b%factions_factionpower%"
  - "%factions_faction_map_row_1%"
  - "%factions_faction_map_row_2%"
  - "%factions_faction_map_row_3%"
  - "%factions_faction_map_row_4%"
  - "%factions_faction_map_row_5%"
  - "%factions_faction_map_row_6%"   
  - "%factions_faction_map_row_7%"      
  - "%factions_faction_map_row_8%"      
  - "%factions_faction_map_row_9%"      
  - "&a&lFaction: ■ %factions_faction%"
  - "&7&l■ Neutral &b&l■ Ally"
  - "&4&l■ Enemy"
  - "&e&l■ You are Here"
```

### Tab List Examples

**TabList Plugin:**
```yaml
header: |
  &7Welcome to the server!
  &7Your faction: &f%factions_faction_name%
  
footer: |
  &7Power: &f%factions_player_power%&7/&f%factions_player_powermax%
  &7Online: &f%factions_faction_onlinemembers% members
```

## Troubleshooting

### Common Issues

**Placeholders showing as text:**

- Ensure PlaceholderAPI is installed and running
- Verify the plugin supports PlaceholderAPI
- Check placeholder spelling and syntax (make sure you are using percent signs and not brackets for your placeholders - we do not support bracket placeholders)

**Blank placeholders:**

- Player may not be in a faction (use `force` variants if needed)
- Faction may not have the requested data (e.g., no home set)
- Territory placeholders require the player to be in claimed land

### Testing Placeholders

Use the PlaceholderAPI test command:
```
/papi parse <player> <placeholder>
```

Example:
```
/papi parse Steve %factions_faction_name%
```

### Legacy Placeholders

As mentioned above, some legacy placeholders from older versions may still work but are not officially supported. If you experience issues using these legacy placeholders, we recommend migrating to the documented placeholders listed above.
