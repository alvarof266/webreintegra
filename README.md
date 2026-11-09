# Webs del despacho (Pacheco&Soto Abogados)

Una carpeta por dominio, cada una con su web de captación completa:

- Raíz del repositorio: la web de Reintegra (`index.html`, `aviso-legal.html`, `cookies.html`, `privacidad.html`, `configuracion.js`, `fotos/`). Se sirve como web común.
- `pachecosotoabogados.es/`: la web corporativa del despacho.
- `accidentia.pachecosotoabogados.es/`: la web de Accidentia (accidentes de tráfico).

El servidor del despacho publica las tres con `instalar_web.sh`: la raíz se copia en `/srv/web-publica` y cada carpeta de dominio en `/srv/web-publica/<dominio>/`. Caddy sirve a cada dominio su carpeta (`WEB_URL` del `.env`, separada por comas); si un dominio no tiene carpeta propia, se sirve la web raíz. Las páginas interiores (por ejemplo, `politica-de-privacidad.html`) las sirve la plataforma a través de `/web/pagina/`, que busca primero en la carpeta del dominio.

Netlify sigue publicando la rama `main` automáticamente (la web de Reintegra). No hay que construir nada.
