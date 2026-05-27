# Kumo Shibori

Spiderweb binding. Radiating circles.

## What It Is

Kumo ("spider") shibori creates **radiating circular patterns** by pleating fabric into small points and binding them with thread in a specific spiderweb-like pattern.

## Construction

- **Pleating**: Small sections of fabric pleated upward
- **Spiderweb binding**: Thread wound in radiating lines from center point
- **Dye bath**: Bound areas resist; dye penetrates between bindings
- **Unbinding**: Reveals spiderweb pattern radiating from points

## Visual DNA

- **Radiating lines**: Thread-like lines spreading from center points
- **Circular motifs**: Each bound point becomes a circular pattern
- **Spiderweb appearance**: Resembles spiderweb or starburst
- **Soft edges**: Dye bleeds slightly between bindings
- **Common uses**: Silk, traditional Japanese garments, ceremonial textiles

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `web_center` | vec2 | Location of spiderweb center |
| `radial_lines` | 4–16 | Number of radiating threads |
| `web_tightness` | 0.0–0.1 | How tight the binding |
| `dye_bleed` | 0.0–0.02 | Soft edge blur |

## GLSL Snippet

```glsl
float kumo(vec2 uv, float lines, float seed) {
    float angle = atan(uv.y, uv.x);
    float radius = length(uv);
    float web = sin(angle * lines) * 0.5 + 0.5;
    float dye = smoothstep(0.0, 0.1, radius) * web;
    return dye;
}
```

## Prompt Template

> "Kumo spiderweb shibori in indigo, radiating thread lines from bound center points, spiderweb pattern on silk, soft dye bleed between bindings, Japanese resist-dye textile"

## Anti-Drift

- **Spiderweb specifically**: The radiating binding pattern defines kumo
- **Not regular tie-dye**: Specific Japanese technique with deliberate web binding
- **Radiating from points**: Each center is a bound pleat

---

*Pleat, bind like a spider, dye. The web is the pattern.*
