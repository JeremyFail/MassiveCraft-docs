![Factions3 Logo](../img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }

# Commands

Below is a list of all the currently available Factions commands.

## Basic Commands

| Command | Description |
|---------|-------------|
| `/f ?,h,help [page=1]` | Lists all factions commands in-game |
| `/f list [page=1]` | Lists all factions |
| `/f f,faction [faction=you]` | Displays faction information |
| `/f player [player=you]` | Displays player information |
| `/f status [page=1] [faction=you] [sort=time]` | Display faction status |
| `/f join <faction>` | Join a faction |
| `/f leave` | Leave your current faction |

## Faction Management

| Command | Description |
|---------|-------------|
| `/f create,new <name>` | Create a new faction |
| `/f name <new name> [faction=you]` | Set your faction's name |
| `/f description <desc>` | Change your faction's description |
| `/f motd [new=read]` | See the faction motd (message of the day) |
| `/f disband [faction=you]` | Disband a faction |
| `/f color <primary|secondary> <color>` | Set your faction's colors |

## Territory Management

| Command | Description |
|---------|-------------|
| `/f map [on/off=once]` | Show faction territory/claims map |
| `/f claim` | Claim faction territory |
| `/f unclaim` | Unclaim faction territory |
| `/f seeChunk,sc [active=toggle]` | Display faction info about the chunk you're in |
| `/f territorytitles,tt [on|off=toggle]` | Toggle faction territory titles (when entering/leaving a faction's territory) |

## Warps and Home

| Command | Description |
|---------|-------------|
| `/f warp` | Use faction warps |
| `/f warp go <warp> [faction=you]` | Teleport to a specific faction warp |
| `/f warp list [faction=you] [page=1]` | List all faction warps |
| `/f warp add,create <name> [faction=you]` | Add a new faction warp |
| `/f warp remove <warp> [faction=you]` | Remove a faction warp |
| `/f home [faction=you]` | Teleport to your faction home warp |
| `/f sethome [faction=you]` | Set your faction home warp |
| `/f unsethome or /f delhome [faction=you]` | Unset your faction home warp |

## Member Management

| Command | Description |
|---------|-------------|
| `/f invite` | Manage faction invites |
| `/f kick` | Kick a player from your faction |
| `/f title [title=none]` | Set a player's faction title |
| `/f rank` | Manage faction ranks |
| `/f rank set <player><rank>` | Set a player's faction rank |
| `/f rank show <player>` | Display a player's faction rank |
| `/f rank list [page=1][faction=you]` | List faction ranks |
| `/f rank edit` | Edit faction ranks |
| `/f rank edit create <name> <priority> [prefix=none] [faction=you]` | Create a new faction rank |
| `/f rank edit delete <rank> [faction=you]` | Delete a faction rank |
| `/f rank edit name <rank> <new name> [faction=you]` | Set a faction rank's name |
| `/f rank edit prefix <rank> <new prefix> [faction=you]` | Set a faction rank's prefix |
| `/f rank edit priority <rank> <new priority> [faction=you]` | Set a faction rank's priority |

## Economy and Banking

| Command | Description |
|---------|-------------|
| `/f money` | Manage faction money |
| `/f money balance [faction=you]` | Display faction money |
| `/f money deposit <amount> [faction=you]` | Deposit money into the faction bank |
| `/f money withdraw <amount> [faction=you]` | Withdraw money from the faction bank |
| `/f money ff <amount> <faction> <faction>` | Transfer money between factions |
| `/f money fp <amount> <faction> <player>` | Transfer money from faction to player |
| `/f money pf <amount> <player> <faction>` | Transfer money from player to faction |

## Faction Relations and Permissions

| Command | Description |
|---------|-------------|
| `/f access` | Manage faction access |
| `/f relation` | Manage faction relations |
| `/f perm` | Manage/change faction permissions |
| `/f flag` | Manage faction flags |

## Information and Statistics

| Command | Description |
|---------|-------------|
| `/f top <Topcategory> [page=1]` | Display a list of top factions |

## Utility Commands

| Command | Description |
|---------|-------------|
| `/f unstuck` | Teleport to the nearest wilderness |

## Administrative Commands

| Command | Description |
|---------|-------------|
| `/f override,admin [on/off=flip]` | Toggle faction override/admin mode |
| `/f powerBoost` | Manage faction powerboosts |
| `/f setpower,sp` | Set a faction's power |
| `/f config` | Modify faction config |
| `/f clean` | Clean the factions database |
| `/f v,version` | Display plugin version |
