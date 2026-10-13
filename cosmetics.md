# Cosmetic files

Every `.yml` file in `plugins/AgaCosmetics/cosmetics/` (sub folders included) is loaded. The format is the
HMCCosmetics one, so existing files work as they are. Saving a file reloads it.

```yaml
witch_hat:                      # the id, used in commands, menus and placeholders
  slot: HELMET
  permission: "cosmetics.witch_hat"   # leave out = everyone may wear it
  dyeable: true
  item:
    material: nexo:witch_hat
    name: "<primary>Witch Hat"
```

## Slots

| Slot | Shown as |
|---|---|
| `HELMET`, `CHESTPLATE`, `LEGGINGS`, `BOOTS` | the armor slot (the real armor stays on the server) |
| `OFFHAND`, `MAINHAND` | the held item (only while the hand is empty, see `slot-options`) |
| `BACKPACK` | a model on the back that turns with the body; optional first-person model |
| `BALLOON` | a floating model with a lead |
| `SHOULDER` | a small model on the shoulder ([Shoulder pets & auras](shoulder-and-auras.md)) |
| `AURA` | particles around the player ([Shoulder pets & auras](shoulder-and-auras.md)) |

## Options

| Option | |
|---|---|
| `permission` | Needed to wear it. Without a permission (and without a price) it's free for everyone. |
| `dyeable` | Players can recolour it (dye menu, `/agac dye`). |
| `item` | The item, see below. |
| `firstperson-item` | Backpacks: the model the wearer sees above their head. |
| `height` | Backpacks: how high the first-person model sits (default 5, like HMCCosmetics). |
| `show-lead` | Balloons: draw a lead (default `cosmetic-settings.balloon-lead-default`). |
| `model` | Balloons: a ModelEngine model to draw instead of the item (needs ModelEngine). |
| `balloon-offset` | Balloons: `"x,y,z"` from the player, in blocks. |
| `display-transform` | The item display transform (default `HEAD`). |
| `price`, `currency` | Sell it: [Shop](shop.md). |
| `variants` | Other styles: [Styles](variants.md). |
| `animation`, `animations`, `frames` | Movement: [Animations](animations.md). |
| `particle` | Auras: [Shoulder pets & auras](shoulder-and-auras.md). |
| `bedrock-icon` | Button image in Bedrock forms: [Bedrock](bedrock.md). |
| `display` | Position fixes, written for you by `/agac adjust`: [Positioning](adjusting.md). |

## Items

```yaml
item:
  material: PAPER          # or nexo:<id> | itemsadder:<ns>:<id> | oraxen:<id> | mythicmobs:<id>
                           # | mmoitems:<TYPE>:<id> | craftengine:<ns>:<id> | denizen:<item> | eco:<key>
  model-data: 12           # custom model data
  model-id: ns:key         # item_model component (alias: item-model)
  name: "<primary>Name"    # MiniMessage; theme colours work
  lore: ["<muted>A line"]
  color: "#ff0000"         # leather, potions, maps... (also "r,g,b")
  glowing: true
  item-flags: [HIDE_ATTRIBUTES]
  enchants: { sharpness: 1 }
  hide-tooltip: false
  tooltip-style: ns:key
  texture: <base64>        # player heads
  owner: PlayerName        # player heads
```

Items from item plugins are picked up the moment those plugins finish loading their items, and again whenever
they reload. See [Compatible plugins](compatibility.md) for every plugin and its syntax.

{% hint style="success" %}
**Chat shows the item's name**

Messages such as "Now wearing ..." use the item's name, so give items a readable `name`.
{% endhint %}
