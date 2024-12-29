---
id: code
title: Presenting Code
layout: default
---

# Presentar Código

reveal.js incluye un poderoso conjunto de funciones destinadas a presentar código resaltado por sintaxis, gracias a [highlight.js](https://highlightjs.org/). Esta funcionalidad se encuentra en el plugin de resaltado y se incluye en nuestra plantilla de presentación predeterminada.

A continuación se muestra un ejemplo con código de clojure que se resaltará sintácticamente. Cuando el atributo `data-trim` está presente, los espacios en blanco dentro del elemento `<code>` se eliminan automáticamente.

El HTML no se ejecutará por defecto. Para evitar esto, agregue `data-noescape` al elemento `<code>`.

```html
<section>
  <pre><code data-trim data-noescape>
(def lazy-fib
  (concat
   [0 1]
   ((fn rfib [a b]
        (lazy-cons (+ a b) (rfib b (+ a b)))) 0 1)))
  </code></pre>
</section>
```

<div class="reveal reveal-example">
  <div class="slides">
    <section>
      <pre><code data-trim data-noescape>
      (def lazy-fib
        (concat
         [0 1]
         ((fn rfib [a b]
              (lazy-cons (+ a b) (rfib b (+ a b)))) 0 1)))
      </code></pre>
    </section>
  </div>
</div>

## Temas
Asegúrese de que su documento incluya un tema de resaltado de sintaxis. Incluimos Monokai de forma predeterminada, que se distribuye con el repositorio reveal.js en [plugin/highlight/monokai.css](https://github.com/hakimel/reveal.js/tree/master/plugin/highlight/monokai.css). Puede encontrar una lista completa de temas disponibles en <https://highlightjs.org/demo/>.
```html
<link rel="stylesheet" href="plugin/highlight/monokai.css" />
<script src="plugin/highlight/highlight.js"></script>
<script>
  Reveal.initialize({
    plugins: [RevealHighlight],
  });
</script>
```

## Números de línea y resaltados

Puede habilitar los números de línea agregando `data-line-numbers` a sus etiquetas `<code>`. Si desea resaltar líneas específicas, puede proporcionar una lista separada por comas de números de línea usando el mismo atributo. Por ejemplo, en el siguiente ejemplo, las líneas 3 y 8-10 están resaltadas:

```html
<pre><code data-line-numbers="3,8-10">
<table>
  <tr>
    <td>Apples</td>
    <td>$1</td>
    <td>7</td>
  </tr>
  <tr>
    <td>Oranges</td>
    <td>$2</td>
    <td>18</td>
  </tr>
</table>
</code></pre>
```

<div class="reveal reveal-example">
  <div class="slides">
    <section>
<pre><code data-line-numbers="3,8-10" data-trim data-noescape>
&lt;table&gt;
  &lt;tr&gt;
    &lt;td>Apples&lt;/td&gt;
    &lt;td>$1&lt;/td&gt;
    &lt;td>7&lt;/td&gt;
  &lt;/tr&gt;
  &lt;tr&gt;
    &lt;td>Oranges&lt;/td&gt;
    &lt;td>$2&lt;/td&gt;
    &lt;td>18&lt;/td&gt;
  &lt;/tr&gt;
&lt;/table&gt;
</code></pre>
    </section>
  </div>
</div>

#### Desplazamiento del número de línea <span class="r-version-badge new">4.2.0</span>

Puede desplazar el número de línea si desea mostrar un extracto de un conjunto de código más largo. En el siguiente ejemplo, establecemos `data-ln-start-from="7"` para que los números de línea comiencen desde 7.

```html
<pre><code data-line-numbers data-ln-start-from="7">
<tr>
  <td>Oranges</td>
  <td>$2</td>
  <td>18</td>
</tr>
</code></pre>
```

<div class="reveal reveal-example">
  <div class="slides">
    <section>
<pre><code data-line-numbers data-ln-start-from="7" data-trim data-noescape>
&lt;tr&gt;
  &lt;td>Oranges&lt;/td&gt;
  &lt;td>$2&lt;/td&gt;
  &lt;td>18&lt;/td&gt;
&lt;/tr&gt;
</code></pre>
    </section>
  </div>
</div>

## Resaltados paso a paso

Puede recorrer múltiples resaltados de código en el mismo bloque de código. Delimite cada uno de sus pasos de resaltado con el carácter `|`. Por ejemplo, `data-line-numbers="1|2-3|4,6-10"` producirá tres pasos. Comenzará resaltando la línea 1, el siguiente paso son las líneas 2-3 y finalmente la línea 4 y del 6 al 10.

```html
<pre><code data-line-numbers="3-5|8-10|13-15">
<table>
  <tr>
    <td>Apples</td>
    <td>$1</td>
    <td>7</td>
  </tr>
  <tr>
    <td>Oranges</td>
    <td>$2</td>
    <td>18</td>
  </tr>
  <tr>
    <td>Kiwi</td>
    <td>$3</td>
    <td>1</td>
  </tr>
</table>
</code></pre>
```

<div class="reveal reveal-example">
  <div class="slides">
    <section>
<pre><code data-line-numbers="3-5|8-10|13-15" data-trim data-noescape>
&lt;table&gt;
  &lt;tr&gt;
    &lt;td>Apples&lt;/td&gt;
    &lt;td>$1&lt;/td&gt;
    &lt;td>7&lt;/td&gt;
  &lt;/tr&gt;
  &lt;tr&gt;
    &lt;td>Oranges&lt;/td&gt;
    &lt;td>$2&lt;/td&gt;
    &lt;td>18&lt;/td&gt;
  &lt;/tr&gt;
  &lt;tr&gt;
    &lt;td>Kiwi&lt;/td&gt;
    &lt;td>$3&lt;/td&gt;
    &lt;td>1&lt;/td&gt;
  &lt;/tr&gt;
&lt;/table&gt;
</code></pre>
    </section>
  </div>
</div>

## Entidades HTML <span class="r-version-badge new">4.1.0</span>

El contenido agregado dentro de un bloque `<code>` se analiza como HTML por el navegador. Si tiene caracteres HTML (<>) en su código, deberá escaparlos ($lt; $gt;).

Para evitar tener que escapar estos caracteres manualmente, puedes envolver tu código en `<script type="text/template">` y nosotros lo manejaremos por ti.

```html
<pre><code><script type="text/template">
sealed class Either<out A, out B> {
  data class Left<out A>(val a: A) : Either<A, Nothing>()
  data class Right<out B>(val b: B) : Either<Nothing, B>()
}
</script></code></pre>
```

## API de highlight.js y beforeHighlight <span class="r-version-badge new">4.2.0</span>

Si desea interactuar con highlight.js antes de que se resalte su código, puedes usar `beforeHighlight`. Por ejemplo, esto puede ser útil si deseas registrar un nuevo idioma a través de la [API de highlight.js](https://highlightjs.readthedocs.io/en/latest/api.html).

```js
Reveal.initialize({
  highlight: {
    beforeHighlight: (hljs) => hljs.registerLanguage(/*...*/),
  },
  plugins: [RevealHighlight],
});
```

## Resaltado manual

Todos sus bloques de código se resaltan automáticamente cuando se inicia reveal.js. Si desea deshabilitar este comportamiento y activar el resaltado por su cuenta, puede establecer el indicador `highlightOnLoad` en "false".

```js
Reveal.initialize({
  highlight: {
    highlightOnLoad: false,
  },
  plugins: [RevealHighlight],
}).then(() => {
  const highlight = Reveal.getPlugin('highlight');
  highlight.highlightBlock(/* code block element to highlight */);
});
```
