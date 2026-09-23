![Factions3 Logo](../img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }

# Configuration

Configuring Factions is **optional**. The default configuration works perfectly in most cases.

Factions can be fully configured while your server is running! Use the `/f config` command to modify main configuration values while in-game, or you can edit and save any of the configuration files. The modifications will automatically be detected and loaded into the server after a few seconds. You don't need to run any additional reload command or restart the server for the modified settings to take effect.

## Main Configuration

You can modify the main configuration settings. This configuration file is located at `/mstore/factions_mconf/instance.json`.

!!! warning "Warning"
    Comments have been added to the configuration examples below to explain the values, but these comments should **NOT** be added to your actual configuration file as it will cause errors.

### Command Aliases

```javascript
{
  // Don't you want "f" as the base command alias? Simply change it here.
  "aliasesF": [
    "f"
  ]
}
```

### World Features

Use this blacklist/whitelist system to toggle features on a per world basis.

```javascript
{
  "worldsClaimingEnabled": {
    "standard": true,
    "exceptions": []
  },
  "worldsPowerLossEnabled": {
    "standard": true,
    "exceptions": []
  },
  "worldsPowerGainEnabled": {
    "standard": true,
    "exceptions": []
  },
  "worldsPvpRulesEnabled": {
    "standard": true,
    "exceptions": []
  }
}
```

### Player Management

```javascript
{
  // Add player names here who should bypass all protections.
  // Should /not/ be used for admins. There is "/f admin" for that.
  "playersWhoBypassAllProtection": [],
  
  // Should players be kicked from their faction and their data erased when banned?
  "removePlayerWhenBanned": true,
  
  // After how many milliseconds should players be automatically kicked from their faction?
  "cleanInactivityToleranceMillis": 864000000, // 10 days
  
  // Which faction should new players be followers of?
  // "none" means Wilderness. Remember to specify the id, not the name.
  "defaultPlayerFactionId": "none",
  
  // What power should the player start with?
  "defaultPlayerPower": 0.0
}
```

### Power System

```javascript
{
  // What is the maximum player power?
  "powerMax": 10.0,
  
  // What is the minimum player power?
  "powerMin": 0.0,
  
  // How much power should be regained per hour online on the server?
  "powerPerHour": 2.0,
  
  // How much power should be lost on death?
  "powerPerDeath": -2.0,
  
  // Can players with negative power leave their faction?
  "canLeaveWithNegativePower": true
}
```

### Faction Limits

```javascript
{
  // Is there a maximum amount of members per faction?
  // 0 means there is not.
  "factionMemberLimit": 0,
  
  // Is there a maximum faction power cap?
  // 0 means there is not.
  "factionPowerMax": 0.0,
  
  // Limit the length of faction names here.
  "factionNameLengthMin": 3,
  "factionNameLengthMax": 16
}
```

### Territory Claims

```javascript
{
  // Must claims be connected to each other?
	// If you set this to false you will allow factions to claim more than one base per world map.
	// This allows for outposts or multiple small bases.
  "claimsMustBeConnected": true,
  
  // Must claims be connected to each other enforced strictly?
	// If this is enabled, a check is performed on unclaim which makes 
  // sure you can't make two different bases by unclaiming land.
  "claimsMustBeConnectedStrict": false,
  
  // Would you like to allow unconnected claims when conquering land from another faction?
	// Setting this to true would allow taking over someone else's base even if claims normally have to be connected.
	// Note that even without this you can pillage/unclaim another factions territory in war.
	// You just won't be able to take the land as your own.
  "claimsCanBeUnconnectedIfOwnedByOtherFaction": false,
  
  // Is claiming from other factions even allowed?
  // Set this to false to disable territorial warfare altogether.
  "claimingFromOthersAllowed": true,

  // Is unclaiming from other factions allowed?
	// Set this to true to enable faction pillaging (taking the value of another faction's land, but not conquering it yourself)
	// Use caution when enabling this - ensure you don't enable exploits with your cost/reward system by allowing a player
	// to pillage and then claim for cheaper than conquering directly!
	"unclaimingFromOthersAllowed": false,
  
  // Is it required for factions to have an inflated land/power ratio in order to have their land conquered by another faction?
 	// Set this to false to allow factions to invade each other without requiring them to have an inflated land/power ratio.
  "claimingFromOthersMustBeInflated": true,
  
  // Is a minimum distance to other factions required?
  "claimMinimumChunksDistanceToOthers": 0,
  
  // Do you need a minimum amount of faction members to claim land?
  "claimsRequireMinFactionMembers": 1,
  
  // Is there a maximum limit to chunks claimed?
  "claimedLandsMax": 0,
  
  // The max amount of worlds in which a player can have claims in.
  "claimedWorldsMax": -1
}
```

