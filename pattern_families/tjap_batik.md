# Tjap / Cap Batik

Stamped wax, repeated motifs.

## What It Is

Tjap (or cap) batik uses a **copper stamp** to apply hot wax in repeated patterns. It's faster than hand-drawn canting batik and produces consistent, repeatable motifs.

## Construction

- **Copper stamp**: Intricate pattern cut into copper sheet
- **Hot wax dip**: Stamp heated, dipped in wax, pressed to cloth
- **Repeated impressions**: Same motif stamped across fabric
- **Often combined**: Tjap for ground pattern, canting for details

## Visual DNA

- **Repeated motifs**: Same pattern appearing regularly
- **Slight variation**: Each stamp impression slightly different
- **Intricate detail**: Fine lines possible with precision stamps
- **Faster production**: More regular than hand-drawn
- **Common uses**: Commercial batik, traditional garments, textiles

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `stamp_repeat` | 0.05–0.2 | Distance between impressions |
| `imprint_variation` | 0.0–0.1 | Slight misalignment |
| `wax_coverage` | 0.3–0.8 | How much cloth is waxed |
| `detail_level` | 0.5–1.0 | Intricacy of stamp pattern |

## GLSL Snippet

```glsl
float tjap_batik(vec2 uv, float repeat) {
    vec2 tile = fract(uv / repeat);
    float stamp = texture(tjap_pattern, tile).r;
    float variation = noise(uv * 100.0) * 0.05;
    return stamp + variation;
}
```

## Prompt Template

> "Javanese tjap batik in brown and cream, copper-stamped repeated [MOTIF] pattern across cotton, slight variation between impressions, faster production than hand-drawn canting"

## Anti-Drift

- **Not canting batik**: Tjap is stamped; canting is hand-drawn with tool
- **Repeated pattern**: Tjap produces repeats; canting is often unique
- **Copper stamp**: The tool is a metal stamp, not a pen-like canting

---

*Stamp and repeat. The copper is the printer.*
