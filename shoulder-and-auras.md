# Shoulder pets & auras

## Shoulder pets

`slot: SHOULDER` puts a small model on the player's shoulder. It rides the player like a backpack, so it turns
with the body in the same tick.

```yaml
parrot_pet:
  slot: SHOULDER
  item: { material: nexo:parrot_pet }
  animation: { type: TILT, amount: 10, seconds: 2 }
```

Placement: `display.shoulder-base-height` (1.3 blocks) and `display.shoulder-base-scale` (0.4) in `config.yml`,
and the global `shoulder` correction (left shoulder by default: `x: -6`). Fine-tune one cosmetic with
`/agac adjust shoulder ...` or the adjust menu.

## Auras

`slot: AURA` draws particles around the player. Particles are sent only to the wearer and the players who can
see them, so players who hide others' cosmetics don't get them.

```yaml
golden_halo:
  slot: AURA
  item: { material: GLOWSTONE_DUST }     # menu icon (optional)
  particle:
    type: DUST              # any Bukkit particle name
    color: "#FFD27F"        # DUST and coloured particles
    size: 0.8               # DUST
    shape: HALO
    every: 2                # ticks between bursts
```

| Shape | Looks like | Defaults |
|---|---|---|
| `AROUND` | random particles around the body | height 1.0, spread 0.4 |
| `HALO` | a turning ring above the head | height 2.15, radius 0.4 |
| `ORBIT` | two points circling the waist | height 1.0, radius 0.8 |
| `TRAIL` | left at the feet while walking | height 0.1 |
| `SPIRAL` | climbing around the body | radius 0.8 |

Other options: `count`, `radius`, `height`, `spread`, `speed`.

## Player size

All cosmetics, including auras, grow and shrink with the player's scale attribute (size potions, origins,
`/attribute`). Turn it off with `display.scale-with-player: false`.
