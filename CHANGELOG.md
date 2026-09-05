# Changelog

## [1.0.0] - 2026-09-04

### Added
- Postprocessing: bloom suave (`UnrealBloomPass`, 0.15/0.5/0.95) + antialiasing (`SMAAPass`) vía `EffectComposer`
- Entorno procedural con reflejos suaves (`PMREMGenerator` + paneles de luz cálida/fría)
- Gradiente de fondo por temporada (`createBackgroundTexture` con `shade()`)
- Scripts de Three.js y addons vendored localmente en `vendor/` (sin CDN ni SRI)

### Fixed
- Orden de carga de scripts vendor: `EffectComposer.js` debe cargar **antes** de `ShaderPass.js`/`MaskPass.js` porque define `THREE.Pass`. Sin esto la página moría con `TypeError: THREE.ShaderPass is not a constructor`
- `shade()` ahora acepta números (los `season.bg` son números `0xRRGGBB`): antes lanzaba `TypeError: hex.slice is not a function`
- `createBackgroundTexture()` convierte `season.bg` a string hex antes de `addColorStop`: antes lanzaba `SyntaxError: Failed to execute 'addColorStop'`