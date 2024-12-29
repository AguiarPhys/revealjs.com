---
id: backgrounds
title: Backgrounds
layout: default
---

# Fondos de diapositiva

De forma predeterminada, las diapositivas están contenidas dentro de una porción limitada de la pantalla para permitirles adaptarse a cualquier pantalla y escalar uniformemente. Puede aplicar fondos de página completa fuera del área de la diapositiva agregando un atributo `data-background` a sus elementos `<section>`. Se admiten cuatro tipos diferentes de fondos: color, imagen, video e iframe.

## Fondos de color

Se admiten todos los formatos de color CSS, incluidos valores hexadecimales, palabras clave, `rgba()` o `hsl()`.

```html/0,3
<section data-background-color="aquamarine">
  <h2>🍦</h2>
</section>
<section data-background-color="rgb(70, 70, 255)">
  <h2>🍰</h2>
</section>
```

<div class="reveal reveal-example">
  <div class="slides">
    <section data-background-color="aquamarine">
      <h2 style="font-size: 4em;">🍦</h2>
    </section>
    <section data-background-color="rgb(70, 70, 255)">
      <h2 style="font-size: 4em;">🍰</h2>
    </section>
  </div>
</div>

Se admiten todos los formatos de degradado CSS, incluidos `linear-gradient`, `radial-gradient` y `conic-gradient`.

```html/0,3
<section data-background-gradient="linear-gradient(to bottom, #283b95, #17b2c3)">
  <h2>🐟</h2>
</section>
<section data-background-gradient="radial-gradient(#283b95, #17b2c3)">
  <h2>🐳</h2>
</section>
```

<div class="reveal reveal-example">
  <div class="slides">
    <section data-background-gradient="linear-gradient(to bottom, #283b95, #17b2c3)">
      <h2 style="font-size: 4em;">🐟</h2>
    </section>
    <section data-background-gradient="radial-gradient(#283b95, #17b2c3)">
      <h2 style="font-size: 4em;">🐳</h2>
    </section>
  </div>
</div>

## Fondos de imagen

De forma predeterminada, las imágenes de fondo se redimensionan para cubrir toda la página. Opciones disponibles:

| Attribute                | Default <div style="width:80px"></div> | Description                                                                                       |
| :----------------------- | :------------------------------------- | :------------------------------------------------------------------------------------------------ |
| data-background-image    |                                        | URL de la imagen. Los GIFs reinician cuando inicia la diapositiva.                                |
| data-background-size     | cover                                  | Vea [background-size](https://developer.mozilla.org/docs/Web/CSS/background-size) en MDN.         |
| data-background-position | center                                 | Vea [background-position](https://developer.mozilla.org/docs/Web/CSS/background-position) en MDN. |
| data-background-repeat   | no-repeat                              | Vea [background-repeat](https://developer.mozilla.org/docs/Web/CSS/background-repeat) en MDN.     |
| data-background-opacity  | 1                                      | Controla la opacidad de la imagen de fondo (entre 0 y 1). 0 es transparente y 1 es completamente opaco.|

{.nowrap-1st}

```html/0,3-4
<section data-background-image="http://example.com/image.png">
  <h2>Image</h2>
</section>
<section data-background-image="http://example.com/image.png"
          data-background-size="100px" data-background-repeat="repeat">
  <h2>This background image will be sized to 100px and repeated</h2>
</section>
```

## Fondo de videos

Automáticamente reproduce un video en pantalla completa detrás de la diapositiva.

| Atributo                   | Predeterminado | Descripción                                                                                 |
| :-------------------------- | :------ | :------------------------------------------------------------------------------------------------ |
| data-background-video       |         | Una sola fuente de video o una lista separada por comas de fuentes de video.                      |
| data-background-video-loop  | false   | Indica si el video debe reproducirse repetidamente.                                               |
| data-background-video-muted | false   | Indica si el audio debe estar silenciado.                                                         |
| data-background-size        | cover   | Usa `cover` para pantalla completa y algún recorte o `contain` para "letterboxing".               |
| data-background-opacity     | 1       | Opacidad del video de fondo en una escala de 0 a 1. 0 es transparente y 1 es completamente opaco. |

{.nowrap-1st}

```html/0-1
<section data-background-video="https://static.slid.es/site/homepage/v1/homepage-video-editor.mp4"
          data-background-video-loop data-background-video-muted>
  <h2>Video</h2>
</section>
```

<div class="reveal reveal-example">
  <div class="slides">
    <section data-background-video="https://static.slid.es/site/homepage/v1/homepage-video-editor.mp4" 
          data-background-video-loop data-background-video-muted>
      <h2>Video</h2>
    </section>
  </div>
</div>

## Fondos Iframe

Incorpora una página web como fondo de diapositiva que cubre el 100% del ancho y alto de reveal.js. El iframe está en la capa de fondo, detrás de tus diapositivas, por lo que no es posible interactuar con él en la configuración predeterminada. Para hacer que tu fondo sea interactivo, puedes agregar el atributo `data-background-interactive`.

| Atributo                   | Predeterminado | Description                                                                                                                                     |
| :-------------------------- | :------ | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| data-background-iframe      |         | URL del iframe a cargar                                                                                                                   |
| data-background-interactive | false   | Incluye este atributo para poder interactuar con el contenido del iframe. Esto evitará que interactues con el contenido de la diapositiva.|

{.nowrap-1st}

```html/0-1
<section data-background-iframe="https://slides.com"
          data-background-interactive>
  <h2>Iframe</h2>
</section>
```

Los iframes se cargan de forma diferida cuando se vuelven visibles. Si desea precargar los iframes con anticipación, puede agregar un atributo `data-preload` a la sección `<section>` de la diapositiva. También puede habilitar la precarga globalmente para todos los iframes utilizando la opción de configuración `preloadIframes`.

## Transiciones de fondo

Utilizaremos una transición de desvanecimiento cruzado entre los fondos de diapositiva de forma predeterminada. Esto se puede cambiar usando la opción de configuración [`backgroundTransition`](/transitions/#background-transitions).

## Fondo Parallax

Si desea utilizar un fondo con desplazamiento paralaje, establezca las dos primeras propiedades a continuación al inicializar reveal.js (las otras dos son opcionales).

```javascript/1-11
Reveal.initialize({
  // Parallax background image
  parallaxBackgroundImage: '', // e.g. "https://s3.amazonaws.com/hakim-static/reveal-js/reveal-parallax-1.jpg"

  // Parallax background size
  parallaxBackgroundSize: '', // CSS syntax, e.g. "2100px 900px" - actualmente solo puedes usar pixeles only píxeles (no uses % o auto)

  //  Número de píxeles para mover el fondo de parallax por diapositiva
  // - Calculado automáticamente, a menos que lo especifiques
  // - Poner en 0 para inhabilitar el movimiento a lo largo de un eje.
  parallaxBackgroundHorizontal: 200,
  parallaxBackgroundVertical: 50
});
```
Asegúrese de que el tamaño de fondo sea mucho mayor que el tamaño de la pantalla para permitir cierto desplazamiento. [Ejemplo](/demo?parallaxBackgroundImage=https%3A%2F%2Fs3.amazonaws.com%2Fhakim-static%2Freveal-js%2Freveal-parallax-1.jpg&parallaxBackgroundSize=2100px%20900px).