![FactionsChat3 Logo](../img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }

# Chat Formatting

FactionsChat supports various formatting options to style your messages with colors, formatting codes, and more. This guide covers all available formatting features.

**Permissions:** Almost every formatting feature is **locked behind a permission** (for example `factions.chat.color`, `factions.chat.format`, and MiniMessage-specific nodes). If you type codes and they show **literally** (e.g. `&c` instead of red text), you usually **lack the matching permission** - ask your server admin. A full list is in **[Permissions](../admin-guide/permissions.md)**.

**Config gates:** Even with permission, the server must allow styling in **`config.yml`**: `ChatSettings.AllowColorCodes` (legacy colors / formats / hex), `ChatSettings.AllowClickableLinks` (URLs), and `ChatSettings.AllowClickableLinksUnderline` (URL underline). Admins can enable permissions for players but keep these `false` to disable formatting globally.

**Spigot vs Paper:** Legacy ampersand (`&`) and section (`§`) codes, hex colors, and automatic URLs work on **both** Spigot and Paper. **MiniMessage** tags (angle-bracket markup such as `<green>hello</green>`) are parsed **only on Paper**; on Spigot they are treated as plain text.

!!! warning "MiniMessage is Paper-only"
    If your server runs **Spigot** (or a fork without Paper’s chat stack), MiniMessage tags in chat will **not** be interpreted - they will show literally. Use legacy `&` codes on those servers.

!!! info "Permissions + config"
    **Permission** = whether *you* may use a feature. **Config** = whether the *server* allows that class of features at all. You need **both** where applicable. Details: **[Permissions](../admin-guide/permissions.md)**.

## Color Codes

FactionsChat supports formatting your chat message text with colors **when you have** `factions.chat.color` **and** `ChatSettings.AllowColorCodes` is `true` in `config.yml`.

### Basic Colors

Use the ampersand symbol (`&`) followed by a color code to change text color.

```
&0 = Black          &8 = Dark Gray
&1 = Dark Blue      &9 = Blue
&2 = Dark Green     &a = Green
&3 = Dark Aqua      &b = Aqua
&4 = Dark Red       &c = Red
&5 = Dark Purple    &d = Light Purple
&6 = Gold           &e = Yellow
&7 = Gray           &f = White
```

Without **`factions.chat.color`** (or with `AllowColorCodes: false`), these sequences stay **plain text** in chat.

### Hex/RGB Colors

For more precise color control, use hex color codes with `&#`:

**Example:**
```
&#RRGGBB
```

Where:
- `RR` = Red value (00-FF)
- `GG` = Green value (00-FF)
- `BB` = Blue value (00-FF)

Hex in chat requires **`factions.chat.rgb`** in addition to **`factions.chat.color`** (and `AllowColorCodes`), unless your admin sets things differently.

