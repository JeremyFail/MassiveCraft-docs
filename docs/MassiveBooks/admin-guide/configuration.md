![MassiveBooks Logo](../img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }

# Configuration

This page covers serverbooks, item frames, powertools, the main config file, and color codes.

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

## Main configuration file

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

  // Book colors - translate ampersand color codes in book titles, authors, and pages if true
  "translateColorCodesInBookTitles": true,
  "translateColorCodesInBookAuthors": true,
  "translateColorCodesInBookPages": true,
	
  // Removes all color codes from book titles, authors, and pages if true.
  // Applied after translateColorCodesInBook* options, so color codes will be 
  // stripped even if translation is enabled.
  "stripColorFromBooks": false;

  // When true, /book give run from console does not send a message to the player (e.g. "@console gave you ...").
  "suppressGiveMessageFromConsole": false
}
```

## Color codes

In vanilla Minecraft, colored text in written books has traditionally used the **section symbol** (`§`) plus a character (e.g. `§a` for green). **Since Minecraft 1.21.6**, the section symbol can no longer be entered in book and quill or written book text without client-side mods, so players cannot type `§` in the book UI to add colors.

MassiveBooks adds support for **parsing of alternate color codes** so that colored books still work (if enabled using the `translateColorCodes` settings):

- **Format** - Use the **ampersand** (`&`) instead of the section symbol. Standard Minecraft color codes apply: `&0` through `&9`, `&a` through `&f`, and formatting codes such as `&l` (bold), `&o` (italic), `&n` (underline), `&m` (strikethrough), `&k` (obfuscated), `&r` (reset).
- **When parsing happens** - When a player **signs** a book (clicks "Sign" in the book and quill), MassiveBooks runs its color-code parser on the title, author, and every page (if enabled in the config). Any `&` codes are converted into the proper colors/formatting so that the signed book displays in color/with formats.
- **Unlocking** - When a signed book is unlocked for editing, the plugin converts the formatted text back to `&` codes so the player can see and edit `&a`, `&b`, etc. in the book and quill again.
- **Titles** - The `/book title` command accepts color codes. Players need the **`massivebooks.title.color`** permission to use `&` codes in the title; otherwise they can still set a plain title.

So authors should write `&a`, `&b`, `&c`, and so on in their book and quill. When they sign the book, MassiveBooks applies the colors to the signed book. This works on all supported server versions, including 1.21.6 and later where vanilla no longer allows typing the section symbol in books.

For a better experience (to see color codes live), we recommend using client-side mods such as [Scribble](https://modrinth.com/mod/scribble).
