# Styles (variants)

One cosmetic, several styles. The menu shows one entry that opens a style picker, instead of a page full of
near-identical items.

```yaml
witch_hat:
  slot: HELMET
  permission: cosmetics.witch_hat
  item: { material: nexo:witch_hat }
  variants:
    green:
      item: { material: nexo:witch_hat_green }
    gold:
      item: { material: nexo:witch_hat_gold }
      price: 1000                      # this style is sold on its own
```

- A style's id is `<cosmetic>:<style>`, e.g. `/agac apply witch_hat:green`.
- A style takes everything it doesn't set from its base: slot, permission, price, dyeable, position fixes,
  animations, auras...
- **Unlocking**: owning the base (permission or bought) unlocks every style that has no `permission` or `price`
  of its own. A style with its own permission or price is unlocked separately.
- Position fixes made with `/agac adjust` while wearing a style are saved on the base and apply to all styles.
- Placeholders count styles too (`owned_<slot>`, `collection_<slot>`).
