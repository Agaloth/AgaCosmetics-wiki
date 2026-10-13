# Showcases

Mannequins that wear a look, for your spawn, a shop or an event. They are packets only (no NPC plugin needed),
shown to players within `showcases.view-distance` blocks.

## Making one

1. Put on the look you want to show.
2. Stand where the showcase should stand.
3. `/agac showcase create <id>`. It copies your cosmetics, position and skin.

```
/agac showcase dress <id>                 copy your current look onto it
/agac showcase move <id>                  move it to where you stand
/agac showcase skin <id> <player>         any player's skin (online or not)
/agac showcase name <id> <text|none>      a name above it (MiniMessage)
/agac showcase click <id> try_on|menu|none
/agac showcase spin <id> <degrees per second>   0 = stand still
/agac showcase delete <id>
/agac showcase list
```

## Clicking it

- `try_on` (default): the player wears the whole look for `preview-seconds`, nothing is saved
- `menu`: opens the cosmetics menu
- `none`: nothing

Showcases support every slot: armor, held items, backpacks, balloons, shoulder pets, auras and animations.
They are saved in `showcases.yml`.
