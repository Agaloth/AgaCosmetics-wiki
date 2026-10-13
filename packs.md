# Adding cosmetic packs

Packs made for HMCCosmetics (MCModels and others) install without a restart.

1. Drop the pack (zip or folder) into `plugins/AgaCosmetics/import/`.
2. Within a few seconds (or right away with `/agac import`):
    - cosmetic files go to `cosmetics/<pack>/`, menus to `menus/`
    - Nexo / ItemsAdder files are copied into those plugins, and `nexo reload all` / `iazip` is run
    - the pack is moved to `import/done/`
3. Java players see the new cosmetics at once. Bedrock players need the items in your Geyser pack:
   convert it as usual and restart Geyser ([Bedrock](bedrock.md)).

Turn the copying into item plugins off with `import.install-nexo-files` / `import.install-itemsadder-files`.

Editing any file in `cosmetics/`, `menus/` or `wardrobes/` reloads it by itself (`auto-reload.enabled`).
