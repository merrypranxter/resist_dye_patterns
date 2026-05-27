# Crackle Networks

The map of broken wax.

## What It Is

Crackle is the **fine vein pattern** that appears in batik when the wax resist cracks during handling or dyeing. Dye seeps into these cracks, creating a network of dark lines that overlays the main pattern.

## Construction

- **Wax brittleness**: Hot wax becomes brittle when cool
- **Handling cracks**: Flexing the cloth breaks the wax
- **Dye penetration**: Dye enters cracks before wax is removed
- **Unpredictable**: Each piece has unique crackle pattern

## Visual DNA

- **Fine random lines**: Irregular network across the cloth
- **Darker than ground**: Crackle lines are usually the darkest color
- **Overlay effect**: Crackle sits on top of the main pattern
- **Organic chaos**: No two pieces have the same crackle
- **Common uses**: Characteristic of traditional batik; sometimes simulated in prints

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `crackle_density` | 10–100 | Lines per unit area |
| `crackle_width` | 0.001–0.003 | Very fine lines |
| `color` | RGB | Usually darkest dye color |
| `random_seed` | 0–1000 | Unique per piece |

## GLSL Snippet

```glsl
float crackle_network(vec2 uv, float density, float seed) {
    float noise1 = fbm(uv * density + seed);
    float noise2 = fbm(uv * density * 1.5 + seed + 100.0);
    float crack = abs(noise1 - noise2);
    return smoothstep(0.05, 0.0, crack);
}
```

## Prompt Template

> "Batik crackle detail showing fine dark vein network over indigo ground, random organic lines from broken wax resist, unique unrepeatable pattern, traditional textile art"

## Anti-Drift

- **Not drawn lines**: Crackle is random; drawn lines are intentional
- **Not all batik has crackle**: Some modern batik avoids cracking deliberately
- **Signature of handwork**: Machine batik usually lacks natural crackle

---

*Broken wax, dye finds the gaps. The crackle is the fingerprint.*
