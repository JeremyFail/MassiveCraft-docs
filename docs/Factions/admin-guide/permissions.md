![Factions3 Logo](../img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }

# Permissions

Below is a list of all permission nodes that must be assigned in order for a player to use the corresponding faction commands. Note that this only gives them overall server permission to run the command (meaning they can type it into the chat). Even if they have that permission, some commands also require permission _within their faction_ to actually use that command, as some commands are still limited to only specific ranks within the faction.

## General Player Permissions

### Core Commands
| Permission Node | Description |
|-----------------|-------------|
| `factions.basecommand` | Use main factions command |
| `factions.create` | Create new faction |
| `factions.join` | Join faction |
| `factions.join.others` | Have another player join faction |
| `factions.leave` | Leave your faction |
| `factions.list` | List all factions |
| `factions.faction` | Show faction information |
| `factions.player` | Show player information |
| `factions.status` | Show status |
| `factions.documentation` | Show documentation |
| <span class="indent-1">`factions.documentation.flags`</span> | Show flag documentation |
| <span class="indent-1">`factions.documentation.power`</span> | Show power documentation |
| <span class="indent-1">`factions.documentation.perms`</span> | Show perms documentation |
| <span class="indent-1">`factions.documentation.ranks`</span> | Show rank documentation |
| <span class="indent-1">`factions.documentation.tax`</span> | Show tax documentation |
| <span class="indent-1">`factions.documentation.warps`</span> | Show warp documentation |
| `factions.expansions` | List expansions |
| `factions.version` | See plugin version |

### Faction Management
| Permission Node | Description |
|-----------------|-------------|
| `factions.name` | Set faction name |
| `factions.color` | Manage faction colors |
| <span class="perm-indent-1">`factions.color.set`</span> | Set faction colors |
| <span class="perm-indent-2">`factions.color.set.primary`</span> | Set primary faction color |
| <span class="perm-indent-2">`factions.color.set.secondary`</span> | Set secondary faction color |
| <span class="perm-indent-1">`factions.color.show`</span> | Show faction colors |
| <span class="perm-indent-2">`factions.color.show.primary`</span> | Show primary faction color |
| <span class="perm-indent-2">`factions.color.show.secondary`</span> | Show secondary faction color |
| `factions.description` | Change faction description |
| `factions.motd` | Faction motd |
| `factions.open` | Set if invitation is required to join |
| `factions.disband` | Disband faction |

### Member Management
| Permission Node | Description |
|-----------------|-------------|
| `factions.invite` | Manage invites |
| <span class="perm-indent-1">`factions.invite.list`</span> | List invited players |
| <span class="perm-indent-2">`factions.invite.list.other`</span> | List invited players of another faction |
| <span class="perm-indent-1">`factions.invite.add`</span> | Invite player |
| <span class="perm-indent-1">`factions.invite.remove`</span> | Revoke an invite |
| `factions.kick` | Kick player from faction |
| `factions.title` | Set player title |
| <span class="perm-indent-1">`factions.title.color`</span> | Set player title with color |

### Rank Management
| Permission Node | Description |
|-----------------|-------------|
| `factions.rank` | Manage/show ranks |
| <span class="indent-1">`factions.rank.show`</span> | Show rank |
| <span class="indent-1">`factions.rank.set`</span> | Set rank |
| <span class="indent-1">`factions.rank.list`</span> | List ranks |
| <span class="indent-1">`factions.rank.edit`</span> | Edit ranks |
| <span class="indent-2">`factions.rank.edit.create`</span> | Create rank |
| <span class="indent-2">`factions.rank.edit.name`</span> | Set rank name |
| <span class="indent-2">`factions.rank.edit.prefix`</span> | Set rank prefix |
| <span class="indent-2">`factions.rank.edit.priority`</span> | Set rank priority |
| <span class="indent-2">`factions.rank.edit.delete`</span> | Delete rank |

