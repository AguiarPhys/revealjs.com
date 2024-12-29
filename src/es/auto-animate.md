---
id: auto-animate
title: Auto-Animate
layout: default
---

# Auto-Animar <span class="r-version-badge new">4.0.0</span>

reveal.js puede animar elementos automáticamente entre diapositivas. Solo necesitas agregar el atributo `data-auto-animate` a dos elementos `<section>` de diapositivas adyacentes, y Auto-Animar animará todos los elementos coincidentes entre ambos.

Aquí hay un ejemplo simple para darte una mejor idea de cómo se puede usar.

```html
<section data-auto-animate>
  <h1>Auto-Animate</h1>
</section>
<section data-auto-animate>
  <h1 style="margin-top: 100px; color: red;">Auto-Animate</h1>
</section>
```

<div class="reveal reveal-example">
  <div class="slides">
    <section data-auto-animate>
      <h1>Auto-Animate</h1>
    </section>
    <section data-auto-animate>
      <h1 style="margin-top: 100px; color: red;">Auto-Animate</h1>
    </section>
  </div>
</div>

En este ejemplo, se utiliza la propiedad `margin-top` para mover el elemento, pero internamente reveal.js utilizará una transformación CSS para garantizar un movimiento suave. Este mismo enfoque de animación funciona con la mayoría de las propiedades CSS animables, lo que significa que puedes realizar transiciones en elementos como `position`, `font-size`, `line-height`, `color`, `background-color`, `padding` y `margin`.

### Animaciones de Movimiento

Las animaciones no se limitan a cambios de estilo. Auto-Animate también se puede usar para mover automáticamente elementos a su nueva posición a medida que se agrega, elimina o reorganiza contenido en una diapositiva. Todo esto sin una sola línea de CSS.

```html
<section data-auto-animate>
  <h1>Implicit</h1>
</section>
<section data-auto-animate>
  <h1>Implicit</h1>
  <h1>Animation</h1>
</section>
```

<div class="reveal reveal-example">
  <div class="slides">
    <section data-auto-animate>
      <h1>Implicit</h1>
    </section>
    <section data-auto-animate>
      <h1>Implicit</h1>
      <h1>Animation</h1>
    </section>
  </div>
</div>

## Cómo se hacen coincidir los elementos

Al navegar entre dos diapositivas con animación automática, haremos todo lo posible para encontrar automáticamente elementos coincidentes en las dos diapositivas. Para el texto, consideramos que hay una coincidencia si tanto el contenido del texto como el tipo de nodo son idénticos. Para imágenes, videos e iframes, comparamos el atributo `src`. También tenemos en cuenta el orden en que aparece el elemento en el DOM.

En situaciones en las que la coincidencia automática no es factible, puede asignar a los objetos que desea animar entre sí un atributo data-id coincidente. Priorizamos los valores data-id coincidentes sobre nuestra coincidencia automática.

Aquí hay un ejemplo donde hemos dado a ambos bloques un ID coincidente ya que la coincidencia automática no tiene contenido en el que basarse.

```html
<section data-auto-animate>
  <div data-id="box" style="height: 50px; background: salmon;"></div>
</section>
<section data-auto-animate>
  <div data-id="box" style="height: 200px; background: blue;"></div>
</section>
```

<div class="reveal reveal-example">
  <div class="slides">
    <section data-auto-animate>
	  <div data-id="box" style="height: 50px; background: salmon;"></div>
	</section>
	<section data-auto-animate>
	  <div data-id="box" style="height: 200px; background: blue;"></div>
	</section>
  </div>
</div>

## Configuración de Animación

Puede anular configuraciones de animación específicas, como el suavizado (easing) y la duración, ya sea para toda la presentación, por diapositiva o individualmente para cada elemento animado. Los siguientes atributos de configuración se pueden usar para cambiar la configuración de una diapositiva o elemento específico:

