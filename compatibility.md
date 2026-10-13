# Compatible plugins

## Item plugins

Use their items as `material:` in any cosmetic or menu item:

| Plugin | `material:` | Tested |
|---|---|---|
| **Nexo** | `nexo:<id>` | yes |
| **ItemsAdder** | `itemsadder:<namespace>:<id>` (or `ia:`) | yes |
| **Oraxen** | `oraxen:<id>` | no |
| **MythicMobs** | `mythicmobs:<item id>` (or `mythic:`, `mm:`) | yes (5.14) |
| **MMOItems** | `mmoitems:<TYPE>:<id>` (or `mi:`) | no |
| **CraftEngine** | `craftengine:<namespace>:<id>` (or `ce:`) | no |
| **Denizen** | `denizen:<script item>` (anything Denizen reads as an item) | no |
| **eco** (EcoItems and the other Auxilor plugins) | `eco:<lookup key>`, e.g. `eco:ecoitems:my_item` | no |

Items appear as soon as their plugin has loaded them, and again whenever it reloads. Until then those cosmetics
are listed as loading. "Tested" means checked live on a server; the others follow the plugin's published API.

## Other plugins

| Plugin | What it does with AgaCosmetics |
|---|---|
| **ModelEngine 4** | balloons with `model: <model id>` are drawn by ModelEngine (the HMCCosmetics format), moving and turning with the player; the lead still works. Bedrock players see them through GeyserModelEngine. Tested with R4.2.0. |
| **LibsDisguises** | while a player is disguised, their cosmetics are hidden; they come back when the disguise ends. Tested with 26.9.26 (it needs PacketEvents 2.14+). |
| **Geyser / Floodgate** | Bedrock detection and form menus; the jar is also a Geyser extension |
| **GeyserDisplayEntity** | draws display-entity cosmetics for Bedrock players |
| **Vault** | currency `vault` for the shop (any Vault economy) |
| **CoinsEngine** | currency `coinsengine:<currency id>` |
| **PlaceholderAPI** | [placeholders](placeholders.md), also as `%hmccosmetics_...%` |
| **WorldGuard** | flags `cosmetic-enable` (hide cosmetics in a region) and `cosmetic-wardrobe` (enter a wardrobe in a region) |
| **HMCCosmetics** | one-command migration of everything, see [Migrating](migrating.md) |
| **Vanish plugins** (PremiumVanish, SuperVanish, CMI, EssentialsX) | vanished players are never sent to others, so their cosmetics aren't either. This follows from how cosmetics are tracked; it was not tested with each plugin. |
| **ViaVersion / ViaBackwards** | players on other client versions see cosmetics |
| **Folia** | supported |

## Not supported

| Plugin | Note |
|---|---|
| HMCColor | the built-in dye menu (and the Bedrock dye form) is used |
| Emotes | not included |
