# Messages & colours

Every text players read is in `messages.yml`, in [MiniMessage](https://docs.advntr.dev/minimessage/format.html)
format. Set a message to `""` to turn it off. Words in `<angle brackets>` such as `<cosmetic>` are filled in.

## The colour palette

The top of `messages.yml` defines colour tags you can use anywhere: messages, menu titles, item names and lore.

```yaml
colors:
  primary: "#B9A7FF"   # headings, commands
  accent: "#F5A8E8"
  text: "#CBC6DA"      # normal text
  muted: "#8C879C"     # hints
  value: "#FFFFFF"     # names and numbers
  success: "#8FE3A5"
  warn: "#FFD27F"
  error: "#FF8F8F"
```

```yaml
equip-cosmetic: "%prefix% <text>Now wearing <value><cosmetic></value>."
```

Change a colour once and everything using it follows. Hex or colour names both work.

## Sections

| Keys | |
|---|---|
| `prefix` | put in front of messages with `%prefix%` |
| general, cosmetics, wardrobes, help, admin | chat messages |
| shop & gifts, outfits, showcases | messages of those features |
| `placeholders` | the words yes / no / none / offline used by placeholders |
| `gui.browse` | the built-in menu |
| `gui.adjust` | the adjust menu |
| `gui.bedrock` | Bedrock forms (Bedrock has 16 colours; hex colours are rounded to the nearest) |

Bedrock players see the same chat colours, rounded the same way.
