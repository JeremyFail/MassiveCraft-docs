![MassiveBooks Logo](img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }

# Welcome to MassiveBooks

MassiveBooks is a book-focused plugin for Minecraft Spigot/Paper servers. It adds better display names for books, copying and unlocking books, server-saved books, in-game libraries using item frames, and powertools (books that run commands or say messages when used).

## What is MassiveBooks?

MassiveBooks extends how written books and book and quills work on your server. Players can unlock and edit signed books, copy books (with optional economy costs), manage serverbooks that auto-update for all holders, and use item frames as in-game libraries. Moderators can save and give serverbooks, and powertools let books execute commands or chat when used.

## Key Features

- **Better display names** - Book and quill items show title and author in the item name; unlocked books and powertools are clearly labeled.
- **Unlock and lock** - Unlock signed books to edit them again; lock books while keeping title and author.
- **Serverbooks** - Save books on the server; all copies with the same title stay in sync when you update the serverbook.
- **Item frame libraries** - Place books in item frames; click with a book and quill to load the framed book, click again to unload.
- **Powertools** - Turn books into tools that run commands or send chat when used; supports placeholders for player and target.
- **Copyright** - Mark books as copyrighted so only the author can copy them (others need special permission).
- **Admin control** - Permissions, configurable copy costs (with Vault), new-player commands, and more.

## Quick Start

=== "For players"
    1. Hold a book and quill or written book.
    2. Use `/book` (or `/books`) with subcommands like `unlock`, `lock`, `clear`, `title`, `copy`, `list`, `load`.
    3. Put books in item frames to build libraries; click with a book and quill to load/unload.

=== "For admins"
    1. Install [MassiveCore](https://factions.wiki/MassiveCore/) (required).
    2. Install the MassiveBooks plugin.
    3. Configure permissions.
    4. (Optionally) Edit the configuration.

## Documentation Sections

Use the navigation menu to explore:

- **[Player Guide](player-guide.md)** - Commands and features for regular players (unlock, lock, copy, serverbooks, item frames, powertools).
- **[Admin Guide](admin-guide)** - Commands, permissions, configuration, and troubleshooting.

## Requirements

- **Server software:** Spigot or Paper
- **Dependencies:** MassiveCore
- **Permissions:** By default, no book commands are granted; configure as needed (see Admin Guide).

## Credits

[![License: MIT](https://img.shields.io/badge/License-MIT-7c4dff.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

Continuation of [MassiveBooks](https://www.spigotmc.org/resources/massivebooks.1907/) by MassiveCraft, updated to support modern Minecraft versions.