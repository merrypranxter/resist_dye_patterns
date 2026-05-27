# Discharge Dyeing

Color removal. Negative space.

## What It Is

Discharge dyeing removes **color from already-dyed fabric** using discharge agents (like bleach or thiourea dioxide). It creates light patterns on dark fabric — the inverse of normal dyeing.

## Construction

- **Dyed base fabric**: Dark-colored cloth as starting point
- **Discharge agent**: Applied to specific areas to remove color
- **Chemical reaction**: Agent breaks down dye molecules
- **Neutralization**: Process stopped at desired level

## Visual DNA

- **Light on dark**: Pale patterns on dark background
- **Soft edges**: Discharge bleeds slightly into surrounding fabric
- **Color variation**: Discharged areas may be white, cream, or slightly colored
- **Negative space**: The pattern is absence of color
- **Common uses**: Dark t-shirts, art fabric, punk fashion, experimental textiles

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `base_color` | RGB | Dark starting color |
| `discharge_color` | RGB | Usually white or cream |
| `edge_bleed` | 0.0–0.03 | Discharge spread |
| `pattern_type` | — | Stencil, freehand, etc. |

## GLSL Snippet

```glsl
float discharge(vec2 uv, float base, float agent) {
    float pattern = discharge_pattern(uv);
    float edge = gaussian_blur(pattern, edge_bleed);
    float result = mix(base, discharge_color, edge);
    return result;
}
```

## Prompt Template

> "Discharge-dyed black fabric with [PATTERN] in pale cream, negative-space technique removing color from dark ground, soft bleach edges, punk art textile"

## Anti-Drift

- **Not dyeing**: Discharge removes color; dyeing adds it
- **Dark base required**: Only works on already-dark fabric
- **Chemical process**: Requires discharge agents, not just bleach

---

*Remove, not add. The absence is the pattern.*
