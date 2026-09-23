![MassiveBooks Logo](../img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }

# Admin Guide

## Commands

All book commands operate on the book the player is holding. The base command is typically `/book` or `/books` (configurable via `aliasesBook` in the config).

| Command | Description | Permission |
|---------|-------------|------------|
| `/book` or `/books` | Base command, shows help | `massivebooks.book` |
| `/book unlock` | Unlock a signed book | `massivebooks.unlock` |
| `/book lock` | Lock a book | `massivebooks.lock` |
| `/book clear` | Clear a book | `massivebooks.clear` |
| `/book title <title>` | Set book title | `massivebooks.title` |
| `/book author <author>` | Set book author | `massivebooks.author` |
| `/book copy [times]` | Copy the book | `massivebooks.copy` |
| `/book list [page]` | List serverbooks | `massivebooks.list` |
| `/book load <title>` | Load a serverbook | `massivebooks.load` |
| `/book give <player> <amount\|ensure> [title\|all]` | Give serverbook(s) to a player | `massivebooks.give` |
| `/book givesilent <player> ...` | Same as give, no message to player | `massivebooks.givesilent` |
| `/book save` | Save held book as serverbook | `massivebooks.save` |
| `/book delete <title>` | Delete a serverbook | `massivebooks.delete` |
| `/book autoupdate [true\|false\|toggle]` | Toggle autoupdate for your books | `massivebooks.autoupdate` |
| `/book pt` or `/book powertool [true\|false\|toggle]` | Set powertool state | `massivebooks.powertool` |
| `/book cr` or `/book copyrighted [true\|false\|toggle]` | Set copyrighted state | `massivebooks.copyrighted` |
| `/book v` or `/book version` | Show plugin version | `massivebooks.version` |
| `/book config` | Edit configuration (in-game) | `massivebooks.config` |

There are separate permissions for acting on **another author’s book** (e.g. unlock, lock, clear, title, author, copy, powertool, copyrighted). For instance, `massivebooks.unlock.other`, `massivebooks.copy.copyrighted`. See the full list below.

## Permissions

### Player Permissions

| Node | Description |
|------|-------------|
| `massivebooks.book` | Access the base `/book` command |
| `massivebooks.unlock` | Unlock own book |
| `massivebooks.lock` | Lock own book |
| `massivebooks.clear` | Clear own book |
| `massivebooks.title` | Change own book title |
| `massivebooks.copy` | Copy own book |
| `massivebooks.list` | List serverbooks |
| `massivebooks.load` | Load a serverbook |
| `massivebooks.copyrighted` | Toggle copyrighted on own book |
| `massivebooks.version` | See plugin version |

### Moderator / Admin Permissions

| Node | Description |
|------|-------------|
| `massivebooks.unlock.other` | Unlock another author’s book |
| `massivebooks.lock.other` | Lock another author’s book |
| `massivebooks.clear.other` | Clear another author’s book |
| `massivebooks.title.other` | Change title of another’s book |
| `massivebooks.title.color` | Use color codes in titles |
| `massivebooks.author` | Set author on own book |
| `massivebooks.author.other` | Set author on another’s book |
| `massivebooks.copy.other` | Copy another author’s book |
| `massivebooks.copy.copyrighted` | Copy copyrighted books by others |
| `massivebooks.give` | Give serverbooks to players |
| `massivebooks.givesilent` | Give serverbooks silently |
| `massivebooks.save` | Save a book as serverbook |
| `massivebooks.delete` | Delete a serverbook |
| `massivebooks.autoupdate` | Change autoupdate state |
| `massivebooks.powertool` | Set powertool on own book |
| `massivebooks.powertool.other` | Set powertool on another’s book |
| `massivebooks.copyrighted.other` | Set copyrighted on another’s book |
| `massivebooks.config` | Edit plugin config |

### Permission Kits

The plugin defines optional "kit" parents for convenience:

- **`massivebooks.kit.default`** (default: true) - Grants `massivebooks.kit.rank0`.
- **`massivebooks.kit.rank0`** - Basic player: book, unlock, lock, clear, title, copy, list, load, copyrighted, version.
- **`massivebooks.kit.rank1`** - Adds rank0 plus moderator-style: unlock/lock/title/author/copy copyrighted/give/save/delete/autoupdate/powertool/copyrighted for others.
- **`massivebooks.kit.rank2`** - Currently no different from rank1.
- **`massivebooks.kit.rank3`** - Includes rank2 and acces to `massivebooks.config`.
- **`massivebooks.kit.op`** (default: op) - Grants `massivebooks.*` (all nodes).

