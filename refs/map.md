# 地图 Map

**Best for**: World maps, continent maps, regional maps, city maps, dungeon floor plans, naval charts, tactical battle maps.

## Aspect Ratios
- World / regional map: `16:9` or `4:3`
- City / district map: `1:1` or `4:3`
- Dungeon / building floor plan: `1:1`

## Prompt Template
```
[map style], [map type: world / regional / city / dungeon] map of [name],
[terrain features], [key locations and landmarks],
[color palette], detailed cartography, [era / aesthetic decorations]
```

## Map Styles
| Style | Keywords |
|-------|----------|
| Classic RPG | `hand-drawn parchment fantasy map, aged sepia tones` |
| Ornate historical | `medieval illuminated manuscript map, gold leaf details` |
| Clean digital | `modern digital fantasy cartography, clean vector style` |
| Pixel / retro | `top-down pixel art map, 16-bit style` |
| TTRPG battle | `battle map, tactical grid overlay, top-down view, flat lighting` |
| Nautical | `nautical chart, maritime cartography, compass rose, depth markings` |

## Terrain Keywords
`snow-capped mountain ranges` · `ancient dense forests` · `winding river delta` · `volcanic archipelago` · `desert wastes and sand dunes` · `frozen tundra` · `floating sky islands` · `sunken coastal ruins` · `rolling plains` · `swamp and marshland`

## Map Decorations (add to prompt for richness)
`decorative compass rose` · `illustrated border frame` · `legend and scale bar` · `sea monster illustrations in ocean` · `city/town icon markers` · `road and trade route lines` · `heraldic crests at borders`

## CLI Command
```bash
nano-banana "[prompt]" -a 16:9 -s 4K -m pro -o [world-name]-map
```

Use `4K` for maps — the detail density rewards high resolution.

## Example
```bash
nano-banana "hand-drawn parchment fantasy world map, continent of Aethoria, snow-capped mountain ranges in the north, ancient dense forests in the east, coastal city-states along the southern shore, vast desert wastes in the west, illustrated settlements connected by roads, aged sepia and ochre tones, decorative compass rose, ornate border frame, legend and scale bar, detailed cartography" -a 16:9 -s 4K -m pro -o aethoria-worldmap
```

## Common Pitfalls
- Skipping map style → model generates a generic overhead view without cartographic aesthetics
- Not naming terrain regions → output is abstract; name specific zones even if fictional
- Using 2K for large world maps → detail is lost; use 4K
