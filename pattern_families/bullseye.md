# Bullseye Tie-Dye

Target practice with dye.

## What It Is

Bullseye tie-dye creates **concentric circles** by picking up points of fabric and binding them, creating multiple target-like rings across the cloth. Each bound point becomes a bullseye.

## Construction

- **Multiple pinches**: Several points picked up across fabric
- **Binding**: Each point bound tightly with string or rubber band
- **Dye bath**: Cloth immersed in dye
- **Resisted circles**: Bound points resist dye creating circles

## Visual DNA

- **Multiple targets**: Several concentric circle patterns across cloth
- **Resisted center**: Innermost circle usually lightest/undyed
- **Ring layers**: Dye penetrates progressively from outside in
- **Scattered placement**: Bullseyes placed randomly or in pattern
- **Common uses**: T-shirts, fabrics, casual wear, retro fashion

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `bullseye_count` | 1–20 | Number of targets |
| `ring_width` | 0.01–0.05 | Width of each ring |
| `center_resist` | 0.0–1.0 | How well center resists dye |
| `scatter` | 0.0–1.0 | Random vs. ordered placement |

## GLSL Snippet

```glsl
float bullseye(vec2 uv, vec2 centers[], float ring_w) {
    float min_dist = 100.0;
    for (int i = 0; i < centers.length; i++) {
        min_dist = min(min_dist, length(uv - centers[i]));
    }
    float ring = floor(min_dist / ring_w);
    return ring / max_rings;
}
```

## Prompt Template

> "Bullseye tie-dye in [COLOR PALETTE], multiple target circles with resisted centers and concentric dye rings, scattered across cotton fabric, retro casual textile"

## Anti-Drift

- **Multiple points**: Unlike spiral, bullseye has many centers
- **Binding creates circles**: Each bound point is a bullseye origin
- **Not spiral**: Spiral has one center with radiating twist; bullseye has many simple circles

---

*Pick, bind, dye. The target is the mark.*
