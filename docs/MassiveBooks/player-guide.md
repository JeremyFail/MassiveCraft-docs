![MassiveBooks Logo](img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }

# Player Guide

This guide covers how to use MassiveBooks as a player. All commands operate on the book you are holding.

!!! info "Note"
    The command aliases (e.g. `/book` vs `/books`) and available features can be changed by your server. Ask an administrator if something doesn't match this guide.

## Commands Overview

Commands are used with the base command `/book` or `/books` (depending on server config). You must be holding the relevant book in your hand.

## For Regular Players

- **`/book unlock`**  
  Unlock a book that has been signed/locked so you can edit its content again.

- **`/book lock`**  
  Lock the book and keep the current title and author. Often used on an unlocked book so you don't have to retype the title.

- **`/book clear`**  
  Clear the book completely. It becomes an empty book and quill; title, author, and content are removed.

- **`/book title <title>`**  
  Set a new title. Color codes may be allowed if the server enables it (permission `massivebooks.title.color`).

- **`/book copy [times=1]`**  
  Create copies of the book. In survival, you need the required materials (and possibly economy cost if the server uses Vault).

- **`/book list [page=1]`**  
  List serverbooks available on the server (if your server uses them).

- **`/book load <title>`**  
  Load a serverbook by title into the book you're holding. Existing content in that book will be overwritten.

- **`/book cr` or `/book copyrighted [true|false|toggle]`**  
  Toggle whether the book is copyrighted. Copyrighted books can only be copied by the author (unless someone has copy-copyrighted permission). Only the book in your hand is changed; existing copies are not updated unless it's a serverbook.

- **`/book v` or `/book version`**  
  Show plugin version and related info.

## Better Item Display Names

MassiveBooks improves how books appear in your inventory:

- **Signed books** - The item name can show the book title and author.
- **Unlocked books** - Unlocked (editable) books can show title and author so you can tell them apart from empty or signed books.
- **Powertools** - Books that are powertools can get a distinct prefix (e.g. purple) so you can tell them from normal books.

This makes it easier to manage many books and to see what each one is without opening it.

## Serverbooks, item frames, and powertools

If your server uses them:

- **Serverbooks** - Books saved on the server. Use `/book list` to see them and `/book load <title>` to load one into the book you're holding. Saving and managing serverbooks is done by staff; see the Admin Guide.
- **Item frame libraries** - You can place books in item frames and, with a book and quill, click the frame to load or unload the book. Exact behavior is configured by your server; see the Admin Guide.
- **Powertools** - Some books are set up so that using them runs commands or sends chat. How they're created and what placeholders they support is documented in the Admin Guide.
