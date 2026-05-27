# Accordion Fold

Stripes from folding.

## What It Is

Accordion fold tie-dye creates **parallel stripe patterns** by folding fabric back and forth like a fan, then binding and dyeing. The folds create resisted stripes.

## Construction

- **Folding**: Fabric folded back and forth in even pleats
- **Binding**: Tied across the folded stack
- **Dye application**: Dye applied to edges or sections
- **Unfolding**: Reveals parallel stripe pattern

## Visual DNA

- **Parallel stripes**: Even, regular lines across fabric
- **Fold marks**: Slight lines where folds were
- **Symmetry**: Mirror symmetry from the fold
- **Stripe width**: Determined by fold width
- **Common uses**: Scarves, fabrics, shibori variations, bandhani

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `fold_width` | 0.02–0.1 | Width of each pleat |
| `stripe_count` | 2–50 | Number of stripes |
| `binding_interval` | 0.05–0.3 | How often bound |
| `dye_penetration` | 0.0–1.0 | How far dye seeps |

## GLSL Snippet

```glsl
float accordion_fold(vec2 uv, float fold_w) {
    float stripe = abs(fract(uv.x / fold_w) - 0.5) * 2.0;
    float resist = smoothstep(0.3, 0.7, stripe);
    return resist;
}
```

## Prompt Template

> "Accordion fold tie-dye in [COLOR], parallel stripes from folded and bound fabric, even regular lines, mirror symmetry, shibori-inspired resist pattern"

## Anti-Drift

- **Not shibori**: Accordion fold is a general technique; shibori is specifically Japanese
- **Parallel only**: Creates stripes, not circles or spirals
- **Fold width = stripe width**: The pleat size determines the pattern scale

---

*Fold, bind, unfold. The stripe is the fold.*
