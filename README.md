# Siestaria — sitio sin Cargo

Este es el sitio de Siestaria reconstruido como **HTML estático**: tres páginas
de texto y una hoja de estilos. No hay Cargo, no hay panel de administración,
no hay nada que pagar más allá del dominio que ya tenés. Para cambiar textos
abrís un archivo y editás lo que está entre etiquetas. Eso es todo.

## Archivos

| Archivo | Qué es |
|---|---|
| `index.html` | La home: título "Siestaria", navegación y el "Archive" de abajo. |
| `about.html` | La página About (texto de arranque que podés reemplazar). |
| `contact.html` | La página Contact (mail y créditos). |
| `styles.css` | El diseño (colores, tipografía, tamaños). Casi nunca hay que tocarlo. |

## Cómo cambiar un texto

1. Abrí el `.html` que quieras (por ejemplo `about.html`) con cualquier editor
   de texto. Sirve el Bloc de notas / TextEdit, pero es más cómodo
   [VS Code](https://code.visualstudio.com/) (gratis).
2. Buscá el texto que querés cambiar. Está **entre etiquetas**, así:

   ```html
   <p>Siestaria is an ongoing artistic research project…</p>
   ```

   Cambiás solo lo de adentro:

   ```html
   <p>Tu nuevo texto acá.</p>
   ```

3. Guardás. Listo. Si lo abrís en el navegador (doble clic en el archivo) ya
   ves el cambio.

Reglas mínimas para no romper nada:
- No borres las etiquetas (`<p>`, `</p>`, etc.), solo el texto del medio.
- Cada párrafo nuevo va en su propio `<p>…</p>`.
- Dejé comentarios verdes (`<!-- así -->`) marcando cada zona editable. No se
  ven en la web, son notas para vos.

### Cambiar el mail de contacto
En `contact.html`, reemplazá `siestariazzz@gmail.com` (aparece dos veces en la
misma línea: una en `mailto:` y otra en el texto visible).

### Cambiar el link del Portfolio
Está en las tres páginas, dentro de `href="https://drive.google.com/…"`.
Reemplazá esa dirección por la nueva.

### Cambiar colores o tamaño del título
En `styles.css`, arriba de todo, en el bloque `:root`. Por ejemplo, para fondo
negro y texto blanco: poné `--bg: #000000;` y `--ink: #ffffff;`.

## Cómo publicarlo en GitHub Pages (gratis)

Es el mismo flujo que ya usás para tatianaheuman.com:

1. Creá un repositorio nuevo en GitHub (por ejemplo `siestaria`).
2. Subí estos cuatro archivos (`index.html`, `about.html`, `contact.html`,
   `styles.css`) a la raíz del repo.
3. En el repo: **Settings → Pages → Build and deployment → Source: Deploy from
   a branch**, elegí la rama `main` y la carpeta `/ (root)`. Guardá.
4. A los pocos minutos el sitio queda online en
   `https://TU-USUARIO.github.io/siestaria/`.

### Conectar tu dominio siestaria.com
1. En **Settings → Pages → Custom domain**, escribí `siestaria.com` y guardá.
   GitHub crea un archivo `CNAME` en el repo.
2. En el panel de tu proveedor del dominio (donde lo registraste), apuntá el
   dominio a GitHub con estos registros DNS:
   - Cuatro registros **A** del apex (`siestaria.com`) a:
     `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - Un registro **CNAME** para `www` que apunte a `TU-USUARIO.github.io`
3. Volvé a GitHub Pages y activá **Enforce HTTPS** cuando esté disponible.

> Importante sobre las fechas: Cargo vence el **10 de agosto**. Hacé el cambio
> de DNS **unos días antes** para que cuando Cargo deje de servir el dominio,
> el sitio nuevo ya esté apuntado y no haya ningún hueco. Mientras tanto podés
> tener el sitio nuevo funcionando en la URL `github.io` para probarlo.

## ¿Y qué tan complicado es, en una frase?

Editar texto: muy fácil, es abrir un archivo y escribir.
Publicar la primera vez: un rato de configurar GitHub Pages + DNS (igual que ya
hiciste con tu sitio personal). Después de eso, cada cambio es: editás, guardás,
subís a GitHub, y a los minutos está online.

## Tipografía

El sitio original usa **Diatype** (de la fundición Dinamo), una fuente con
licencia atada a Cargo que no se puede copiar a otro lado. Acá usé una grotesca
neutra muy parecida (Helvetica Neue / Arial / Inter como respaldo) que carga al
instante. Si algún día licenciás Diatype u otra fuente, se cambia en una sola
línea de `styles.css` (la variable `--font`).
