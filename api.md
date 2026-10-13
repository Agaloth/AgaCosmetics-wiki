# Developer API

Everything another plugin needs is in one class, `me.agaloth.agacosmetics.api.AgaCosmeticsAPI`, plus the events in
`me.agaloth.agacosmetics.api.event`. These names stay the same between versions; the rest of the plugin is internal
and may change (or be obfuscated) at any time, so only use the API package.

## Setup

Add the AgaCosmetics jar as a `compileOnly` dependency:

```kotlin
dependencies {
    compileOnly(files("libs/AgaCosmetics-1.0.0.jar"))
}
```

and in your `plugin.yml`:

```yaml
softdepend: [AgaCosmetics]
```

Call the API on the main thread (on Folia: the player's region thread). Methods that may write to the database for
offline players return a `CompletableFuture`.

## Quick start

```java
Cosmetic hat = AgaCosmeticsAPI.cosmetic("witch_hat").orElseThrow();

AgaCosmeticsAPI.give(player.getUniqueId(), hat, Duration.ofDays(7)); // a 7 day rental (null = for good)
AgaCosmeticsAPI.equip(player, hat);                                   // checks the permission / ownership
AgaCosmeticsAPI.hide(player);                                         // hide while your minigame runs
AgaCosmeticsAPI.show(player);
```

## Methods

### Cosmetics

| Method | Returns |
|---|---|
| `cosmetic(String id)` | `Optional<Cosmetic>`; styles are `base:style` |
| `cosmetics()` | every cosmetic, styles included |
| `cosmetics(CosmeticSlot slot)` | the base cosmetics of one slot |

### What players wear

| Method | Notes |
|---|---|
| `isLoaded(Player)` | false until the player's data is loaded (see `CosmeticUserLoadEvent`) |
| `equipped(Player, CosmeticSlot)` | `Optional<Cosmetic>` |
| `equipped(Player)` | `Map<CosmeticSlot, Cosmetic>` |
| `equip(Player, Cosmetic)` | false if not allowed, cancelled or not loaded |
| `equip(Player, Cosmetic, Color, boolean checkPermission)` | `checkPermission=false` puts it on even if not owned |
| `unequip(Player, CosmeticSlot)` / `unequipAll(Player)` | |
| `dye(Player, CosmeticSlot, Color)` | `null` removes the dye |
| `tryOn(Player, Cosmetic)` | temporary preview, not saved, works on locked cosmetics |

### Visibility

| Method | Notes |
|---|---|
| `hide(Player)` / `show(Player)` | uses `HiddenReason.PLUGIN`; saved with the player until you show them again |
| `isHidden(Player)` | true when hidden for any reason (command, world, wardrobe, disguise...) |
| `hidesOthers(Player)` / `setHidesOthers(Player, boolean)` | whether they hide other players' cosmetics |

### Ownership & shop

| Method | Notes |
|---|---|
| `canUse(Player, Cosmetic)` | permission, bought or given |
| `owns(Player, Cosmetic)` | bought or given only (permissions don't count) |
| `give(UUID, Cosmetic, Duration)` | works for offline players; `null` duration = for good |
| `take(UUID, Cosmetic)` | completes with false if they didn't have it |
| `buy(Player, Cosmetic)` | `Shop.Result`: `BOUGHT`, `ALREADY_OWNED`, `NOT_FOR_SALE`, `NO_CURRENCY`, `TOO_POOR`, `FAILED`, `CANCELLED`; sends no messages |
| `price(Cosmetic)` | `Optional<String>` as players read it ("500 Coins") |

### Outfits

| Method | Notes |
|---|---|
| `outfits(Player)` | saved outfit names |
| `saveOutfit(Player, String)` | names: letters, numbers, `-`, `_`, up to 16; ignores the outfit limit |
| `wearOutfit(Player, String)` | `Optional<List<String>>` of skipped cosmetics; empty if there's no such outfit |
| `deleteOutfit(Player, String)` | |

### Menus & wardrobes

| Method | Notes |
|---|---|
| `openMenu(Player)` | the main menu (a form for Bedrock players) |
| `openMenu(Player, String menu)` | false if there's no such menu |
| `toggleWardrobe(Player, String wardrobe)` / `inWardrobe(Player)` | |

### Items & platform

| Method | Notes |
|---|---|
| `registerItemSource(String namespace, Function<String, ItemStack>)` | cosmetics can then use `material: <namespace>:<id>` |
| `unregisterItemSource(String namespace)` | |
| `isBedrock(Player)` | whether AgaCosmetics treats them as a Geyser player |
| `reload()` | like `/agac reload` |

```java
// cosmetics.yml can now use  material: myitems:ruby_crown
AgaCosmeticsAPI.registerItemSource("myitems", id -> MyItems.get(id)); // return null when there's no such item
```

## Events

All in `me.agaloth.agacosmetics.api.event`.

| Event | Cancellable | Extra |
|---|---|---|
| `CosmeticEquipEvent` | yes | `getUser()`, `getCosmetic()`, `setCosmetic(...)` to swap what is put on |
| `CosmeticPostEquipEvent` | no | `getUser()`, `getCosmetic()` |
| `CosmeticUnequipEvent` | yes | `getUser()`, `getCosmetic()` |
| `CosmeticHideEvent` / `CosmeticShowEvent` | yes | `getUser()`, `getReason()` (`HiddenReason`) |
| `CosmeticUserLoadEvent` | no | `getUser()`; the player's data finished loading |
| `CosmeticPurchaseEvent` | yes | `getPlayer()`, `getCosmetic()`, `getPrice()`, `setPrice(double)` (discounts!) |
| `CosmeticUnlockEvent` | no | `getPlayerId()`, `getCosmetic()`, `getUntil()`, `isRental()`; bought, given or rented |
| `MenuOpenEvent` | yes | `getUser()`, `getMenu()` |
| `WardrobeEnterEvent` / `WardrobeLeaveEvent` | enter: yes | `getUser()`, `getWardrobe()` |

```java
@EventHandler
public void onPurchase(CosmeticPurchaseEvent event) {
    if (event.getPlayer().hasPermission("vip.discount")) event.setPrice(event.getPrice() * 0.8);
}

@EventHandler
public void onEquip(CosmeticEquipEvent event) {
    if (event.getCosmetic().id().startsWith("event_") && !eventRunning) event.setCancelled(true);
}
```
