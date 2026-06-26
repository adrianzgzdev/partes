# Pedido Servicios — PWA de partes de campo

App offline-first para capturar partes de trabajo sin cobertura y volcarlos
después al sistema. Hecha con HTML/CSS/JS, sin dependencias. Los datos se
guardan en el dispositivo de cada usuario (localStorage); no hay servidor.

## Archivos

- `index.html` — la app (todo en uno).
- `manifest.json` — nombre, iconos y colores para poder instalarla.
- `service-worker.js` — cachea la app para que arranque y funcione sin conexión.
- `icon-192.png`, `icon-512.png`, `icon-512-maskable.png` — iconos.

## Publicar en GitHub Pages (en una subcarpeta del dominio)

La idea es dejarlo en `adrianzgzdev.com/partes/`. En el repositorio que ya
sirve tu GitHub Pages:

```bash
# en la raíz del repo de tu Pages
mkdir -p partes
# copia aquí los 6 archivos de esta carpeta
git add partes
git commit -m "feat: add offline PWA for field work orders"
git push
```

Espera 1–2 minutos a que GitHub Pages despliegue.

### Requisitos para que la PWA funcione
- Debe servirse por **HTTPS** (GitHub Pages ya lo hace). En Settings → Pages,
  deja activado **Enforce HTTPS**.
- Las rutas del manifest y del service worker son **relativas** (`./`), así que
  funciona igual en `/partes/` que en cualquier otra subcarpeta.

## Instalar en el móvil / portátil

Abre `https://adrianzgzdev.com/partes/` una vez **con cobertura** (para que se
cachee) y luego:

- **Android (Chrome):** menú ⋮ → *Instalar aplicación* / *Añadir a pantalla de inicio*.
- **iPhone (Safari):** Compartir → *Añadir a pantalla de inicio*.
- **Escritorio (Chrome/Edge):** icono de instalar en la barra de direcciones.

A partir de ahí abre desde el icono y funciona **sin conexión**.

## Compartir con compañeros

Pásales solo el enlace `https://adrianzgzdev.com/partes/`. Cada uno instala y
sus datos quedan **solo en su dispositivo** (no se ven entre sí). El botón de
exportar/backup lo podemos reactivar si queréis copia de seguridad.

## Actualizar la app más adelante

1. Edita `index.html` (u otros archivos).
2. Sube la versión de la caché en `service-worker.js`: cambia
   `pedido-servicios-v1` por `-v2`, `-v3`, etc.
3. `git commit` + `git push`. Los usuarios reciben la versión nueva la próxima
   vez que abran la app (puede requerir cerrarla y reabrirla una vez).
