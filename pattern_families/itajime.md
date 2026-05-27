# Itajime Shibori

Folded and clamped. Geometric precision.

## What It Is

Itajime is a **Japanese resist-dye technique** where fabric is folded into geometric shapes and clamped between two boards before dyeing. The clamped areas resist dye, creating precise geometric patterns.

## Construction

- **Folding**: Fabric folded accordion-style into squares, triangles, or diamonds
- **Clamping**: Wooden boards placed on both sides, held tight
- **Dye bath**: Immersed in dye; clamped areas resist
- **Unfolding**: Reveals geometric pattern from the fold lines

## Visual DNA

- **Geometric precision**: Sharp, regular shapes — squares, triangles, chevrons
- **Mirror symmetry**: Each fold creates mirrored pattern
- **Sharp edges**: Unlike tied techniques, edges are crisp
- **Repeating tessellation**: Pattern tiles across the fabric
- **Common uses**: Silk, cotton fabrics, traditional Japanese textiles, art fabric

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `fold_type` | square/triangle/diamond | Base fold geometry |
| `fold_count` | 2–20 | Number of accordion folds |
| `clamp_shape` | square/triangle/circle | Resist shape |
| `edge_crispness` | 0.8–1.0 | Sharp vs. soft |

## GLSL Snippet

```glsl
float itajime(vec2 uv, float folds, float shape) {
    vec2 folded = abs(fract(uv * folds) - 0.5) * 2.0;
    float clamped = smoothstep(shape, shape - 0.01, max(folded.x, folded.y));
    return clamped;
}
```

## Prompt Template

> "Itajime shibori in indigo, geometric [SHAPE] pattern from folded and clamped fabric, sharp mirror symmetry, precise tessellation, Japanese resist-dye textile art"

## Anti-Drift

- **Not tie-dye**: Itajime uses folding and clamping, not binding
- **Sharp edges**: Clamping creates crisp boundaries
- **Geometric only**: The technique produces angular, not organic, patterns

---

*Fold, clamp, dye, unfold. The geometry is the clamp.*