### Territory Management
| Permission Node | Description |
|-----------------|-------------|
| `factions.claim` | Claim faction territory |
| <span class="indent-1">`factions.claim.one`</span> | Claim a single chunk |
| <span class="indent-1">`factions.claim.auto`</span> | Claim as you walk around |
| <span class="indent-1">`factions.claim.fill`</span> | Claim by filling |
| <span class="indent-1">`factions.claim.square`</span> | Claim by square and radius |
| <span class="indent-1">`factions.claim.circle`</span> | Claim by circle and radius |
| <span class="indent-1">`factions.claim.all`</span> | Claim all faction land |
| `factions.unclaim` | Unclaim faction territory |
| <span class="indent-1">`factions.unclaim.one`</span> | Unclaim a single chunk |
| <span class="indent-1">`factions.unclaim.auto`</span> | Unclaim as you walk around |
| <span class="indent-1">`factions.unclaim.fill`</span> | Unclaim by filling |
| <span class="indent-1">`factions.unclaim.square`</span> | Unclaim by square and radius |
| <span class="indent-1">`factions.unclaim.circle`</span> | Unclaim by circle and radius |
| <span class="indent-1">`factions.unclaim.all`</span> | Unclaim all faction land |
| `factions.map` | Show territory map |
| `factions.seechunk` | See the chunk you stand in |
| `factions.territorytitles` | Toggle territory titles |
| `factions.chunkname` | Set chunk name |

### Access and Permissions
| Permission Node | Description |
|-----------------|-------------|
| `factions.access` | Manage faction access (if the player also has permission within the faction) |
| <span class="indent-1">`factions.access.deny`</span> | Deny faction access |
| <span class="indent-2">`factions.access.deny.one`</span> | Deny access in a single chunk |
| <span class="indent-2">`factions.access.deny.fill`</span> | Deny access by filling |
| <span class="indent-2">`factions.access.deny.square`</span> | Deny access by square and radius |
| <span class="indent-2">`factions.access.deny.circle`</span> | Deny access by circle and radius |
| <span class="indent-1">`factions.access.grant`</span> | Grant faction access |
| <span class="indent-2">`factions.access.grant.one`</span> | Grant access in a single chunk |
| <span class="indent-2">`factions.access.grant.fill`</span> | Grant access by filling |
| <span class="indent-2">`factions.access.grant.square`</span> | Grant access by square and radius |
| <span class="indent-2">`factions.access.grant.circle`</span> | Grant access by circle and radius |
| <span class="indent-1">`factions.access.inspect`</span> | Inspect where someone has access |
| <span class="indent-1">`factions.access.view`</span> | View access |
| `factions.perm` | Change faction permissions |
| <span class="indent-1">`factions.perm.list`</span> | List perms |
| <span class="indent-1">`factions.perm.set`</span> | Set perms |
| <span class="indent-1">`factions.perm.inspect`</span> | Inspect who has perm (and where it comes from) |
| <span class="indent-1">`factions.perm.view`</span> | View perms given to |
| <span class="indent-1">`factions.perm.viewall`</span> | View all perms held by |
| <span class="indent-1">`factions.perm.manage`</span> | Manage perms (using manage perms table) |
| <span class="indent-1">`factions.perm.manage.bypass`</span> | Manage perms for any faction (bypassing permission requirements) |

### Flags and Relations
| Permission Node | Description |
|-----------------|-------------|
| `factions.flag` | Manage faction flags |
| <span class="indent-1">`factions.flag.list`</span> | List flags |
| <span class="indent-1">`factions.flag.set`</span> | Set flags |
| <span class="indent-1">`factions.flag.show`</span> | Show flags |
| `factions.relation` | Manage faction relations |
| <span class="indent-1">`factions.relation.list`</span> | List all factions with certain relation |
| <span class="indent-1">`factions.relation.set`</span> | Set relation wish to another faction |
| <span class="indent-1">`factions.relation.wishes`</span> | List the relation wishes |

### Warps and Travel
| Permission Node | Description |
|-----------------|-------------|
| `factions.warp` | Use warps |
| <span class="indent-1">`factions.warp.go`</span> | Go to a warp |
| <span class="indent-1">`factions.warp.list`</span> | List warps |
| <span class="indent-1">`factions.warp.add`</span> | Add new warp |
| <span class="indent-1">`factions.warp.remove`</span> | Remove warp |
| `factions.fly` | Faction fly |
| <span class="indent-1">`factions.fly.other`</span> | Set faction fly for others |
| `factions.unstuck` | Teleport to nearest wilderness |

