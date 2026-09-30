# TILE-MAP — PASS assets → NAMES.H bases

Источник ID: `source/NAMES.H` (ветка `master` репозитория). Полный файл GPL — **не** копируем сюда; см. `names-excerpt.md`.

Эти PNG — маркетинговые / mock / viewmodel-референсы. Подмена runtime потребует ART/GRP pipeline или hires overlay.

| PASS file | Role | NAMES.H base(s) | Notes |
|-----------|------|-----------------|-------|
| `weapons/duke-pistol-v2.png` | Pistol viewmodel | `FIRSTGUN` **2524+**, reload `FIRSTGUNRELOAD` 2528; world pickup `FIRSTGUNSPRITE` 21 | Viewmodel strip starts at 2524 |
| `weapons/duke-shotgun-v2.png` | Shotgun viewmodel | `SHOTGUN` **2613**; shells `SHOTGUNSHELL` **2535**; world `SHOTGUNSPRITE` 28, ammo `SHOTGUNAMMO` 49 | |
| `weapons/duke-chaingun-v1.png` | Chaingun viewmodel | `CHAINGUN` **2536** | **PASS** |
| `weapons/duke-rpg-v1.png` | RPG viewmodel | `RPGGUN` **2544**; muzzle flash `RPGMUZZLEFLASH` **2545** | **PASS** |
| `weapons/duke-foot-v1.png` | Mighty Foot / melee | `KNEE` **2521**; related `FIST` **1640** | Melee kick / fist sequence |
| `enemies/duke-trooper-v1.png` | Assault Trooper | `LIZTROOP` **1680+** (`LIZTROOPRUNNING` 1681, shoot 1715, jetpack 1725, …) | PASS |
| `enemies/duke-pigcop-v1.png` | Pig Cop | `PIGCOP` **2000+** (`PIGCOPSTAYPUT` 2001, dive 2045, dead 2060) | **PASS** |
| `enemies/duke-octabrain-v1.png` | LIZTROOP-style enemy / Octabrain | `OCTABRAIN` **1820+** (`OCTABRAINSTAYPUT` 1821) | **PASS** |
| `hud/hud-fidelity-v1.1.png` | HUD bar fidelity | `BOTTOMSTATUSBAR` **2462**, `DIGITALNUM` **2472**, `CROSSHAIR` **2523** | Mock / fidelity pass, not ART yet |
| `hud/hud-fidelity-v1.1-sidebyside.png` | HUD compare | (same) | Design reference |
| `hero/duke-hero-v2.png` | Hero marketing still | **not a tile** (site/launcher); player body `APLAYER` **1405**, `APLAYERTOP` 1400 | Site art |
| `cover/launcher-cover.png` | Launcher / skill card | **not GRP** — site asset | Deploy: `design/deploy/` |
| `cover/duke-cover-v2.png` | Full cover | site / marketing | |
| `cover/duke-cover-v2-320x200.png` | Cover 320×200 | site / launcher slot | |
| `ref/ref-duke-modern.png` | Quality anchor | n/a | AAA bar; pixel/PS1 = FAIL |

## Pipeline note

1. Live game: 8-bit tiles in `DUKE3D.GRP` / wasm `vendor/index.data`.
2. This folder: staging only.
3. Next engineering step: ART tile replacement or hires remap keyed by the IDs above.
