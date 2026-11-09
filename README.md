# webreintegra

Repositorio de las webs públicas del despacho Pacheco&Soto Abogados. Se publica en `/srv/web-publica` con `instalar_web.sh` (repositorio Reintegra) y lo sirve Caddy, generando un bloque por cada dominio de `WEB_URL` en el `.env` del VPS.

## Arquitectura

Tres webs independientes, cada una en su subdominio, construidas con la misma plantilla visual y estructural (cabecera, hero, tipografías Schibsted Grotesk y Libre Caslon, tarjetas, botones, márgenes, comportamiento responsive y animaciones idénticos). Solo cambian la identidad cromática, los logotipos, los contenidos y la finalidad.

| Web | Dominio | Color | Carpeta |
| --- | --- | --- | --- |
| Pacheco&Soto (institucional) | pachecosotoabogados.es | Rojo teja #A94F3C | `pachecosotoabogados.es/` |
| Reintegra (prima única) | reintegra.pachecosotoabogados.es | Azul #18233A / #FFC53D | raíz del repositorio |
| Accidentia (accidentes) | accidentia.pachecosotoabogados.es | Verde #32734A | `accidentia.pachecosotoabogados.es/` |

`WEB_URL` debe contener los tres dominios separados por comas:
`https://pachecosotoabogados.es,https://reintegra.pachecosotoabogados.es,https://accidentia.pachecosotoabogados.es`

Cada dominio con carpeta propia se sirve desde su carpeta; el dominio de Reintegra se sirve desde la raíz, que también contiene `fotos/` (fotografías de los socios, usadas por las tres webs) y `configuracion.js`.

## Contenido de cada web

- `index.html` en la raíz: web de Reintegra (mantiene su diseño y azul original).
- `pachecosotoabogados.es/`: portada institucional (despacho, socios, trayectoria, áreas, cómo trabajamos) con dos tarjetas a los subdominios de Reintegra y Accidentia. Sin formulario: el contacto es el teléfono y el WhatsApp del despacho.
- `accidentia.pachecosotoabogados.es/`: web de accidentes de tráfico e indemnizaciones, con formulario de contacto.
- Cada carpeta de dominio incluye su `politica-de-privacidad.html`.

## Detalles comunes

- Botones de llamada (915 425 307) y WhatsApp (637 597 988) en cabecera y barra fija inferior en móvil.
- Canonical autorreferente en cada página. No hay sitemap ni robots.txt.
- Las páginas `.html` se sirven a través de la plataforma (`web_pagina`), que cuenta la visita sin cookies e inyecta el reto de ALTCHA en los formularios; el resto de archivos (fotos, configuracion.js) los sirve Caddy directamente.
