![MassiveHat Logo](img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }

# Admin Guide

## Commands

MassiveHat uses a base command (e.g. `/massivehat`) and optional shortcut commands (e.g. `/hat`, `/mhat`, `/blockhat`) that map to "use". Aliases are set in the config.

| Command | Description | Permission |
|---------|-------------|------------|
| `/massivehat` (or configured alias) | Base command, shows help | `massivehat.basecommand` |
| `/massivehat use` (or `wear`, `apply`) | Wear the item in hand as a hat | `massivehat.use` |
| `/hat`, `/mhat`, `/blockhat` (if configured) | Shortcuts for "use" - wear item in hand as hat | `massivehat.use` |
| `/massivehat config` | Edit configuration in-game | `massivehat.config` |
| `/massivehat v` or `/massivehat version` | Show plugin version | `massivehat.version` |

## Permissions

### Player Permissions

| Node | Description |
|------|-------------|
| `massivehat.use` | Wear the block/item in hand as a hat |

Without this permission, players cannot use the hat command. **You must grant `massivehat.use`** for players to wear hats.

### Operator / Admin Permissions

| Node | Description |
|------|-------------|
| `massivehat.basecommand` | Use the base command (e.g. `/massivehat`) and see help |
| `massivehat.config` | Edit the MassiveHat config in-game |
| `massivehat.version` | See plugin version |

### Star notation

- **`massivehat.*`** (default: op) - Grants all MassiveHat permissions (basecommand, use, config, version). Useful for giving admins full access.

## Configuration

The config file is **`/mstore/massivehat_mconf/instance.json`**. You can edit it with a text editor or in-game with `/massivehat config` (with `massivehat.config`). Changes are detected automatically after a few seconds; no restart or reload command is needed.

### Supported Configuration Values

Configuring MassiveHat is **optional**. The default configuration works for most servers.

You can modify the settings in the configuration file. Modifications will automatically be detected and loaded after a few seconds.

!!! warning
    Comments have been added to the configuration example below to explain the values, but these comments should **NOT** be added to your actual configuration file as it will cause errors.

```javascript
{
  // Aliases for the main base command (e.g. /massivehat).
  "aliasesMassiveHat": ["massivehat"],
  // Shortcut aliases that act like "use": wear the item in hand (e.g. /hat, /mhat = /massivehat use).
  "aliasesMhat": ["mhat", "usehat", "blockhat", "hat"],
  // Subcommand aliases for "use" under the base (e.g. /massivehat use, /massivehat wear).
  "aliasesHatUse": ["use", "wear", "apply"],
  "aliasesHatConfig": ["config"],
  "aliasesHatVersion": ["v", "version"],

  // Non-block items that may be worn as hats. standard: false = only exceptions are allowed; list material names (e.g. BANNER).
  "itemHats": {
    "standard": false,
    "exceptions": ["BANNER"]
  },
  // Block types that may be used as hats. standard: true = all blocks allowed except those in exceptions; empty = no exclusions.
  "blockHats": {
    "standard": true,
    "exceptions": []
  },
  // Vanilla headwear: these are handled normally by the server (not as MassiveHat block hats). standard: false = only these are treated as normal helmets.
  "normalHelmets": {
    "standard": false,
    "exceptions": [
      "CARVED_PUMPKIN",
      "CHAINMAIL_HELMET",
      "COPPER_HELMET",
      "CREEPER_HEAD",
      "DIAMOND_HELMET",
      "DRAGON_HEAD",
      "GOLD_HELMET",
      "IRON_HELMET",
      "LEATHER_HELMET",
      "NETHERITE_HELMET",
      "PIGLIN_HEAD",
      "PLAYER_HEAD",
      "SKELETON_SKULL",
      "WITHER_SKELETON_SKULL",
      "ZOMBIE_HEAD"
    ]
  },

  // When a player tries to place an item in the helmet slot but doesn't have permission, show them a message?
  "hatPlacePermDenyVerbose": true
}
```

## Troubleshooting

### Players can’t wear hats

- Ensure **MassiveCore** is installed and the correct version for your server.
- Grant **`massivehat.use`** to the player or a group. By default no one has use permission.
- If they use a shortcut like `/hat`, ensure that alias is in **`aliasesMhat`** in the config.

### "Unknown command" or no response

- Grant **`massivehat.basecommand`** if they need to use `/massivehat` and see help.
- Grant **`massivehat.use`** for the actual hat action (and ensure the alias they use is configured).

### Certain blocks or items don’t work

- Check **`blockHats`** and **`itemHats`** in the config. Some blocks or items may be excluded for balance or performance.
- Banners and other non-block items are controlled by **`itemHats`**.

### Config changes not applying

- Wait a few seconds; the plugin reloads config automatically.
- Ensure the JSON is valid (no comments, no trailing commas).
- If using in-game config, run `/massivehat config` and save correctly.

### Getting help

- Check the server console for errors when the command is used.
- Verify MassiveCore and MassiveHat versions are compatible.
- Open an issue on the project repository with server type/version, plugin version, and steps to reproduce.