## Serverbooks

Serverbooks are books saved on the server. Players with `massivebooks.list` and `massivebooks.load` can list and load them; only staff with `massivebooks.save` and `massivebooks.delete` can save or delete serverbooks.

When a serverbook is saved, its **title** is the identifier. Any book that has the same title as a serverbook is updated to match the serverbook when autoupdate is enabled. So if you update the "Rules" serverbook and save it, everyone holding a book titled "Rules" will get the new content automatically.

**Commands for staff:** `/book save` (save the held book as a serverbook), `/book delete <title>`, `/book give <player> <amount|ensure> [title|all]`, `/book givesilent` (same as give, no message to the player).

!!! tip
    When editing an existing serverbook, turn off autoupdate first: `/book autoupdate off`. Otherwise your edits may be overwritten by the current serverbook before you save. After saving, you can turn autoupdate back on if desired.

## Item frames

Item frames can be used as **in-game libraries**. Players place a book in an item frame, then hold a book and quill and click the frame to **load** the book from the frame into their hand, or click again to **unload** (clear the book in hand; the frame keeps the book).

Behavior is configured in the main config:

- **`itemFrameLoadIfSneakTrue`** / **`itemFrameLoadIfSneakFalse`** - Whether clicking the frame loads the book when the player is sneaking or not sneaking.
- **`itemFrameDisplaynameIfSneakTrue`** / **`itemFrameDisplaynameIfSneakFalse`** - Whether the frame shows the book's display name when the player is sneaking or not.
- **`itemFrameRotateIfSneakTrue`** / **`itemFrameRotateIfSneakFalse`** - Whether right-clicking rotates the item in the frame when sneaking or not.

Players can place any book in a frame (signed, unsigned, serverbook). To clear a book they're holding, they use `/book clear`.

## Powertools

A **powertool** is a book that, when used (e.g. by clicking a block or entity), runs each line as a command (if it starts with `/`) or sends it as chat.

**Creating powertools:** Staff (or players with `massivebooks.powertool` or `massivebooks.powertool.other`) use `/book pt` or `/book powertool [true|false|toggle]` on the held book to set or clear the powertool state.

**Placeholder tags** (curly braces) are replaced when the powertool runs:

| Tag | Description |
|-----|-------------|
| `{me.name}` | Name of the player using the powertool |
| `{me.id}` | ID of the player using the powertool |
| `{me.displayname}` | Display name of the player using the powertool |
| `{you.name}` | Name of the clicked/targeted player |
| `{you.id}` | ID of the clicked/targeted player |
| `{you.displayname}` | Display name of the clicked/targeted player |
| `{block.x}`, `{block.y}`, `{block.z}` | Coordinates of the clicked block |

Lines starting with `#` are ignored (comments).

## Copy Cost

MassiveBooks supports charging players to copy a book. This is done through the **[Economy Integration](integrations/economy.md)**. Please see the dedicated page for additional details about how this works.

## Configuration

The main config is **`/mstore/massivebooks_mconf/instance.json`**. Changes are picked up automatically after a short delay; no restart or reload command is required.

### Supported Configuration Values

Configuring MassiveBooks is **optional**. The default configuration works for most servers.

You can modify the settings in the configuration file. Modifications will automatically be detected and loaded after a few seconds. You don't need to run any reload command or restart the server.

!!! warning
    Comments have been added to the configuration example below to explain the values, but these comments should **NOT** be added to your actual configuration file as it will cause errors.

