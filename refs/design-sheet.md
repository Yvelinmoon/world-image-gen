# 设定图 Design / Reference Sheet

**Best for**: Character turnarounds, costume design documentation, creature concept sheets, vehicle/architecture design references.

## Aspect Ratios
- `16:9` — standard reference sheet (most common)
- `1:1` — square layout for simpler sheets

## Prompt Template
```
character design reference sheet, [character description],
[views: front / side / back / three-quarter], [art style],
clean white background, [outfit / costume details],
proportional character turnaround, [optional: expression samples]
```

## Key Trigger Phrases
Include at least one of: `reference sheet` · `turnaround sheet` · `multiple views` · `design documentation` · `character turnaround`

These phrases strongly signal to the model that multiple angles are expected.

## Sheet Variants
| Variant | Add to prompt |
|---------|--------------|
| Full turnaround | `front view, side view, back view, three-quarter view` |
| Expression sheet | `expression reference sheet, multiple facial expressions: happy, angry, sad, surprised, neutral` |
| Costume detail | `costume detail sheet, close-up views of key accessories and outfit elements` |
| Proportion guide | `proportional guide, height comparison, silhouette reference` |
| Creature sheet | `creature design sheet, multiple angles, anatomy notes, scale reference` |

## Background
Always use `clean white background` or `plain neutral background` — it's standard for design sheets and keeps the focus on the design.

## CLI Command
```bash
nano-banana "[prompt]" -a 16:9 -s 2K -m pro -o [character-name]-reference-sheet
```

## Example
```bash
nano-banana "character design reference sheet, young male alchemist, front view, side view, and back view, fantasy anime style, clean white background, long rust-colored coat with many pockets, goggles pushed up on forehead, brown leather boots, proportional turnaround, professional character sheet" -a 16:9 -s 2K -m pro -o kael-design-sheet
```

## Common Pitfalls
- Forgetting "reference sheet" keyword → model generates a single-view portrait instead
- Colored background → distracts from the design; always use white/neutral
- Too many details in one shot → split complex designs into separate sheets (costume detail, face close-up, etc.)
