---
id: config
title: Config
layout: default
---

# Opciones de Configuración

El comportamiento de la presentación se puede ajustar con precisión utilizando una amplia gama de opciones de configuración. Estos objetos se pueden incluir donde [inicializas](/initialization/) reveal.js. También es posible [cambiar los valores de configuración en momento de ejecución](#reconfiguring).

Tenga en cuenta que **todos** los valores de configuración son **opcionales** y tomarán de forma predeterminada los valores especificados a continuación.

```javascript
Reveal.initialize({
  // Mostrar flechas de control de presentación
  controls: true,

  // Ayudar al usuario a aprender los controles proporcionando sugerencias, por ejemplo,
  // haciendo rebotar la flecha hacia abajo cuando encuentran una diapositiva vertical por primera vez
  controlsTutorial: true,

  // Determina dónde aparecen los controles, "edges" o "bottom-right"
  controlsLayout: 'bottom-right',

  // Regla de visibilidad para las flechas de navegación hacia atrás; "faded", "hidden"
  // o "visible"
  controlsBackArrows: 'faded',

  // Mostrar una barra de progreso de la presentación
  progress: true,

  // - true:    Mostrar número de diapositiva
  // - false:   Ocultar número de diapositiva
  //
  // Se puede establecer opcionalmente como una cadena que especifica el formato del número:
  // - "h.v":   Número de diapositiva horizontal . vertical (predeterminado)
  // - "h/v":   Número de diapositiva horizontal / vertical
  // - "c":   Número de diapositiva aplanado
  // - "c/t":   Número de diapositiva aplanado / total de diapositivas
  //
  // Alternativamente, puede proporcionar una función que devuelve el número de diapositiva 
  // para la diapositiva actual. La función debe recibir un objeto de diapositiva 
  // y devolver una matriz con una cadena [slideNumber] o 
  // tres cadenas [n1,delimiter,n2]. Ver #formatSlideNumber().
  slideNumber: false,

  // Se puede usar para limitar los contextos en los que aparece el número de diapositiva
  // - "all":      Mostrar siempre el número de diapositiva
  // - "print":    Solo al imprimir en PDF
  // - "speaker":  Solo en la vista del presentador
  showSlideNumber: 'all',

  // Usar indexación basada en 1 para enlaces # para que coincida con el número de diapositiva 
  // (el valor predeterminado es cero)
  hashOneBasedIndex: false,

  // Agregar el número de diapositiva actual al hash de la URL para que recargar la 
  // página/copiar la URL lo devuelva a la misma diapositiva
  hash: false,

  // Indica si debemos monitorear el hash y cambiar las diapositivas en consecuencia
  respondToHashChanges: true,

  // Habilitar atajos de navegacion para saltar a una diapostiva
  jumpToSlide: true,

  // Enviar cada cambio de diapositiva al historial del navegador. Supone que `hash: true`
  history: false,

  // Habilitar atajos de teclado para la navegación
  keyboard: true,

  // Función opcional que bloquea los eventos del teclado cuando devuelve falso
  //
  // Si establece esto en 'focused', solo capturaremos eventos de teclado
  // para presentaciones incrustadas cuando estén en foco
  keyboardCondition: null,

  // Deshabilita el diseño predeterminado de la diapositiva reveal.js (escalado y centrado)
  // para que pueda usar un diseño CSS personalizado
  disableLayout: false,

  // Habilitar el modo de vista general de la presentación (overview mode)
  overview: true,

  // Centrado vertical de las diapositivas
  center: true,

  // Habilita la navegación táctil en dispositivos con entrada táctil
  touch: true,

  // Bucle la presentación
  loop: false,

  // Cambiar la dirección de la presentación a RTL
  rtl: false,

  // Cambia el comportamiento de nuestras direcciones de navegación.
  //
  // "default"
  // Las teclas de flecha izquierda/derecha avanzan entre diapositivas horizontales, 
  // las teclas de flecha arriba/abajo avanzan entre diapositivas verticales. 
  // La barra espaciadora avanza a través de todas las diapositivas (tanto horizontales como verticales).
  //
  // "linear"
  // Elimina las flechas arriba/abajo. Las flechas izquierda/derecha avanzan a través de todas 
  // las diapositivas (tanto horizontales como verticales).
  //
  // "grid"
  // Cuando esto está habilitado, avanzar izquierda/derecha desde una pila vertical 
  // a una pila vertical adyacente lo llevará al mismo índice vertical.
  //
  // Considere una presentación con seis diapositivas ordenadas en dos pilas verticales:
  // 1.1    2.1
  // 1.2    2.2
  // 1.3    2.3
  //
  // Si está en la diapositiva 1.3 y navega a la derecha, normalmente se moverá 
  // de 1.3 -> 2.1. Si se usa "grid", la misma navegación lo lleva 
  // de 1.3 -> 2.3.
  navigationMode: 'default',

  // Aleatoriza el orden de las diapositivas cada vez que se carga la presentación
  shuffle: false,

  // Activa y desactiva los fragmentos globalmente
  fragments: true,

  // Indica si se debe incluir el fragmento actual en la URL,
  // para que al recargar lo lleve a la misma posición del fragmento
  fragmentInURL: true,

  // Indica si la presentación se está ejecutando en un modo incrustado,
  // es decir, contenido dentro de una porción limitada de la pantalla
  embedded: false,

  // Indica si se debe mostrar una dialogo de ayuda cuando se presiona la tecla de interrogación
  help: true,

  // Indica si debería ser posible pausar la presentación (blackout)
  pause: true,

  // Indica si las notas del orador deben ser visibles para todos los espectadores
  showNotes: false,

  // Anulación global para la reproducción automática de medios incrustados (video/audio/iframe)
  // - null:   Los medios solo se reproducirán automáticamente si está presente data-autoplay
  // - true:   Todos los medios se reproducirán automáticamente, independientemente de la configuración individual
  // - false:  Ningún medio se reproducirá automáticamente, independientemente de la configuración individual
  autoPlayMedia: null,

  // Anulación global para la precarga de iframes cargados diferidamente
  // - null:   Los iframes con data-src Y data-preload se cargarán cuando estén dentro 
  //           de la viewDistance, los iframes con solo data-src se cargarán cuando sean visibles
  // - true:   Todos los iframes con data-src se cargarán cuando estén dentro de la viewDistance
  // - false:  Todos los iframes con data-src solo se cargarán cuando sean visibles
  preloadIframes: null,

  // Se puede usar para deshabilitar globalmente la animación automática
  autoAnimate: true,

  // Opcionalmente, proporcione un comparador de elementos personalizado que se 
  // utilizará para dictar qué elementos podemos animar entre sí.
  autoAnimateMatcher: null,

  // Configuración predeterminada para nuestras transiciones de animación automática, 
  // se puede anular por diapositiva o por elemento a través de argumentos de datos
  autoAnimateEasing: 'ease',
  autoAnimateDuration: 1.0,
  autoAnimateUnmatched: true,

  // Propiedades CSS que se pueden animar automáticamente. Posición y escala 
  // se comparan por separado, por lo que no es necesario incluir estilos 
  // como top/right/bottom/left, width/height o margin.
  autoAnimateStyles: [
    'opacity',
    'color',
    'background-color',
    'padding',
    'font-size',
    'line-height',
    'letter-spacing',
    'border-width',
    'border-color',
    'border-radius',
    'outline',
    'outline-offset',
  ],

  // Controla la progresión automática a la siguiente diapositiva
  // - 0:      El deslizamiento automático solo ocurre si el atributo HTML data-autoslide 
  //           está presente en la diapositiva o fragmento actual
  // - 1+:     Todas las diapositivas progresarán automáticamente en el intervalo dado
  // - false:  No hay deslizamiento automático, incluso si está presente data-autoslide
  autoSlide: 0,

  // Detener el deslizamiento automático después de la entrada del usuario
  autoSlideStoppable: true,

  // Use este método para la navegación cuando se realiza un deslizamiento automático (el valor predeterminado es navigateNext)
  autoSlideMethod: null,

  // Especifique el tiempo promedio en segundos que cree que pasará 
  // presentando cada diapositiva. Esto se usa para mostrar un temporizador en 
  // la vista del presentador
  defaultTiming: null,

  // Habilitar la navegación por diapositivas con la rueda del ratón
  mouseWheel: false,

  // Abre enlaces en una superposición de vista previa del iframe
  // Agregue `data-preview-link` y `data-preview-link="false"` para personalizar cada enlace
  // individualmente
  previewLinks: false,

  // Expone la API reveal.js a través de window.postMessage
  postMessage: true,

  // Despacha todos los eventos reveal.js a la ventana principal a través de postMessage
  postMessageEvents: false,

  // Centra el cuerpo cuando la visibilidad de la página cambia para garantizar que funcionen los atajos de teclado
  focusBodyOnPageVisibilityChange: true,

  // Estilo de transición
  transition: 'slide', // none/fade/slide/convex/concave/zoom

  // Velocidad de transición
  transitionSpeed: 'default', // default/fast/slow

  // Estilo de transición para fondos de diapositiva de página completa
  backgroundTransition: 'fade', // none/fade/slide/convex/concave/zoom

  // El número máximo de páginas que una sola diapositiva puede expandirse al guardar
  // a PDF, ilimitado de forma predeterminada
  pdfMaxPagesPerSlide: Number.POSITIVE_INFINITY,

  // Imprime cada fragmento en una diapositiva separada
  pdfSeparateFragments: true,

  // Desplazamiento utilizado para reducir la altura del contenido dentro de las páginas PDF exportadas.
  // Esto existe para tener en cuenta las diferencias ambientales según cómo
  // imprime en PDF. Las opciones de impresión de CLI, como phantomjs y wkpdf, pueden terminar
  // precisamente en la altura total del documento, mientras que la impresión en el navegador
  // debe terminar un píxel antes.
  pdfPageHeightOffset: -1,

  // Número de diapositivas alejadas de la actual que son visibles
  viewDistance: 3,

  // Número de diapositivas alejadas de la actual que son visibles en dispositivos móviles.
  // Es aconsejable establecer esto en un número menor que 
  // viewDistance para ahorrar recursos.
  mobileViewDistance: 2,

  // El modo de visualización que se utilizará para mostrar diapositivas
  display: 'block',

  // Ocultar cursor si está inactivo
  hideInactiveCursor: true,

  // Tiempo antes de que se oculte el cursor (en ms)
  hideCursorTime: 5000,
});
```

## Reconfiguración

La configuración se puede actualizar después de la inicialización utilizando el método `configure`.

```javascript
// Apaga el autoSlide
Reveal.configure({ autoSlide: 0 });

// Comienza el auto-sliding cada 5s
Reveal.configure({ autoSlide: 5000 });
```
