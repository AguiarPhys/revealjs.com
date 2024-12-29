---
id: auto-slide
title: Auto-Slide
layout: default
---

# Auto-Slide

Las presentaciones se pueden configurar para que avancen a través de las diapositivas automáticamente, sin ninguna entrada del usuario. Para habilitar esto, deberá especificar un intervalo para los cambios de diapositiva utilizando la opción de configuración `autoSlide`. El intervalo se proporciona en milisegundos.

```javascript
// Slide every five seconds
Reveal.initialize({
  autoSlide: 5000,
  loop: true,
});
```

<div class="reveal reveal-example" data-config='{"autoSlide": 5000, "loop": true}'>
  <div class="slides">
    <section>Slide 1</section>
    <section>Slide 2</section>
    <section>Slide 3</section>
  </div>
</div>

Un elemento de control de reproducción/pausa aparecerá automáticamente para las presentaciones con "auto-slide". El deslizamiento se pausa automáticamente si el usuario comienza a interactuar con la presentación. También es posible pausar o reanudar el deslizamiento presionando »A« en el teclado (no funcionará en la demostración integrada aquí).

Puede deshabilitar los controles de "auto-slide" e impedir que el deslizamiento se pause especificando `autoSlideStoppable: false` en sus [opciones de configuración](/config/).

## Sincronización de diapositiva

También es posible anular la duración de la diapositiva para diapositivas y fragmentos individuales utilizando el atributo `data-autoslide`.

```html
<section data-autoslide="2000">
  <p>After 2 seconds the first fragment will be shown.</p>
  <p class="fragment" data-autoslide="10000">
    After 10 seconds the next fragment will be shown.
  </p>
  <p class="fragment">
    Now, the fragment is displayed for 2 seconds before the next slide is shown.
  </p>
</section>
```

## Método Auto-Slide

La opción de configuración `autoSlideMethod` se puede usar para anular la función predeterminada utilizada para la navegación con "auto-slide".

De forma predeterminada, avanzamos a través de todas las diapositivas, tanto horizontales como [verticales](/vertical-slides/). Para navegar solo a lo largo de la capa superior e ignorar las diapositivas verticales, puede proporcionar un método que llame a `Reveal.right()`.

```js
Reveal.configure({
  autoSlideMethod: () => Reveal.right(),
});
```

## Eventos

Ejecutamos eventos cada vez que se pausa o reanuda el "auto-slide".

```javascript
Reveal.on('autoslideresumed', (event) => {
  /* ... */
});
Reveal.on('autoslidepaused', (event) => {
  /* ... */
});
```
