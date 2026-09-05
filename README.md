# 🌳 qrTree — Árbol de Bloques

> **Versión:** v1.0.0 · **[▶ Ver en vivo](https://andregil003.github.io/qrTree/)** — abre el generador directo en tu navegador.

Generador de **QR 3D procedural** que convierte cualquier enlace en un árbol voxelizado que crece sobre el suelo de tu código QR real.

## ¿Qué es?

Un archivo HTML standalone que usa **Three.js** para generar una escena 3D interactiva donde:

- El suelo es tu **código QR funcional** (escaneable con la cámara)
- La **grama** crece sobre los módulos oscuros del QR
- Un **árbol procedural** brota del centro con ramificaciones recursivas
- Puedes cambiar entre **4 temporadas** (Primavera, Verano, Otoño, Invierno)
- Alternar entre vista de **árbol 3D** y **QR plano**
- Descargar la escena como imagen PNG

## Uso

Solo abre `index.html` en cualquier navegador moderno. No necesita servidor ni instalación.

```
# Opcional: si quieres un servidor local
npx serve .
```

## Características

- **QR funcional** — el código generado se puede escanear con cualquier lector QR
- **Árbol procedural** — tronco orgánico con CatmullRomCurves, ramificación recursiva y copa frondosa
- **Render premium** — bloom suave, antialiasing SMAA, reflejos de entorno (envMap procedural) y gradiente de fondo por temporada
- **4 temporadas** — cada una con paleta de colores, partículas (pétalos, polen, hojas, nieve) y comportamiento único
- **Árboles únicos con semilla** — cada árbol se genera con una semilla reproducible; el botón 🎲 genera uno nuevo
- **Compartir con un enlace** — la URL guarda `?url=...&season=...&seed=...` para que cualquiera abra tu árbol exacto
- **Persistencia** — recuerda tu última URL, temporada y semilla (localStorage)
- **Interactivo** — arrastra para girar, rueda o pellizco para acercar/alejar
- **Descarga** — exporta la escena 3D (hasta 2K) o el QR plano como PNG
- **Animación de crecimiento** — el árbol crece y se aplana con easing elástico
- **Accesible** — respeta `prefers-reduced-motion` y estados ARIA en los controles

## Compartir

Cualquier árbol se puede compartir copiando el enlace (botón 🔗). El enlace codifica la URL del QR, la temporada y la semilla del árbol:

```
https://andregil003.github.io/qrTree/?url=https%3A%2F%2Fgithub.com%2Fandregil003&season=autumn&seed=123456789
```

## Stack

- [Three.js](https://threejs.org/) (vendored local) — renders 3D + postprocessing (EffectComposer, UnrealBloomPass, SMAAPass)
- [qrcode-generator](https://github.com/kazuhikoarase/qrcode-generator) — generación de QR
- CSS custom — diseño editorial con tipografía Fraunces + Inter
- JavaScript vanilla — sin build tools, sin frameworks
- Scripts de Three.js y sus addons en `vendor/` — sin CDN ni SRI

## Licencia

MIT
