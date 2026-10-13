# Commands & permissions

Main command `/agac` (aliases `/agacosmetics`, `/cosmetics`, `/cosmetic`). `/agac help` lists what you may use;
click a line to type it. Add `-s` to run a command silently (`agacosmetics.cmd.silent`).

Every command's permission is `agacosmetics.cmd.<name>`; `.other` allows using it on other players.

## Players (allowed by default)

| Command | Permission |
|---|---|
| `/agac` | opens the menu (`cmd.default`) |
| `/agac menu [menu]` | `cmd.menu` |
| `/agac apply <cosmetic>` / `unapply <slot\|all>` | `cmd.apply` / `cmd.unapply` |
| `/agac dye <slot> [color]` | `cmd.dye` (choosing a colour by command: `cmd.apply.color`) |
| `/agac wardrobe [name]` | `cmd.wardrobe` |
| `/agac hideothers` | `cmd.hideothers` |
| `/agac buy <cosmetic>` | `cmd.buy` |
| `/agac outfit save\|wear\|delete\|list [name]` | `cmd.outfit` |
| `/agac unlocks` | `cmd.unlocks` |

## Staff (op by default)

| Command | Permission |
|---|---|
| `/agac apply\|unapply\|menu\|wardrobe ... <player>` | `.other` of each |
| `/agac hide\|show\|toggle [player]` | `cmd.hide` / `cmd.show` / `cmd.toggle` |
| `/agac give <player> <cosmetic> [7d]` / `take <player> <cosmetic>` | `cmd.give` / `cmd.take` |
| `/agac unlocks <player>` | `cmd.unlocks.other` |
| `/agac adjust ...` | `cmd.adjust` |
| `/agac wardrobe create\|set\|delete\|list`, `setwardrobesetting` | `cmd.setwardrobesetting` |
| `/agac showcase ...` | `cmd.showcase` |
| `/agac import` | `cmd.import` |
| `/agac migrate hmccosmetics [--dry-run] [--no-data] [--keep-existing]` | `cmd.migrate` |
| `/agac bedrock patchpack [path]` | `cmd.bedrock` |
| `/agac reload` | `cmd.reload` |
| `/agac dump [player]` | `cmd.dump` |
| `/agac dataclear <player>` | `cmd.dataclear` (keeps bought/given cosmetics and outfits) |
| `/agac hiddenreasons\|clearhiddenreasons [player]` | as named |
| `/agac disableall <true\|false>` | `cmd.disableall` |
| `/agac debug` | `cmd.debug` |

## Other permissions

| Permission | |
|---|---|
| a cosmetic's `permission:` | wear that cosmetic |
| `agacosmetics.outfits.<n>` | save up to n outfits |
| `agacosmetics.unapplydeath.bypass` | keep cosmetics on death (with `unapply-on-death`) |
| `agacosmetics.wardrobe.<name>` | use a wardrobe (as set in its file) |
| `hmccosmetics.cmd.*` | accepted as well, after migrating |
