# assets/modern — Luck4Luck AAA remaster staging

**RU:** Склад PASS-артов для ремастера Duke Nukem 3D на Luck4Luck. Это **не** готовые in-engine drop-in тайлы.

**EN:** Staging warehouse for Luck4Luck AAA remasters. **Not** drop-in Build engine tiles.

## Важно / Important

| | RU | EN |
|---|---|---|
| Runtime | Живой wasm-порт по-прежнему читает 8-bit Build-тайлы из `DUKE3D.GRP` / browser `vendor/index.data`. | Live runtime still uses 8-bit Build tiles in `DUKE3D.GRP` / browser `vendor/index.data`. |
| Следующий шаг | Замена тайлов в GRP/ART или hires-pipeline для wasm-порта. | Next: GRP/ART tile replacement or hires pipeline for the wasm port. |
| Якорь качества | `ref/ref-duke-modern.png` — эталон AAA. Пиксель / PS1 = **FAIL**. | Quality anchor: `ref/ref-duke-modern.png`. Pixel / PS1 = **FAIL**. |

## Содержимое / Layout

```
assets/modern/
  cover/     — launcher / skill-card (сайт), не GRP
  hero/      — маркетинговый hero still
  weapons/   — viewmodels (pistol v5, shotgun, mighty foot, chaingun v6.2, RPG v2, pipebomb v3.1)
  enemies/   — trooper (PASS), pigcop (PASS), octabrain (PASS)
  hud/       — DIGITALNUM + CROSSHAIR + INV v2 PASS refs; v1/statusbar refs noted
  ref/       — quality anchor
  ref-vanilla/inv/ — vanilla inventory crops and NN×8 tile refs
  TILE-MAP.md — PASS file → NAMES.H tile bases
  names-excerpt.md — цитаты #define (не полный GPL NAMES.H)
```

## Статус ассетов / Asset status

| Файл | Статус |
|------|--------|
| cover/*, hero/*, current PASS weapons (except explicitly superseded entries), ref/* | **PASS** (AD deploy-ready) |
| weapons/duke-pistol-v5.png (+ side-by-side) | **PASS** (AD §2d; `FIRSTGUN` 2524+; v2 superseded) |
| weapons/duke-pistol-v2.png | **SUPERSEDED** (replaced by pistol remaster v5; retained for history) |
| weapons/duke-shotgun-v4.png (+ side-by-side) | **PASS** (AD §2d; `SHOTGUN` 2613; v2 superseded) |
| weapons/duke-shotgun-v2.png | **SUPERSEDED** (replaced by shotgun remaster v4; retained for history) |
| weapons/duke-foot-v2.png (+ side-by-side) | **PASS** (AD §2d; `KNEE` 2521 / `FIST` 1640; v1 superseded) |
| weapons/duke-foot-v1.png | **SUPERSEDED** (replaced by foot remaster v2; retained for history) |
| weapons/duke-chaingun-v62.png (+ side-by-side, crop-knuckle) | **PASS** (AD §2d; `CHAINGUN` 2536 / TILES009_232; v1 superseded) |
| weapons/duke-chaingun-v1.png | **SUPERSEDED** (replaced by chaingun remaster v6.2; retained for history) |
| weapons/duke-rpg-v2.png (+ side-by-side) | **PASS** (AD §2d; `RPGGUN` 2544 / `RPGMUZZLEFLASH`; v1 superseded) |
| weapons/duke-rpg-v1.png | **SUPERSEDED** (replaced by RPG remaster v2; retained for history) |
| weapons/duke-pipebomb-v31.png (+ side-by-side) | **PASS** (AD §2d; `HANDTHROW` 2573 / `HANDREMOTE` 2570 / `HEAVYHBOMB` 26; v1/v2/v3 superseded, not staged) |
| enemies/duke-trooper-v21.png (+ side-by-side, overlay-iou) | **PASS** (AD §2d hires remaster of vanilla tiles; `LIZTROOP` 1680+; v1 superseded) |
| enemies/duke-pigcop-v21.png (+ side-by-side, overlay-iou) | **PASS** (AD §2d hires remaster of vanilla tiles; `PIGCOP` 2000+; v1 superseded) |
| enemies/duke-octabrain-v1.png (+ side-by-side, overlay-iou) | **PASS** (AD §2d hires remaster of vanilla tiles, IoU 0.962; `OCTABRAIN` 1820+; the earlier octabrain v1 was replaced by the remaster under the same filename) |
| enemies/duke-commander-v62.png (+ side-by-side, overlay-iou) | **PASS** (AD §2d hires remaster of vanilla tiles; `COMMANDER` 1920+) |
| enemies/duke-trooper-v1.png, enemies/duke-pigcop-v1.png | **SUPERSEDED** (replaced by trooper v2.1 / pigcop v2.1; retained for history) |
| hud/hud-digitalnum-v1.png | **PASS** (AD revised; `DIGITALNUM` 2472) |
| hud/hud-crosshair-v1.png | **PASS** (AD revised; `CROSSHAIR` 2523) |
| hud/hud-inv-icons-v2.png (+ `.html`, notes) | **PASS** (AD §2d; NN×8 hires of existing inventory tiles; v1 superseded) |
| hud/hud-inv-icons-v1.png, hud/hud-statusbar-with-inv-v1.png | **FAIL / excluded** (v1 superseded; not staged) |

См. также `TILE-MAP.md` для привязки к тайлам `source/NAMES.H`.

**Fidelity / Alex rule:** only hires of existing DN3D assets, per AD-BRIEF §2d; INV v2 is nearest-neighbor ×8 of the vanilla crops. v1 is superseded; the statusbar overlay remains excluded.
