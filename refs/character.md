# 角色立绘 Character Illustration

**Best for**: Official character art, hero/villain portraits, NPC reference art, expression sheets.

## Aspect Ratios
- Full body: `3:4` or `2:3`
- Half body (waist up): `3:4`
- Bust / face close-up: `4:5` or `1:1`

## Prompt Template
```
[art style], [framing], [character: species/race, gender, age range, build],
[outfit: material, colors, key features], [pose / action], [expression / emotion],
[background], [lighting], [quality tags]
```

**Art style always goes first.**

## Style Options
| Style | Keywords |
|-------|----------|
| Anime | `anime illustration`, `JRPG character art`, `shounen manga style` |
| Western fantasy | `fantasy concept art`, `RPG character design` |
| Realistic | `realistic digital painting`, `cinematic portrait` |
| Painterly | `painterly illustration`, `watercolor character art` |
| Ink | `ink illustration`, `detailed linework`, `graphic novel style` |

## Lighting Power Words
`rim lighting` · `dramatic side lighting` · `soft ambient light` · `candlelight glow` · `bioluminescent light` · `golden hour` · `cold moonlight`

## Background Options
- Simple (keeps focus on character): `simple gradient background`, `plain dark background`, `bokeh background blur`
- World-relevant: describe the actual environment
- Abstract: `abstract magical energy`, `painterly color wash`

## Quality Tags
`highly detailed` · `professional character sheet` · `sharp focus` · `clean linework` · `intricate costume details`

## CLI Command
```bash
nano-banana "[prompt]" -a 3:4 -s 2K -m pro -o [character-name]-portrait
```

## Example
```bash
nano-banana "anime illustration, full body, young elven woman warrior, silver waist-length hair, battle-worn leather armor with glowing blue runestone pauldrons, confident standing pose, slight smile, ancient forest background with dappled sunlight, dramatic rim lighting, highly detailed" -a 3:4 -s 2K -m pro -o elara-portrait
```

## Existing IP Characters

When drawing a character from an existing IP (game, anime, film):

### Step 1: Search for a reference image
Do not rely on the model's internal knowledge. Search first:
```
WebSearch: "[IP name] [character name] official art"
WebSearch: "[IP name] [character name] concept art / screenshot"
```
Prefer: official character art, high-res screenshots, promotional renders.
Avoid: fan art (inconsistent), low-res thumbnails.

### Step 2: Download and pass as `-r`
```bash
curl -fsSL "[found_image_url]" -o /tmp/char-ref.jpg
nano-banana "[prompt]" -r /tmp/char-ref.jpg -a 3:4 -s 2K -m pro -o [output]
rm /tmp/char-ref.jpg
```

### Step 3: Describe visually, not by name
Even with a reference image, add explicit visual description to anchor the key features:
```
realistic medieval fantasy art style, [character's actual appearance: armor color,
distinctive equipment, face features, faction markings], inspired by [IP] visual style
```
Do not just write `[Character Name] from [IP]` — describe what they actually look like.

### Accuracy expectations
| Has reference image | Prompt has visual detail | Expected result |
|--------------------|--------------------------|-----------------|
| Yes | Yes | Close to target — style and key features match |
| Yes | No | Style matches, details may drift |
| No | Yes | Reasonable approximation, no style guarantee |
| No | No | Generic; may not resemble target at all |

`-r` is style transfer, not reproduction. The more distinctive and visually described the character, the better.

## Common Pitfalls
- Too vague on outfit → describe materials and colors explicitly
- Generic pose → name a specific pose: `three-quarter view`, `action stance`, `seated cross-legged`
- Background competing with character → use `simple gradient` or keep background description brief
