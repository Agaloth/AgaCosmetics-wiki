# Animations

Backpacks, balloons and shoulder models can move. Display entities blend smoothly between the poses they are
sent, so the client plays the animation: a few small packets per second per viewer and no server ticks.

```yaml
my_balloon:
  slot: BALLOON
  item: { material: nexo:heart_balloon }
  animations:
    - { type: BOB, amount: 3, seconds: 3 }
    - { type: SWAY, amount: 6, seconds: 4 }
```

A single animation can also be written as `animation: { type: SPIN, seconds: 6 }`.

| Type | `amount` | Movement |
|---|---|---|
| `BOB` | pixels (16 = 1 block) | floats up and down |
| `SWAY` | degrees | rocks from side to side |
| `TILT` | degrees | tips forwards and back (flapping wings, a nodding pet) |
| `SPIN` | 1 or -1 (direction) | turns a full circle per cycle |
| `PULSE` | percent | grows and shrinks |

`seconds` is the length of one cycle (at least half a second). Several animations play together.

## Flipbook frames

Show items one after another, for models made as separate frames:

```yaml
frames:
  ticks: 4                      # ticks per frame
  items:
    - { material: nexo:wings_frame_1 }
    - { material: nexo:wings_frame_2 }
    - { material: nexo:wings_frame_3 }
```

## Settings

`display.animation-interval` in `config.yml` (default 4 ticks) is how often a new pose is sent. Lower is
smoother and sends more packets. Turning with the body always uses the short `rotation-interpolation`, so
animated backpacks still follow the player without delay.

{% hint style="info" %}
**Bedrock**

GeyserDisplayEntity shows `BOB`, `PULSE` and flipbook frames. The rotating types depend on its support for
display rotations.
{% endhint %}
