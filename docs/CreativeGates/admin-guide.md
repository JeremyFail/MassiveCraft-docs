![CreativeGates Logo](img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }

# Admin Guide

## Commands

| Command                        | Description                       | Permission                   |
|---------------------------------|-----------------------------------|------------------------------|
| `/cg` or `/creativegates`       | Base command, shows help          | `creativegates.cg`           |
| `/cg version`                   | Show plugin version               | `creativegates.cg.version`   |
| `/cg world`                     | World management commands         | `creativegates.cg.world`     |
| `/cg world list`                | List gates in a world             | `creativegates.cg.world.list`|
| `/cg world delete <world>`      | Delete all gates in a world       | `creativegates.cg.world.delete`|
| `/cg config`                    | Edit configuration (advanced)     | `creativegates.cg.config`    |

## Permissions

### Player Permissions

| Node                   | Description                |
|------------------------|----------------------------|
| `creativegates.create` | Create a gate              |
| `creativegates.use`    | Use a gate                 |

### Operator/Admin Permissions

| Node                                  | Description                       |
|---------------------------------------|-----------------------------------|
| `creativegates.create.bypassdisabled` | Create a gate in worlds that have gate creation disabled |
| `creativegates.cg`                    | Use base command                  |
| `creativegates.cg.world`              | Use world management commands     |
| `creativegates.cg.world.list`         | List gates in a world             |
| `creativegates.cg.world.delete`       | Delete all gates in a world       |
| `creativegates.cg.version`            | See plugin version                |
| `creativegates.cg.config`             | Edit configuration                |

## Configuration

### Portal vs Water

CreativeGates can use either portal blocks or water blocks for portal content. You decide which to use in the configuration.

While nether portal blocks do work, one issue that can occur is that if a player creates a nether portal that would normally exit near your gate, when entering the nether portal, they might exit through your CreativeGate instead of the regular nether portal. If you encounter issues while also using standard nether portals, you can always disable the nether through your `server.properties` or game rules (depending on the version of Minecraft you are running) and add a custom nether map through other map plugins, along with a warp command or public portal to allow players to access that world. Alternatively, you can also switch to use water for your portals instead which would prevent that issue.

For water blocks to work you don't need to do anything special. If you want both the vanilla nether world and portals while also using CreativeGates though, you may want to consider changing to use water portals in the config.

### Supported Configuration Values

Configuring CreativeGates is **optional**. The default configuration works perfectly in most cases.

That said, you can modify the main configuration settings. This configuration file is located at `/mstore/creativegates_mconf/instance.json`. Modifications will automatically be detected and loaded into the server after a few seconds. You don't need to run any additional reload command or restart the server for the modified settings to take effect.

!!! warning "Warning"
    Comments have been added to the configuration example below to explain the values, but these comments should **NOT** be added to your actual configuration file as it will cause errors.

```javascript
{
    // If you set this to false the plugin will be disabled.
    "enabled": true,
    
    // You can decide what you want the base command aliases to be here.
    "aliasesCg": ["cg", "creativegates", "creativegate"],
    
    // Should players hear a sound when teleporting through a CreativeGate?
    "teleportationSoundActive": true,
    
    // Should players receive a message when teleporting through a CreativeGate?
    "teleportationMessageActive": true,
    
    // Should players get permission to create gates per default? 
    // Valid options are "TRUE", "FALSE", "OP" and "NOT_OP".
    "permissionDefaultCreate": "TRUE",
    
    // Should players get permission to use gates per default? 
    // Valid options are "TRUE", "FALSE", "OP" and "NOT_OP".
    "permissionDefaultUse": "TRUE",
    
    // CreativeGates uses portal blocks for portals by default. 
    // Some people prefer portals made out of water. 
    // Set this to true to switch to water.
    "usingWater": false,
    
    // Should Zombified Piglins (previously known as Zombie Pigmen) 
    // be allowed to spawn from CreativeGates?
    "pigmanPortalSpawnAllowed": true,
    
    // This defines the maximum gate content size. The flood fill algorithm stops
    // running if no frame is found when the content has reached this size.
    "maxarea": 200,
    
    // The blocks required in the frame. Defaults to two emerald blocks.
    "blocksrequired": {
        "EMERALD_BLOCK": 2
    },
    
    // Is the name removed from the creation tool when creating a gate?
    "removingCreateToolName": true,
    
    // Is the whole create tool item removed when creating a gate?
    "removingCreateToolItem": false,
    
    // The material used for the gate creation tool.
    "materialCreate": "CLOCK",
    
    // The material used for the gate inspection tool.
    "materialInspect": "BLAZE_POWDER",
    
    // The material used for the network secrecy tool.
    "materialSecret": "MAGMA_CREAM",
    
    // The material used for the gate enter/exit mode tool.
    "materialMode": "BLAZE_ROD",
    
    // A comma-separated list of world names that do not allow creation of CreativeGates. 
    // This is used to limit CreativeGates creation to only specific worlds.
    // This does not prevent USAGE of gates in these worlds, only creation.
    // NOTE: Players with the creativegates.create.bypassdisabled permission will bypass this 
    //       restriction and be able to create CreativeGates in the worlds listed in this setting.
    "gateCreationDisabledWorlds": []
}
```

## Troubleshooting

### Gates Not Working

- **Make sure MassiveCore is installed and up to date** - CreativeGates requires MassiveCore as a dependency
- **Check permissions** - Ensure players have the correct permissions to create (`creativegates.create`) or use (`creativegates.use`) gates
- **Verify frame requirements** - Ensure you have the required number of frame blocks as configured (default is 2 emerald blocks)
- **Check world restrictions** - Make sure gate creation isn't disabled in the world you're trying to create gates in

### Portal Conflicts

If you're experiencing issues with nether portals interfering with CreativeGates:

1. Consider switching to water portals in the configuration by setting `"usingWater": true`
2. Disable the nether through `server.properties` or game rules
3. Use custom nether maps through other plugins with warp commands

### Configuration Issues

- Configuration changes are automatically detected and loaded after a few seconds
- No server restart or reload command is needed
- Ensure your JSON configuration file has no syntax errors (comments should not be included in the actual file)

### Getting Help

If you continue to experience issues:

1. Check the server console for any error messages
2. Verify all dependencies are properly installed
3. Review your configuration file for syntax errors
4. Open an issue on [GitHub](https://github.com/JeremyFail/MassiveCraft) with detailed information about your problem