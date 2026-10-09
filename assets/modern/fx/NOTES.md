# FX remaster v1 — notes (§2d: enlarge/clean only)
Source: vanilla ART tiles read directly from shareware DUKE3D.GRP (archive.org `dukesw-11`, v1.1; TILES000-012.ART + PALETTE.DAT, index 255 = transparent). Tile numbers = NAMES.H. Native crops in `ref-vanilla/`.
| file | NAMES.H tile | tile # | vanilla size | scale |
|---|---|---|---|---|
| explosion2-f05-v1.png | EXPLOSION2 (1890 + frame 4) | 1894 | 118x102 | x8 |
| smallsmoke-v1.png | SMALLSMOKE | 2329 | 16x16 | x16 |
| shotspark1-v1.png | SHOTSPARK1 (frame 1) | 2596 | 18x12 | x16 |
| fire-v1.png | FIRE | 2271 | 32x55 | x8 |
| shrinkspark-v1.png | SHRINKSPARK | 1646 | 46x41 | x8 |
Each also has `-sidebyside.png` (vanilla NN | remaster, checkerboard) and `-crop100.png` (1:1 centre crop of the remaster).
Method (`tools/remaster.py`): palette->RGB; transparent pixels colour-bled from nearest opaque pixel (no halo); bicubic upscale; bilateral blend to remove stair-stepping; mild unsharp; alpha = bicubic-upscaled vanilla mask, soft-thresholded at 0.5 (same silhouette, anti-aliased edge). No generative redraw, no new detail, palette hues unchanged. Dark rim pixels on smoke/explosion are vanilla opaque pixels, kept.
Not used: RPGMUZZLEFLASH 2545/2546 (tile contains the RPG barrel = viewmodel, covered by rpg-v2 PASS). DN3D has no flamethrower; FIRE used instead.

## v2 (EXPLOSION2 f05 / FIRE only) — AD rejected v1 (plain upscale); v2 adds material inside the same silhouette
Files: `explosion2-f05-v2*.png`, `fire-v2*.png` (+ `-sidebyside`, `-crop100`). Script: `tools/v2.py`.
Alpha IoU (remaster alpha>0.5 vs upscaled vanilla mask):
| tile | IoU vs bicubic-upscaled vanilla mask | IoU vs nearest-neighbour upscaled mask |
|---|---|---|
| EXPLOSION2 f05 (1894) | **0.9998** | 0.9947 |
| FIRE (2271) | **0.9990** | 0.9756 |
Method: vanilla = reference. Heat map from blurred vanilla luminance + distance-to-edge; colour ramp built from the tile's own vanilla pixels (sorted by luminance, only the hottest end eased toward warm white) so hues stay vanilla. Detail by procedural fBm: domain-warped turbulence (warp follows the vanilla luminance gradient) + ridged-noise smoke veins (explosion: darker vanilla orange/brown, no black); fire: vertically stretched, upward-sheared noise = separate tongues, dark-orange gaps between them, yellow-white core. Vanilla rim colours blended back at the edge (dark-orange outline); local contrast on luminance only, faded out near the edge. Final alpha = vanilla mask (soft 0.5 threshold, anti-aliased), all colour clipped to it; transparent pixels colour-bled, so no halo/black fringe. No generative models used.

