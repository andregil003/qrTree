# Changelog

## [1.2.0] - 2026-09-09

### Added
- **5 estilos de QR** (suelo 3D + QR plano): Clásico, Redondo, Diamante, Voxel (módulos con altura variable) y Minimal
- **Color de acento personalizado** para los módulos oscuros del QR (persistente + en la URL)
- **Pixel art por tile**: modo "Pintar tiles" para colorear cada cuadro del QR haciendo clic, con botón restablecer
- **Importar imagen**: sube una imagen y se convierte en pixel art sobre la grilla del QR
- **Título de negocio**: texto opcional que se imprime bajo el QR plano
- **Forma de copa**: Redonda, Piramidal, Paraguas y Llorona (afecta ramas y distribución de hojas)
- **Rama central vertical** en el árbol: rellena el hueco central que quedaba sobre el tronco
- **GIF animado**: botón "Descargar GIF" que renderiza el árbol creciendo (~3s, 480px) con gif.js vendored localmente
- URL por defecto: `https://github.com/andregil003` (fallback del JS)

### Changed
- El QR plano ahora dibuja todos los tiles (soporta pixel art) y crece en altura si hay título
- `generate()` persiste estilo, copa, acento, título y tiles (localStorage + URL)

### Fixed
- Fallback de URL en `generate()` y `copyLinkBtn` apuntaba a `claude.ai` → ahora `github.com/andregil003`

## [1.1.0] - 2026-09-09

### Added
- PWA mínima: `manifest.webmanifest` + iconos 192/512/maskable + `theme-color` → instalable y standalone en móvil (iOS 16.4+)
- Anuncios de screen reader (`aria-live`) al cambiar temporada y generar árbol
- Navegación por teclado: flechas orbitan la cámara, `+`/`-` zoom
- Compartir nativo en móvil (`navigator.share`) para el enlace y las imágenes

### Changed
- Móvil: el stage 3D ahora va ARRIBA del panel en pantallas ≤880px
- Móvil: hint correcto ("Arrastra para girar · Pellizca para acercar")
- Móvil: DPR limitado a 1.5 (vs 2 en desktop) y SMAA desactivado → rendimiento estable
- Móvil: sombras a 1024px y menos instancias (hojas, nieve, hojas caídas, brotes, grama)
- Móvil: el render loop salta frames impares cuando el árbol está estable (mitad de coste)
- Móvil: el render loop se pausa cuando el stage no está visible (IntersectionObserver)
- Frustum portrait: en vertical el contenido se ajusta al ancho visible
- Descargas con `toBlob()` + `URL.createObjectURL` (el `toDataURL` falla en iOS Safari)
- Export de escena: 2048px máx en móvil, 2560px en desktop

### Fixed
- `touch-action: none` en el canvas → el navegador ya no roba el drag/pinch en móvil
- QR plano responsive (hasta 220px) en pantallas pequeñas

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