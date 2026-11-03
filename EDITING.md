# Cómo editar Midnight Commit

El HTML está en los archivos `.astro`. Los colores, tamaños y posiciones están en CSS. No hace falta cambiar JavaScript para ajustar el diseño.

## Dónde cambiar cada cosa

| Qué quieres cambiar | Texto y estructura | Estilos |
| --- | --- | --- |
| Header | `src/components/Header.astro` | `src/styles/header.css` |
| Navbar | `src/components/NavBar.astro` | `src/styles/navbar.css` |
| Footer | `src/components/Footer.astro` | `src/styles/footer.css` |
| Portada | `src/pages/index.astro` | `src/styles/home.css` |
| Latest Commit | `src/components/LatestCommit.astro` | Sección `.latest-*` de `home.css` |
| Ventanas: barra y botones | `src/components/Window.astro` | `src/styles/windows.css` |
| Calendario | `src/components/Calendar.astro` | Bloque `<style>` del mismo archivo |
| Últimas fotos | `src/components/LatestPics.astro` | Bloque `<style>` del mismo archivo |
| Galería | `src/pages/pics.astro` | `src/styles/pics.css` |
| Lista de posts | `src/pages/blog/index.astro` | `src/styles/blog.css` |
| Artículo | `src/layouts/BlogPost.astro` | Bloque `<style>` del mismo archivo |

## Ajustes habituales de la portada

Todos están en `src/styles/home.css`:

- `.home-windows`: los tres anchos en orden About / Latest Commit / My System. `700px` es el ancho de la ventana central; `1fr` reparte el espacio restante. `gap` es la separación.
- La regla siguiente controla la **altura mínima** de las tres ventanas. Crecen juntas si el contenido necesita más espacio; no se recorta el texto.
- `.windows-container`: margen interior de toda la portada (`padding`).
- `.latest-image`: ancho de la foto del último post.
- `.latest-commit`: distancia entre foto y texto (`gap`).
- `.gameboy-corner`: anchos y separación de la fila inferior.
- `.retro-panel`: fondo y bordes de los cuadros de memoria.
- `.retro-panel::after`: contactos dorados de abajo.
- `.retro-panel .window--static:not(.maximized)`: posición y ancho de las ventanas dentro de los cuadros. Un `margin-top` negativo las sube.

Los selectores `:not(.maximized)` y `:not(.minimized)` evitan que las medidas normales estorben al maximizar o minimizar. No son medidas adicionales.

## Ajustes del footer

En `src/styles/footer.css`:

- `.site-footer`: fondo, borde y espacio interior.
- `.footer-content`: columnas y separación.
- `.footer-logo img`: tamaño y filtro blanco del logo.
- `.footer-about .footer-signature`: posición de “Inspired by the old web”.

## Móvil y colores

Las reglas `@media` al final de cada CSS son las excepciones para pantallas pequeñas. Si un cambio solo falla en móvil, revisa esa sección.

Los colores y fuentes compartidos están en `:root`, al inicio de `src/styles/global.css`. Los colores propios del footer y de los cuadros de memoria están en sus respectivas reglas.

El código de `Window.astro` mantiene el arrastre y los botones. Las llamadas a `astro:page-load` permiten que los controles funcionen al navegar entre páginas.
