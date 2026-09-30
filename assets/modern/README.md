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
  weapons/   — viewmodels (pistol v5, shotgun, mighty foot, chaingun, RPG)
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
| cover/*, hero/*, current PASS weapons (except explicitly superseded entries), enemies/duke-trooper-v1.png, ref/* | **PASS** (AD deploy-ready) |
| weapons/duke-pistol-v5.png (+ side-by-side) | **PASS** (AD §2d; `FIRSTGUN` 2524+; v2 superseded) |
| weapons/duke-pistol-v2.png | **SUPERSEDED** (replaced by pistol remaster v5; retained for history) |
| weapons/duke-shotgun-v4.png (+ side-by-side) | **PASS** (AD §2d; `SHOTGUN` 2613; v2 superseded) |
| weapons/duke-shotgun-v2.png | **SUPERSEDED** (replaced by shotgun remaster v4; retained for history) |
| weapons/duke-chaingun-v1.png | **PASS** (AD deploy-ready) |
| weapons/duke-rpg-v1.png | **PASS** (AD deploy-ready) |
| enemies/duke-pigcop-v1.png | **PASS** (AD deploy-ready) |
| enemies/duke-octabrain-v1.png | **PASS** (AD deploy-ready) |
| hud/hud-digitalnum-v1.png | **PASS** (AD revised; `DIGITALNUM` 2472) |
| hud/hud-crosshair-v1.png | **PASS** (AD revised; `CROSSHAIR` 2523) |
| hud/hud-inv-icons-v2.png (+ `.html`, notes) | **PASS** (AD §2d; NN×8 hires of existing inventory tiles; v1 superseded) |
| hud/hud-inv-icons-v1.png, hud/hud-statusbar-with-inv-v1.png | **FAIL / excluded** (v1 superseded; not staged) |

См. также `TILE-MAP.md` для привязки к тайлам `source/NAMES.H`.

**Fidelity / Alex rule:** only hires of existing DN3D assets, per AD-BRIEF §2d; INV v2 is nearest-neighbor ×8 of the vanilla crops. v1 is superseded; the statusbar overlay remains excluded.
