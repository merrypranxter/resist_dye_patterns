# Ice Dye

Frozen crystals, random diffusion.

## What It Is

Ice dye is a **modern tie-dye technique** where fabric is covered with ice, and powdered dye is sprinkled on top. As the ice melts, the dye dissolves and diffuses randomly into the fabric.

## Construction

- **Fabric setup**: Cloth scrunched or arranged on a rack
- **Ice layer**: Ice cubes or crushed ice placed on top
- **Powder dye**: Dry dye powder sprinkled over ice
- **Melting process**: Ice melts, carrying dye in unpredictable paths

## Visual DNA

- **Random diffusion**: No predictable pattern; organic flow
- **Crystal textures**: Dye follows ice melt paths
- **Color blending**: Where different dyes meet, they blend
- **High contrast edges**: Sharp boundaries between color areas
- **Common uses**: Modern tapestries, art fabric, experimental textiles

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `diffusion_rate` | 0.0–0.1 | How far dye spreads |
| `crystal_size` | 0.01–0.1 | Ice crystal scale |
| `color_mixing` | 0.0–1.0 | How much colors blend |
| `randomness` | 0.5–1.0 | Organic unpredictability |

## GLSL Snippet

```glsl
float ice_dye(vec2 uv, float seed) {
    float ice = cellular_noise(uv * 20.0 + seed);
    float melt_path = fbm(uv * 5.0 + ice);
    float dye = powder_spread(uv, melt_path, seed);
    return dye;
}
```

## Prompt Template

> "Ice-dyed fabric in [COLOR PALETTE], random organic dye diffusion from melting ice crystals, unpredictable color blending, high contrast edges, modern experimental textile art"

## Anti-Drift

- **Not traditional tie-dye**: Ice dye uses powder and melting; traditional uses liquid and binding
- **Random not repeatable**: Each piece is unique
- **Powder not liquid**: Dry dye sprinkled, not liquid dye applied

---

*Ice melts, dye follows. The crystal is the map.*
