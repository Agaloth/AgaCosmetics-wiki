# Positioning (adjust)

Models from different packs sit differently, and Bedrock draws some of them slightly off. Fix it in-game.

## The adjust menu

Wear the cosmetic and run `/agac adjust`. Then:

- **Part**: backpack, first-person model, shoulder model or balloon (cycles through what you wear)
- **Players**: Java or Bedrock (they are adjusted separately)
- **Applies to**: this cosmetic, or every cosmetic of that kind
- **Step**: how far one click moves
- −/+ for **x** (sideways, + is right), **y** (up/down), **z** (away from the back) and **scale**

Changes show to everyone at once, without the model blinking, and are saved straight away.

## By command

```
/agac adjust y +2                      up/down in pixels (16 = 1 block)
/agac adjust x -1                      sideways
/agac adjust z +1                      away from the back
/agac adjust scale 0.9                 or +0.1 / -0.1
/agac adjust show | reset
/agac adjust firstperson y +4          the model the wearer sees
/agac adjust shoulder x -2
/agac adjust balloon bedrock y -8      part and platform explicitly
/agac adjust global bedrock y -2       every cosmetic of that kind
/agac adjust cosmetic <id> bedrock ... from the console, without wearing it
```

## Where it is saved

In the cosmetic's own file:

```yaml
my_wings:
  display:
    java:    { x: 0, y: 0, z: 0, scale: 1.0 }
    bedrock: { x: 0, y: -2, z: 1, scale: 1.0 }
    firstperson:
      bedrock: { x: 0, y: 4, z: 0, scale: 1.0 }
```

Global corrections are in `config.yml`: `display.java.<part>` and `bedrock.offsets.<part>`.

{% hint style="success" %}
**Adjusting a backpack you can't see**

With a first-person model, the wearer sees that model instead of the normal backpack. Adjust `firstperson`
for your own view, or ask someone else to look while you adjust the backpack.
{% endhint %}
