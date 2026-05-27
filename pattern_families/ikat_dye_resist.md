# Ikat / Kasuri

Pre-dyed threads. Blurred edges.

## What It Is

Ikat (Japanese: kasuri) is a **resist-dye technique applied to threads before weaving**. Sections of warp, weft, or both are bound and dyed before the fabric is woven, creating patterns with characteristic blurred edges.

## Construction

- **Thread binding**: Individual threads bound in sections before dyeing
- **Resist dye**: Bound sections resist dye
- **Weaving**: Pre-dyed threads woven into fabric
- **Alignment**: Pattern emerges from aligned dyed sections

## Visual DNA

- **Blurred edges**: Slightly feathered pattern boundaries from thread movement in weaving
- **Feathered motifs**: Characteristic soft, fuzzy edges
- **Color layering**: Multiple dye baths create complex colors
- **Thread-aligned**: Pattern follows warp or weft direction
- **Common uses**: Traditional garments, luxury textiles, Central Asian, Southeast Asian, Japanese fabrics

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `edge_feather` | 0.0–0.02 | Blur from thread shift |
| `thread_count` | 20–200 | Threads per pattern repeat |
| `warp_weft` | 0–2 | 0 = warp, 1 = weft, 2 = both |
| `dye_layers` | 1–5 | Number of color applications |

## GLSL Snippet

```glsl
float ikat(vec2 uv, float feather, float seed) {
    float pattern = thread_dye_pattern(uv, seed);
    float blur = gaussian_blur(pattern, feather);
    float woven = weave_texture(uv, thread_count);
    return mix(blur, woven, 0.3);
}
```

## Prompt Template

> "Ikat textile in [COLOR PALETTE], pre-dyed [warp/weft] threads woven into geometric pattern, characteristic blurred feathered edges from thread alignment, traditional Uzbek/Japanese kasuri textile"

## Anti-Drift

- **Not tie-dye**: Ikat dyes threads before weaving; tie-dye dyes finished fabric
- **Blurred edges**: The slight misalignment is the signature
- **Thread-level resist**: Resist applied to threads, not cloth

---

*Bind threads, dye, weave. The blur is the alignment.*
