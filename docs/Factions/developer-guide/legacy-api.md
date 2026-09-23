![Factions3 Logo](../img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }

# Legacy API

Factions has a long history. In Factions V2, the API was completely rewritten as Factions had a major rewrite at that time. This caused a rift in the community as some did not like the changes that MassiveCraft made with this rewrite, and forks of the original Factions V1 were created. Some of these forks are still alive today and continue to use implementations of that original V1 API. 

In Factions V3, we have kept the same API structure as Factions V2, maintaining backwards compatibility with Factions V2 while also building new features on top of that.

The forks of Factions V1 that still use that original V1 API (or offshoots of it) use what we now refer to as the "legacy API". Some of the classes in the legacy API were `FPlayer`, `FLocation`, `Board` (not the same as the new `Board` class - the package path is different), `Faction` (not the same as the new `Faction` class - the package path is different). If you ever see reference to these in code, know that these are references to that legacy API used by other Factions forks, **_not_** the V2/V3 API structure that we support and maintain.

**We do _NOT_ officially support the legacy API for usage with Factions V3.** However, we did build in a basic compatibility layer to allow plugins that integrate with these other Factions plugins using the legacy API to _theoretically_ work with Factions V3 for a short time until they can implement full proper support. We may remove this at any time - it exists solely to allow quick implementation of support of Factions3 for plugins that already support other Factions offshoots while developers work on full, proper implementations of the supported API.

## What This Is

- **Wrapper classes** that delegate to the modern Factions implementation
- **Bridge interfaces** that translate between old and new API calls
- **Compatibility methods** that support simple compatibility for plugins not yet properly integrated with Factions3

## What This Is NOT

- :x: A full-featured API for new development
- :x: A maintained or actively developed API
- :x: A recommended approach for modern plugins
- :x: A complete implementation of all legacy features

## For Plugin Developers

### If you're developing a NEW plugin:
**Use the modern API**: Read the [API Documentation](api.md) or the [Basic Usage](basic-usage.md) pages for more details.

### If you're maintaining an EXISTING plugin that integrates with other Factions plugins:
1. **Preferred**: Update your plugin to use the modern API for full-featured Factions3 support.
2. **Temporary**: This compatibility layer may help during migration. Understand that it's deprecated, is not supported, may not fully work, and may be removed at a later date. If you experience issues, we will not be able to provide assistance.

## Warnings and Limitations

- **Performance**: Additional overhead due to wrapper delegation
- **Features**: Not all legacy methods are implemented
- **Maintenance**: This layer receives minimal maintenance
- **Compatibility**: May break with future Factions updates
- **Support**: Limited support for issues with legacy API usage

## Usage Monitoring

This compatibility layer includes usage tracking and will log warnings when legacy API methods are called. This helps server administrators identify plugins that need updating.

## Migration Guide

To migrate from the legacy API to the modern API:

1. Update method calls to use the modern API equivalents
2. Review faction entity structure changes
3. Test thoroughly with the new API

## Legal Notice

This compatibility layer is provided "as-is" without warranty. Use at your own risk for existing plugin compatibility only and make a plan to implement proper Factions3 support into your integration.
