# Spiral Tie-Dye

The classic psychedelic swirl.

## What It Is

Spiral tie-dye creates a **concentric ring pattern** by pinching the fabric center, twisting it into a spiral, binding it, and dyeing. The result is radiating color rings from a central point.

## Construction

- **Central pinch**: Pinch fabric at desired spiral center
- **Twist**: Rotate the fabric into a tight spiral
- **Bind**: Rubber bands or string hold the spiral shape
- **Dye application**: Dye applied in wedges or sections

## Visual DNA

- **Concentric rings**: Color bands radiating from center
- **Central point**: The pinch point is the pattern origin
- **Color bleed**: Dye seeps under bindings creating soft edges
- **Symmetry**: Radial pattern, often multi-colored
- **Common uses**: T-shirts, tapestries, festival clothing, psychedelic fashion

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `spiral_tightness` | 0.5–3.0 | How many turns |
| `ring_count` | 3–12 | Number of color bands |
| `center_size` | 0.0–0.05 | Tight central point |
| `bleed_softness` | 0.0–0.05 | Edge blur |

## GLSL Snippet

```glsl
float spiral_tie_dye(vec2 uv, float rings) {
    float angle = atan(uv.y, uv.x);
    float radius = length(uv);
    float spiral = fract((angle + radius * 5.0) / (2.0 * PI));
    float ring = floor(spiral * rings) / rings;
    return ring;
}
```

## Prompt Template

> "Psychedelic spiral tie-dye in [COLOR PALETTE], concentric color rings radiating from central pinch point, slight dye bleed at edges, classic festival t-shirt pattern"

## Anti-Drift

- **Not batik**: Spiral is bound and dyed; batik uses wax
- **Central origin**: The pattern always has a clear center point
- **Binding marks**: Slight lines where bindings were placed

---

*Pinch, twist, bind, dye. The spiral is the trip.*
