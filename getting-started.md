# Installing

## Requirements

- **Paper or Folia 1.21.8 or newer** (tested on 1.21.8 and 1.21.11). Spigot is not supported.
- **Java 21** or newer.
- Nothing else. PacketEvents is included in the jar.

Optional plugins AgaCosmetics works with: Nexo, ItemsAdder, Oraxen, CraftEngine, MythicMobs, MMOItems, Denizen,
eco, ModelEngine, LibsDisguises, Geyser + Floodgate + GeyserDisplayEntity, Vault or CoinsEngine, PlaceholderAPI,
WorldGuard. See [Compatible plugins](compatibility.md).

## Steps

1. Put `AgaCosmetics-<version>.jar` in `plugins/` and start the server.
2. Join and run `/agac`. The built-in menu lists the example cosmetics.
3. Add your own cosmetics in `plugins/AgaCosmetics/cosmetics/`, or drop a pack into
   `plugins/AgaCosmetics/import/` ([Adding cosmetic packs](packs.md)). Files reload by themselves.
4. Bedrock players? Follow [Bedrock](bedrock.md).

{% hint style="warning" %}
**Don't use /reload or PlugMan**

Update by replacing the jar and restarting. Hot-reloading breaks PacketEvents' connection handling until
the next restart. Paper's `plugins/update/` folder lets you drop the new jar in while the server runs.
{% endhint %}

## The files

| File / folder | What it holds |
|---|---|
| `config.yml` | Settings, see [Configuration](configuration.md) |
| `messages.yml` | Every text players read, plus the colour palette ([Messages & colours](messages.md)) |
| `cosmetics/` | Your cosmetics, any `.yml` files and sub folders ([Cosmetic files](cosmetics.md)) |
| `menus/` | Menus in HMCCosmetics format ([Menus](menus.md)) |
| `wardrobes/` | Wardrobes ([Wardrobes](wardrobes.md)) |
| `showcases.yml` | Showcase mannequins, written by `/agac showcase` |
| `import/` | Drop packs here to install them |
| `data.db` | Player data (SQLite). MySQL is available in `config.yml`. |

## Updating

Replace the jar and restart. When a new version changes the layout of `config.yml` or `messages.yml`, the files
are rewritten once: anything you changed is kept, and the old files go to `backups/`.
