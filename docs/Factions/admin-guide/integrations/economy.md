![Factions3 Logo](../../img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }

# Economy Integration

Factions provides comprehensive economy integration through [Vault](https://www.spigotmc.org/resources/vault.34315/) and economy plugins that hook into Vault, allowing you to add costs to faction actions, implement faction banks, and create economic gameplay mechanics around territorial control and faction management.

## Requirements

- **Vault Plugin** - Required for economy integration
- **Economy Plugin** - Any Vault-compatible economy plugin

## Features

### Faction Banking System
- **Faction Banks** - Shared money storage for faction members
- **Deposits/Withdrawals** - Members can contribute to and withdraw from faction funds
- **Bank Permissions** - Control who can deposit/withdraw via faction ranks
- **Inter-Faction Transfers** - Send money between factions
- **Transaction Logging** - Track all money movements

### Action Costs
- **Creation Costs** - Charge for creating new factions
- **Claiming Costs** - Set prices per chunk claimed
- **Warp Costs** - Charge for setting/using faction warps
- **Relation Costs** - Set costs for changing faction relationships
- **Command Costs** - Add costs to various faction commands

### Economy-Based Gameplay
- **Territory Economics** - Different costs for different claim types
- **Faction Maintenance** - Optional recurring costs through tax system
- **Economic Warfare** - Financial strategies in faction conflicts

## Configuration

### Basic Economy Settings

```javascript
{
  // Enable economy features (requires Vault)
  "econEnabled": true,
  
  // Account to receive money (empty = money destroyed)
  "econUniverseAccount": "",
  
  // Should faction bank pay costs instead of individual players?
  "bankFactionPaysCosts": true,
  
  // Enable faction banking system
  "bankEnabled": true
}
```

### Claiming Costs

```javascript
{
  // What is the price per chunk when using /f set?
  "econChunkCost": {
    "BUY": 1.0,      // Cost when claiming from wilderness
    "SELL": 0.0,     // Refund when selling back to wilderness  
    "CONQUER": 0.0,  // Cost when claiming from another faction
    "PILLAGE": 0.0   // Cost when unclaiming from another faction
  }
}
```

### Faction Action Costs

```javascript
{
  // Basic faction operations
  "econCostCreate": 100.0,           // Creating a faction
  "econCostJoin": 0.0,               // Joining a faction
  "econCostLeave": 0.0,              // Leaving a faction
  "econCostKick": 0.0,               // Kicking a member
  "econCostInvite": 0.0,             // Inviting a player
  "econCostDeinvite": 0.0,           // Removing an invite
  
  // Faction customization
  "econCostName": 0.0,               // Changing faction name
  "econCostDescription": 0.0,        // Changing description
  "econCostTitle": 0.0,              // Setting player titles
  "econCostFlag": 0.0,               // Changing faction flags
  
  // Warps and travel
  "econCostWarpAdd": 0.0,            // Creating a warp
  "econCostWarpRemove": 0.0,         // Removing a warp
  "econCostWarpGo": 0.0,             // Using a warp
  
  // Relationships
  "econRelCost": {
    "ENEMY": 0.0,                    // Declaring war
    "ALLY": 0.0,                     // Forming alliance
    "TRUCE": 0.0,                    // Making truce
    "NEUTRAL": 0.0                   // Returning to neutral
  }
}
```

## Faction Banking

### Basic Commands

```yaml
# Check faction bank balance
/f money balance

# Deposit money to faction bank
/f money deposit <amount>

# Withdraw money from faction bank
/f money withdraw <amount>

# Transfer between factions
/f money ff <amount> <fromFaction> <toFaction>

# Transfer faction to player
/f money fp <amount> <faction> <player>

# Transfer player to faction  
/f money pf <amount> <player> <faction>
```

### Bank Permissions

Control banking access through default faction permissions:

```javascript
{
  "perm2default": {
    "deposit": [
      "LEADER", "OFFICER", "MEMBER", "RECRUIT",
      "ALLY", "TRUCE", "NEUTRAL", "ENEMY"  // Anyone can deposit
    ],
    "withdraw": [
      "LEADER"  // Only leaders can withdraw
    ]
  }
}
```

## Economy-Based Gameplay

### 1. Claiming Economics

**Progressive claiming costs:**
```javascript
{
  "econChunkCost": {
    "BUY": 10.0,     // Each claim costs $10
    "SELL": 5.0,     // Refund $5 when unclaiming
    "CONQUER": 20.0, // Conquering enemy land costs $20
    "PILLAGE": 0.0   // Pillaging is free
  }
}
```

**Economic warfare mechanics:**
- Expensive conquering encourages strategic claiming
- Sell refunds make temporary claiming viable
- Free pillaging rewards successful attacks

### 2. Faction Maintenance

**Creation barriers:**
```javascript
{
  "econCostCreate": 1000.0  // High cost prevents faction spam
}
```

**Relationship costs:**
```javascript
{
  "econRelCost": {
    "ENEMY": 500.0,   // Declaring war costs money
    "ALLY": 200.0,    // Alliances require investment
    "TRUCE": 100.0,   // Truces cost less
    "NEUTRAL": 0.0    // Free to go neutral
  }
}
```

### 3. Warp Economics

```javascript
{
  "econCostWarpAdd": 100.0,    // Creating warps costs money
  "econCostWarpRemove": 0.0,   // Removing is free
  "econCostWarpGo": 5.0        // Each warp use has a cost
}
```

### 4. Administrative Costs

```javascript
{
  "econCostName": 50.0,        // Changing name costs money
  "econCostDescription": 25.0, // Updating description
  "econCostTitle": 10.0,       // Setting member titles
  "econCostFlag": 20.0         // Changing faction settings
}
```

## Troubleshooting

### Common Issues

**Economy not working:**
- Verify Vault is installed and running
- Check that economy plugin is Vault-compatible
- Ensure `econEnabled` is `true`
- Test with `/vault-info` command

**Faction bank errors:**
- Verify `bankEnabled` is `true`
- Check faction permissions for deposit/withdraw
- Ensure players have sufficient personal funds for deposits
- Test with `/f money balance`

**Costs not being charged:**
- Verify specific cost settings are greater than 0
- Check `bankFactionPaysCosts` setting
- Ensure faction has sufficient funds if using faction bank
- Test with admin account to rule out permission issues

### Debug Commands

**Test economy integration:**
```yaml
# Check Vault status
/vault-info

# Test basic economy (commands may vary based on installed economy plugin)
/money
/pay <player> <amount>

# Test faction banking
/f money balance
/f money deposit 1
```

**Check configurations:**
```yaml
# View current settings
/f config econEnabled
/f config bankEnabled
/f config econCostCreate
```

### Performance Considerations

**Thread Safety:**
- Ensure economy plugin is thread-safe
- Monitor console for warnings
- Consider disabling money display in Dynmap if issues occur (see the [Dynmap Integration Configuration](dynmap.md) for more details)

## Migration Guide

### From Non-Economy Setup

1. **Install Vault and economy plugin**
2. **Test basic economy functionality**
3. **Enable Factions economy integration**
4. **Configure costs gradually**
5. **Communicate changes to players**

### Changing Economy Plugins

1. **Backup all economy data**
2. **Export faction bank balances**
3. **Install new economy plugin**
4. **Import/recreate economy data**
5. **Test integration thoroughly**
