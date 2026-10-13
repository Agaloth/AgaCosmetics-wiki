# Menus

## The built-in menu

`/agac` opens the **browse** menu (`default-menu: browse` in `config.yml`). It builds itself from your cosmetics,
so every cosmetic is reachable without writing a menu file:

- a category page per slot, then paged lists
- left click: wear / take off; shift + right click a worn dyeable cosmetic: dye
- a cosmetic with [styles](variants.md) opens its style picker
- locked cosmetics: right click to **try it on** for `preview-seconds`; left click to **buy** if it has a price
- **Outfits** button ([Outfits](outfits.md)), a filter for unlocked cosmetics only, take-off buttons
- toggles to hide your own cosmetics and to hide everyone else's

Bedrock players get the same menu as native forms ([Bedrock](bedrock.md)). All its text is under `gui.browse` in
`messages.yml`.

## Your own menus

Menu files in `menus/` use the HMCCosmetics format and open with `/agac menu <id>`. Set
`default-menu: <id>` to make one the main menu.

```yaml
title: "<dark_gray>Hats"
rows: 3
permission: cosmetics.menu.hats   # optional
refresh-rate: 20                  # optional, ticks
items:
  witch_hat:
    slots: [10]
    type: cosmetic                # click wears / takes off "cosmetic"
    cosmetic: witch_hat
    item: { material: agacosmetics:witch_hat }   # the cosmetic's own item
    equipped-item: { ... }        # optional, while worn
    locked-item: { ... }          # optional, while locked
  close:
    slots: [26]
    type: empty                   # only runs actions
    item: { material: BARRIER, name: "<error>Close" }
    actions:
      any: ["[CLOSE]"]
```

Action lists: `any`, `left-click`, `right-click`, `shift-left-click`, `shift-right-click`, `on-equip`,
`on-unequip`, `no-permission`.

| Action | Does |
|---|---|
| `[MENU] <id>` | open another menu (`browse` works) |
| `[SOUND] <sound> [volume] [pitch]` | play a sound |
| `[MESSAGE] <text>` | send a MiniMessage line |
| `[CONSOLE-COMMAND] <cmd>` / `[PLAYER-COMMAND] <cmd>` | run a command (`%player%` works) |
| `[CLOSE]` | close the menu |
| `[EQUIP] <id>` / `[UNEQUIP] <slot\|all>` | wear / take off |
| `[EQUIP-RANDOM] <slot>` | wear a random unlocked cosmetic of that slot |
| `[HIDE]` / `[SHOW]` / `[TOGGLE]` | your own cosmetics |
| `[DYE] <slot>` | open the dye menu |

Placeholders (PlaceholderAPI and [our own](placeholders.md)) work in names and lore.

## Dye menu

`menus/functional/internal_dye_menu.yml`: `$` slots hold the main colours, `%` slots the shades of the last
clicked colour. Every click dyes right away.
