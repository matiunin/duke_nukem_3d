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
  weapons/   — viewmodels (pistol, shotgun, mighty foot, chaingun, RPG)
  enemies/   — trooper (PASS), pigcop (PASS), octabrain (PASS)
  hud/       — DIGITALNUM + CROSSHAIR PASS refs; rejected INV/statusbar refs noted
  ref/       — quality anchor
  TILE-MAP.md — PASS file → NAMES.H tile bases
  names-excerpt.md — цитаты #define (не полный GPL NAMES.H)
```

## Статус ассетов / Asset status

| Файл | Статус |
|------|--------|
| cover/*, hero/*, weapons/*, enemies/duke-trooper-v1.png, ref/* | **PASS** (AD deploy-ready) |
| weapons/duke-chaingun-v1.png | **PASS** (AD deploy-ready) |
| weapons/duke-rpg-v1.png | **PASS** (AD deploy-ready) |
| enemies/duke-pigcop-v1.png | **PASS** (AD deploy-ready) |
| enemies/duke-octabrain-v1.png | **PASS** (AD deploy-ready) |
| hud/hud-digitalnum-v1.png | **PASS** (AD revised; `DIGITALNUM` 2472) |
| hud/hud-crosshair-v1.png | **PASS** (AD revised; `CROSSHAIR` 2523) |
| hud/hud-inv-icons-v1.png, hud/hud-statusbar-with-inv-v1.png | **FAIL / excluded** (AD revised; not staged) |

См. также `TILE-MAP.md` для привязки к тайлам `source/NAMES.H`.

**Fidelity / Alex rule:** only hires of existing DN3D assets, per AD-BRIEF §2c; the revised HUD PASS is limited to DIGITALNUM and CROSSHAIR.
