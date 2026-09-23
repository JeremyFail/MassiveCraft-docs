![MassiveBooks Logo](../img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }

# Commands

All book commands operate on the book the player is holding. The base command is typically `/book` or `/books` (configurable via `aliasesBook` in the config).

| Command | Description | Permission |
|---------|-------------|-------------|
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

There are separate permissions for acting on **another author's book** (e.g. unlock, lock, clear, title, author, copy, powertool, copyrighted). For example: `massivebooks.unlock.other`, `massivebooks.copy.copyrighted`. See [Permissions](permissions.md) for the full list.
