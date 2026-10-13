# Placeholders

With PlaceholderAPI, use `%agacosmetics_<name>%`. `%hmccosmetics_<name>%` works too, so scoreboards made for
HMCCosmetics keep working. Inside AgaCosmetics menus they work even without PlaceholderAPI.

| Placeholder | Gives |
|---|---|
| `current_<slot>` | id of the worn cosmetic in a slot |
| `current_<slot>_name` | its item name |
| `equipped_<id>` / `using_<id>` | yes/no: wearing that cosmetic |
| `unlocked_<id>` | yes/no: may wear it (permission, bought or given) |
| `amount` | how many cosmetics are worn |
| `hidden` | yes/no: own cosmetics hidden |
| `in_wardrobe` | yes/no |
| `owned` / `owned_<slot>` | how many cosmetics are unlocked |
| `total` / `total_<slot>` | how many cosmetics exist |
| `collection` / `collection_<slot>` | percent unlocked (0-100) |
| `outfits` / `outfits_max` | saved outfits / how many may be saved |
| `price_<id>` | price with currency ("500 Coins"), or none |
| `rental_<id>` | time left on a rental ("3d 4h"), or none |

Slots: `helmet`, `chestplate`, `leggings`, `boots`, `offhand`, `mainhand`, `backpack`, `balloon`, `shoulder`,
`aura`. The words for yes/no/none are in `messages.yml` under `placeholders`.