!!! info "Finding Hex Colors"
    Use online color pickers (like [htmlcolorcodes.com](https://htmlcolorcodes.com) or [colorpicker.me](https://colorpicker.me)) to find hex codes for any color you want.

## Format Codes

Format codes modify the style of your text. **`factions.chat.format`** controls bold, italic, underline, strikethrough, and reset-style format codes; **`factions.chat.magic`** is required for **`&k`** (obfuscated). Same **`AllowColorCodes`** gate as colors.

```
&l = Bold
&m = Strikethrough
&n = Underline
&o = Italic
&k = Magic/Obfuscated (requires factions.chat.magic)
&r = Reset (removes all formatting)
```

**Example combining multiple formats:**
```
&lBold text &r&oItalic text &r&nUnderlined text
```

## Combining Formatting

You can combine colors and formatting codes to create rich text - the color must be specified before the format. You still need **`factions.chat.color`** for the color part and **`factions.chat.format`** for **`&l` / `&o` / `&n` / `&m`** (and **`factions.chat.magic`** for **`&k`**).

### Color + Format

**Bold and colored:**
```
&c&lBold Red Text
```

**Italic and colored:**
```
&9&oItalic Blue Text
```

## Reset Formatting

Use `&r` to reset all formatting and colors to return to default. Reset does **not** require a separate permission beyond what you already needed for the codes **before** the reset.

```
&c&lBold red text &rback to normal &9blue text
```

!!! info "Reset Best Practice"
    Always use `&r` before applying new formatting to avoid unexpected results from previous formatting codes.

## MiniMessage (Paper only)

On **Paper**, FactionsChat parses [MiniMessage](https://docs.papermc.io/adventure/minimessage/format) in the **same** chat line as legacy `&` / `§` codes. Each tag family has its own **`factions.chat.*`** permission - see **[Permissions](../admin-guide/permissions.md)** under *MiniMessage & advanced chat*. Legacy rules above still apply to `&` segments.

You can mix a legacy prefix with MiniMessage in the message body (though we typically advise sticking to one or the other), for example:

```
&cImportant: <green>read the rules</green> <gray>(thanks!)</gray>
```

### Named and hex colors

MiniMessage supports named colors, gradients, and more. Examples:

```
<red>Red text</red>
<#55FF55>Custom hex</#55FF55>
<gradient:#ff0000:#0000ff>Rainbow-ish title</gradient>
```

Named / simple colors still need **`factions.chat.color`** (and config). Tags like **`<gradient>`**, **`<rainbow>`**, **`<transition>`**, **`<pride>`**, **`<font>`** have **dedicated** permissions - your admin grants them explicitly (they are **not** implied only by `factions.chat.color`).

### Decorations and reset

Common tags (aliases may exist - see Paper’s MiniMessage docs):

```
<bold> or <b>
<italic> or <i>
<underlined> or <u>
<strikethrough> or <st>
<obfuscated> or <obf>
<reset> or <r>
```

Decoration tags follow **`factions.chat.format`** (and **`factions.chat.magic`** for obfuscated), same idea as legacy **`&l` / `&o` / …**.

`<reset>` / `<r>` clears MiniMessage styling; behavior can differ slightly from legacy `&r` when mixed with Adventure components. Prefer `<reset>` between MiniMessage sections if results look "sticky."

### Interactive tags (permissions)

These MiniMessage features are **gated by permissions** (defaults are often `op` - ask your admin). Full list: **[Permissions](../admin-guide/permissions.md)**.

| Feature | Typical tags | Permission (examples) |
|--------|----------------|-------------------------|
| Hover | `<hover:show_text:'...'>` and related | `factions.chat.hover` |
| Clicks (not plain URLs) | `<click:run_command:...>`, `suggest_command`, `copy_to_clipboard`, … | `factions.chat.click` |
| Insert (shift-click paste) | `<insert:...>` | `factions.chat.insert` |
| Keybind | `<key:key.jump>` | `factions.chat.keybind` |
| Translatable | `<lang:...>`, `<translate>`, … | `factions.chat.translatable` |
| Rainbow / gradient / transition / font / pride | `<rainbow>`, `<gradient:...>`, … | `factions.chat.rainbow`, `.gradient`, `.transition`, `.font`, `.pride`, … |
| Selector / score / NBT / data | `<selector>`, `<score>`, … | `factions.chat.selector`, `.score`, `.nbt` |
| Sprite / head (newer MiniMessage) | `<sprite:...>`, `<head:...>` | `factions.chat.sprite`, `.head` |

**Blacklisted commands:** On Paper, run/suggest click payloads can be blocked by `ChatSettings.BlacklistedMiniMessageCommands` in `config.yml`. Players with `factions.chat.click.bypass` skip that check.

### Plain URLs

Plain `https://…` links need **`factions.chat.url`** and **`ChatSettings.AllowClickableLinks`**. They are **not** the same as MiniMessage’s `<click:open_url:…>` (admins may still configure both).

### What you see without permission

If you use a MiniMessage tag you **don’t** have permission for, FactionsChat keeps that tag as **literal visible text** (it is not parsed into styling). Legacy `&` codes you’re not allowed to use behave similarly - they stay visible instead of applying color.

!!! info "Authoritative MiniMessage reference"
    Tag names, arguments, and escaping rules change with Adventure/MiniMessage versions. When in doubt, use the official [Paper MiniMessage format](https://docs.papermc.io/adventure/minimessage/format) documentation.

## URLs in Chat

If your server allows it, you can send clickable URLs in chat (**`factions.chat.url`** + **`ChatSettings.AllowClickableLinks`**):

```
Check out our website: https://example.com
```

Players can click the URL to open it in their browser. Underline style depends on **`ChatSettings.AllowClickableLinksUnderline`**.

## Troubleshooting

### Formatting codes aren't working

- You may not have **`factions.chat.color`**, **`factions.chat.format`**, etc. - see **[Permissions](../admin-guide/permissions.md)**
- **`ChatSettings.AllowColorCodes`** may be `false` in `config.yml`
- Check that you're using `&` not other symbols
- Try using `&r` before your formatting codes
- Make sure there's no space between `&` and the code

### Colors look different than expected

- Different Minecraft versions may render colors slightly differently
- Some texture packs or mods can affect color display
- Lighting in-game can affect how colors appear

### Hex colors not working

- Ensure you have **`factions.chat.rgb`** (and usually **`factions.chat.color`**) plus **`AllowColorCodes`**
- Check the format: `&#RRGGBB` (no spaces)
- Verify the server supports hex colors (requires newer Minecraft versions)
- Try basic color codes first to confirm formatting works

### MiniMessage tags show as plain text

- Confirm the server is **Paper** (or a Paper-based fork with the same chat pipeline) - MiniMessage is **not** applied on Spigot-only servers
- You may lack the specific **`factions.chat.*`** permission for that tag family - see **[Permissions](../admin-guide/permissions.md)**
- Check for typos; unclosed `<tag>` sections can look "broken" in chat

## Related Guides

- **[Player Guide Overview](index.md)** - Return to the main player guide
- **[Chat Channels](chat-channels.md)** - Learn about available chat channels
- **[Player Ignoring](player-ignoring.md)** - Learn how the ignore system works to ignore messages from other players
