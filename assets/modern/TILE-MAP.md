# TILE-MAP — PASS assets → NAMES.H bases

Источник ID: `source/NAMES.H` (ветка `master` репозитория). Полный файл GPL — **не** копируем сюда; см. `names-excerpt.md`.

Эти файлы — staging-референсы и vanilla tile crops. Подмена runtime потребует ART/GRP pipeline или hires overlay.

| PASS file | Role | NAMES.H base(s) | Notes |
|-----------|------|-----------------|-------|
| `weapons/duke-pistol-v5.png` (+ `duke-pistol-v5-sidebyside.png`) | Pistol remaster viewmodel | `FIRSTGUN` **2524+**, reload `FIRSTGUNRELOAD` 2528; world pickup `FIRSTGUNSPRITE` 21 | **PASS FIRSTGUN 2524+** — AD §2d remaster; side-by-side included |
| `weapons/duke-pistol-v2.png` | Pistol viewmodel | `FIRSTGUN` **2524+**, reload `FIRSTGUNRELOAD` 2528; world pickup `FIRSTGUNSPRITE` 21 | **SUPERSEDED** — remaster replaced by v5; retained for history |
| `weapons/duke-shotgun-v4.png` (+ `duke-shotgun-v4-sidebyside.png`) | Shotgun remaster viewmodel | `SHOTGUN` **2613**; shells `SHOTGUNSHELL` **2535**; world `SHOTGUNSPRITE` 28, ammo `SHOTGUNAMMO` 49 | **PASS** — AD §2d remaster; v2 superseded |
| `weapons/duke-shotgun-v2.png` | Shotgun viewmodel | `SHOTGUN` **2613**; shells `SHOTGUNSHELL` **2535**; world `SHOTGUNSPRITE` 28, ammo `SHOTGUNAMMO` 49 | **SUPERSEDED** — remaster replaced by v4; retained for history |
| `weapons/duke-chaingun-v62.png` (+ `duke-chaingun-v62-sidebyside.png`, `duke-chaingun-v62-crop-knuckle.png`) | Chaingun remaster viewmodel | `CHAINGUN` **2536** (vanilla tile ref TILES009_232) | **PASS CHAINGUN 2536** — AD §2d remaster; v1 superseded |
| `weapons/duke-chaingun-v1.png` | Chaingun viewmodel | `CHAINGUN` **2536** | **SUPERSEDED** — remaster replaced by v6.2; retained for history |
| `weapons/duke-rpg-v2.png` (+ `duke-rpg-v2-sidebyside.png`) | RPG remaster viewmodel | `RPGGUN` **2544**; muzzle flash `RPGMUZZLEFLASH` **2545** | **PASS RPGGUN 2544 / RPGMUZZLEFLASH** — AD §2d remaster; v1 superseded |
| `weapons/duke-rpg-v1.png` | RPG viewmodel | `RPGGUN` **2544**; muzzle flash `RPGMUZZLEFLASH` **2545** | **SUPERSEDED** — remaster replaced by v2; retained for history |
| `weapons/duke-pipebomb-v31.png` (+ `duke-pipebomb-v31-sidebyside.png`) | Pipebomb remaster viewmodel / remote | `HANDTHROW` **2573**; `HANDREMOTE` **2570**; world `HEAVYHBOMB` **26** | **PASS HANDTHROW / HANDREMOTE / HEAVYHBOMB** — AD §2d remaster; v1/v2/v3 superseded (not staged) |
| `weapons/duke-foot-v2.png` (+ `duke-foot-v2-sidebyside.png`) | Mighty Foot / melee remaster | `KNEE` **2521**; related `FIST` **1640** | **PASS** — AD §2d remaster; v1 superseded |
| `weapons/duke-foot-v1.png` | Mighty Foot / melee | `KNEE` **2521**; related `FIST` **1640** | **SUPERSEDED** — remaster replaced by v2; retained for history |
| `enemies/duke-trooper-v1.png` | Assault Trooper | `LIZTROOP` **1680+** (`LIZTROOPRUNNING` 1681, shoot 1715, jetpack 1725, …) | PASS |
| `enemies/duke-pigcop-v1.png` | Pig Cop | `PIGCOP` **2000+** (`PIGCOPSTAYPUT` 2001, dive 2045, dead 2060) | **PASS** |
| `enemies/duke-octabrain-v1.png` | LIZTROOP-style enemy / Octabrain | `OCTABRAIN` **1820+** (`OCTABRAINSTAYPUT` 1821) | **PASS** |
| `hud/hud-digitalnum-v1.png` | Digital LED number strip | `DIGITALNUM` **2472** | **PASS** — revised HUD pack; hires existing DN3D asset per §2c |
| `hud/hud-crosshair-v1.png` | Crosshair reference | `CROSSHAIR` **2523** | **PASS** — revised HUD pack; hires existing DN3D asset per §2c |
| `hud/hud-inv-icons-v2.png` (+ `.html`, notes) | Inventory icon strip | `FIRSTAID_ICON` **2460**, `HEAT_ICON` **2461**, `BOOT_ICON` **2463**, `JETPACK_ICON` **2467**, `AIRTANK_ICON` **2468**, `STEROIDS_ICON` **2469**, `HOLODUKE_ICON` **2470**, `ACCESS_ICON` **2471** (icon range **2460–2471**, excluding `BOTTOMSTATUSBAR` 2462) | **PASS v2** — nearest-neighbor ×8 (`ref-vanilla/inv/tile-*.png`); v1 superseded |
| `hud/hud-statusbar-with-inv-v1.png` | Statusbar + inventory overlay | `BOTTOMSTATUSBAR` **2462** | **FAIL / excluded** by revised AD; not committed |
| `hud/hud-fidelity-v1.1.png`, `hud/hud-fidelity-v1.1-sidebyside.png` | Superseded HUD composite references | `BOTTOMSTATUSBAR` **2462**, `DIGITALNUM` **2472**, `CROSSHAIR` **2523** | Legacy reference; not current revised HUD PASS |
| `hero/duke-hero-v2.png` | Hero marketing still | **not a tile** (site/launcher); player body `APLAYER` **1405**, `APLAYERTOP` 1400 | Site art |
| `cover/launcher-cover.png` | Launcher / skill card | **not GRP** — site asset | Deploy: `design/deploy/` |
| `cover/duke-cover-v2.png` | Full cover | site / marketing | |
| `cover/duke-cover-v2-320x200.png` | Cover 320×200 | site / launcher slot | |
| `ref/ref-duke-modern.png` | Quality anchor | n/a | AAA bar; pixel/PS1 = FAIL |

## Pipeline note

1. Live game: 8-bit tiles in `DUKE3D.GRP` / wasm `vendor/index.data`.
2. This folder: staging only.
3. Next engineering step: ART tile replacement or hires remap keyed by the IDs above.
