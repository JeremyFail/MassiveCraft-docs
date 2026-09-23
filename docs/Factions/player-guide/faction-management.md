![Factions3 Logo](../img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }

# Faction Management

This guide covers everything you need to know about managing your faction, from basic settings to advanced territory management and economic systems.

## Managing Your Faction

### Faction Information

**Set your faction's description:**
```
/f description <desc>
```

**Set or view the Message of the Day (MOTD):**
```
/f motd [new message]
```

**Change your faction's name:**
```
/f name <new name>
```

**Disband your faction:**
```
/f disband
```

!!! warning "Warning"

    This permanently deletes the faction!

### Inviting Members

**Invite a player:**
```
/f invite add <player>
```

**View pending invites:**
```
/f invite list
```

**Remove an invite:**
```
/f invite remove <player>
```

**Kick a member:**
```
/f kick <player>
```

### Ranks and Titles

Factions have a rank system that determines what members can do.

**Set a player's rank:**
```
/f rank set <player> <rank>
```

**View ranks:**
```
/f rank list
```

**Set a player's title (cosmetic):**
```
/f title <player> <title>
```

## Territory Management

### Claiming Strategies

**Single claim:** Stand in a chunk and use `/f claim`

**Auto-claim:** Walk around and automatically claim chunks:
```
/f claim auto
```

**Claim patterns:**

- `/f claim fill` - Fill in unclaimed chunks within your territory
- `/f claim square <radius>` - Claim a square area
- `/f claim circle <radius>` - Claim a circular area

### Unclaiming

Similar commands exist for unclaiming:

- `/f unclaim` - Unclaim single chunk
- `/f unclaim auto` - Auto-unclaim as you walk
- `/f unclaim fill` - Unclaim pattern
- `/f unclaim all` - Unclaim all territory

### Home and Warps

**Set your faction home:**
```
/f sethome
```

**Teleport to faction home:**
```
/f home
```

**Create faction warps:**
```
/f warp add <name>
```

**List warps:**
```
/f warp list
```

**Use a warp:**
```
/f warp go <warp>
```

**Remove a warp:**
```
/f warp remove <warp>
```

## Permissions and Access

### Faction Permissions

Factions have a detailed permission system that controls what different ranks and relations can do in your territory.

**View permissions:**
```
/f perm list
```

**Manage permissions:**
```
/f perm manage
```

**Set permissions:**
```
/f perm set
```

**View flags:**
```
/f flag list
```

**Set flags:**
```
/f flag set
```

### Territory Access

You can grant or deny specific players access to specific chunks:

**Grant access:**
```
/f access grant <player>
```

**Deny access:**
```
/f access deny <player>
```

**View access:**
```
/f access view
```

## Economy

If your server has economy integration enabled, factions can have banks.

**View faction balance:**
```
/f money balance
```

**Deposit money:**
```
/f money deposit <amount>
```

**Withdraw money:**
```
/f money withdraw <amount>
```

**Transfer between factions:**
```
/f money ff <amount> <faction> <faction>
```

**Transfer from faction to player:**
```
/f money fp <amount> <faction> <player>
```

**Transfer from player to faction:**
```
/f money pf <amount> <player> <faction>
```

## Best Practices

### Territory Management

1. **Always claim before building** - unclaimed builds can be destroyed
2. **Build away from chunk borders** to avoid edge cases
3. **Use `/f seechunk`** to visualize chunk boundaries
4. **Create a buffer zone** of claimed chunks around your base
5. **Don't build too close to enemies** unless prepared for war
6. **Plan your claims strategically** - quality over quantity
7. **Monitor your power** to ensure you can maintain your claims

### Faction Leadership

1. **Set clear rules** for your faction members
2. **Use the MOTD** to communicate important information
3. **Manage permissions** carefully to prevent griefing
4. **Maintain good relationships** with potential allies
5. **Set up a faction home** in a secure location
6. **Create warps** for important locations like farms, storage, or gathering points
7. **Monitor your power** regularly with `/f status`
8. **Keep the faction bank well-funded** for emergencies

### Permission Management

1. **Start restrictive** - it's easier to grant permissions than revoke them
2. **Use ranks effectively** - create a hierarchy that reflects trust levels
3. **Test permissions** in a safe area before applying them widely
4. **Document your permission setup** in the faction MOTD or description
5. **Review permissions regularly** as your faction grows
6. **Use territory access** for sensitive areas like storage rooms

### Economic Strategy

1. **Establish a faction tax system** if your server supports it
2. **Keep a reserve** in the faction bank for emergencies
3. **Invest in territory** - claimed land is a valuable asset
4. **Trade with allied factions** for mutual benefit
5. **Use the faction bank** for shared resources and projects

## Related Guides

- **[Player Guide Overview](index.md)** - Return to the main player guide
- **[Strategy & Tips](strategy-tips.md)** - Master raiding, defending, and get tips for becoming a dominant faction