## v3 batch (after AD PASS of explosion2-f05-v2 + fire-v2) — files still named `*-v2*`
Script: `tools/v3.py` (reuses `tools/v2.py` helpers). IoU = remaster alpha>0.5 vs upscaled vanilla mask (smooth = bicubic-upscaled+soft threshold, same mask the recipe clips to; NN = hard nearest-neighbour upscale).
| tile | NAMES.H | scale | IoU smooth | IoU NN |
|---|---|---|---|---|
| shrinkspark-v2 | SHRINKSPARK 1646 | x12 | 0.9962 | 0.9788 |
| smallsmoke-v2 | SMALLSMOKE 2329 | x16 | 1.0000 | 0.9343 |
| shotspark1-v2 | SHOTSPARK1 2596 | x16 | 1.0000 | 0.9502 |
| explosion2-f01-v2 | EXPLOSION2 1890 | x8 | 0.9993 | 0.9802 |
| explosion2-f02-v2 | EXPLOSION2 1891 | x8 | 0.9996 | 0.9922 |
| explosion2-f03-v2 | EXPLOSION2 1892 | x8 | 0.9997 | 0.9933 |
| explosion2-f04-v2 | EXPLOSION2 1893 | x8 | 0.9998 | 0.9945 |
| explosion2-f05-v2 | EXPLOSION2 1894 | x8 | 0.9998 | 0.9947 |
| explosion2-f06-v2 | EXPLOSION2 1895 | x8 | 0.9997 | 0.9947 |
| explosion2-f07-v2 | EXPLOSION2 1896 | x8 | 0.9997 | 0.9941 |
| explosion2-f08-v2 | EXPLOSION2 1897 | x8 | 0.9998 | 0.9953 |
| explosion2-f09-v2 | EXPLOSION2 1898 | x8 | 0.9998 | 0.9948 |
| explosion2-f10-v2 | EXPLOSION2 1899 | x8 | 0.9997 | 0.9946 |
| explosion2-f11-v2 | EXPLOSION2 1900 | x8 | 0.9997 | 0.9946 |
| explosion2-f12-v2 | EXPLOSION2 1901 | x8 | 0.9998 | 0.9949 |
| explosion2-f13-v2 | EXPLOSION2 1902 | x8 | 0.9998 | 0.9953 |
| explosion2-f14-v2 | EXPLOSION2 1903 | x8 | 0.9998 | 0.9955 |

EXPLOSION2 series (1890–1903 = f01–f14): shared colour ramp pooled from all 14 vanilla frames (same luminance->colour mapping on every frame), heat = rank of vanilla luminance in the pooled distribution + vanilla mid-frequency structure; noise fields are one world-space canvas cropped around each frame centre (same turbulence everywhere -> no shimmer); vein strength scaled down on large-core frames (`vein_scale` in `explosion2-series-v2-meta.json`, 1.0 small core -> 0.25 big core). Frames keep native size x8; sprite origin offsets (picanm xoff/yoff x8) are in the meta json and used to align `explosion2-series-v2-contact.png` (vanilla counterpart: `explosion2-series-vanilla-contact.png`).
CAVEAT: `explosion2-f05-v2*.png` is the AD-PASSed file, left untouched. `explosion2-f05-series-v2*.png` is f05 rendered by the series pipeline (slightly different noise/ramp) — use that one for animation continuity if the PASSed f05 flickers vs neighbours; the contact sheet uses it.
SHRINKSPARK: rays kept sharp (alpha from NN-mask, light smoothing), vanilla green hue kept, polar streaks + core gradient. SMALLSMOKE: ramp floor lifted (min luminance ~60) so vanilla near-black edge pixels do not give a dark rim; soft billow/wisp texture. SHOTSPARK1: alpha footprint = vanilla pixels (corners slightly rounded); per spark cluster a white-hot core at the brightest pixel fading to orange tail, hue from vanilla; transparent pixels colour-bled (no pink/magenta key colour fringe).

## v3 batch (AD verdict: SMALLSMOKE v2 + SHRINKSPARK v2 PASS, untouched; SHOTSPARK1 v2 + EXPLOSION2 series v2 FAIL -> new `*-v3*` files; nothing existing overwritten)
Script: `tools/v4.py` (new; imports helpers from `tools/v3.py`; refuses to overwrite). Meta: `explosion2-series-v3-meta.json`. Contact: `explosion2-series-v3-contact.png` (vanilla counterpart `explosion2-series-vanilla-contact.png`). **f05 canonical = series version** `explosion2-f05-v3*`.
EXPLOSION2 v3 method: same pooled 14-frame vanilla colour ramp and same world-space noise canvas. Tone now follows vanilla: heat = rank of the frame's own (lightly blurred) vanilla luminance in the pooled distribution -> ramp; only thin low-amplitude texture on top (fine grain + soft mottling, amplitude ~0.03-0.035 in ramp units; no warp, no ridged veins, no big contrast gain); small subtle core lift; vanilla rim colours blended at the edge; then **per-frame luminance histogram matching** to the vanilla pixel luminance of that frame (so the light stalk f11-f14, dark core f10-f14, pale-yellow f01-f05 are carried over from vanilla). Alpha = same vanilla-mask clip as before.
SHOTSPARK1 v3: colours taken directly from vanilla pixels (NN upscale + light smoothing, no ramp, no darkening); pixel footprint unchanged (corners lightly rounded); sharp white core (sigma 0.2 px) on the brightest pixel(s) of each spark cluster.