### Faction Warps

```javascript
{
  // Is the warps feature enabled?
  "warpsEnabled": true,
  
  // How many warps can they have?
  "warpsMax": 1,
  
  // Must warps be located inside the faction's territory?
  "warpsMustBeInClaimedTerritory": true,
  
  // And what faction warp should be used when a player types /f home
  "warpsHomeName": "home",
  
  // These options can be used to limit rights to warp under different circumstances.
  "warpsTeleportAllowedFromEnemyTerritory": true,
  "warpsTeleportAllowedFromDifferentWorld": true,
  "warpsTeleportAllowedEnemyDistance": 32.0,
  "warpsTeleportIgnoreEnemiesIfInOwnTerritory": true,
  
  // Should players teleport to faction warp on death?
  "warpsTeleportToOnDeathActive": false,
  
  // And what faction warp should it be?
  "warpsTeleportToOnDeathName": "home",
  
  // This value can be used to tweak compatibility with other plugins.
  "warpsTeleportToOnDeathPriority": "NORMAL"
}
```

### Protection Settings

```javascript
{
  // Protects the faction land from liquid flow
  "protectionLiquidFlowEnabled": true,
  
  // Protects the faction land from piston extending/retracting
  "handlePistonProtectionThroughDenyBuild": true
}
```

### Territory Information

```javascript
{
  "territoryInfoTitlesDefault": true,
  "territoryInfoTitlesMain": "{relcolor}{name}",
  "territoryInfoTitlesSub": "<i>{desc}",
  "territoryInfoTitlesTicksIn": 5,
  "territoryInfoTitlesTicksStay": 60,
  "territoryInfoTitleTicksOut": 5,
  "territoryInfoChat": "<i> ~ {relcolor}{name} <i>{desc}",
  "territoryAccessShowMessage": true
}
```

### PvP and Combat

```javascript
{
  // Set this option to true if want to block the promotion of new leaders for permanent factions.
  "permanentFactionsDisableLeaderPromotion": false,
  
  // How much health damage should a player take upon placing or breaking a block in a "pain build" territory?
  "actionDeniedPainAmount": 2.0,
  
  // If you set this option to true then factionless players cant partake in PVP.
  "disablePVPForFactionlessPlayers": false,
  
  // Set this option to true to create an exception to the rule above.
  "enablePVPAgainstFactionlessInAttackersLand": false,
  
  // Set this option to false to prevent players from hurting neutral players while they are in the neutral player's territory.
  "enablePVPAgainstNeutralInTheirTerritory": true,
  
  // Inside your own faction territory you take less damage.
  "territoryShieldFactor": 0.1,

  // Will flying be disabled on pvp? (Also mentioned below in the fly section)
  "flyDisableOnPvp": false,
}
```

### Faction Fly

