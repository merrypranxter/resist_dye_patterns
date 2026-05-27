# Resist Dye Patterns

Bound, waxed, stitched, clamped — and then let chemistry do the rest.

This repository documents resist-dye systems as **constrained diffusion processes** — patterns created by preventing dye from reaching certain areas of cloth, then allowing the dye to bleed, pool, and react within the boundaries.

## The Core Principle

Resist dye creates pattern through **absence** — by blocking dye, the untouched cloth becomes the design.

- **Wax resist (batik)**: Hot wax applied to cloth blocks dye; cracks in wax create "veins"
- **Bind resist (tie-dye, shibori)**: Physical compression prevents dye penetration
- **Stitch resist (nui shibori)**: Sewn thread creates gathered lines of resistance
- **Clamp resist (itajime)**: Wooden blocks press the cloth, creating geometric blanks
- **Paste resist**: Rice paste or other thickener blocks dye (e.g., Japanese tsutsugaki)

## Visual DNA of Resist-Dyed Cloth

- **Feathered / blurred edges**: Dye bleeds past resist boundaries
- **Crackle networks**: Wax breaks; dye enters cracks creating fine dark lines
- **Symmetry from folding**: Tie-dye and shibori create mirror/repeat patterns
- **Color layers**: Multiple dye baths with partial resist removal between
- **Organic irregularity**: Hand-applied resist is never perfectly uniform

## The Resist Families

### Wax Resist (Batik)
- [Traditional batik](pattern_families/batik.md) — tjanting tool, canting lines, copper stamps
- [Crackle networks](pattern_families/crackle.md) — wax break patterns, fine vein lines
- [Tjap / cap batik](pattern_families/tjap_batik.md) — stamped wax, repeated motifs

### Bind Resist (Tie-Dye / Shibori)
- [Spiral tie-dye](pattern_families/spiral_tie_dye.md) — central bind, concentric rings
- [Bullseye tie-dye](pattern_families/bullseye.md) — multiple points, radial rings
- [Accordion fold](pattern_families/accordion_fold.md) — parallel binds, stripe patterns
- [Ice dye](pattern_families/ice_dye.md) — dye powder on ice, random diffusion
- [Low-water immersion](pattern_families/low_water_immersion.md) — crumpled cloth, limited liquid

### Shibori (Japanese Resist)
- [Arashi shibori](pattern_families/arashi.md) — pole-wrapped diagonal lines
- [Itajime](pattern_families/itajime.md) — clamp-resist, geometric shapes
- [Nui shibori](pattern_families/nui.md) — stitch-resist, gathered lines
- [Kumo shibori](pattern_families/kumo.md) — spiderweb binding, radiating lines
- [Miura shibori](pattern_families/miura.md) — looped binding, water-ripple

### Dye-Weave Hybrids
- [Ikat / kasuri](pattern_families/ikat.md) — resist-dyed threads before weaving
- [Bandhani / tie-dye dots](pattern_families/bandhani.md) — tiny bound dots, Indian tradition

### Chemical / Discharge
- [Discharge dye](pattern_families/discharge.md) — removing dye instead of adding
- [Bleach patterning](pattern_families/bleach.md) — selective color removal

## Shader Translation: Resist-Dye Parameters

| Parameter | What It Controls | Range | Notes |
|-----------|---------------|-------|-------|
| `resist_mask` | Areas blocked from dye | 0–1 | Binary or gradient |
| `dye_diffusion_radius` | How far dye bleeds | 0.0–0.2 | UV space |
| `crackle_density` | Wax crackle line frequency | 0–50 | Lines per unit |
| `crackle_width` | Crackle line thickness | 0.001–0.01 | UV space |
| `fold_symmetry` | Mirror/repeat from binding | 2–16 | Number of symmetrical sections |
| `color_layer_count` | Multiple dye baths | 1–5 | Each adds complexity |
| `color_bleed_overlap` | How colors mix at edges | 0.0–1.0 | 0 = hard edge, 1 = total mix |

## Resist-to-Shader Logic

### Dye Diffusion
```glsl
float resist_dye(vec2 uv, float resist_mask, float diffusion) {
    float dye = gaussian_blur(1.0 - resist_mask, uv, diffusion);
    return dye; // 1.0 = fully dyed, 0.0 = resisted
}
```

### Wax Crackle
```glsl
float crackle(vec2 uv, float density, float seed) {
    float noise = fbm(uv * density + seed);
    float crack = smoothstep(0.45, 0.5, noise) * smoothstep(0.55, 0.5, noise);
    return crack; // 1.0 = crack line, 0.0 = solid wax
}
```

### Fold Symmetry
```glsl
vec2 fold_symmetry(vec2 uv, int folds) {
    float angle = atan(uv.y, uv.x);
    float sector = PI / float(folds);
    float folded = abs(fract(angle / (2.0 * sector)) - 0.5) * 2.0;
    return vec2(folded * length(uv), 0.0); // Radial fold
}
```

## Prompt Templates

### Batik
> "Traditional Javanese batik in [COLOR PALETTE] on cotton, showing hand-drawn wax-resist [MOTIF] pattern with fine crackle veins where dye entered wax breaks, slight dye bleed at edges, photographed flat with soft even light"

### Tie-Dye Spiral
> "A psychedelic spiral tie-dye in [COLOR LIST], showing concentric rings radiating from central bind point, color bleed between rings, slight asymmetry from hand binding, cotton t-shirt fabric"

### Shibori
> "Japanese [TYPE] shibori in indigo on cotton, showing [PATTERN] created by [METHOD], characteristic blurred edges and white resisted areas, traditional craft aesthetic, flat lay photograph"

## Anti-Drift: Resist-Dye Specific

- **Batik vs printed imitation**: Real batik has wax crackle; printed batik is smooth
- **Tie-dye vs ice dye**: Tie-dye = deliberate binding; ice dye = random powder placement
- **Shibori is not just "tie-dye"**: Shibori is a specific Japanese tradition with named techniques
- **Discharge is not bleach**: Discharge uses reducing agents; bleach uses oxidation
- **Multiple dye baths** should show layering, not flat color

---

*This repo treats resist as a boundary condition for a diffusion equation. The pattern is the solution.*
