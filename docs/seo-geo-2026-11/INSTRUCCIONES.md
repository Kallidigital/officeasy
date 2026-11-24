# OfficEasy: archivos para la web (llms.txt y GEO)

Sitio: https://officeasy.com.ar (www redirige al dominio sin www).
Plataforma: sitio HTML estático alojado en **Netlify** (lo confirma el header `server: Netlify`; el formulario de contacto usa el honeypot típico de Netlify Forms). En el pie figura “Web Adapted by Kalli Digital” (https://kallidigital.com.ar), así que es muy probable que ellos administren el deploy.

Estado al 24/11/2026 (America/Buenos_Aires):

- No existía `/llms.txt` ni `/llms-full.txt` (404).
- No existía `/robots.txt` ni `/sitemap.xml` (404). Por lo tanto, hoy no hay bloqueos a GPTBot, ClaudeBot, PerplexityBot, Google-Extended ni CCBot; igual conviene publicar un robots.txt que los autorice de forma explícita y apunte al sitemap.
- No hay JSON-LD / schema.org.
- El `<title>` de todas las páginas es solo “Officeasy”.
- La home tiene una meta description genérica (“Soluciones modulares personalizadas y de alta calidad en construcción.”). Las fichas de producto no tienen description.
- El HTML está en `lang="en"` y debería ser `es-AR`.
- No hay canonical ni Open Graph.

Estos archivos **no se subieron al sitio**. Hay que cargarlos en Netlify (o pedírselo a Kalli Digital). No hace falta WordPress, Wix ni Tienda Nube.

## Archivos de esta carpeta

| Archivo | Qué hacer |
| --- | --- |
| `llms.txt` | Subir a la raíz del sitio (junto a `index.html`) para que quede en https://officeasy.com.ar/llms.txt |
| `llms-full.txt` | Igual, a la raíz: https://officeasy.com.ar/llms-full.txt |
| `robots.txt` | Igual, a la raíz. Autoriza crawlers de IA y declara el sitemap. |
| `sitemap.xml` | Igual, a la raíz. Incluye solo las 4 URLs reales del sitio. |
| `schema-jsonld.html` | No va a la raíz como archivo suelto. Es un snippet para pegar en el `<head>` de la home. |
| `meta-tags.html` | Snippets de title, description, canonical y Open Graph por página, más JSON-LD de cada producto. |

Los textos no incluyen precios, promociones, stock, ni baño/cocina. La superficie de 2,8 m² que aparece hoy en la ficha de la casa expandible no se usó (contradice los 54 m² de la home; conviene corregirlo en el sitio). Tampoco se usaron datos de la plantilla original que siguen en el HTML (dirección en Letonia, teléfono +7, +54 9 11 1234-5678, horarios de ejemplo, “0 clientes / 0 proyectos”, Calendly “evento-de-prueba”).

## Cómo subir los archivos de la raíz (Netlify)

1. Entrá a [app.netlify.com](https://app.netlify.com) con la cuenta dueña de officeasy.com.ar. Si no la tenés, pedile a Kalli Digital que suba estos cuatro archivos a la raíz del publish directory (la carpeta donde está `index.html`).
2. Identificá el sitio de OfficEasy.
3. Si el sitio está conectado a Git: copiá `llms.txt`, `llms-full.txt`, `robots.txt` y `sitemap.xml` a la raíz del directorio que Netlify publica, commiteá y dejá que se haga el deploy.
4. Si el deploy es manual: en **Deploys**, bajá el deploy actual (o usá la carpeta del proyecto), agregá esos cuatro archivos en la raíz (al mismo nivel que `index.html`) y subí un nuevo deploy arrastrando la carpeta o con **Deploy manually**.
5. Cuando termine el deploy, comprobá que abran en el navegador:
   - https://officeasy.com.ar/llms.txt
   - https://officeasy.com.ar/llms-full.txt
   - https://officeasy.com.ar/robots.txt
   - https://officeasy.com.ar/sitemap.xml

   Tienen que devolver texto plano / XML (`200`), no la página 404 de Netlify.

## Cómo cargar schema y metas (hace falta editar el HTML)

Eso no se resuelve soltando un archivo en la raíz: hay que editar el `<head>` de cada página (home, `oficina_plegable`, `oficina_apilable`, `casa_expandible`) o pedírselo a Kalli Digital.

1. En todas las páginas, cambiá `<html lang="en">` por `<html lang="es-AR">`.
2. Reemplazá el `<title>` y la meta description por los de `meta-tags.html` (uno por página) y sumá canonical + Open Graph.
3. En la home, pegá el bloque de `schema-jsonld.html` justo antes de `</head>`.
4. En cada ficha, opcionalmente pegá el JSON-LD de Product que está en `meta-tags.html`.
5. Republish en Netlify y revisá con [Google Rich Results Test](https://search.google.com/test/rich-results) y viendo el código de la página.

## Otras mejoras rápidas de GEO / SEO (no incluidas como archivos)

- Corregir `lang="en"` (ya mencionado).
- Sacar o completar restos de la plantilla que pueden confundir a las IAs y a Google: dirección “Greenbe street 5B, Latvia”, teléfonos de ejemplo (`+7 950 457 5654`, `tel:79504575654`, `+54 9 11 1234-5678`), bloque “Our company in numbers” en 0, horarios comentados que no son de OfficEasy, widget de Calendly `juankarabinnn/evento-de-prueba`, copyright “Construction”.
- Unificar la superficie de la casa expandible (home: 54 m²; ficha: 2,8 m², casi seguro un typo).
- Los íconos de Facebook, Twitter, Telegram y VK no tienen perfil real detrás; o se enlazan cuentas oficiales o se ocultan.
- Cuando estén publicados, se puede avisar el sitemap en Google Search Console.
