![MassiveBooks Logo](../../img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }

# Integrations Overview

MassiveBooks supports several built-in integrations with external plugins to extend book content and add economy-based costs. Configuration is optional; the plugin works without any of these.

## Built-in Integrations

MassiveBooks currently includes built-in support for the following:

- **PlaceholderAPI** - Placeholders in book text (title, author, pages) are parsed when a player views or receives the book. Any PlaceholderAPI placeholder from any plugin can be used; the viewer is the context.
- **Economy** - Vault-based economy integration for **copy cost**: when players copy books with `/book copy`, they can be charged a configurable amount per copy based on their permissions.

## Third-Party Integrations

Other plugins can work alongside MassiveBooks (for example, chat or scoreboard plugins that use PlaceholderAPI). MassiveBooks does not register its own PlaceholderAPI placeholders; it only **parses** placeholders inside book content. So any placeholder that works in PlaceholderAPI will work inside books when PlaceholderAPI is installed.

## Getting Help

If you have issues with integrations:

1. Check the specific integration page (PlaceholderAPI or Economy) for setup and troubleshooting.
2. Ensure plugin versions are compatible (MassiveCore, PlaceholderAPI, Vault, and your economy plugin).
3. Check the server console for integration-related errors or warnings.
4. Test with a minimal setup (e.g. only MassiveCore + MassiveBooks + the integration plugin) to isolate the problem.

### Best Practices

- Test integrations after updating MassiveBooks or any integrated plugin.
- Watch the console for integration warnings on server start.
- After changing economy or placeholder-related config, give the config a few seconds to reload (or confirm in-game that values are as expected).
