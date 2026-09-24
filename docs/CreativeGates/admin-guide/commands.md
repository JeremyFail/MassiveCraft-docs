![CreativeGates Logo](../img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }

# Commands

Base aliases default to `/cg`, `/creativegates`, and `/creativegate` (configurable via `aliasesCg`).

| Command | Description | Permission |
|---------|-------------|------------|
| `/cg` | Base command / help | `creativegates.cg` |
| `/cg inspect [page]` | Inspect the gate you are looking at | `creativegates.cg.inspect` |
| `/cg manage [gate] [page]` | Open manage UI for the looked-at gate (or by id) | `creativegates.cg.manage` |
| `/cg tool [on\|off]` | Toggle whether inspect/manage **item** tools work for you | `creativegates.cg.tool` |
| `/cg override [on\|off]` | Toggle override mode (manage others' gates, bypasses) | `creativegates.cg.override` |
| `/cg world` | World management | `creativegates.cg.world` |
| `/cg world list` | List gate counts per world | `creativegates.cg.world.list` |
| `/cg world delete <world>` | Delete all gates in a world | `creativegates.cg.world.delete` |
| `/cg config` | Edit configuration in-game (advanced) | `creativegates.cg.config` |
| `/cg version` | Show plugin version | `creativegates.cg.version` |

## Player workflows (tools)

Most players never need commands. Defaults:

| Action | Default item | Notes |
|--------|--------------|-------|
| Create | Clock (named) | Opens fill picker when the player may choose fills |
| Inspect | Blaze powder | Same data as `/cg inspect` |
| Manage | Blaze rod | Same as `/cg manage` - settings + optional fill change |

`/cg tool` only disables the **item** tools for that player; `/cg inspect` and `/cg manage` still work if they have permission.

## Manage UI

- **Paper (native dialog available):** dialog with toggles for Secret, Entry, Exit, Players, Mobs, Vehicles, and Gate Fill
- **Fallback:** clickable chat table (same settings)

Only the gate creator can manage unless the player has override mode or `creativegates.cg.override.bypass`.

## Override mode

`/cg override` lets staff manage and inspect secret gates they do not own. While overriding (or with bypass), they can also:

- Create in worlds listed in `gateCreationDisabledWorlds`
- Skip required frame materials (`blocksrequired`)

See [Permissions](permissions.md).
