# Miura Shibori

Hooked and looped. Diamond grid.

## What It Is

Miura is a **Japanese resist-dye technique** where fabric is gathered with a hooked needle in a continuous looping pattern, creating a diamond grid of resisted points without cutting the thread.

## Construction

- **Hooked needle**: Special tool hooks and pulls fabric
- **Continuous thread**: One thread loops through all gathering points
- **Diamond grid**: Points arranged in regular diamond pattern
- **Dye bath**: Looped points resist dye

## Visual DNA

- **Diamond grid**: Regular diamond-shaped pattern of resisted points
- **Continuous line**: The thread path is visible as connecting lines
- **Soft dots**: Resisted points are soft circles, not sharp
- **Geometric regularity**: Very regular, tessellating pattern
- **Common uses**: Silk, traditional Japanese garments, komon (small pattern) kimono

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `grid_size` | 0.02–0.1 | Diamond cell size |
| `point_size` | 0.005–0.02 | Resisted dot size |
| `thread_visibility` | 0.0–0.5 | How visible connecting thread |
| `regularity` | 0.8–1.0 | How uniform the grid |

## GLSL Snippet

```glsl
float miura(vec2 uv, float size) {
    vec2 diamond = abs(fract(uv / size) - 0.5) * 2.0;
    float points = smoothstep(0.2, 0.0, length(diamond - 0.5));
    return points;
}
```

## Prompt Template

> "Miura shibori silk in indigo, diamond grid of resisted points from hooked-needle looping, continuous thread path visible between points, komon small-pattern Japanese textile"

## Anti-Drift

- **Hooked needle**: Special tool distinguishes miura from other shibori
- **Continuous thread**: One thread for all points; not cut between
- **Diamond grid**: Specific geometric arrangement

---

*Hook, loop, hook, loop. The diamond is the grid.*