```javascript
{
  // Command aliases: base command (e.g. /book, /books)
  "aliasesBook": ["book", "books"],
  "aliasesBookUnlock": ["unlock"],
  "aliasesBookLock": ["lock"],
  "aliasesBookClear": ["clear"],
  "aliasesBookTitle": ["title"],
  "aliasesBookAuthor": ["author"],
  "aliasesBookCopy": ["copy"],
  "aliasesBookList": ["list"],
  "aliasesBookLoad": ["load"],
  "aliasesBookGive": ["give"],
  "aliasesBookGiveSilent": ["givesilent"],
  "aliasesBookSave": ["save"],
  "aliasesBookDelete": ["delete"],
  "aliasesBookAutoupdate": ["autoupdate"],
  "aliasesBookPowertool": ["powertool", "pt"],
  "aliasesBookCopyrighted": ["copyrighted", "cr"],
  "aliasesBookConfig": ["config"],
  "aliasesBookVersion": ["v", "version"],

  // New Player Commands:
  // Run commands for players the first time they join. {p} is replaced with the player name.
  "usingNewPlayerCommands": false,
  "newPlayerCommands": ["book give {p} ensure all"],
  // Wait a few ticks before running new player commands (20 ticks = 1 second).
  "usingNewPlayerCommandsDelayTicks": true,
  "newPlayerCommandsDelayTicks": 5,

  // Copy cost: if Vault is present, copying books can cost money based on permissions that players have.
  // Permissions are checked top to bottom in this list; the first match found is used. 
  // You can modify/create as many permissions as needed.
  "permToCopyCost": {
    "massivebooks.copycost.free": 0.0,
    "massivebooks.copycost.0": 0.0,
    "massivebooks.copycost.0.01": 0.01,
    "massivebooks.copycost.0.02": 0.02,
    "massivebooks.copycost.0.03": 0.03,
    "massivebooks.copycost.0.1": 0.1,
    "massivebooks.copycost.0.2": 0.2,
    "massivebooks.copycost.0.3": 0.3,
    "massivebooks.copycost.1": 1.0,
    "massivebooks.copycost.2": 2.0,
    "massivebooks.copycost.3": 3.0,
    "massivebooks.copycost.10": 10.0,
    "massivebooks.copycost.20": 20.0,
    "massivebooks.copycost.30": 30.0,
    "massivebooks.copycost.default": 0.0
  },

  // Should books with a serverbook title be auto-updated to match the saved serverbook content?
  "autoupdatingServerbooks": true,
  // Should book item display names be auto-updated (title, author, powertool state)?
  "autoupdatingDisplayNames": true,
  // Use the author's display name instead of regular name in book display (only known for online players).
  "usingAuthorDisplayName": false,
  // When true, server books and other typed books show their type as an extra lore line when updated.
  "showBookTypeAsLore": true,

  // Item frame: when can players load a book from a frame by clicking? (sneaking vs not sneaking)
  "itemFrameLoadIfSneakTrue": false,
  "itemFrameLoadIfSneakFalse": true,
  // Item frame: when to show the book's display name on the frame? (sneaking vs not sneaking)
  "itemFrameDisplaynameIfSneakTrue": false,
  "itemFrameDisplaynameIfSneakFalse": true,
  // Item frame: when can players rotate the item in the frame by right-clicking? (sneaking vs not sneaking)
  "itemFrameRotateIfSneakTrue": true,
  "itemFrameRotateIfSneakFalse": true,

  // When true, /book give run from console does not send a message to the player (e.g. "@console gave you ...").
  "suppressGiveMessageFromConsole": false
}
```

## Integrations

MassiveBooks supports built-in integrations with external plugins. See the dedicated pages for setup and details:

- **[Integrations Overview](integrations/index.md)** - Summary of supported integrations and getting help.
- **[PlaceholderAPI](integrations/placeholderapi.md)** - Using PlaceholderAPI placeholders in book content (title, author, pages); resolved for the viewer when they read or receive the book.
- **[Economy Plugins](integrations/economy.md)** - Vault-based economy for copy cost: charge players when they use `/book copy`, configured via permissions and `permToCopyCost`.

## Troubleshooting

### Books or commands not working

- Ensure **MassiveCore** is installed and up to date.
- Check that the player has **`massivebooks.book`** and the specific subcommand permission (e.g. `massivebooks.unlock`, `massivebooks.load`).
- Confirm the player is holding the correct book when running the command.

### Serverbooks not updating

- Ensure **`autoupdatingServerbooks`** is true in config.
- The book’s **title** must match the serverbook name exactly.
- Remind staff to use **`/book autoupdate off`** while editing a serverbook, then save, then turn autoupdate back on if desired.

### Copy cost not charging

- Install **Vault** and an economy plugin.
- Configure **`permToCopyCost`** so at least one permission maps to a cost (or 0). The player must have one of those permissions for the cost to apply.

### Getting help

- Check the server console for errors when using book commands.
- Verify config JSON is valid (no comments, trailing commas, or syntax errors).
- Open an issue on the project repository with server version, plugin version, and steps to reproduce.
