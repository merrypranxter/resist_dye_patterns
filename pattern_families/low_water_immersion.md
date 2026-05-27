# Low-Water Immersion

Crumpled, limited, unpredictable.

## What It Is

Low-water immersion dyeing creates **organic, mottled patterns** by using minimal liquid and crumpled fabric. The limited dye bath can't reach all areas evenly, creating tonal variation.

## Construction

- **Crumpled fabric**: Cloth crushed and placed in container
- **Limited liquid**: Small amount of dye solution added
- **Uneven penetration**: Dye reaches some areas more than others
- **Fixing**: Soda ash or other fixative helps dye bond

## Visual DNA

- **Mottled texture**: Uneven color with light and dark areas
- **Crumple marks**: Lines where fabric was folded
- **Watermarks**: Edges where dye stopped penetrating
- **Organic chaos**: No two pieces are the same
- **Common uses**: Art fabric, quilting, background dyeing, experimental

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `mottle_scale` | 0.02–0.1 | Size of tonal patches |
| `crumple_visibility` | 0.0–0.3 | Fold line intensity |
| `dye_coverage` | 0.3–0.9 | How much cloth is dyed |
| `color_variation` | 0.0–0.5 | Tonal range |

## GLSL Snippet

```glsl
float low_water_immersion(vec2 uv, float seed) {
    float crumple = fbm(uv * 8.0 + seed);
    float dye_pool = cellular_noise(uv * 3.0 + seed);
    float mottle = crumple * dye_pool;
    return mottle;
}
```

## Prompt Template

> "Low-water immersion dyed fabric in [COLOR], mottled organic texture from limited dye penetration, visible crumple marks and watermark edges, unpredictable art fabric"

## Anti-Drift

- **Not tie-dye**: No binding; the pattern comes from crumpling and limited liquid
- **Not batik**: No wax resist; just uneven dye penetration
- **Minimal liquid**: The "low water" is the key parameter

---

*Crumple, pour a little, wait. The unevenness is the beauty.*
