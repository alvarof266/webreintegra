# Webs del despacho (Pacheco&Soto Abogados)

Las tres webs viven bajo un único dominio, pachecosotoabogados.es:

- `pachecosotoabogados.es/`: la web corporativa del despacho (portada del dominio).
- Raíz del repositorio: la web de Reintegra (`index.html`, `aviso-legal.html`, `cookies.html`, `privacidad.html`, `configuracion.js`, `fotos/`), servida en la sección `/reintegra/`.
- `accidentia.pachecosotoabogados.es/`: la web de Accidentia, servida en la sección `/accidentia/`.

El nombre de cada carpeta coincide con el subdominio antiguo: el servidor publica todo el repositorio en `/srv/web-publica`, Caddy sirve cada dominio su carpeta y las secciones `/reintegra/` y `/accidentia/` del dominio principal; los subdominios antiguos redirigen (HTTP 301) a sus secciones. Las páginas interiores (por ejemplo, `politica-de-privacidad.html`) las sirve la plataforma a través de `/web/pagina/`, que busca primero en la carpeta de la sección.

Las tres webs enlazan entre sí con rutas relativas al dominio (`/`, `/reintegra/`, `/accidentia/`) y declaran su URL canónica.

Netlify sigue publicando la rama `main` automáticamente (la web de Reintegra). No hay que construir nada.
