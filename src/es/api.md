---
id: methods
title: API Methods
layout: default
---

# API

Proveemos un API de JavaScript extensivo para controlar la navegación y comprobar el estado actual de la presentación. Si estás trabajando en una sola presentación, podrás acceder a la API a través del objeto global `Reveal`.

### Navegación

```javascript
// Navegar a una diapositiva en particular
Reveal.slide(indexh, indexv, indexf);

// Navegación relativa
Reveal.left();
Reveal.right();
Reveal.up();
Reveal.down();
Reveal.prev();
Reveal.next();

// Navegación fragmentada
Reveal.navigateFragment(indexf); // (-1 means all fragments are invisible)
Reveal.prevFragment();
Reveal.nextFragment();

// Comprueba a qué direcciones puedes navegar
// {top: false, right: true, bottom: false, left: false}
Reveal.availableRoutes();

// Comprueba a qué fragmentos de dirección podemos navegar.
// {prev: false, next: true}
Reveal.availableFragments();
```

### Misceláneos

```javascript
// Ejecuta esta función si añades o remueves diapositivas para actualizar los controles, el progreso, etc. 
Reveal.sync();
// Ejecuta esta función para sincronizar solo una diapositiva
Reveal.syncSlide((slide = currentSlide));
// Ejecuta esta función para sincronizar los fragmentos de una diapositiva
Reveal.syncFragments((slide = currentSlide));

// Ejecuta esta función para actualizar la escala de la presentación en función del área de visualización disponible
Reveal.layout();

// Aleatorizar el orden de las diapositivas
Reveal.shuffle();

// Muestra las opciones de configuración actuales
Reveal.getConfig();

// Muestra la escala actual de la presentación
Reveal.getScale();

// Devuelve un objecto con presentationWidth y presentationHeight a escala
Reveal.getComputedSlideSize();

Reveal.getIndices((slide = currentSlide)); // Coordinates of the slide (e.g. { h: 0, v: 0, f: 0 })
Reveal.getProgress(); // (0 == first slide, 1 == last slide)

// Arreglos de mapas key:value de los atributos de cada diapositiva
Reveal.getSlidesAttributes();

// Devuelve los elemetos del fondo de la diapositiva en el índice especificado
Reveal.getSlideBackground(indexh, indexv);

// Devuelve las notas del presentador para la diapositiva
Reveal.getSlideNotes((slide = currentSlide));

// Devuelve la cadena de consulta como un mapa key:value
Reveal.getQueryHash();

// Devuelve la ruta hacia la diapositiva según su representación en la URL
Reveal.getSlidePath((slide = currentSlide));
```

### Diapositivas

```javascript
// Devuelve el elemento de diapositiva que coincide con el índice especificado
Reveal.getSlide(indexh, indexv);

// Recupera los elementos de diapositiva anterior y actual
Reveal.getPreviousSlide();
Reveal.getCurrentSlide();

// Devuelve todas las diapositivas horizontales/verticales de la presentación
Reveal.getHorizontalSlides();
Reveal.getVerticalSlides();

// Número total de diapositivas
Reveal.getTotalSlides();
Reveal.getSlidePastCount();

// Arreglo de todas las diapositivas
Reveal.getSlides();
```

### Estado de la diapositiva

```javascript
// Comprueba si la presentación incluye dos o más 
// diapositivas horizontales/verticales
Reveal.hasHorizontalSlides();
Reveal.hasVerticalSlides();

// Comprueba si la presentación se ha movido en algún eje al menos una vez
Reveal.hasNavigatedHorizontally();
Reveal.hasNavigatedVertically();

Reveal.isFirstSlide();
Reveal.isLastSlide();
Reveal.isVerticalSlide();
Reveal.isLastVerticalSlide();
```

### Modos

```javascript
// Muestra una superposición de ayuda con atajos de teclado, opcionalmente pasa verdadero/falso 
// para forzar encendido/apagado
Reveal.toggleHelp();

// Alterna estados de presentación, opcionalmente pasa verdadero/falso para forzar encendido/apagado
Reveal.toggleOverview();
Reveal.toggleAutoSlide();
Reveal.togglePause();

Reveal.isOverview();
Reveal.isAutoSliding();
Reveal.isPaused();
```

### Elementos DOM

```javascript
// Recuperar elementos DOM clave
Reveal.getRevealElement(); // <div class="reveal">
Reveal.getSlidesElement(); // <div class="slides">
Reveal.getViewportElement(); // <div class="reveal-viewport">
Reveal.getBackgroundsElement(); // <div class="backgrounds">
```

## Lecturas Adicionales

- [Plugin API](/plugins/#api)
