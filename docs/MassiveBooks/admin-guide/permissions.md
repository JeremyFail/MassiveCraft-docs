![MassiveBooks Logo](../img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }

# Permissions

## Player Permissions

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

## Moderator / Admin Permissions

| Node | Description |
|------|-------------|
| `massivebooks.unlock.other` | Unlock another author's book |
| `massivebooks.lock.other` | Lock another author's book |
| `massivebooks.clear.other` | Clear another author's book |
| `massivebooks.title.other` | Change title of another's book |
| `massivebooks.title.color` | Use color codes in titles |
| `massivebooks.author` | Set author on own book |
| `massivebooks.author.other` | Set author on another's book |
| `massivebooks.copy.other` | Copy another author's book |
| `massivebooks.copy.copyrighted` | Copy copyrighted books by others |
| `massivebooks.give` | Give serverbooks to players |
| `massivebooks.givesilent` | Give serverbooks silently |
| `massivebooks.save` | Save a book as serverbook |
| `massivebooks.delete` | Delete a serverbook |
| `massivebooks.autoupdate` | Change autoupdate state |
| `massivebooks.powertool` | Set powertool on own book |
| `massivebooks.powertool.other` | Set powertool on another's book |
| `massivebooks.copyrighted.other` | Set copyrighted on another's book |
| `massivebooks.config` | Edit plugin config |

## Permission Kits

The plugin defines optional "kit" parents for convenience:

- **`massivebooks.kit.default`** (default: true) - Grants `massivebooks.kit.rank0`.
- **`massivebooks.kit.rank0`** - Basic player: book, unlock, lock, clear, title, copy, list, load, copyrighted, version.
- **`massivebooks.kit.rank1`** - Adds rank0 plus moderator-style: unlock/lock/title/author/copy copyrighted/give/save/delete/autoupdate/powertool/copyrighted for others.
- **`massivebooks.kit.rank2`** - Currently no difference from rank1.
- **`massivebooks.kit.rank3`** - Includes rank2 and access to `massivebooks.config`.
- **`massivebooks.kit.op`** (default: op) - Grants `massivebooks.*` (all nodes).
