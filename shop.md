# Shop, gifts & rentals

## Selling cosmetics

Give a cosmetic a price:

```yaml
crown:
  slot: HELMET
  price: 500
  currency: coinsengine:gems     # optional, default: shop.currency in config.yml
  item: { material: nexo:crown }
```

Players buy it from the menu (with a confirm screen, `shop.confirm`) or with `/agac buy <id>`, and it's put on
straight away.

| Currency | |
|---|---|
| `vault` | any Vault economy (EssentialsX, CMI, VaultUnlocked...) |
| `coinsengine:<currency id>` | a CoinsEngine currency |
| `levels` | experience levels, needs no plugin |

**Who can wear a priced cosmetic**: players who bought it, and players with its `permission` if it has one.
A cosmetic with a price and no permission is locked until bought.

Bought cosmetics are saved with the player in the AgaCosmetics database. With MySQL they follow players across
every server that shares it. No permission plugin is involved.

## Gifts and rentals

```
/agac give <player> <cosmetic>            for good
/agac give <player> <cosmetic> 7d         for 7 days (30m, 12h, 7d, 2w...)
/agac take <player> <cosmetic>            take it back
/agac unlocks [player]                    what a player owns, with time left
```

- Works for offline players (crates, vote rewards, store packages from Tebex and similar).
- Giving a rental again extends it to the later end; a permanent unlock stays permanent.
- When a rental runs out the player is told and the cosmetic comes off by itself.
- `/agac take` only removes bought or given cosmetics; access through a permission stays.

## Placeholders

`%agacosmetics_price_<id>%`, `%agacosmetics_rental_<id>%` (time left), `%agacosmetics_owned%`,
`%agacosmetics_collection%` and more: [Placeholders](placeholders.md).
