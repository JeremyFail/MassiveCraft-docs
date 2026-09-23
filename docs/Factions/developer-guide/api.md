![Factions3 Logo](../img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }

# Factions3 API Documentation

!!! info Note

    This documentation is not complete, nor is it exhaustive. The Factions3 API is extensive and there are multitudes of different ways you can interact with it and build an integration. Feel free to browse the [source code](https://github.com/JeremyFail/MassiveCraft) and reach out if you have questions.

There are several core components to the Factions3 API. To integrate with Factions you may want to understand how data is stored in the Factions plugin and how you can retrieve that data. The core functionality you'll want to know about are included in the following classes:

- FactionColl (`com.massivecraft.factions.entity.FactionColl`)
- Faction (`com.massivecraft.factions.entity.Faction`)
- MPlayer (`com.massivecraft.factions.entity.MPlayer`)
- BoardColl (`com.massivecraft.factions.entity.BoardColl`)
- Board (`com.massivecraft.factions.entity.Board`)

Note that in the below documentation, we have not included every last bit of detail about every method (we have even left some methods out). Factions is open-source so if you need to integrate with additional features, you can always check the source code of these classes to read up on them more. Additionally, there are other entity classes dealing with configuration, permissions, etc. which you can review the source code if you need to integrate with those features.

## FactionColl

The `FactionColl` class is a collection class that serves as the central management system for all factions in the Factions plugin.

### Public Methods

| Method | Return Type | Description |
|--------|-------------|-------------|
| `get()` | `FactionColl` | **Static** method to get the FactionColl singleton instance |
| `get()` | `Faction` | **Instance** method to get a faction by ID |
| `getAll()` | `Collection<Faction>` | Gets a collection of all factions |
| `getNone()` | `Faction` | Gets the Wilderness (None) faction |
| `getSafezone()` | `Faction` | Gets the SafeZone faction |
| `getWarzone()` | `Faction` | Gets the WarZone faction |
| `getByName(String name)` | `Faction` | Gets a faction by name (case-insensitive) |
| `getRelationNames(Faction faction, Set<Rel> rels)` | `Map<Rel, List<String>>` | Gets faction names grouped by relation type |
| `containsId(String id)` | `boolean` | Returns true if the Factions Collection contains a faction with the given ID |
| `isNameTaken(String name)` | `boolean` | Returns true if the specified name is already in use by another Faction in the Factions Collection |

### Special Factions

The FactionColl manages three special system factions that are automatically created:

1. Wilderness (None) Faction
    - **Purpose**: Represents unclaimed territory
    - **Default Flags**: Permanent, infinite power, allows PvP, explosions, monsters
    - **Default Permissions**: All interactions allowed
2. SafeZone Faction  
    - **Purpose**: Represents protected areas - protected and safe
    - **Default Flags**: Permanent, peaceful, infinite power, no PvP, no explosions, no monsters
    - **Default Permissions**: Interaction allowed but no building
3. WarZone Faction
    - **Purpose**: Represents high-conflict areas - protected, but not safe
    - **Default Flags**: Permanent, infinite power, allows PvP, friendly fire, explosions, monsters
    - **Default Permissions**: Interaction allowed but no building

## Faction

The `Faction` class represents a player faction. It manages faction properties, members, permissions, and territory.

### Public Methods

| Method | Return Type | Description |
|--------|-------------|-------------|
| `get(Object oid)` | `Faction` | Static method to get a Faction instance by ID |
| `isNone()` | `boolean` | Checks if this is the Wilderness (none) faction |
| `isNormal()` | `boolean` | Checks if this is a normal faction (not Wilderness, WarZone, or SafeZone) |
| `isWarZone()` | `boolean` | Checks if this is the WarZone faction |
| `isSafeZone()` | `boolean` | Checks if this is the SafeZone faction |
| `getName()` | `String` | Gets the faction name (sanitized, no color codes) |
| `getNameUnsanitized()` | `String` | Gets the faction name with color codes preserved |
| `getComparisonName()` | `String` | Gets the name formatted for comparison (lowercase, no special chars) |
| `getName(String prefix)` | `String` | Gets the faction name with a prefix |
| `getNameUnsanitized(String prefix)` | `String` | Gets the unsanitized faction name with a prefix |
| `getName(RelationParticipator observer)` | `String` | Gets the faction name formatted for the observer |
| `getNameUnsanitized(RelationParticipator observer)` | `String` | Gets the unsanitized faction name formatted for the observer |
| `setName(String name)` | `void` | Sets the faction name |
| `hasDescription()` | `boolean` | Checks if the faction has a description |
| `getDescription()` | `String` | Gets the faction description |
| `setDescription(String description)` | `void` | Sets the faction description |
| `getDescriptionDesc()` | `String` | Gets a formatted description for display |
| `hasMotd()` | `boolean` | Checks if the faction has a message of the day |
| `getMotd()` | `String` | Gets the faction's message of the day |
| `setMotd(String motd)` | `void` | Sets the faction's message of the day |
| `getMotdDesc()` | `String` | Gets a formatted MOTD for display |
| `getMotdMessages()` | `List<Object>` | Gets MOTD messages for sending to players |
| `getCreatedAtMillis()` | `long` | Gets the faction creation timestamp |
| `setCreatedAtMillis(long createdAtMillis)` | `void` | Sets the faction creation timestamp |
| `getAge()` | `long` | Gets the faction age in milliseconds |
| `getAge(long now)` | `long` | Gets the faction age relative to a timestamp |
| `getCreatedDate()` | `Date` | Gets the faction created date as a `Date` object |
| `getCreatedDateString()` | `String` | Gets the faction created date using the `foundedDateFormat` config value |
| `getWarps()` | `EntityInternalMap<Warp>` | Gets the faction's warps collection |
| `getWarp(Object oid)` | `Warp` | Gets a specific warp by ID |
| `getWarpPS(Object oid)` | `PS` | Gets the location of a specific warp as a `PS` object |
| `addWarp(Warp warp)` | `String` | Adds a warp to the faction |
| `removeWarp(Warp warp)` | `Warp` | Removes a warp from the faction |
| `getPowerBoost()` | `double` | Gets the faction's power boost |
| `setPowerBoost(Double powerBoost)` | `void` | Sets the faction's power boost |
| `getMoney()` | `double` | Gets the faction's money balance |
| `setMoney(Double money)` | `void` | Sets the faction's money balance |
| `getInvitations()` | `EntityInternalMap<Invitation>` | Gets the faction's invitations collection |
| `isInvited(String playerId)` | `boolean` | Checks if a player is invited |
| `isInvited(MPlayer mplayer)` | `boolean` | Checks if an MPlayer is invited |
| `uninvite(String playerId)` | `boolean` | Removes an invitation for a player |
| `uninvite(MPlayer mplayer)` | `boolean` | Removes an invitation for an MPlayer |
| `invite(String playerId, Invitation invitation)` | `void` | Invites a player to the faction |
| `getRanks()` | `EntityInternalMap<Rank>` | Gets the faction's ranks collection |
| `hasRank(Rank rank)` | `boolean` | Checks if the faction has a specific rank |
| `getRank(String rankId)` | `Rank` | Gets a rank by ID |
| `getLeaderRank()` | `Rank` | Gets the leader rank |
| `getLowestRank()` | `Rank` | Gets the lowest rank |
| `getVotes()` | `EntityInternalMap<Vote>` | Gets the faction's votes collection |
| `addVote(Vote vote)` | `void` | Adds a vote to the faction |
| `getVoteByName(String name)` | `Optional<Vote>` | Gets a vote by name |
| `getRelationWishes()` | `Map<String, Rel>` | Gets the faction's relation wishes |
| `setRelationWishes(Map<String, Rel> relationWishes)` | `void` | Sets the faction's relation wishes |
| `getRelationWish(String factionId)` | `Rel` | Gets the relation wish to a faction |
| `getRelationWish(Faction faction)` | `Rel` | Gets the relation wish to a faction |
| `setRelationWish(String factionId, Rel rel)` | `void` | Sets the relation wish to a faction |
| `setRelationWish(Faction faction, Rel rel)` | `void` | Sets the relation wish to a faction |
| `getFlags()` | `Map<MFlag, Boolean>` | Gets the faction's flags |
| `setFlags(Map<MFlag, Boolean> flags)` | `void` | Sets the faction's flags |
| `setFlagIds(Map<String, Boolean> flagIds)` | `void` | Sets flags by ID |
| `getFlag(String flagId)` | `boolean` | Gets a flag value by ID |
| `getFlag(MFlag flag)` | `boolean` | Gets a flag value |
| `setFlag(String flagId, boolean value)` | `Boolean` | Sets a flag value by ID |
| `setFlag(MFlag flag, boolean value)` | `Boolean` | Sets a flag value |
| `getPerms()` | `Map<String, Set<String>>` | Gets the faction's permissions |
| `isPlayerPermitted(MPlayer mplayer, String permId)` | `boolean` | Checks if a player has a permission |
| `isPlayerPermitted(MPlayer mplayer, MPerm mperm)` | `boolean` | Checks if a player has a permission |
| `isFactionPermitted(Faction faction, String permId)` | `boolean` | Checks if a faction has a permission |
| `isFactionPermitted(Faction faction, MPerm mperm)` | `boolean` | Checks if a faction has a permission |
| `getPermitted(String permId)` | `Set<String>` | Gets entities with a permission |
| `getPermitted(MPerm mperm)` | `Set<String>` | Gets entities with a permission |
| `getPermittedPermables(String permId)` | `Set<MPermable>` | Gets permables with a permission |
| `getPermittedPermables(MPerm mperm)` | `Set<MPermable>` | Gets permables with a permission |
| `isPermitted(String permableId, String permId)` | `boolean` | Checks if an entity has a permission |
| `setPermitted(MPermable mpermable, String permId, boolean permitted)` | `boolean` | Sets permission for an entity |
| `setPermitted(MPermable mpermable, MPerm mperm, boolean permitted)` | `boolean` | Sets permission for an entity |
| `setPermittedRelations(String permId, Collection<MPermable> permables)` | `void` | Sets permissions for relations |
| `setPermittedRelations(MPerm perm, Collection<MPermable> permables)` | `void` | Sets permissions for relations |
| `getTax()` | `Map<String, Double>` | Gets the faction's tax configuration |
| `getTaxFor(String id)` | `Double` | Gets tax for a specific ID |
| `getTaxFor(Identified identified)` | `Double` | Gets tax for an identified entity |
| `getTaxForPlayer(MPlayer mplayer)` | `double` | Gets tax for a player |
| `getTaxAndReasonForPlayer(MPlayer mplayer)` | `Optional<Entry<String, Double>>` | Gets tax and reason for a player |
| `setTaxFor(String id, Double value)` | `Double` | Sets tax for a specific ID |
| `setTaxFor(Identified identified, Double value)` | `Double` | Sets tax for an identified entity |
| `describeTo(RelationParticipator observer, boolean ucfirst)` | `String` | Gets description for an observer |
| `describeTo(RelationParticipator observer)` | `String` | Gets description for an observer |
| `getRelationTo(RelationParticipator observer)` | `Rel` | Gets relation to an observer |
| `getRelationTo(RelationParticipator observer, boolean ignorePeaceful)` | `Rel` | Gets relation to an observer |
| `getColorTo(RelationParticipator observer)` | `ChatColor` | Gets color for an observer |
| `getDisplayName(Object senderObject)` | `String` | Gets display name for a sender |
| `getPower()` | `double` | Gets the faction's total power |
| `getPowerMax()` | `double` | Gets the faction's maximum power |
| `getPowerRounded()` | `int` | Gets the faction's power rounded |
| `getPowerMaxRounded()` | `int` | Gets the faction's maximum power rounded |
| `getLandCount()` | `int` | Gets the number of claimed chunks |
| `getLandCountInWorld(String worldName)` | `int` | Gets claimed chunks in a world |
| `hasLandInflation()` | `boolean` | Checks if faction has too much land for power |
| `getClaimedWorlds()` | `Set<String>` | Gets worlds where faction has claims |
| `getMPlayers()` | `List<MPlayer>` | Gets all faction members |
| `getMPlayers(Predicate<? super MPlayer>, Comparator<? super MPlayer>, Integer, Integer)` | `List<MPlayer>` | Gets filtered faction members |
| `getMPlayersWhere(Predicate<? super MPlayer> predicate)` | `List<MPlayer>` | Gets members matching predicate |
| `getMPlayersWhereOnline(boolean online)` | `List<MPlayer>` | Gets online/offline members |
| `getMPlayersWhereOnlineTo(Object senderObject)` | `List<MPlayer>` | Gets members visible to sender |
| `getMPlayersWhereRank(Rank rank)` | `List<MPlayer>` | Gets members with specific rank |
| `getLeader()` | `MPlayer` | Gets the faction leader |
| `getMPlayerIds()` | `Set<String>` | Gets IDs of all faction members |
| `getOnlineCommandSenders()` | `List<CommandSender>` | Gets online command senders |
| `getOnlinePlayers()` | `List<Player>` | Gets online players |
| `promoteNewLeader()` | `void` | Promotes a new leader when current leaves |
| `isAllMPlayersOffline()` | `boolean` | Checks if all members are offline |
| `isAnyMPlayersOnline()` | `boolean` | Checks if any members are online |
| `isFactionConsideredOffline()` | `boolean` | Checks if faction is considered offline |
| `isFactionConsideredOnline()` | `boolean` | Checks if faction is considered online |
| `isExplosionsAllowed()` | `boolean` | Checks if explosions are allowed in faction |
| `sendMessage(Object message)` | `boolean` | Sends message to all faction members |
| `sendMessage(Object... messages)` | `boolean` | Sends messages to all faction members |
| `sendMessage(Collection<Object> messages)` | `boolean` | Sends messages to all faction members |
| `msg(String msg)` | `boolean` | Sends formatted message to faction |
| `msg(String msg, Object... args)` | `boolean` | Sends formatted message with args |
| `msg(Collection<String> msgs)` | `boolean` | Sends collection of messages |
| `clean(String message)` | `String` | Static method to clean a message |

## MPlayer

The `MPlayer` class represents a player in the Factions plugin, storing faction-related data and providing faction-specific functionality for players.

### Public Methods

| Method | Return Type | Description |
|--------|-------------|-------------|
| `get(Object oid)` | `MPlayer` | Static method to get an MPlayer instance by ID |
| `isDefault()` | `boolean` | Checks if this is a default MPlayer with no custom data |
| `getAutoClaimFaction()` | `Faction` | Gets the faction for auto-claiming |
| `setAutoClaimFaction(Faction autoClaimFaction)` | `void` | Sets the faction for auto-claiming |
| `isSeeingChunk()` | `boolean` | Checks if player is seeing chunk borders |
| `setSeeingChunk(boolean seeingChunk)` | `void` | Sets whether player sees chunk borders |
| `resetFactionData()` | `void` | Resets all faction-related data for the player |
| `getLastActivityMillis()` | `long` | Gets the last activity timestamp |
| `setLastActivityMillis(long lastActivityMillis)` | `void` | Sets the last activity timestamp |
| `setLastActivityMillis()` | `void` | Sets last activity to current time |
| `shouldBeCleaned(long now)` | `boolean` | Checks if player should be cleaned up |
| `isFactionOrphan()` | `boolean` | Checks if player's faction no longer exists |
| `getFactionId()` | `String` | Gets the player's faction ID |
| `getFaction()` | `Faction` | Gets the player's faction |
| `hasFaction()` | `boolean` | Checks if player has a faction |
| `setFactionId(String factionId)` | `void` | Sets the player's faction ID |
| `setFaction(Faction faction)` | `void` | Sets the player's faction |
| `getRank()` | `Rank` | Gets the player's rank in their faction |
| `setRank(Rank rank)` | `void` | Sets the player's rank |
| `hasTitle()` | `boolean` | Checks if player has a custom title |
| `getTitle()` | `String` | Gets the player's title |
| `setTitle(String title)` | `void` | Sets the player's title |
| `getPowerBoost()` | `double` | Gets the player's power boost |
| `setPowerBoost(Double powerBoost)` | `void` | Sets the player's power boost |
| `hasPowerBoost()` | `boolean` | Checks if player has a power boost |
| `getPowerMaxUniversal()` | `double` | Gets the universal maximum power |
| `getPowerMax()` | `double` | Gets the player's maximum power |
| `getPowerMin()` | `double` | Gets the player's minimum power |
| `getPowerPerHour()` | `double` | Gets power gained per hour |
| `getPowerPerDeath()` | `double` | Gets power lost per death |
| `getLimitedPower(double power)` | `double` | Limits power to valid range |
| `getPowerMaxRounded()` | `int` | Gets maximum power rounded to integer |
| `getPowerMinRounded()` | `int` | Gets minimum power rounded to integer |
| `getPowerMaxUniversalRounded()` | `int` | Gets universal max power rounded |
| `getDefaultPower()` | `double` | Gets the default starting power |
| `getPower()` | `double` | Gets the player's current power |
| `setPower(Double power)` | `void` | Sets the player's power |
| `getPowerRounded()` | `int` | Gets current power rounded to integer |
| `isMapAutoUpdating()` | `boolean` | Checks if map auto-updates for player |
| `setMapAutoUpdating(Boolean mapAutoUpdating)` | `void` | Sets map auto-updating preference |
| `isOverriding()` | `boolean` | Checks if player is in override mode |
| `setOverriding(Boolean overriding)` | `void` | Sets override mode for player |
| `isTerritoryInfoTitles()` | `boolean` | Checks if territory info titles are enabled |
| `setTerritoryInfoTitles(Boolean territoryInfoTitles)` | `void` | Sets territory info titles preference |
| `isFlying()` | `boolean` | Checks if player is flying in faction territory |
| `setFlying(Boolean flying)` | `void` | Sets faction flight status |
| `getFactionName()` | `String` | Gets the name of player's faction |
| `getNameAndSomething(String color, String something)` | `String` | Gets formatted name with custom suffix |
| `getNameAndFactionName()` | `String` | Gets name with faction name |
| `getNameAndTitle(String color)` | `String` | Gets name with title in specified color |
| `getNameAndTitle(Faction faction)` | `String` | Gets name with title for faction context |
| `getNameAndTitle(MPlayer mplayer)` | `String` | Gets name with title for another player |
| `describeTo(RelationParticipator observer, boolean ucfirst)` | `String` | Gets description for an observer |
| `describeTo(RelationParticipator observer)` | `String` | Gets description for an observer |
| `getRelationTo(RelationParticipator observer)` | `Rel` | Gets relation to an observer |
| `getRelationTo(RelationParticipator observer, boolean ignorePeaceful)` | `Rel` | Gets relation ignoring peaceful status |
| `getColorTo(RelationParticipator observer)` | `ChatColor` | Gets color for an observer |
| `heal(int amnt)` | `void` | Heals the player by specified amount |
| `isInOwnTerritory()` | `boolean` | Checks if player is in their faction's territory |
| `isInOthersTerritory()` | `boolean` | Checks if player is in another faction's territory |
| `isInAllyTerritory()` | `boolean` | Checks if player is in allied territory |
| `isInNeutralTerritory()` | `boolean` | Checks if player is in neutral territory |
| `isInEnemyTerritory()` | `boolean` | Checks if player is in enemy territory |
| `leave()` | `void` | Makes the player leave their faction |
| `tryClaim(Faction newFaction, Collection<PS> pss)` | `boolean` | Attempts to claim chunks for a faction |
| `tryClaim(Faction newFaction, Collection<PS> pss, String formatOne, String formatMany)` | `boolean` | Attempts to claim with custom messages |
| `getClaimInformees(MPlayer msender, Faction... factions)` | `Set<MPlayer>` | Static method to get players to inform about claims |

## BoardColl

The `BoardColl` class is a collection that manages all `Board` entities across different worlds. In essence, it serves as the central management system for all faction territory data. It provides methods to interact with faction territory claims and board data globally.

### Public Methods

| Method | Return Type | Description |
|--------|-------------|-------------|
| `get()` | `BoardColl` | Static method to get the BoardColl singleton instance |
| `getTerritoryAccessAt(PS ps)` | `TerritoryAccess` | Gets territory access information at a location |
| `getFactionAt(PS ps)` | `Faction` | Gets the faction that owns a chunk at the given location |
| `getFactionAt(Location location)` | `Faction` | Gets the faction that owns a chunk at the given location |
| `setTerritoryAccessAt(PS ps, TerritoryAccess territoryAccess)` | `void` | Sets territory access at a location |
| `setFactionAt(PS ps, Faction faction)` | `void` | Sets faction ownership of a chunk |
| `removeAt(PS ps)` | `void` | Removes faction claim at a location |
| `removeAll(Faction faction)` | `void` | Removes all claims for a faction |
| `getChunks(Faction faction)` | `Set<PS>` | Gets all chunks claimed by a faction |
| `getChunks(String factionId)` | `Set<PS>` | Gets all chunks claimed by a faction ID |
| `getFactionToChunks()` | `Map<Faction, Set<PS>>` | Gets mapping of factions to their claimed chunks |
| `getFactionToChunks(boolean withWorld)` | `Map<Faction, Set<PS>>` | Gets faction to chunks mapping, optionally including world info |
| `getWorldToFactionToChunks(boolean withWorld)` | `Map<String, Map<Faction, Set<PS>>>` | Gets world to faction to chunks mapping |
| `getCount(Faction faction)` | `int` | Gets the number of chunks claimed by a faction |
| `getCount(String factionId)` | `int` | Gets the number of chunks claimed by a faction ID |
| `getFactionToCount()` | `Map<Faction, Long>` | Gets mapping of factions to their claim counts |
| `hasClaimed(Faction faction)` | `boolean` | Checks if a faction has any claims |
| `hasClaimed(String factionId)` | `boolean` | Checks if a faction ID has any claims |
| `isBorderPs(PS ps)` | `boolean` | Checks if a location is on a faction border |
| `isAnyBorderPs(Set<PS> pss)` | `boolean` | Checks if any location in the set is on a border |
| `isConnectedPs(PS ps, Faction faction)` | `boolean` | Checks if a location is connected to faction territory |
| `isAnyConnectedPs(Set<PS> pss, Faction faction)` | `boolean` | Checks if any location is connected to faction territory |
| `getClaimedWorlds(Faction faction)` | `Set<String>` | Gets worlds where a faction has claims |
| `getClaimedWorlds(String factionId)` | `Set<String>` | Gets worlds where a faction ID has claims |
| `getNearbyChunks(PS psChunk, int distance)` | `Set<PS>` | Static method to get nearby chunks within distance |
| `getNearbyChunks(Collection<PS> chunks, int distance)` | `Set<PS>` | Static method to get chunks near a collection of chunks |
| `getDistinctFactions(Collection<PS> chunks)` | `Set<Faction>` | Static method to get unique factions from chunk collection |
| `getChunkFaction(Collection<PS> chunks)` | `Map<PS, Faction>` | Static method to map chunks to their owning factions |

## Board

The `Board` class represents faction territory data for a specific world, managing which chunks are claimed by which factions.

### Public Methods

| Method | Return Type | Description |
|--------|-------------|-------------|
| `get(Object oid)` | `Board` | Static method to get a Board instance by ID |
| `isDefault()` | `boolean` | Checks if this is the default (empty) board |
| `getMap()` | `Map<PS, TerritoryAccess>` | Gets unmodifiable map of chunks to territory access |
| `getMapRaw()` | `Map<PS, TerritoryAccess>` | Gets the raw (modifiable) map of chunks |
| `getTerritoryAccessAt(PS ps)` | `TerritoryAccess` | Gets territory access at a specific location |
| `getFactionAt(PS ps)` | `Faction` | Gets the faction owning a chunk at the location |
| `setTerritoryAccessAt(PS ps, TerritoryAccess territoryAccess)` | `void` | Sets territory access at a location |
| `setFactionAt(PS ps, Faction faction)` | `void` | Sets faction ownership of a chunk |
| `removeAt(PS ps)` | `void` | Removes faction claim at a location |
| `removeAll(Faction faction)` | `void` | Removes all claims for a specific faction |
| `getChunks(Faction faction)` | `Set<PS>` | Gets all chunks claimed by a faction |
| `getChunks(String factionId)` | `Set<PS>` | Gets all chunks claimed by a faction ID |
| `getFactionToChunks()` | `Map<Faction, Set<PS>>` | Gets mapping of factions to their chunks |
| `getFactionToChunks(boolean withWorld)` | `Map<Faction, Set<PS>>` | Gets faction to chunks mapping with world option |
| `getWorldToFactionToChunks(boolean withWorld)` | `Map<String, Map<Faction, Set<PS>>>` | Gets world to faction to chunks mapping |
| `getCount(Faction faction)` | `int` | Gets number of chunks claimed by a faction |
| `getCount(String factionId)` | `int` | Gets number of chunks claimed by a faction ID |
| `getFactionToCount()` | `Map<Faction, Long>` | Gets mapping of factions to their claim counts |
| `hasClaimed(Faction faction)` | `boolean` | Checks if a faction has claims in this world |
| `hasClaimed(String factionId)` | `boolean` | Checks if a faction ID has claims in this world |
| `isBorderPs(PS ps)` | `boolean` | Checks if a location is on a faction border |
| `isAnyBorderPs(Set<PS> pss)` | `boolean` | Checks if any location in set is on a border |
| `isConnectedPs(PS ps, Faction faction)` | `boolean` | Checks if location is connected to faction territory |
| `isAnyConnectedPs(Set<PS> pss, Faction faction)` | `boolean` | Checks if any location is connected to faction territory |

## Events

Factions has several events you can listen to in your plugins. You can see them here: [https://github.com/JeremyFail/MassiveCraft/tree/master/Factions/src/com/massivecraft/factions/event](https://github.com/JeremyFail/MassiveCraft/tree/master/Factions/src/com/massivecraft/factions/event)

### Example

Here is a simple example of hooking into a Factions event (in this case an event that is triggered when a faction's name changes):

```java
@EventHandler(priority = EventPriority.NORMAL, ignoreCancelled = true)
public void dissallowRenamingToHurr(EventFactionsNameChange event)
{
    // If the new faction name is "FooBar" ...
    if (!"FooBar".equalsIgnoreCase(event.getNewName())) return;

    // ... then cancel the event ...
    event.setCancelled(true);
	
    // ... and inform the command sender.
    event.getSender().sendMessage("You may not rename your faction to FooBar!");
}
```
