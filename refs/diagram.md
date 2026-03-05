# 图表 Lore Diagram

**Best for**: Faction relationship maps, character relationship webs, historical timelines, magic system diagrams, power hierarchies, dynasty/lineage trees.

## Aspect Ratios
- `16:9` — timelines, horizontal trees, wide relationship webs
- `1:1` — radial/circular charts, balanced webs, element wheels

## Prompt Template
```
[diagram type] infographic, [world context],
[visual style], [color scheme],
[specific nodes / elements to include],
decorative [world aesthetic] design, clean readable layout, [background]
```

## Diagram Types
| Type | Keywords |
|------|----------|
| Family / lineage | `family tree, lineage chart, dynasty genealogy` |
| Faction relations | `faction relationship diagram, alliance and conflict web, political map` |
| Timeline | `historical timeline infographic, chronological events, ages and eras` |
| Power hierarchy | `power hierarchy pyramid, authority structure, rank chart` |
| Magic system | `magic system element wheel, spell school diagram, power tree` |
| Character relations | `character relationship web, social connections diagram` |

## Visual Styles
| World Aesthetic | Style Keywords |
|----------------|---------------|
| Medieval fantasy | `illuminated manuscript chart, gold leaf, parchment background` |
| Dark / gothic | `dark fantasy UI overlay, obsidian and crimson, rune borders` |
| Ancient / mystical | `ancient stone inscription diagram, carved runes, weathered surface` |
| Stained glass | `stained glass mosaic diagram, leaded glass aesthetic, jewel tones` |
| Clean / modern | `infographic design, clean layout, geometric nodes, sans-serif` |

## Connection Line Vocabulary
For relationship diagrams, specify line meanings in the prompt:
- `gold connecting lines for alliances, red for conflicts, grey for neutral`
- `solid lines for direct relations, dashed for indirect influence`

## CLI Command
```bash
nano-banana "[prompt]" -a 16:9 -s 2K -m pro -o [name]-diagram
```

## Example
```bash
nano-banana "faction relationship diagram infographic, five noble houses of the Valdris Empire, web of alliances and rivalries, illuminated manuscript aesthetic, gold and crimson color scheme, each house represented by heraldic crest, gold connecting lines for alliances and red for conflicts, dark parchment background, clean readable layout" -a 16:9 -s 2K -m pro -o valdris-faction-chart
```

## Common Pitfalls
- Too many nodes without layout direction → specify `clean layout` and limit to 5–8 key nodes per image
- No visual style specified → output looks like a generic modern infographic regardless of world tone
- Forgetting to specify connection line meanings → relationships look ambiguous
