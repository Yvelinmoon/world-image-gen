# 分镜图 Storyboard / Comic Panel

**Best for**: Manga pages, comic panels, sequential story visualization, storyboard frames for animation or film planning.

## Aspect Ratios
- `3:4` — manga page (most common, vertical scroll)
- `16:9` — cinematic widescreen panel
- `1:1` — square panel, social media format

## Single Panel Prompt Template
```
[comic/manga style], [panel scene: characters + action],
[expression / emotion], [dynamic composition cue],
[inking style], [shading / tone style]
```

## Multi-Panel Layout Template
Gemini can generate grid layouts when explicitly described:
```
comic page layout, [N]-panel grid, [art style],
sequential story:
panel 1: [description]
panel 2: [description]
panel 3: [description]
clean panel borders, [inking style]
```

Keep multi-panel descriptions brief per panel — one action per panel.

## Comic Style Options
| Style | Keywords |
|-------|----------|
| Black & white manga | `black and white manga, screentone shading, clean linework` |
| American comics | `american comic book style, bold inks, cel shading, vibrant colors` |
| Webtoon | `webtoon style, full color, soft cel shading, vertical scroll format` |
| European BD | `bande dessinée style, ligne claire, clean outlines, flat colors` |
| Light novel illust. | `light novel illustration, soft pastel, anime style, white background` |

## Dynamic Composition Cues
`speed lines radiating from impact` · `dynamic diagonal perspective` · `dramatic low angle` · `extreme close-up on eyes` · `explosive action lines` · `motion blur` · `floating panel layout` · `silhouette against light source`

## Inking Styles
`clean thin linework` · `bold expressive brushwork` · `scratchy ink texture` · `precise vector lines` · `variable weight inking`

## Shading / Tone
`screentone pattern shading` · `flat cel shading` · `crosshatch shadows` · `soft gradient shading` · `high contrast black fills`

## CLI Commands
```bash
# Single panel
nano-banana "[prompt]" -a 3:4 -s 2K -m pro -o [scene-name]-panel

# Widescreen cinematic panel
nano-banana "[prompt]" -a 16:9 -s 2K -m pro -o [scene-name]-wide-panel

# Multi-panel page
nano-banana "[prompt]" -a 3:4 -s 2K -m pro -o [scene-name]-page
```

## Example
```bash
nano-banana "black and white manga panel, dramatic low angle shot, young warrior drawing a glowing sword from a stone altar, expression of shock and fierce determination, magical energy swirling outward, speed lines radiating from the sword, screentone shading on background, clean linework, dynamic diagonal composition" -a 3:4 -s 2K -m pro -o sword-drawing-panel
```

## Iteration Strategy for Sequential Panels
Generate panels one at a time, using the previous panel as a `-r` reference to maintain character and style consistency:
```bash
# Panel 1 (no reference)
nano-banana "[panel 1 prompt]" -a 3:4 -s 2K -m pro -o scene-panel-01

# Panel 2 (reference panel 1 for consistency)
nano-banana "[panel 2 prompt]" -r ./scene-panel-01.png -a 3:4 -s 2K -m pro -o scene-panel-02
```

## Common Pitfalls
- No composition cue → output is static and flat; always add a dynamic composition term
- Forgetting inking style → Gemini defaults to a generic illustrative style
- Trying to describe too much in one panel → one clear action or moment per panel
- Multi-panel without `clean panel borders` → panels may bleed into each other
