# DISTRIGAMA v5.9 — Modularización JS completa

## Qué cambió
- 7 módulos nuevos en `js/`: config, auth, censo, utils, cartera, pdf-xlsx, reporte.
- `index.html`: 2.431 → 1.140 líneas (453 → 392 KB). El bloque inline solo conserva el setup del tab Pedido + imports.
- Estado compartido (`cart`, `disc`, `userProfile`, etc.) ahora vive en el objeto `state` exportado desde `js/config.js`.
- Todos los handlers `onclick` siguen en `window.*` — el HTML no cambió (head idéntico byte a byte, verificado con md5).
- `APP_VERSION = '5.9'` (ahora en `js/config.js`, no en index.html).
- `sw.js`: cache `distrigama-v4` + los 7 archivos js en `OFFLINE_ASSETS`.
- Desviaciones menores vs el plan: `fbEl` quedó en `utils.js` (no en reporte.js) y `renderCart`/`calcCartSub` en `pdf-xlsx.js` (lógica de carrito, no de cartera).

## Subir al fork (puche3a/distrigama-app)
1. Crear carpeta `js/` y subir los 7 archivos.
2. Reemplazar `index.html` y `sw.js`.
3. Probar en `puche3a.github.io/distrigama-app/`: login, censo, pedido+PDF, cartera, mi día, admin.

> Nota: el banner "actualización disponible" aparecerá en pruebas porque Firestore aún dice 5.8. Es normal.

## Deploy a producción (cuenta itdistrigama)
- [ ] Subir `index.html`, `sw.js` y carpeta `js/` (data-catalog.js y manifest.json no cambian)
- [ ] Firestore: `config/app → version: "5.9"`
- [ ] Probar en Android + iOS
