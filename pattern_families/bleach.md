# Bleach Effects

Controlled destruction. Faded beauty.

## What It Is

Bleach effects use **chlorine or oxygen bleach** to selectively fade or remove color from fabric, creating patterns through controlled chemical damage. It's the most accessible form of discharge.

## Construction

- **Bleach application**: Applied with brush, spray, or stencil
- **Controlled exposure**: Timing determines how much color is removed
- **Neutralization**: Vinegar or peroxide stops the bleach
- **Wash and dry**: Removes residue

## Visual DNA

- **Faded areas**: Gradual color loss from bleached zones
- **Soft diffusion**: Bleed from application edges
- **Texture damage**: Slight fabric weakening in bleached areas
- **Color shift**: May reveal underlying dye colors
- **Common uses**: Denim, t-shirts, DIY fashion, distressed textiles

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `bleach_strength` | 0.0–1.0 | How much color removed |
| `edge_diffusion` | 0.0–0.05 | Bleed radius |
| `pattern_method` | brush/spray/stencil | Application type |
| `fabric_damage` | 0.0–0.3 | Visible texture change |

## GLSL Snippet

```glsl
float bleach_effect(vec2 uv, float strength) {
    float bleach = bleach_pattern(uv);
    float fade = bleach * strength;
    float edge = smoothstep(0.0, edge_diffusion, bleach);
    return mix(fabric_color, bleached_color, fade + edge);
}
```

## Prompt Template

> "Bleached denim with [PATTERN] in faded white, controlled bleach application on indigo ground, soft diffusion edges, distressed casual textile, DIY fashion"

## Anti-Drift

- **Not discharge dyeing**: Bleach is a subset of discharge; discharge can use other agents
- **Fabric damage**: Bleach weakens fiber; other discharge agents may not
- **Accessibility**: Bleach is the most common household method

---

*Apply, wait, stop. The fade is the design.*
