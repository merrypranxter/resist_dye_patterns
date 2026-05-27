# Batik

Wax resist, dye, crackle, soul.

## What It Is

Batik is a **wax-resist dyeing technique** where hot wax is applied to cloth, blocking dye from penetrating. The wax is then removed, revealing the resisted pattern. Fine crackle lines where wax breaks are the signature.

## Construction

- **Wax application**: Hot wax applied with canting (hand-drawn) or tjap (stamped)
- **Dye bath**: Cloth immersed in dye; waxed areas resist
- **Wax removal**: Boiled or ironed off after dyeing
- **Multiple layers**: Wax and dye applied repeatedly for complex patterns

## Visual DNA

- **Crackle veins**: Fine dark lines where dye entered wax cracks
- **Feathered edges**: Slight blur where wax boundary wasn't sharp
- **Color layers**: Multiple dye baths create depth
- **Hand-drawn quality**: Slight irregularity from hand application
- **Common uses**: Garments, wall hangings, scarves, traditional dress

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `crackle_density` | 0–50 | Fine crackle lines per unit |
| `crackle_width` | 0.001–0.005 | Crackle line thickness |
| `dye_bleed` | 0.0–0.02 | Slight blur at edges |
| `wax_coverage` | 0.0–1.0 | Percentage of cloth waxed |
| `color_layers` | 1–5 | Number of dye baths |

## GLSL Snippet

```glsl
float batik(vec2 uv, float crackle_d, float seed) {
    float wax = wax_pattern(uv);
    float crackle = fbm(uv * crackle_d + seed);
    float crack = smoothstep(0.45, 0.5, crackle) * smoothstep(0.55, 0.5, crackle);
    float dye = (1.0 - wax) + crack;
    return dye;
}
```

## Prompt Template

> "Traditional Javanese batik in indigo and brown, hand-drawn wax-resist [MOTIF] pattern with fine crackle veins where dye entered wax breaks, slight feathered edges, cotton fabric"

## Anti-Drift

- **Not printed batik**: Real batik has wax crackle; printed imitations are smooth
- **Not tie-dye**: Batik uses wax; tie-dye uses binding
- **Crackle is signature**: The fine veins from broken wax are definitive
- **Hot wax required**: Cold wax or paste doesn't produce the same effect

---

*Wax blocks, dye flows, cracks reveal. The crackle is the soul.*
