# Bedrock

Bedrock players (through Geyser) see the same display-entity cosmetics as Java players, drawn by the
GeyserDisplayEntity extension.

## Setup

1. Install **Geyser** (and Floodgate if you use it) and the official **GeyserDisplayEntity** extension.
2. Convert your Java resource pack for Geyser as usual (e.g. with your item plugin's converter).
3. Also put the **AgaCosmetics jar** in Geyser's `extensions/` folder. On every Geyser start it hands Geyser a
   patched copy of each converted pack, so item models attach to display entities correctly. Your original packs
   are not changed. This works with Geyser-Spigot, Geyser on a proxy and Geyser Standalone, also on hosts
   without SSH.
4. Restart. Bedrock players download the patched pack automatically.

Alternatives to step 3: `/agac bedrock patchpack [path]` patches the packs in `plugins/Geyser-Spigot/packs/`,
and `java -jar AgaCosmetics.jar patchpack <folder or pack>` does it from a terminal. Patching twice is harmless.

## Position fixes

Bedrock sometimes draws a model a little differently. Fix it with `/agac adjust` as a Bedrock player (it picks
Bedrock automatically) or choose **Bedrock** in the adjust menu. Bedrock and Java fixes are kept separately.
Pixels mean the same on both: 16 = one block. See [Positioning](adjusting.md).

## Menus as forms

With `bedrock.forms: true`, Bedrock players get the cosmetics menu as native forms: categories → cosmetics
with their status and price → wear, styles, dye, buy, try on; plus outfits and the hide toggles. Your own
HMC-format menu files still open as chests.

Give buttons an image with `bedrock-icon:` in a cosmetic: a texture path from a Bedrock pack
(`textures/...`) or an `https://` image URL.

## Options (`config.yml` → `bedrock`)

| Option | |
|---|---|
| `detection` | `AUTO` (Floodgate, then Geyser), `FLOODGATE`, `GEYSER`, `NONE` |
| `show-firstperson` | show Bedrock wearers the first-person backpack model (off: they see the normal backpack) |
| `rotation` | `BODY` or `HEAD`: what Bedrock backpacks turn with |
| `forms` | menus as forms |
| `offsets.<part>` | global fixes for Bedrock viewers |

Chest menu titles that use font glyphs (shifts, backgrounds) are shown as plain readable titles on Bedrock.
