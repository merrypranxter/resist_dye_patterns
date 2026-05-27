# Bandhani / Bandhej

Tied dots. Thousands of knots.

## What It Is

Bandhani is an **Indian tie-dye technique** where tiny points of fabric are pinched and bound with thread, creating dense patterns of small dots. It's traditional in Gujarat and Rajasthan.

## Construction

- **Pinch and bind**: Tiny fabric points lifted and tied with thread
- **Thousands of knots**: A single piece may have thousands of bindings
- **Dye bath**: Bound points resist dye
- **Knot removal**: Reveals pattern of thousands of dots

## Visual DNA

- **Dense dot field**: Hundreds or thousands of small dots across fabric
- **Geometric patterns**: Dots arranged in specific motifs — peacocks, flowers, etc.
- **Color contrast**: Usually bright colors (red, yellow, green) with white or black dots
- **Fine detail**: Very small, precise dots
- **Common uses**: Sarees, dupattas, turbans, traditional Indian dress

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `dot_density` | 50–500 | Dots per unit area |
| `dot_size` | 0.002–0.01 | Tiny points |
| `pattern_type` | 0–5 | Peacock, flower, geometric, etc. |
| `color_base` | RGB | Bright background |
| `dot_color` | RGB | Usually white or black |

## GLSL Snippet

```glsl
float bandhani(vec2 uv, float density, float seed) {
    vec2 grid = floor(uv * density);
    float dot = random(grid + seed);
    float shape = smoothstep(0.1, 0.0, length(fract(uv * density) - 0.5));
    return dot * shape;
}
```

## Prompt Template

> "Bandhani tie-dye in [COLOR] with [DOT COLOR] dots, thousands of tiny pinched and tied points creating dense [MOTIF] pattern, traditional Gujarat textile, fine detail"

## Anti-Drift

- **Not batik**: Bandhani ties fabric; batik uses wax
- **Dot density**: The sheer number of dots is the signature
- **Indian tradition**: Specific to Gujarat and Rajasthan

---

*Pinch, tie, dye, untie. The dot is the knot.*
