# Configuration

`config.yml` explains each option in place; this page is the overview. Most changes apply on save.

| Section | What it controls |
|---|---|
| `default-menu` | the menu `/agac` opens (`browse` = built-in) |
| `database-settings` | `sqlite` (default) or `mysql`; MySQL shares player data across servers |
| `cosmetic-settings` | try-on length (`preview-seconds`), creative hint, disabled worlds and game modes, poses that hide backpacks, balloon defaults, `slot-options` |
| `auto-reload`, `import` | reload edited files by themselves; install packs from `import/` |
| `display` | how models are placed (HMCCosmetics armor-stand parity), shoulder placement, `scale-with-player`, `animation-interval`, global Java fixes |
| `bedrock` | detection, first-person model, rotation, forms, global Bedrock fixes |
| `shop` | on/off, default currency, confirm screen |
| `outfits` | how many outfits a player may save |
| `showcases` | how far away showcases are shown |
| `menu-settings` | click cooldown, shading (glyph backgrounds), which click equips / dyes |
| `dye-menu` | on/off and title |
| `wardrobe` | see [Wardrobes](wardrobes.md) |
| `hook-settings` | Nexo / ItemsAdder reloads, WorldGuard move checks, `%HMCCosmetics_...%` alias |
| `compatibility` | accept `hmccosmetics.*` permissions |

## Slot options

```yaml
slot-options:
  helmet:  { add-enchantments: false, require-empty: false }
  offhand: { add-enchantments: false, require-empty: true }
```

`require-empty`: only show the cosmetic while the real slot is empty. `add-enchantments`: keep the real item's
enchantment glint on the cosmetic.

## Display defaults

`base-height: 1.6885` and `base-scale: 0.625` reproduce exactly where HMCCosmetics' armor stands drew a model,
so packs made for HMCCosmetics line up without changes. Balloons use half of both, like HMC's small armor
stands.

## Updates

When a new version adds options, `config.yml` and `messages.yml` are rewritten once in the new layout. Every
value you changed is kept; the old files are saved in `backups/`.