Faction fly is enabled by configuring the `fly` flag. By default it is disabled and can only be set manually by admins in override mode. You can enable it by modifying the flag defaults to enable it, manually enable it for factions you wish to allow it in, or even allow it to be editable by faction leaders. For more details on how to configure flags, see the [Flags Configuration](#flags-configuration) section.

Additional global settings can be configured in the main configuration file:

```javascript
{
  // At what speed can players fly with /f fly?
  "flySpeed": 0.1,

  // Will flying be disabled on pvp?
  "flyDisableOnPvp": false,
}
```

### Miscellaneous Settings

```javascript
{
  // Require users to confirm before a faction is disbanded when running the /f disband command
  "requireConfirmationForFactionDisbanding": true,

  // The date format used when displaying the founded date of a faction
  // Follows Java's SimpleDateFormat patterns
  // For reference: https://docs.oracle.com/en/java/javase/21/docs/api/java.base/java/text/SimpleDateFormat.html
  "foundedDateFormat": "yyyy-MM-dd";
}
```

### Command Restrictions

```javascript
{
  // A list of commands to block for members of permanent factions.
  "denyCommandsPermanentFactionMember": [],
  
  // Lists of commands to deny depending on your relation to the current faction territory.
  "denyCommandsTerritoryRelation": {
    "ENEMY": [
      "home", "homes", "sethome", "createhome", "tpahere", "tpaccept",
      "tpyes", "tpa", "call", "tpask", "warp", "warps", "spawn"
    ],
    "NEUTRAL": [],
    "TRUCE": [],
    "ALLY": [],
    "MEMBER": []
  },
  
  // The distance for denying the following commands. Set to -1 to disable.
  "denyCommandsDistance": -1,
  
  // Lists of commands to deny depending on your relation to a nearby enemy.
  "denyCommandsDistanceRelation": {
    "ENEMY": ["home"],
    "NEUTRAL": [],
    "TRUCE": [],
    "ALLY": [],
    "FACTION": []
  },
  
  // Allow bypassing the above setting when in these territories.
  "denyCommandsDistanceBypassIn": [
    "ALLY",
    "FACTION"
  ]
}
```

### Faction Relation Colors

```javascript
{
  "colorMember": "GREEN",
  "colorAlly": "DARK_PURPLE",
  "colorTruce": "LIGHT_PURPLE",
  "colorNeutral": "WHITE",
  "colorEnemy": "RED",
  "colorNoPVP": "GOLD",
  "colorFriendlyFire": "DARK_RED"
}
```

### Faction Colors

```javascript
{
  // Default faction primary color used when no custom color is set via /f color.
  // This is a generic setting used by various integrations (Dynmap, etc.).
  // Format: "#RRGGBB" (e.g., "#00FF00" for green)
  "defaultFactionPrimaryColor": "#00FF00",
  
  // Default faction secondary color used when no custom color is set via /f color.
  // This is a generic setting used by various integrations (Dynmap, etc.).
  // Format: "#RRGGBB" (e.g., "#00FF00" for green)
  "defaultFactionSecondaryColor": "#00FF00"
}
```

### Tax System

```javascript
{
  // Should the tax system be enabled?
  "taxEnabled": false,
  
  // How much can you tax a player?
  "taxPlayerMinimum": -10,
  "taxPlayerMaximum": 10,
  
  // When is a player inactive?
  "taxInactiveDays": 3,
  
  // When the last run time was (in unix time)
  "taxTaskLastMillis": 0,
  
  // Tax run when?
  "taxTaskInvocationOffsetMillis": 0,
  
  // How often should the task be run?
  "taxTaskPeriodMillis": 86400000
}
```

### Default Ranks

```javascript
{
  "defaultRanks": [
    {
      "name": "Leader",
      "priority": 400,
      "prefix": "**"
    },
    {
      "name": "Officer",
      "priority": 300,
      "prefix": "*"
    },
    {
      "name": "Member",
      "priority": 200,
      "prefix": "+"
    },
    {
      "name": "Recruit",
      "priority": 100,
      "prefix": "-"
    }
  ]
}
```

## Flags Configuration

You can change the defaults of faction flags by modifying the flag configuration files. These configuration files are located at `/mstore/factions_mflag/*.json`, where the name of the file is the name of the flag.

```javascript
{
  // The sort priority. Low values appear first in sorted lists.
  "priority": 1000,
  
  // The name of the flag.
  "name": "open",
  
  // The flag function described as a question.
  "desc": "Can the faction be joined without an invite?",
  
  // The flag function described when true.
  "descYes": "An invite is required to join.",
  
  // The flag function described when false.
  "descNo": "Anyone can join. No invite required.",
  
  // What is the standard (aka default) flag value?
  "standard": false,
  
  // Is this flag editable by players?
  "editable": true,
  
  // Is this flag visible to players?
  "visible": true
}
```

## Permissions Configuration

You can change the defaults of faction permissions by modifying the permission configuration files. These configuration files are located at `/mstore/factions_mperm/*.json`, where the name of the file is the name of the permission.

```javascript
{
  // The sort priority. Low values appear first in sorted lists.
  "priority": 1000,
  
  // The name of the perm.
  "name": "build",
  
  // The perm function described as an "order".
  "desc": "edit the terrain",
  
  // Is this a territory perm?
  "territory": true,
  
  // Is this perm editable by players?
  "editable": true,
  
  // Is this perm visible to players?
  "visible": true
}
```

## Configuration Tips

### Performance Optimization
- Set reasonable limits for `factionMemberLimit` and `claimedLandsMax`
- Use `cleanInactivityToleranceMillis` to automatically remove inactive players

### Security Settings
- Configure `denyCommandsTerritoryRelation` to prevent teleportation exploits
- Set up `playersWhoBypassAllProtection` only for trusted automation accounts

### Gameplay Balance
- Adjust `powerPerHour` and `powerPerDeath` to balance power recovery vs loss
- Set `territoryShieldFactor` to provide home field advantage
- Configure `econChunkCost` to make territorial expansion meaningful

### Administrative
- Use `/f config` command for live configuration changes
- Monitor server console for configuration validation errors
- Back up configuration files before making major changes
