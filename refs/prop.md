# 道具图 Prop / Item Art

**Best for**: Weapons, artifacts, equipment, magical objects, key items, architectural details.

## Aspect Ratios
- `1:1` — standard item card
- `4:3` — horizontal display (e.g. two-handed weapons, scrolls)

## Prompt Template
```
[art style], [item type and name], [material and appearance],
[distinctive features / markings / runes], [condition: pristine / ancient / battle-worn / cursed],
isolated on [background], [lighting], [style tag]
```

## Background Options
`pure black` · `neutral grey gradient` · `dark velvet surface` · `ancient stone pedestal` · `arcane energy swirl` · `parchment texture`

## Style Tags
`RPG item card style` · `fantasy weapon concept art` · `museum exhibit lighting` · `game asset render` · `detailed illustration`

## Condition Vocabulary
`pristine and newly forged` · `ancient and weathered` · `battle-worn with notches` · `cursed with dark aura` · `glowing with magical energy` · `cracked and mended`

## Material Keywords
`ancient iron` · `enchanted crystal` · `worn leather` · `glowing runes etched in gold` · `obsidian blade` · `living wood` · `dragon bone` · `moonstone inlay`

## Transparent Assets (for game UI / overlays)
Use `-t` flag — auto green screen + background removal via FFmpeg. Requires FFmpeg installed.
```bash
nano-banana "[prompt], isolated, no background" -a 1:1 -s 1K -t -o [item-name]-transparent
```

## Standard CLI Command
```bash
nano-banana "[prompt]" -a 1:1 -s 2K -m pro -o [item-name]
```

## Example
```bash
nano-banana "fantasy concept art, legendary longsword, ancient silver blade with glowing cerulean runes etched along the fuller, ornate golden crossguard shaped like dragon wings, worn leather grip bound in silver wire, isolated on dark gradient background, dramatic rim lighting, highly detailed" -a 1:1 -s 2K -m pro -o runesword-dawnblade
```

## Common Pitfalls
- Not specifying "isolated on [background]" → item gets placed in a scene
- Skipping material details → output looks generic
- Forgetting lighting → museum exhibit lighting or dramatic rim lighting almost always improves results
