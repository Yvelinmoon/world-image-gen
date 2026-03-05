# 剧情图 Narrative / Story Art

**Best for**: Key story moments, dramatic confrontations, emotional scenes, action sequences — characters interacting within their environment. The **moment** is the subject, not the character alone.

## Aspect Ratios
- `16:9` — most dramatic scenes, action sequences
- `4:3` — balanced compositions, dialogue scenes
- `3:4` — intimate vertical scenes, emotional close-ups

## Prompt Template
```
[art style], [framing: wide shot / medium shot / close-up],
[scene: who is doing what where],
[character descriptions, kept brief], [emotional tension / mood],
[environmental context], [lighting that reinforces the emotion],
cinematic composition
```

**Lead with the action/moment, not the character description.**

## Camera Framing Vocabulary
| Framing | Use for |
|---------|---------|
| `wide establishing shot` | Show full environment and scale, characters small |
| `medium shot, waist up` | Body language + environment both visible |
| `two-shot, face to face` | Dialogue, confrontation, tense standoff |
| `over-the-shoulder shot` | POV tension, pursuit, conversation |
| `extreme close-up on face` | Pure emotional intensity, revelation moment |
| `dutch angle` | Disorientation, menace, instability |

## Emotional Beat → Lighting Map
| Story Beat | Lighting |
|------------|---------|
| Isolation / dread | `single torch in vast darkness, deep shadow` |
| Hope after despair | `sunlight breaking through storm clouds` |
| Mystery / danger | `cold blue moonlight, long shadows` |
| Trust / warmth | `warm firelight, intimate close setting` |
| Climax / power reveal | `magical energy crackling, blue-white light` |
| Grief / loss | `grey overcast, flat soft light, no shadows` |
| Triumph | `golden hour, warm backlight, lens flare` |

## Narrative Tension Words
`tense standoff` · `tearful reunion` · `moment of revelation` · `last stand` · `silent understanding` · `betrayal` · `desperate struggle` · `quiet aftermath`

## Style Options
`dramatic fantasy illustration` · `cinematic concept art` · `graphic novel panel` · `film still aesthetic` · `painterly narrative art`

## CLI Command
```bash
nano-banana "[prompt]" -a 16:9 -s 2K -m pro -o [scene-name]-narrative
```

## Example
```bash
nano-banana "dramatic fantasy illustration, wide shot, ancient throne room, lone cloaked figure kneeling before a towering shadowed king on an obsidian throne, dozens of armored guards lining the walls, atmosphere of tense dread and suppressed power, torchlight creating sharp chiaroscuro contrast, cinematic composition, highly detailed" -a 16:9 -s 2K -m pro -o throne-audience
```

## Common Pitfalls
- Describing the character first, action second → flip it; lead with the scene and action
- Generic lighting → lighting is the single most powerful mood lever; always specify it
- Too many characters described in detail → pick the 1–2 central figures; others are `armored guards`, `robed figures`, etc.
- No framing specified → model defaults to a vague medium shot; pick your framing intentionally
