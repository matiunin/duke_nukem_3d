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
  weapons/   — viewmodels (pistol, shotgun, mighty foot)
  enemies/   — trooper (PASS), pigcop (WIP — awaiting AD)
  hud/       — fidelity bar mock + side-by-side
  ref/       — quality anchor
  TILE-MAP.md — PASS file → NAMES.H tile bases
  names-excerpt.md — цитаты #define (не полный GPL NAMES.H)
```

## Статус ассетов / Asset status

| Файл | Статус |
|------|--------|
| cover/*, hero/*, weapons/*, enemies/duke-trooper-v1.png, hud/*, ref/* | **PASS** (AD deploy-ready) |
| enemies/duke-pigcop-v1.png | **WIP** — awaiting Art Director pass |

См. также `TILE-MAP.md` для привязки к тайлам `source/NAMES.H`.
