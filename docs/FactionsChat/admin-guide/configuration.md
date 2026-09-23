![FactionsChat3 Logo](../img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }

# Configuration

All configuration of FactionsChat3 is handled in the `config.yml` file generated in your FactionsChat plugin folder after first run. This file will also be updated with new values when the plugin is updated with new features.

### Example

```yaml
##############################################
#                                            #
#         FactionsChat by Ymerejliaf         #
#        ----------------------------        #
#           Main Configuration File          #
#                                            #
##############################################
version: 5



#----------------- Chat Settings -----------------#
# Chat-related settings not specific to any chat mode
# https://factions.wiki/FactionsChat/admin-guide/configuration/
ChatSettings:
  # The chat format for all messages. 
  # On Paper: §, &, hex, and MiniMessage tags are parsed. 
  # On Spigot: legacy §, &, and hex tags are parsed. Minimessage is not supported.
  #
  # Supports PlaceholderAPI (PAPI) placeholders if PAPI is installed.
  # Also supports modifiers such as |rp (right padding) or |lp (left padding), which 
  # conditionally add right/left padding (a space) if the placeholder is not empty.
  # See the wiki for more details on the PAPI integration:
  # https://factions.wiki/FactionsChat/admin-guide/integrations/placeholderapi/
  #
  # If you do not have PAPI installed, we support a limited set of built-in placeholders, as well as
  # the same modifiers mentioned above. See the wiki for more details:
  # https://factions.wiki/FactionsChat/admin-guide/integrations/placeholderapi/#built-in-placeholders
  ChatFormat: '%factions_chat_prefix|rp%&f<%rel_factions_relation_color%%factions_player_rankprefix%%factions_faction_name|rp%&f%DISPLAYNAME%&f> %factions_chat_color%%MESSAGE%'
  # If true, allows color codes/formatting in chat messages (if players also have permission to use them)
  AllowColorCodes: true
  # If true, allows clickable links in chat messages (if players also have permission to send them)
  # This is separate from specific MiniMessage link parsing - this is a general setting for all chat messages
  # where if a link is detected, it will be allowed to be clicked.
  AllowClickableLinks: true
  # If true, will underline clickable links in chat messages (from links detected via the AllowClickableLinks setting)
  AllowClickableLinksUnderline: true
  # Determines the range (in blocks) for local chat visibility. 
  # Players within this range will see the chat message.
  LocalChatRange: 1000
  # If true, chat reporting for messages sent by players is completely disabled.
  # If false, chat reporting will be enabled, however, if you allow players to use color codes or formatting,
  # messages with color codes or formatting that are parsed will show that they are modified by the server. 
  # This is normal/expected behavior as the server will have modified the original message. If you do not
  # want this behavior, you should not give players permission to use color codes or formatting.
  # NOTE: This setting only applies to Paper servers. For Spigot servers, chat reporting is always disabled.
  DisableChatReporting: false
  # Paper only: keep Adventure components already on the chat message (from plugins that ran earlier), while routing
  # (quick-chat prefix + channel token, etc.) still uses plain text. This allows for greater compatibility with other chat plugins, but
  # may cause issues if that plugin is also parsing text in a similar way to FactionsChat.
  # When false, the chat body is rebuilt only from plain text, meaning any processing/parsing that occurred from other
  # plugins that ran prior to FactionsChat's parsing will effectively be discarded.
  PreserveUpstreamChatComponents: true
  # Quick chat: start a message with Prefix + channel token (+ optional body) for a one-off send or mode toggle.
  # Prefix must not contain whitespace; empty or invalid values fall back to ":".
  QuickChat:
    # Plain-text prefix (default ":"). Example alternatives: "#" or ">>"
    Prefix: ':'
    # When false (default), unknown modes, no permission, or malformed quick-chat lines are sent as normal chat (full line, current channel).
    # When true, those cases cancel the message and show "Invalid chat mode or command."
    ErrorOnInvalidMode: false
  # On Paper (MiniMessage), block chat lines that contain <click:run_command:…> or <click:suggest_command:…> whose
  # command matches any entry below. Leading slashes are ignored.
  # Set to [] to disable. If this key is omitted entirely, a built-in default list is used.
  # Players with the permission factions.chat.click.bypass are not checked.
  BlacklistedMiniMessageCommands:
    - '/minecraft:op'
    - '/minecraft:deop'
    - '/minecraft:ban'
    - '/minecraft:ban-ip'
    - '/minecraft:pardon'
    - '/minecraft:pardon-ip'
    - '/minecraft:kick'
    - '/minecraft:mute'
    - '/minecraft:unmute'
    - '/minecraft:whitelist'
    - '/minecraft:gamemode'
    - '/minecraft:gm'
    - '/minecraft:give'
    - '/minecraft:clear'
    - '/minecraft:effect'
    - '/minecraft:stop'
    - '/minecraft:restart'
    - '/minecraft:reload'
    - '/minecraft:rl'
    - '/op'
    - '/deop'
    - '/ban'
    - '/ban-ip'
    - '/pardon'
    - '/pardon-ip'
    - '/kick'
    - '/mute'
    - '/unmute'
    - '/whitelist'
    - '/gamemode'
    - '/gm'
    - '/give'
    - '/clear'
    - '/effect'
    - '/stop'
    - '/restart'
    - '/reload'
    - '/rl'
    - '/sudo'
    - '/lp'
    - '/luckperms'
    - '/pex'
    - '/permissions'



#---------------- Prefix Settings ----------------#
# Chat prefixes for each chat mode - controls what is displayed in the %factions_chat_prefix% placeholder.
# <fcolor> is a placeholder that is replaced with the faction relation color from Factions.
# You may use § or & for legacy colors/format (including hex like &#RRGGBB where supported in the full chat pipeline).
# On Paper, MiniMessage tags (e.g. <yellow>, <gradient>, etc.) work here too. Minimessage is not supported on Spigot.
# NOTE: This prefix is NOT used unless the %factions_chat_prefix% placeholder appears in ChatFormat.
ChatPrefixes:
  Ally: '§e[<fcolor>ALLY§e]§r'
  Truce: '§e[<fcolor>TRUCE§e]§r'
  Faction: '§e[<fcolor>FACTION§e]§r'
  Enemy: '§e[<fcolor>ENEMY§e]§r'
  Neutral: '§e[<fcolor>NEUTRAL§e]§r'
  Local: '§e[§rLOCAL§e]§r'
  Global: '§e[§6GLOBAL§e]§r'
  Staff: '§e[§4STAFF§e]§r'
  World: '§e[§3WORLD§e]§r'



#-------------- Text Color Settings --------------#
# Text colors for each chat mode - controls what is returned from the %factions_chat_color% placeholder.
# <fcolor> is a placeholder that is replaced with the faction relation color from Factions.
# Use § or & for legacy codes; on Paper, MiniMessage snippets (e.g. <gradient:...>) are also supported.
# NOTE: These colors are NOT used unless the %factions_chat_color% placeholder appears in ChatFormat.
TextColors:
  Ally: '<fcolor>'
  Truce: '<fcolor>'
  Faction: '<fcolor>'
  Enemy: '<fcolor>'
  Neutral: '<fcolor>'
  Local: '§f'
  Global: '§6'
  Staff: '§4'
  World: '§3'



#--------------- Discord Settings ----------------#
# Settings for the DiscordSRV integration (requires DiscordSRV to be installed).
DiscordSRV:
  # If false, FactionsChat will not register with DiscordSRV even when the plugin is present.
  enabled: true
  # The channel ID for the channel in your discord guild to link staff chat to.
  # Right click the text channel, select "copy ID" and replace the current value with copied ID.
  StaffChannel: '000000000000000000'



#-------------- Essentials Settings --------------#
# Settings for the EssentialsX integration (requires Essentials to be installed).
Essentials:
  # If false, FactionsChat will not hook into Essentials even when the plugin is present.
  enabled: true
```

