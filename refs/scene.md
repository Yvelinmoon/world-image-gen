# 场景图 Scene / Environment Art

**Best for**: Location establishing shots, atmospheric environment art, world-building showcase images. Focus is on the place, not characters (or characters are very small in frame).

## Aspect Ratios
- Cinematic widescreen: `21:9` (most impactful for landscapes)
- Standard widescreen: `16:9`
- Standard landscape: `4:3`
- Vertical banner / scroll art: `9:16`

## Prompt Template
```
[art style], [location type and name], [time of day],
[weather / atmosphere], [key visual elements: architecture / terrain / details],
[mood / feeling], [lighting], [color palette], [quality tags]
```

## Time of Day
`golden hour, warm amber light` · `blue hour dusk` · `deep night, moonlit` · `overcast midday, flat grey light` · `pre-dawn, cool blue mist` · `high noon, harsh sunlight`

## Atmosphere Presets
| Mood | Keywords |
|------|----------|
| Epic / grand | `dramatic storm clouds, god rays breaking through` |
| Mysterious | `ethereal mist, soft moonlight, shadows everywhere` |
| Oppressive | `apocalyptic red sky, falling ash, heat haze` |
| Magical | `arcane aurora, shifting colored light, floating particles` |
| Desolate | `grey overcast, barren landscape, cold silence` |
| Serene | `golden hour, gentle breeze, warm amber glow` |

## Location Categories
**Natural**: ancient forest, volcanic coast, floating islands, underground cavern lake, frozen glacier valley, desert canyon, stormy ocean cliff

**Urban**: medieval market city, ruined capital overgrown with vines, magical academy campus, underground dwarven kingdom, spacefaring colony habitat

**Liminal / Symbolic**: ancient battlefield at dawn, the border between two realms, a dimensional rift, the space between worlds

## Quality Tags
`matte painting` · `environment concept art` · `epic scale` · `cinematic composition` · `atmospheric perspective` · `highly detailed` · `award-winning digital art`

## CLI Command
```bash
# Cinematic widescreen (recommended for most scenes)
nano-banana "[prompt]" -a 21:9 -s 4K -m pro -o [location-name]-scene

# Standard widescreen
nano-banana "[prompt]" -a 16:9 -s 2K -m pro -o [location-name]-scene
```

Use `4K` for hero scenes — atmospheric perspective and distant detail reward the resolution.

## Example
```bash
nano-banana "fantasy matte painting, ancient floating island city, enormous crystal spires rising from carved stone platforms, waterfalls cascading into clouds below, golden hour sunlight cutting through mist, warm amber and violet sky, distant silhouettes of sky-ships docking, epic scale, highly detailed environment concept art" -a 21:9 -s 4K -m pro -o skycity-scene
```

## Common Pitfalls
- Describing characters in detail → if characters are present, keep them tiny or silhouetted; this type focuses on environment
- No atmosphere description → output looks flat; lighting and weather are the most impactful elements
- Using 16:9 for landscapes → try `21:9` first; the extra width dramatically improves scenic compositions