| Attribute&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |  Por Defecto | Descripción                                                                                                                  |
| :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------: | :--------------------------------------------------------------------------------------------------------------------------- |
| data-auto-animate-easing                                                                                                                                                                                                                                                          |     ease | A CSS [easing function](https://developer.mozilla.org/en-US/docs/Web/CSS/easing-function).                                   |
| data-auto-animate-unmatched                                                                                                                                                                                                                                                       |     true | Determines whether elements with no matching auto-animate target should fade in. Set to false to make them appear instantly. |
| data-auto-animate-duration                                                                                                                                                                                                                                                        |      1.0 | Animation duration in seconds.                                                                                               |
| data-auto-animate-delay                                                                                                                                                                                                                                                           |        0 | Animation delay in seconds (can only be set for specific elements, not at the slide level).                                  |
| data-auto-animate-id                                                                                                                                                                                                                                                              | _absent_ | An [id](#auto-animate-id-%26-restart) tying auto-animate slides together.                                                    |
| data-auto-animate-restart                                                                                                                                                                                                                                                         | _absent_ | [Breaks apart](#auto-animate-id-%26-restart) two adjacent auto-animate slides (even with the same id).                       |

Si desea cambiar los valores predeterminados para toda la presentación, usa las siguientes opciones de configuración:

```javascript
Reveal.initialize({
  autoAnimateEasing: 'ease-out',
  autoAnimateDuration: 0.8,
  autoAnimateUnmatched: false,
});
```

## Auto Animar ID y Reinicio

Cuando desees grupos separados de diapositivas con animación automática una al lado de la otra, puedes utilizar los atributos `data-auto-animate-id` y `data-auto-animate-restart`.

Con `data-auto-animate-id` puedes especificar identificadores arbitrarios para tus diapositivas. Dos diapositivas adyacentes solo se animarán automáticamente si tienen el mismo ID o si ninguna de las dos lo tiene.

Otra forma de controlar la animación automática es mediante el atributo `data-auto-animate-restart`. Aplicar este atributo a una diapositiva evitará la animación automática entre la diapositiva anterior y esta (incluso si tienen el mismo ID), pero _no_ entre esta y la siguiente diapositiva.

```html
<section data-auto-animate>
  <h1>Group A</h1>
</section>
<section data-auto-animate>
  <h1 style="color: #3B82F6;">Group A</h1>
</section>
<section data-auto-animate data-auto-animate-id="two">
  <h1>Group B</h1>
</section>
<section data-auto-animate data-auto-animate-id="two">
  <h1 style="color: #10B981;">Group B</h1>
</section>
<section data-auto-animate data-auto-animate-id="two" data-auto-animate-restart>
  <h1>Group C</h1>
</section>
<section data-auto-animate data-auto-animate-id="two">
  <h1 style="color: #EC4899;">Group C</h1>
</section>
```

<div class="reveal reveal-example">
	<div class="slides">
		<section data-auto-animate>
			<h1>Group A</h1>
		</section>
		<section data-auto-animate>
			<h1 style="color: #3B82F6;">Group A</h1>
		</section>
		<section data-auto-animate data-auto-animate-id="two">
			<h1>Group B</h1>
		</section>
		<section data-auto-animate data-auto-animate-id="two">
			<h1 style="color: #10B981;">Group B</h1>
		</section>
		<section data-auto-animate data-auto-animate-id="two" data-auto-animate-restart>
			<h1>Group C</h1>
		</section>
		<section data-auto-animate data-auto-animate-id="two">
			<h1 style="color: #EC4899;">Group C</h1>
		</section>
	</div>
</div>

## Eventos

El evento autoanimate se despacha cada vez que se avanza entre dos diapositivas con animación automática.

```javascript
Reveal.on('autoanimate', (event) => {
  // event.fromSlide, event.toSlide
});
```

## Ejemplo: Animando entre bloques de código

Admitimos animaciones entre bloques de código. Asegurate de que el bloque de código tenga habilitado `data-line-numbers` y de que todos los bloques tengan un valor `data-id` coincidente.

```html
<section data-auto-animate>
  <pre data-id="code-animation"><code data-trim data-line-numbers>
    let planets = [
      { name: 'mars', diameter: 6779 },
    ]
  </code></pre>
</section>
<section data-auto-animate>
  <pre data-id="code-animation"><code data-trim data-line-numbers>
    let planets = [
      { name: 'mars', diameter: 6779 },
      { name: 'earth', diameter: 12742 },
      { name: 'jupiter', diameter: 139820 }
    ]
  </code></pre>
</section>
<section data-auto-animate>
  <pre data-id="code-animation"><code data-trim data-line-numbers>
    let circumferenceReducer = ( c, planet ) => {
      return c + planet.diameter * Math.PI;
    }

    let planets = [
      { name: 'mars', diameter: 6779 },
      { name: 'earth', diameter: 12742 },
      { name: 'jupiter', diameter: 139820 }
    ]

    let c = planets.reduce( circumferenceReducer, 0 )
  </code></pre>
</section>
```

<div class="reveal reveal-example">
  <div class="slides">
    <section data-auto-animate>
      <pre data-id="code-animation"><code data-trim data-line-numbers>
        let planets = [
          { name: 'mars', diameter: 6779 },
        ]
      </code></pre>
    </section>
    <section data-auto-animate>
      <pre data-id="code-animation"><code data-trim data-line-numbers>
        let planets = [
          { name: 'mars', diameter: 6779 },
          { name: 'earth', diameter: 12742 },
          { name: 'jupiter', diameter: 139820 }
        ]
      </code></pre>
    </section>
    <section data-auto-animate>
      <pre data-id="code-animation"><code data-trim data-line-numbers>
        let circumferenceReducer = ( c, planet ) => {
          return c + planet.diameter * Math.PI;
        }
        &nbsp;
        let planets = [
          { name: 'mars', diameter: 6779 },
          { name: 'earth', diameter: 12742 },
          { name: 'jupiter', diameter: 139820 }
        ]
        &nbsp;
        let c = planets.reduce( circumferenceReducer, 0 )
      </code></pre>
    </section>
  </div>
</div>

## Ejemplo: Animando entre listas

Hacemos coincidir los elementos de la lista individualmente para permitirle animar la adición o eliminación de nuevos elementos.

```html/2-4,10,12
<section data-auto-animate>
  <ul>
    <li>Mercury</li>
    <li>Jupiter</li>
    <li>Mars</li>
  </ul>
</section>
<section data-auto-animate>
  <ul>
    <li>Mercury</li>
    <li>Earth</li>
    <li>Jupiter</li>
    <li>Saturn</li>
    <li>Mars</li>
  </ul>
</section>
```

<div class="reveal reveal-example">
  <div class="slides">
    <section data-auto-animate>
      <ul>
        <li>Mercury</li>
        <li>Jupiter</li>
        <li>Mars</li>
      </ul>
    </section>
    <section data-auto-animate>
      <ul>
        <li>Mercury</li>
        <li>Earth</li>
        <li>Jupiter</li>
        <li>Saturn</li>
        <li>Mars</li>
      </ul>
    </section>
  </div>
</div>

## Advanced: Avanzado: Atributos de estado

Agregamos atributos de estado a los diferentes elementos involucrados en una animación automática. Estos atributos se pueden vincular si desea, por ejemplo, ajustar el comportamiento de la animación con CSS personalizado.

Justo antes de que comience una animación automática, agregamos `data-auto-animate="pending"` al elemento `<section>` de la diapositiva que entra en vista. En este punto, la próxima diapositiva es visible y todos los elementos animados se han movido a sus posiciones iniciales. Luego cambiamos a `data-auto-animate="running"` para indicar cuándo los elementos comienzan a animarse hacia sus propiedades finales.

Cada elemento individual está decorado con un atributo `data-auto-animate-target`. El valor del atributo es un ID único para esta animación en particular o "unmatched" si este elemento debe animarse como contenido no coincidente.