| frame | tile | IoU smooth | IoU NN | mean lum van / v3 | lum std van / v3 | p10 van / v3 | p90 van / v3 | hue° van / v3 | sat% van / v3 |
|---|---|---|---|---|---|---|---|---|---|
| shotspark1 | 2596 | 1.0000 | 0.9812 | 101.8 / 107.9 | 38.9 / 43.8 | 49.3 / 55.1 | 168.9 / 174.1 | 28.9 / 29.2 | 90.2 / 85.2 |
| explosion2-f01 | 1890 | 0.9993 | 0.9802 | 119.8 / 119.4 | 47.5 / 47.4 | 54.8 / 56.9 | 185.1 / 184.6 | 28.9 / 29.3 | 85.9 / 84.1 |
| explosion2-f02 | 1891 | 0.9996 | 0.9922 | 196.5 / 196.0 | 31.4 / 31.3 | 146.2 / 147.9 | 218.8 / 219.3 | 37.7 / 38.7 | 55.2 / 44.7 |
| explosion2-f03 | 1892 | 0.9997 | 0.9933 | 200.0 / 199.5 | 42.6 / 42.6 | 115.4 / 116.4 | 230.9 / 230.8 | 40.3 / 40.8 | 51.6 / 41.2 |
| explosion2-f04 | 1893 | 0.9998 | 0.9945 | 202.7 / 202.2 | 34.9 / 34.9 | 146.2 / 144.6 | 224.4 / 225.1 | 40.2 / 41.3 | 51.5 / 39.0 |
| explosion2-f05 | 1894 | 0.9998 | 0.9947 | 194.0 / 193.5 | 32.9 / 33.0 | 146.2 / 144.5 | 218.8 / 218.4 | 37.4 / 38.8 | 56.4 / 45.5 |
| explosion2-f06 | 1895 | 0.9997 | 0.9947 | 183.3 / 182.9 | 34.2 / 34.2 | 115.4 / 122.1 | 211.1 / 210.6 | 34.7 / 35.9 | 61.6 / 53.2 |
| explosion2-f07 | 1896 | 0.9997 | 0.9941 | 172.8 / 172.3 | 38.9 / 38.9 | 104.8 / 103.9 | 203.1 / 205.7 | 32.7 / 33.7 | 66.0 / 59.4 |
| explosion2-f08 | 1897 | 0.9998 | 0.9953 | 163.9 / 163.4 | 42.1 / 42.1 | 85.6 / 89.6 | 203.1 / 203.2 | 31.4 / 32.3 | 69.5 / 64.0 |
| explosion2-f09 | 1898 | 0.9998 | 0.9948 | 156.1 / 155.6 | 44.3 / 44.2 | 76.1 / 77.9 | 203.1 / 202.7 | 30.4 / 31.1 | 72.6 / 67.7 |
| explosion2-f10 | 1899 | 0.9997 | 0.9946 | 150.3 / 149.8 | 45.0 / 44.9 | 76.1 / 77.3 | 203.1 / 202.2 | 29.9 / 30.4 | 75.1 / 70.5 |
| explosion2-f11 | 1900 | 0.9997 | 0.9946 | 146.0 / 145.5 | 45.8 / 45.7 | 76.1 / 75.8 | 203.1 / 201.8 | 29.6 / 30.1 | 76.8 / 72.7 |
| explosion2-f12 | 1901 | 0.9998 | 0.9949 | 139.8 / 139.4 | 46.5 / 46.4 | 76.1 / 72.0 | 193.1 / 194.0 | 29.4 / 29.7 | 79.2 / 75.7 |
| explosion2-f13 | 1902 | 0.9998 | 0.9953 | 134.3 / 133.9 | 48.9 / 48.7 | 54.8 / 61.0 | 193.1 / 193.8 | 29.5 / 29.8 | 80.9 / 77.6 |
| explosion2-f14 | 1903 | 0.9998 | 0.9955 | 122.6 / 122.2 | 49.5 / 49.4 | 54.8 / 54.8 | 185.1 / 187.9 | 29.2 / 29.4 | 84.5 / 82.2 |

Caveat: saturation of v3 is up to ~10 points lower than vanilla on pale frames f02-f05 (ramp has a warm-white tint at the hot end and smoothing); hue within ~1.5°. Metrics are over pixels with alpha>=128.
