# Nui Shibori

Stitched resist. Drawn thread control.

## What It Is

Nui is a **Japanese resist-dye technique** where running stitches are sewn into fabric before dyeing. When pulled tight, the stitches gather the fabric, creating resisted lines and patterns.

## Construction

- **Running stitches**: Simple stitches sewn in pattern lines
- **Pulling tight**: Thread drawn to gather fabric into folds
- **Dye bath**: Tight gathers resist dye penetration
- **Stitch removal**: Threads removed after dyeing to reveal pattern

## Visual DNA

- **Fine line resist**: The stitch line itself is the resist boundary
- **Gathered texture**: Fabric has slight crease where stitched
- **Curved or straight**: Stitch pattern determines motif shape
- **Delicate marks**: Subtle compared to binding or clamping
- **Common uses**: Silk, traditional Japanese garments, detailed patterns

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `stitch_path` | — | Pattern of running stitches |
| `gather_depth` | 0.0–0.1 | How tight the gathers are |
| `line_width` | 0.001–0.01 | Stitch resist line width |
| `pattern_type` | 0–5 | Straight, curved, floral, geometric |

## GLSL Snippet

```glsl
float nui(vec2 uv, float thickness) {
    float path = bezier_distance(uv, stitch_path);
    float resist = smoothstep(thickness, 0.0, path);
    return resist;
}
```

## Prompt Template

> "Nui shibori silk in indigo, fine running-stitch resist creating [PATTERN] lines, subtle gathered texture along stitch paths, delicate Japanese textile art"

## Anti-Drift

- **Not embroidery**: Nui stitches are functional resist, not decorative
- **Stitches removed**: After dyeing, the thread is pulled out
- **Fine lines**: Much more delicate than bound or clamped resist

---

*Stitch, pull, dye, remove. The thread is the resist.*