### Options Explanation

- **ChatSettings:**  
  Controls various global chat-related settings

    - **ChatFormat:**
        Sets the format that all messages will conform to. Placeholders can be used which will be replaced with actual values.
        Supports PlaceholderAPI placeholders if PAPI is installed, otherwise supports built-in placeholders (see list below in the Placeholders section).

    - **AllowColorCodes:**
        Whether color/formatting codes (including RGB hex color codes) should be allowed.
        Note that players will still need the proper permission to use color/formatting codes in addition to this setting being enabled.

    - **AllowClickableLinks:**
        Whether to allow URLs to be sent in chat that players can click on.
        Note that players will still need the proper permission to be able to send links.

    - **AllowClickableLinksUnderline:**
        Whether to allow URLs that are sent in chat to be underlined or not.

    - **LocalChatRange:**
        Sets how far (in blocks) local chat messages can be seen from the sender.
    
    - **DisableChatReporting:**
        Disables Mojang chat reporting for all messages. Note that this setting only applies to Paper servers. On Spigot, chat reporting is always disabled.

    - **PreserveUpstreamChatComponents:**
        If plugins that modify chat ran their modifications before it reached FactionsChat, this will preserve those modifications.
    
    - **QuickChat:**
        Controls settings related to Quick Chat functionality (sending chat messages to another channel without switching channels)

        - **Prefix:**
            Sets the prefix used by the quick chat mode (defaults to `:`).
        
        - **ErrorOnInvalidMode:**
            If an invalid mode is detected when using quick chat, will present an error. By default his is disabled, so if an invalid mode is entered, the message will go to normal chat.

    - **BlacklistedMiniMessageCommands:**
        A list of commands you do not want to allow in clickable links created by players who are allowed to create clickable links that run commands.
        Players must have permission to create clickable links in the first place, but this gives an extra layer of protection. See the [Permissions](permissions.md) list for more details.

- **ChatPrefixes:**  
  Customize the prefix shown before messages in each channel.
  Use `<fcolor>` to automatically use the faction color based on the current faction relationship that channel represents.

- **TextColors:**  
  Set the color of the message text for each channel.
  Use Minecraft color codes (e.g., `§6` for gold) or `<fcolor>` for faction color.

- **DiscordSRV:**  
  Controls integration settings with DiscordSRV.

    - **enabled:**
        Controls whether the integration in general should be enabled if detected

    - **StaffChannel:**
        If using DiscordSRV, set this to your Discord staff channel's ID to relay staff chat.

- **Essentials:**
  Controls integration settings with EssentialsX.

    - **enabled:**
        Controls whether the integration in general should be enabled if detected

After making changes, use `/f chat reload` to apply them (or `/chat reload` if you are running FactionsChat in Standalone mode).

For more details on formatting and color codes, see the player guide on [Chat Formatting](../player-guide/chat-formatting.md).