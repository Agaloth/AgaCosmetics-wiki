# Outfits

Players save what they wear and put the whole look back on with one click.

## In the menu

`/agac` → **Outfits**:

- empty slot: click to save your current look
- saved outfit: click to wear it, right-click to save your current look over it, shift + right-click to delete

## By command

```
/agac outfit save <name>      letters, numbers, - and _ (up to 16)
/agac outfit wear <name>
/agac outfit delete <name>
/agac outfit list
```

Wearing an outfit replaces the whole look: its cosmetics go on and the other slots are emptied. Cosmetics the
player can no longer wear (rental over, permission removed, cosmetic deleted) are skipped, and the player is
told which.

## Limits

`outfits.max` in `config.yml` (default 5). Give someone more with `agacosmetics.outfits.<n>`; the highest one
counts. `0` turns outfits off.

Outfits are stored with the player's data (SQLite or MySQL).
