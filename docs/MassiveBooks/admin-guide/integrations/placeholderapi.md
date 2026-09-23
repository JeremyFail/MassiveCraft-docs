![MassiveBooks Logo](../../img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }
![PlaceholderAPI Logo](img/placeholderapi.png){ style="display: block; margin: 10px auto; max-height: 115px;" }

# PlaceholderAPI Integration

MassiveBooks integrates with [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/) so that **book content** (title, author, and page text) can contain placeholders. When a player views, receives, or reads a book, those placeholders are resolved **for that player** (the viewer). MassiveBooks does **not** register its own placeholders; it uses PlaceholderAPI to parse placeholders that are already stored in the book.

!!! info "Note"

    For more information about PlaceholderAPI, visit their plugin listing page or [Wiki](https://wiki.placeholderapi.com/).

## How It Works

- **When writing books** - Placeholders are stored **as text** in the book (e.g. `%player_name%`). They are not resolved when the book is signed or saved.
- **When viewing books** - When a player opens a book, receives a book (e.g. via `/book give` or `/book load`), or the book is updated for them, MassiveBooks asks PlaceholderAPI to resolve all placeholders in the title, author, and pages using that player as the **viewer** (context).
- **Result** - Each reader sees their own values. For example, a book page containing `Hello, %player_name%!` shows the reader’s name when they open it.

## Relational Placeholders

PlaceholderAPI’s **relational placeholders** (e.g. comparing two players) are supported. When the **author** of the book is online, relational placeholders use **(viewer, author)**: the first player is the one viewing the book, the second is the book’s author. If the author is offline, only normal placeholders are resolved; relational placeholders may show as empty or unchanged depending on PlaceholderAPI.

## Installation

1. Install [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/) on your server.
2. Install MassiveBooks (and its dependency, MassiveCore).
3. No extra configuration is required in MassiveBooks; the integration is automatic when PlaceholderAPI is present.

After both plugins are installed, any placeholder that works in PlaceholderAPI can be used inside book text and will be resolved for the viewer when they see the book.

## Usage Examples

- **Player-specific text** - In a book page: `Welcome, %player_name%!` or `You have %vault_balance% money.` (if you use the Vault placeholder expansion).
- **Serverbooks** - Save a serverbook whose pages contain placeholders; when players load or receive that book, they will see the placeholders resolved for themselves.
- **Any expansion** - Install PlaceholderAPI expansions (e.g. for Factions, Vault, or other plugins) and use their placeholders in books the same way.

Placeholders use the standard PlaceholderAPI format with percent signs, e.g. `%placeholder_name%`.

## Troubleshooting

### Placeholders show as raw text (e.g. `%player_name%`)

- Ensure **PlaceholderAPI** is installed and loads before or with MassiveBooks.
- Ensure the placeholder is valid and the expansion that provides it is installed (e.g. for `%player_name%`, PlaceholderAPI’s built-in placeholders are always available). You can use the `/papi parse` command to test that a specific placeholder is valid.
- Check the server console for PlaceholderAPI or MassiveBooks errors.

### Placeholders are blank or wrong for some players

- Normal placeholders always use the **viewer** (the player who is looking at the book). If the book is being shown in a context where there is no player viewer, placeholders may not resolve as expected.
- Relational placeholders require the **author** to be online to resolve as (viewer, author). If the author is offline, relational placeholders may not resolve.

### Books don’t update when I change placeholder content

- Placeholders are resolved when the book is **viewed, loaded, or given**. If a player is already holding a copy of a serverbook, they may need to load it again (or receive an updated copy) to see new placeholder values. Serverbook autoupdate will refresh content when the book is updated for the player.
