![FactionsChat3 Logo](../img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }

# Permissions

Below is a list of permission nodes used by FactionsChat. Assign them with your permissions plugin (e.g. LuckPerms). **Defaults** in `plugin.yml` are often **`op`** for chat styling - give nodes explicitly to non-op players if they should use colors, MiniMessage, URLs, etc.

!!! info "Config + permission"
    Many chat features require **both** a **permission** and a **`config.yml`** flag. The configuration flag enables the feature in general, and the permission grants whichever players you want to use that feature the ability to do so. For example, legacy colors and formats need **`ChatSettings.AllowColorCodes`**, and clickable URLs need **`ChatSettings.AllowClickableLinks`** (and optionally **`AllowClickableLinksUnderline`**). See **[Chat Formatting](../player-guide/chat-formatting.md)** for how this interacts with what players type.

## Parent groups (quick reference)

| Node | Purpose |
|------|---------|
| `factions.chat.*` | Bundles **channels**, **legacy/MiniMessage styling**, **ignore**, and **toggle** - does **not** include staff, reload, admin ignore/toggle, or `click.bypass` / `ignore.bypass`. |
| `factions.chat.player.*` | **Channels** + **ignore** + **toggle** only - **no** color, format, hex, URL, or MiniMessage styling nodes. Useful for "can chat, no cosmetics." |
| `factions.chat.admin.*` | **Staff** channel, **reload**, **ignore admin**, **toggle admin**. |

## Player Permissions

### Channel permissions

| Permission Node | Description |
|-----------------|-------------|
| `factions.chat.ally` | Use Ally chat |
| `factions.chat.truce` | Use Truce chat |
| `factions.chat.faction` | Use Faction chat |
| `factions.chat.enemy` | Use Enemy chat |
| `factions.chat.neutral` | Use Neutral chat |
| `factions.chat.local` | Use Local chat |
| `factions.chat.global` | Use Global chat |
| `factions.chat.world` | Use World chat |

### Legacy styling (chat message body)

These apply to **ampersand / section** color and format codes in the message (Spigot and Paper). All require **`ChatSettings.AllowColorCodes: true`** in `config.yml` to have any effect.

| Permission Node | Description |
|-----------------|-------------|
| `factions.chat.color` | Use legacy **16-color** codes (`&0`–`&9`, `&a`–`&f`) in chat messages |
| `factions.chat.format` | Use legacy **format** codes (`&l`, `&m`, `&n`, `&o`, `&r`) in chat messages |
| `factions.chat.magic` | Use legacy **obfuscated** code (`&k`) in chat messages |
| `factions.chat.rgb` | Use **hex / RGB** patterns (`&#RRGGBB`, `§x…`, etc.) in chat messages |

### URLs and links (chat message body)

| Permission Node | Description |
|-----------------|-------------|
| `factions.chat.url` | Send **clickable** plain URLs in chat (`https://...`). Requires **`ChatSettings.AllowClickableLinks`**. Underline uses **`AllowClickableLinksUnderline`**. |

### MiniMessage & advanced chat (Paper only)

MiniMessage tags are parsed **only on Paper**. Each family has its own node; without it, the tag stays **literal text** in chat.

| Permission Node | Description |
|-----------------|-------------|
| `factions.chat.hover` | MiniMessage **hover** tags (`show_text`, `show_item`, `show_entity`, …) |
| `factions.chat.click` | MiniMessage **click** actions other than plain URLs (`run_command`, `suggest_command`, `copy_to_clipboard`, …) |
| `factions.chat.click.bypass` | Bypass **`ChatSettings.BlacklistedMiniMessageCommands`** checks for run/suggest click payloads (**default: false**) |
| `factions.chat.insert` | MiniMessage **`<insert>`** (shift-click paste into chat box) |
| `factions.chat.keybind` | MiniMessage **keybind** tags (e.g. `key.jump`) |
| `factions.chat.translatable` | MiniMessage **lang / translate / tr** (and `*_or` fallbacks) |
| `factions.chat.rainbow` | MiniMessage **`<rainbow>`** (in practice also needs color permission for sensible output) |
| `factions.chat.gradient` | MiniMessage **`<gradient>`** |
| `factions.chat.transition` | MiniMessage **`<transition>`** |
| `factions.chat.font` | MiniMessage **`<font>`** |
| `factions.chat.selector` | MiniMessage **selector / `sel`** tags |
| `factions.chat.score` | MiniMessage **`<score>`** |
| `factions.chat.nbt` | MiniMessage **NBT / data** tags |
| `factions.chat.pride` | MiniMessage **`<pride>`** |
| `factions.chat.sprite` | MiniMessage **`<sprite>`** (server MiniMessage / Adventure version dependent) |
| `factions.chat.head` | MiniMessage **`<head>`** (server MiniMessage / Adventure version dependent) |

!!! warning "Paper only"
    If the server is **Spigot-only**, MiniMessage tags are **not** parsed; granting these nodes does not enable MiniMessage there.

### Sub-command permissions

| Permission Node | Description |
|-----------------|-------------|
| `factions.chat.toggle` | Use **`/f c toggle`** to enable/disable specific chat modes (channels) for yourself |
| `factions.chat.ignore` | Use **`/f c ignore`**, **`/f c unignore`**, and **`/f c ignorelist`** to manage your ignore list |

## Admin permissions

| Permission Node | Description |
|-----------------|-------------|
| `factions.chat.staff` | Use **Staff** chat (moderators/admins) |
| `factions.chat.reload` | Reload the FactionsChat **`config.yml`** |
| `factions.chat.toggle.admin` | Toggle chat modes for **other** players |
| `factions.chat.ignore.admin` | View or change **other** players’ ignore lists |
| `factions.chat.ignore.bypass` | Send chat that **ignored** players still receive (**default: false**-often for staff) |
