# Arashi Shibori

Storm-wrapped. Diagonal rain.

## What It Is

Arashi ("storm") shibori is a **Japanese resist-dye technique** where fabric is wrapped around a pole, bound with thread, and scrunched down before dyeing. The result is diagonal lines resembling driving rain.

## Construction

- **Pole wrapping**: Cloth wrapped diagonally around PVC pipe or pole
- **Thread binding**: String wound tightly around the wrapped fabric
- **Scrunching**: Fabric pushed down the pole into folds
- **Dye bath**: Immersed in dye; bound areas resist

## Visual DNA

- **Diagonal stripes**: Lines running at an angle across fabric
- **Soft edges**: Dye bleeds slightly under bindings
- **Storm appearance**: Resembles slanted rain or wind
- **Directional**: Clear diagonal bias
- **Common uses**: Silk scarves, art textiles, traditional Japanese fabric

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `diagonal_angle` | 30°–60° | Slant of lines |
| `line_spacing` | 0.01–0.05 | Distance between stripes |
| `edge_softness` | 0.0–0.02 | Dye bleed |
| `wrinkle_depth` | 0.0–0.1 | Fold texture |

## GLSL Snippet

```glsl
float arashi(vec2 uv, float angle, float spacing) {
    vec2 rotated = rotate(uv, angle);
    float lines = sin(rotated.x * PI / spacing);
    float soft = smoothstep(0.0, edge_softness, lines);
    return soft;
}
```

## Prompt Template

> "Arashi shibori silk scarf in indigo, diagonal storm lines from pole wrapping and binding, soft feathered edges, Japanese rain-inspired resist pattern, traditional textile"

## Anti-Drift

- **Not tie-dye**: Arashi is specifically Japanese pole-wrapping technique
- **Diagonal only**: The pole wrapping creates angled lines
- **Storm meaning**: "Arashi" = storm in Japanese

---

*Wrap the pole, bind, scrunch. The diagonal is the storm.*
