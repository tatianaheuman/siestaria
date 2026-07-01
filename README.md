# Siestaria — sitio sin Cargo

Sitio de Siestaria reconstruido como HTML estático. No hay Cargo ni nada que
pagar más allá del dominio. Para cambiar textos, abrís un .html y editás lo que
está entre etiquetas.

## Archivos

| Archivo | Qué es |
|---|---|
| `index.html` | Home: título, navegación, imagen central (escaneo 3D) y Archive. |
| `about.html` | About: pestañas What? / When? / Why? / Sources / Related Projects. |
| `buenos-aires.html` | Documentación de la primera Siestaria en LAR: slideshow de fotos (pasan solas), texto, slideshow de escaneos 3D (pasan al clic), videos y créditos. |
| `contact.html` | Contact (el mail). |
| `styles.css` | Diseño: colores, tipografía, cursor, tamaños, slideshows. |
| `favicon.svg` | El ícono (nube) que aparece en la pestaña del navegador. |
| `SIESTARIA-portfolio-EN.pdf` | El portfolio en PDF. El link "Portfolio" lo abre. |
| `home-collage.png` | Imagen central de la home. |
| `ba-doc-01.png` … `ba-doc-11.png` | Fotos del slideshow de Buenos Aires. |
| `scan1.png` … `scan4.png` | Escaneos 3D del slideshow de Buenos Aires. |

> Las imágenes de la página Buenos Aires (`ba-photo1.png`, `ba-scan.png`) las
> recorté de tus capturas, así que están en calidad media. Cuando quieras, pasame
> los archivos originales y los reemplazo por versiones nítidas (mismo nombre).

## Cómo cambiar un texto

Abrí el `.html` con un editor (sirve [VS Code](https://code.visualstudio.com/),
gratis). El texto está entre etiquetas:

```html
<p>Siestaria is an ongoing artistic research project…</p>
```

Cambiás solo lo de adentro y guardás. No borres las etiquetas. Dejé comentarios
(`<!-- así -->`) marcando cada zona; no se ven en la web.

- **Mail de contacto:** en `contact.html`, reemplazá `siestariazzz@gmail.com`
  (aparece dos veces en la misma línea).
- **Link del Portfolio:** ahora abre el archivo `SIESTARIA-portfolio-EN.pdf` que
  está en el sitio. Para actualizarlo, reemplazá ese PDF por uno nuevo con el
  mismo nombre (o cambiá el `href` en `index.html` y `contact.html`).
- **Slideshows (Buenos Aires):** las fotos que pasan solas son los `ba-doc-…png`
  (en el bloque `<div class="slideshow" data-mode="auto" …>`); los escaneos que
  pasan al clic son los `scan…png` (`data-mode="click"`). Para agregar o quitar
  imágenes, copiá o borrá una línea `<img …>` dentro del bloque. La velocidad del
  automático se cambia en `data-interval` (en milisegundos).
- **Videos de YouTube** (página Buenos Aires): en `buenos-aires.html`, reemplazá
  el código que va después de `embed/`. Ejemplo: para el video
  `youtube.com/watch?v=ABC123`, poné `…/embed/ABC123`.
- **Imágenes:** reemplazá el archivo `.png` por otro con el mismo nombre, o
  cambiá el `src="…"`.
- **About (pestañas):** cada pestaña (What?, When?, Why?, Sources, Related
  Projects) tiene su propio bloque `<section class="panel" id="…">` en
  `about.html`. Editás el texto dentro del que corresponda. El menú de pestañas
  y el scriptito del final hacen el cambio entre ellas solos; no hay que tocarlos.

## Cambiar colores, tamaño del título o el cursor

Todo está en `styles.css`, arriba, en el bloque `:root`:

```
--bg:          #d3d3f8;   /* fondo lila            */
--ink:         #ecfeda;   /* tipografía lima        */
--link:        #7454f5;   /* links violeta          */
--archive-ink: #35353e;   /* texto del Archive      */
```

El cursor es una flecha de línea color lima, definida también en `styles.css`
(propiedad `cursor` dentro de `body`). Si cambiás el color de la tipografía y
querés que el cursor combine, hay que cambiar el código de color dentro del
cursor (`%23ecfeda` es el lima; `%23` significa `#`).

## Cómo ACTUALIZAR el sitio en GitHub (ya está creado)

Como el repositorio ya existe y subiste la primera versión, ahora solo hay que
reemplazar los archivos por estos nuevos:

1. Entrá a tu repo: `https://github.com/tatianaheuman/siestaria`
2. Tocá **Add file → Upload files**.
3. Arrastrá **todos los archivos** de esta carpeta (los 4 `.html`, el `.css`,
   el `favicon.svg`, el PDF y todas las imágenes `.png`) — sueltos, no la carpeta.
   - Los que ya existían se reemplazan solos; los nuevos se agregan.
   - Si algún archivo viejo ya no está en esta carpeta (por ejemplo `ba-photo1.png`
     o `ba-scan.png`), podés borrarlo del repo desde GitHub, pero no molesta si queda.
4. Abajo, botón verde **Commit changes**.
5. En ~1 minuto, GitHub Pages se actualiza solo. Refrescá tu sitio en
   `https://tatianaheuman.github.io/siestaria/` y vas a ver los cambios.

(No hace falta volver a tocar la configuración de Pages: una vez activada, cada
subida de archivos republica el sitio automáticamente.)

## Conectar el dominio siestaria.com (cuando estés lista)

Tu dominio está en **websupport.sk**. Cuando quieras conectarlo, avisame y te
paso la pantalla exacta de ellos. El resumen:

1. En GitHub: **Settings → Pages → Custom domain**, escribí `siestaria.com`.
2. En websupport.sk (zona DNS del dominio), creá:
   - 4 registros **A** del dominio raíz a: `185.199.108.153`, `185.199.109.153`,
     `185.199.110.153`, `185.199.111.153`
   - 1 registro **CNAME** para `www` apuntando a `tatianaheuman.github.io`
3. Volvé a GitHub Pages y activá **Enforce HTTPS** cuando esté disponible.

> Cargo vence el **10 de agosto**. Hacé el cambio de DNS unos días antes para que
> no quede ningún hueco entre que Cargo se apaga y el dominio apunta al sitio nuevo.

## Tipografía

El sitio original usa **Diatype** (de Dinamo), con licencia atada a Cargo, que no
se puede copiar. Acá uso una grotesca neutra muy parecida (Helvetica Neue / Arial).
Si licenciás Diatype, se cambia en una línea de `styles.css` (variable `--font`).
