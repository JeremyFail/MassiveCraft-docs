![Factions3 Logo](../../img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }
![WorldGuard Logo](img/worldguard.svg){ style="display: block; margin: 0px auto; max-height: 115px;" }

# WorldGuard Integration

Factions integrates with [WorldGuard](https://dev.bukkit.org/bukkit-plugins/worldguard/) to provide advanced region protection by preventing faction claims within protected WorldGuard regions. This integration allows server administrators to maintain control over special areas while still allowing faction gameplay in designated zones.

!!! info "Note"

    For more information about WorldGuard, visit their plugin listing page or [Wiki](https://worldguard.enginehub.org/en/latest/).

## How It Works

The WorldGuard integration operates by:

1. **Checking region membership** before allowing faction claims
2. **Respecting WorldGuard priorities** and region hierarchies
3. **Providing bypass permissions** for trusted players
4. **Supporting admin override mode** for administrative tasks

## Configuration

### Basic Settings

```javascript
{
  // Global WorldGuard Integration Switch
  "worldguardCheckEnabled": false,

  // Enable the WorldGuard check per-world 
  // Specify which worlds the WorldGuard Check can be used in
  "worldguardCheckWorldsEnabled": {
    "standard": true,    // Default for all worlds
    "exceptions": []     // Worlds that differ from standard
  }
}
```

### World-Specific Configuration

**Enable only in specific worlds:**
```javascript
{
  "worldguardCheckWorldsEnabled": {
    "standard": false,  // Disabled by default
    "exceptions": ["survival", "factions_world"]  // Only enabled in these worlds
  }
}
```

**Disable in specific worlds:**
```javascript
{
  "worldguardCheckWorldsEnabled": {
    "standard": true,   // Enabled by default
    "exceptions": ["creative", "spawn_world"]  // Disabled in these worlds
  }
}
```

## Setup Instructions

### 1. Install WorldGuard

Ensure WorldGuard is properly installed and configured on your server.

### 2. Enable Factions Integration

Edit your Factions configuration:

```javascript
{
  "worldguardCheckEnabled": true,
  "worldguardCheckWorldsEnabled": {
    "standard": true,
    "exceptions": []
  }
}
```

### 3. Create Protected Regions

Use WorldGuard commands to create protected areas:

```yaml
# Select area with WorldEdit
//wand

# Create protected region
/rg define some-region

# Set region flags
/rg flag some-region pvp deny
/rg flag some-region build deny
etc.
```

### 4. Configure Permissions

Set up bypass permissions for trusted players:

```yaml
# Allow claiming in specific region (example using LuckPerms - command may vary)
/lp user ExamplePlayer permission set factions.allowregionclaim.some-region
```
## Troubleshooting

### Common Issues

**Claims allowed in protected regions:**
- Verify `worldguardCheckEnabled` is `true`
- Check that WorldGuard is installed and running
- Ensure region is properly defined with `/rg info <region>`
- Verify world is enabled in `worldguardCheckWorldsEnabled`

**Cannot claim anywhere:**
- Check if player has bypass permissions
- Verify regions are configured correctly
- Test with `/f admin` mode
- Check console for WorldGuard errors

**Permissions not working:**
- Verify exact region name in permission
- Check permission plugin syntax
- Ensure permissions are applied to correct group/user

## Migration Guide

### From No WorldGuard Integration

1. **Backup faction data**
2. **Install and configure WorldGuard**
3. **Create necessary regions**
4. **Enable Factions integration**
5. **Test thoroughly**
6. **Communicate changes to players**

### Handling Existing Claims

When enabling WorldGuard integration:

- Existing claims in now-protected regions remain
- New claims will be blocked according to rules
- Use `/f admin` to modify existing claims if needed
- Consider grandfathering existing claims vs forcing moves
