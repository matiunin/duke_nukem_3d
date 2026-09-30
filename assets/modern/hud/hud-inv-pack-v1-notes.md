# HUD INV pack v1 — notes (Designer)

**Язык:** AD-BRIEF §2c / `hud-fidelity-v1.1` — vanilla силуэт, без glass/SaaS.

## Файлы
| Файл | Что |
|------|-----|
| `hud-inv-icons-v1.png` (+html) | FIRSTAID, JETPACK, STEROIDS, HOLODUKE, ACCESS, BOOT, HEAT, AIRTANK |
| `hud-digitalnum-v1.png` (+html) | 0–9 + : / · red LED, без neon-glow |
| `hud-crosshair-v1.png` (+html) | жёлтый «+» + точка · 16/24/32 |
| `hud-statusbar-with-inv-v1.png` (+html) | statusbar + INV с FIRSTAID |

## AD review
PASS/FAIL по pack целиком (или по классам). После PASS — Сисадми в `assets/modern` + TILE-MAP.

## AD review (revised)

- **PASS:** `DIGITALNUM` (`2472`) and `CROSSHAIR` (`2523`) only.
- **FAIL / excluded:** inventory icons (`FIRSTAID_ICON` … `ACCESS_ICON`, `2460–2471`) and the statusbar + inventory overlay (`BOTTOMSTATUSBAR`, `2462`). Their source PNGs are intentionally not copied to this branch.
- **Alex rule:** hires of existing DN3D assets only, per AD-BRIEF §2c fidelity; no new fantasy art.
