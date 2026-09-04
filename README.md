# 🌳 qrTree — Árbol de Bloques

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

Solo abre `qrTree.html` en cualquier navegador moderno. No necesita servidor ni instalación.

```
# Opcional: si quieres un servidor local
npx serve .
```

## Características

- **QR funcional** — el código generado se puede escanear con cualquier lector QR
- **Árbol procedural** — tronco orgánico con CatmullRomCurves, ramificación recursiva y copa frondosa
- **4 temporadas** — cada una con paleta de colores, partículas (pétalos, polen, hojas, nieve) y comportamiento único
- **Interactivo** — arrastra para girar, rueda para acercar/alejar
- **Descarga** — exporta la escena 3D o el QR plano como PNG
- **Animación de crecimiento** — el árbol crece y se aplana con easing elástico

## Stack

- [Three.js](https://threejs.org/) r128 — renders 3D
- [qrcode-generator](https://github.com/nicktmro/node-qrcode) — generación de QR
- CSS custom — diseño editorial con tipografía Fraunces + Inter
- JavaScript vanilla — sin build tools, sin frameworks

## Licencia

MIT
