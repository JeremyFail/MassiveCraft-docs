![Factions3 Logo](../img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }

# Factions3 Basic API Usage

Below are a couple basic examples of how you can interact with Factions. We recommend diving deeper into the [Factions3 API Documentation](api.md) for more details into how to integrate with the various components of Factions.

### Getting an MPlayer

Players in Factions are represented by the `MPlayer` class. Here is a basic example of several ways you can get a Factions `MPlayer`:

```java
// Import some classes
import java.util.UUID;
import org.bukkit.command.CommandSender;
import org.bukkit.entity.Player;
import com.massivecraft.factions.entity.MPlayer;
 
// Create a few common types of player identifiers
String uuidString = "3defeec7-b3b1-48d9-82bb-2a8903df24e3";
UUID uuid = UUID.fromString(uuidString);
CommandSender commandSender = Bukkit.getConsoleSender();
Player player = event.getPlayer();
String name = "Cayorion";
 
// The faction player data class
MPlayer mplayer;
 
// Fetching the player is this simple
mplayer = MPlayer.get(uuidString);
mplayer = MPlayer.get(uuid);
mplayer = MPlayer.get(commandSender);
mplayer = MPlayer.get(player);

// If you need to fetch a player by the player's name, you will need to use
// a utility from MassiveCore. This is not recommended though as player names
// can change, meaning you could get the wrong ID back if a name has changed.
mplayer = MPlayer.get(com.massivecraft.massivecore.util.IdUtil.getId(name));
```

### Getting a Faction

Factions are represented by the `Faction` class. Here is a basic example of several ways that you can get a `Faction`:

```java
// Import some classes
import org.bukkit.Bukkit;
import org.bukkit.Location;
import com.massivecraft.factions.entity.BoardColl;
import com.massivecraft.factions.entity.Faction;
import com.massivecraft.factions.entity.FactionColl;
import com.massivecraft.factions.entity.MPlayer;
 
// The faction data class
Faction faction = null;
 
// If you have an MPlayer you can get the Faction it belongs to
// NOTE: If the player has no faction Wilderness/None will be returned
MPlayer mplayer = null;
faction = mplayer.getFaction();
 
// The Wilderness (None), Safezone and Warzone can be retrieved like this:
faction = FactionColl.get().getNone();
faction = FactionColl.get().getSafezone();
faction = FactionColl.get().getWarzone();
 
// What faction owns the land at a certain location?
Location location = new Location(Bukkit.getWorld("derp"), 1337, 1337, 1337);
faction = BoardColl.get().getFactionAt(location);
 
// Get a Faction by name
faction = FactionColl.get().getByName("factionName");
 
// Get a Faction by id
String factionId = "3defeec7-b3b1-48d9-82bb-2a8903df24e3";
if (FactionColl.get().containsId(factionId))
{
    faction = FactionColl.get().get(factionId);
}
 
// Iterating over all Factions
for (Faction faction : FactionColl.get().getAll())
{
    // Do something fancy here
}
```

This is just scratching the surface of what you can do with the Factions API. Check out the [Factions3 API Documentation](api.md) for more details of available methods and classes that you can use to integrate with the various components of Factions.