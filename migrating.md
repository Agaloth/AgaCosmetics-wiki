# Migrating from HMCCosmetics

AgaCosmetics reads the HMCCosmetics formats, so a migration takes a few minutes and no restart.

1. Put AgaCosmetics in `plugins/` next to the `HMCCosmetics` folder and start the server.
2. Preview: `/agac migrate hmccosmetics --dry-run`, then read `plugins/AgaCosmetics/migration-report.txt`.
3. Migrate: `/agac migrate hmccosmetics`
4. Remove HMCCosmetics (and HibiscusCommons if nothing else uses it), and restart when convenient.

## What is carried over

- Cosmetics, menus and wardrobes
- `config.yml` settings that have an AgaCosmetics equivalent
- Messages and translations you changed (untouched HMC defaults use the AgaCosmetics wording)
- Every player's saved cosmetics, from HMC's SQLite or MySQL database
- Before writing anything, the current AgaCosmetics files are copied to `backups/`

Options: `--dry-run` (report only), `--no-data` (skip player data), `--keep-existing` (don't overwrite files that
already exist in AgaCosmetics).

## What keeps working

- **Permissions**: cosmetics keep their `permission:`; `hmccosmetics.cmd.*` nodes are accepted too
  (`compatibility.accept-hmccosmetics-permissions`).
- **Placeholders**: `%HMCCosmetics_...%` is answered next to `%agacosmetics_...%`
  (`hook-settings.placeholderapi.register-hmccosmetics-alias`).
- **Item references**: `material: hmccosmetics:<id>` in menus works like `agacosmetics:<id>`.
- **Storage**: player data uses the HMC row format.

## What is different

- ModelEngine balloon models are drawn by ModelEngine when it is installed (the item is shown otherwise).
- HMCColor is not used; the built-in dye menu is.
- Emotes and the Vulcan / BetterHud hooks are not included.

Offline check without a server: `./gradlew migrateCheck -Phmc=<HMCCosmetics folder> -Pout=<output folder>`.
