# Wardrobes

In a wardrobe, players see themselves as a mannequin that turns slowly, choose cosmetics from the menu, and
sneak to leave. The mannequin and camera exist only for that player.

## Setting one up

1. Stand where the mannequin should stand, facing the way it should face.
2. `/agac wardrobe create <name>`. The camera is placed 3.5 blocks in front of it.
3. Try it: `/agac wardrobe <name>`.

Fine-tune: `/agac wardrobe set <name> npc|camera|leave` moves that point to where you stand;
`/agac wardrobe set <name> menu|permission|distance <value>`; `/agac wardrobe delete <name>`, `list`.

## Entering

- `/agac wardrobe <name>` (or with only one wardrobe: `/agac wardrobe`)
- a WorldGuard region with the flag `cosmetic-wardrobe = <name>`
- `distance` in the wardrobe file limits how far from it players may be (-1 = anywhere)

## Options (`config.yml` → `wardrobe`)

| Option | |
|---|---|
| `rotation-speed` | degrees per tick the mannequin turns |
| `return-last-location` | go back where you entered instead of the leave point |
| `unchecked-wardrobe-cosmetics` | try locked cosmetics inside (taken off on leave) |
| `menu-options.enter-open-menu` | open the menu on entering |
| `bossbar` | a bar with instructions |
| `transition` | a short fade (Java only; Bedrock needs JSON UI for it) |
| `prevent-damage`, `damage-kicked`, `equip-pumpkin`, `gamemode-options` | as named |

If the server stops while someone is in a wardrobe, they get their location and game mode back when they
join again.
