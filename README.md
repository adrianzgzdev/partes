# Pedido Servicios

App web **offline-first** para que un técnico de campo capture sus partes de
trabajo aunque no tenga cobertura, y los vuelque después al sistema de gestión
cuando recupera conexión.

Nace de una necesidad real de campo: sin red no se pueden registrar los partes
en el momento, así que al recuperar cobertura toca rehacerlos de memoria. Esta
herramienta los guarda en el propio dispositivo y los deja listos para volcar,
sin perder ningún dato por el camino.

## Qué hace

- **Captura de partes**: nº de pedido, máquina, cliente, horas del contador,
  comentarios de resolución y defecto, productos imputados y horas de trabajo.
- **Parte de trabajo (jornada)**: monta el timeline del día con todas las líneas
  de horas, suma el total, detecta huecos y solapes entre tramos y permite
  empalmarlos para cuadrar la jornada. Marca el restante para las 8 h y admite
  una línea de comida (H.C).
- **Copiado por casilla**: cada campo se copia por separado para volcarlo rápido.
- **100% sin conexión** e **instalable** como app (PWA).
- **Privacidad**: los datos viven solo en el dispositivo de cada usuario
  (localStorage); no hay servidor ni se comparten entre personas.

## Tecnología

- HTML, CSS y JavaScript *vanilla*, sin frameworks ni dependencias.
- PWA: Web App Manifest + Service Worker (estrategia *cache-first*) para que
  arranque al instante y funcione offline.
- Persistencia local con `localStorage`.

## Uso

Se abre una vez con conexión (para que se cachee) y a partir de ahí funciona sin
red. Para instalarla en pantalla de inicio: en Android desde el menú del
navegador, en iPhone con Compartir → Añadir a pantalla de inicio, y en
escritorio desde el icono de instalar de la barra de direcciones.

## Estructura

- `index.html` — la aplicación completa (todo en uno).
- `manifest.json` — metadatos e iconos para la instalación.
- `service-worker.js` — caché para el funcionamiento offline.
- `icon-192.png`, `icon-512.png`, `icon-512-maskable.png` — iconos.

## Despliegue

Es un sitio totalmente estático: basta servir estos archivos en cualquier
hosting estático con HTTPS. Las rutas son relativas, así que también funciona
alojado en una subcarpeta.