### Economy
| Permission Node | Description |
|-----------------|-------------|
| `factions.money` | Manage faction money |
| <span class="indent-1">`factions.money.balance`</span> | Show faction money |
| <span class="indent-1">`factions.money.balance.any`</span> | Show another faction's money |
| <span class="indent-1">`factions.money.deposit`</span> | Deposit to faction |
| <span class="indent-1">`factions.money.f2f`</span> | Transfer f --> f |
| <span class="indent-1">`factions.money.f2p`</span> | Transfer f --> p |
| <span class="indent-1">`factions.money.p2f`</span> | Transfer p --> f |
| <span class="indent-1">`factions.money.withdraw`</span> | Withdraw from faction |

### Taxes and Voting
| Permission Node | Description |
|-----------------|-------------|
| `factions.tax` | Manage taxes |
| <span class="indent-1">`factions.tax.faction`</span> | Show faction tax |
| <span class="indent-1">`factions.tax.player`</span> | Show player tax |
| <span class="indent-1">`factions.tax.run`</span> | Run a tax collection |
| <span class="indent-1">`factions.tax.set`</span> | Set taxes |
| `factions.vote` | Vote in faction votes |
| <span class="indent-1">`factions.vote.do`</span> | Do vote |
| <span class="indent-1">`factions.vote.list`</span> | List votes |
| <span class="indent-1">`factions.vote.show`</span> | Show vote result |
| <span class="indent-1">`factions.vote.create`</span> | Create a vote |
| <span class="indent-1">`factions.vote.remove`</span> | Remove a vote |

### Information
| Permission Node | Description |
|-----------------|-------------|
| `factions.top` | Show faction top |
| `factions.config` | Edit the factions config |

## Server Operator/Admin Permissions

### Administrative Override
| Permission Node | Description |
|-----------------|-------------|
| `factions.override` | Enable admin override mode |

### Database Management
| Permission Node | Description |
|-----------------|-------------|
| `factions.clean` | Clean the factions database |
| `factions.moneyconvert` | Convert to the new money system |

### Power Management
| Permission Node | Description |
|-----------------|-------------|
| `factions.powerboost` | Manage powerboosts |
| <span class="indent-1">`factions.powerboost.faction`</span> | Manage faction powerboost |
| <span class="indent-2">`factions.powerboost.faction.add`</span> | Add faction powerboost |
| <span class="indent-2">`factions.powerboost.faction.multiply`</span> | Multiply faction powerboost |
| <span class="indent-2">`factions.powerboost.faction.set`</span> | Set faction powerboost |
| <span class="indent-2">`factions.powerboost.faction.show`</span> | Show faction powerboost |
| <span class="indent-2">`factions.powerboost.faction.take`</span> | Take faction powerboost |
| <span class="indent-1">`factions.powerboost.player`</span> | Manage player powerboosts |
| <span class="indent-2">`factions.powerboost.player.add`</span> | Add player powerboost |
| <span class="indent-2">`factions.powerboost.player.multiply`</span> | Multiply player powerboost |
| <span class="indent-2">`factions.powerboost.player.set`</span> | Set player powerboost |
| <span class="indent-2">`factions.powerboost.player.show`</span> | Display player powerboost |
| <span class="indent-2">`factions.powerboost.player.take`</span> | Take player powerboost |
| `factions.setpower` | Set a faction or player's power |

## Default Permission Inheritance

Most permissions follow a hierarchical structure where having a parent permission grants all child permissions. For example:

- `factions.claim` grants all `factions.claim.*` permissions
- `factions.rank` grants all `factions.rank.*` permissions  
- `factions.money` grants all `factions.money.*` permissions

## Special Permission Notes

### WorldGuard Integration
- `factions.allowregionclaim.{regionId}`: Allow claiming in specific WorldGuard regions

### Bypass Permissions
- Some permissions may have bypass variants for special cases
- Admin override mode bypasses most faction-level restrictions
