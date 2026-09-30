# HUD INV icons v2 — notes (Designer)

**Правило:** AD-BRIEF **§2d** — **hires существующих DN3D-тайлов** (тот же силуэт / tile-language), **не** новые иллюстрации.

## AD status
| Артефакт | Статус |
|----------|--------|
| `hud-inv-icons-v1.png` | **FAIL** — too smooth / illustrated (superseded) |
| `hud-inv-icons-v2.png` (+html, this notes) | на ревью AD — NN upscale only |
| `hud-digitalnum-v1` / `hud-crosshair-v1` | **PASS** — не трогали |

## Source
- Spriters Resource sheet **«Status Bar & HUD Elements»** (vanilla DN3D HUD)
- Local: `art/ref-vanilla/inv/statusbar-hud-elements-vanilla.png` (322×209, palette, teal+cyan mask)
- Font Items row → inventory icons; Keys row → blue ACCESS keycard

## Process (v2)
1. Crop each vanilla sprite → `art/ref-vanilla/inv/tile-<NAME>.png` (native px, palette colors, teal/cyan → alpha)
2. **Nearest-neighbor ×8** → `tile-<NAME>-x8.png` — **no** smooth redraw, **no** AI regenerate, **no** vector reimagine
3. Sheet `design/hud-inv-icons-v2.png`: per icon **VANILLA ×4 | HIRES ×8** side-by-side in yellow bevel INV wells
4. Optional HTML mirror: `design/hud-inv-icons-v2.html`

## Crops (native)

| Name | NAMES tile | Crop (x0,y0,x1,y1) | Size | ×8 |
|------|------------|--------------------|------|----|
| FIRSTAID | 2460 | 158,104,175,116 | 17×12 | 136×96 |
| HEAT | 2461 | 176,105,193,116 | 17×11 | 136×88 |
| BOOT | 2463 | 194,102,211,116 | 17×14 | 136×112 |
| JETPACK | 2467 | 230,99,247,116 | 17×17 | 136×136 |
| AIRTANK | 2468 | 213,101,227,116 | 14×15 | 112×120 |
| STEROIDS | 2469 | 250,101,263,116 | 13×15 | 104×120 |
| HOLODUKE | 2470 | 269,98,280,116 | 11×18 | 88×144 |
| ACCESS | 2471 | 284,98,295,103 | 11×5 | 88×40 |

Sheet Font Items L→R: FIRSTAID, HEAT, BOOT, AIRTANK, JETPACK, STEROIDS, HOLODUKE; ACCESS = blue keycard (Keys).

## Forbidden (why v1 failed)
- Smooth 2.5D / illustrated redraw
- Pose / silhouette change
- GenerateImage / AI new icons

## Files
- `design/hud-inv-icons-v2.png`
- `design/hud-inv-icons-v2.html`
- `design/hud-inv-icons-v2-notes.md` (this)
- `art/ref-vanilla/inv/tile-*.png` + `tile-*-x8.png`
