## HTML

Ahora que ya hicimos una introduccion a lso conceptos basicos sobre HTML, vamos a empezar a indagar un poco mas profundo. Es necesario conocer de una mejor manera los componentes de este lenguaje para entender y poder estructurar una pagina.

#### Semantic HTML

El concepto de HTML semantico se centra en el uso de HTML como una herramienta para proveer de contenido y estructura a una pagina, y no apariencia. Sostiene que la mejor manera para escribir codigo HTML es no centrarse en fuentes, colores y tamaños, cosas que te permite hacer HTML, si no en la estructura. Esto es bueno para las computadoras, robost, search engines, y todo el que lea tu codigo, ya que deja que da una mayor legibilidad y organizacion.

Por ejemplo, un web designer podria escribir de esta manera un titulo en una pagina:

```html
<font size="6">   
	<strong>This is a page title</strong> 
</font>
```

Esto lo que va a hacer es ponerte el titulo de una forma mas grande y en negrita, pero sacrifica un monton de organizacion. La computadora no tiene forma de saber que este es el titulo de tu pagina.

Por eso es que se recomienda usar los correctos elementos, y escribir de forma semantica, como aca:

```html
<h1>This is a heading</h1>
```

Lo escribis de esta manera, y luego le das estilos en el documento css.

Por otro lado, escribir de forma semantica una pagina da lugar a algunas mejoras. Por ejemplo, hay gente que usa browsers que leen las cosas por ellos. Si la pagina no esta estructurada de forma que el browser pueda verla, no va a poder leerlo. En otras palabras, da mas accesibilidad.

Otro ejemplo son los search engines, que tienen que entender tu codigo para poder situarte en el buscador, en la categoria a la que perteneces. O sea, sirve para SEO.

Ademas, es mas rapido, porque tiene menos codigo que procesar, hace que la aplicacion del diseño sea mas simple, porque no se aplica de forma individual si no que esta en un archivo aparte. 

Conclusion, escribi de forma semantica.

#### Divisions and Spans

Los `<div>` y `<span>` funcionan como contenedores en HTML, que solo sirven para diferenciar cosas y para propositos de estilo. No tienen un valor semantico como tal, ni un significado, son solo containers. Una division en la estructua hecha para algun proposito.

-------

###### Block vs Inline Elements

La mayoria de los elementos en HTML son de la forma block-level o inline-level. 

Un elemento **block-level** o **en bloque** es todo elemento que empiece una nueva linea, como un parrafo, y que usa el largo completo de la pagina o del container. Puede contener una o mas lineas y tiene un line break antes y despues del elemento.

Un elemento en bloque ocupa todo el espacio de su elemento parent (contenedor), y asi crea un bloque.

Estos elementos deben aparecer solo dentro del `<body>`.

Este comportamiento lo poseen la mayor parte de los elementos.

En cambio, los elementos **inline-level** o **en linea**, no continuan en una nueva linea, si no que siguen el flujo del documento y se adaptan a la misma linea en la que estan. Esto por lo general se ve en elementos que contienen pocas palabras, y que estan dentro de un elemento en bloque.

Estos son dos ejemplos iguales, pero en uno el texto esta puesto en un elemento que funciona en forma de bloque, y el otro en forma de linea.

```html
<div>The following paragraph is a <p class="highlight">block-level element;</p>
its background has been colored to display both the beginning and end of
the block-level element's influence.</div>
```

Esto lo que hace es separar el elemento del parrafo con un salto de linea antes y despues. Y colorea con css ese codigo p, para que se vea que colorea toda la linea.

```html
<div>The following span is an <span class="highlight">inline element</span>;
its background has been colored to display both the beginning and end of
the inline element's influence.</div>
```

El span en cambio es un elemento inline, porque el texto termina poniendose normal, sin saltos de linea, y se colorea solo las lineas que ocupa el elemento. 

--------

Siguiendo con los `<div>` y `<span>`, estos son elementos muy valiosos, que se usan mucho para aplicar estilos a un mismo conjunto de elementos, todos contenidos bajo estos. Ambos funcionan igual, pero tienen una diferencia.

El `<div>` es un elemento *en bloque*, y es usado para hacer de conteiner de un grupo largo de elementos, ayudando a poder construir mejor el diseño de una pagina. Mientras que el elemento `<span>` es un elemento *en linea*, y es mejor para usarlo con un numero chico de cosas, tambien para propositos de estilos y diseño.

Si te fijas en el documento de una pagina, esta repleto de divs y spans. Solo hay que tener en cuenta que no dan ninguna estructura en particular, si no que solo es para agrupar elementos de diferentes maneras y para poder darle estilos a todo el conjunto entero. 

Se suelen usar con los atributos *class* y *id*, porque son los mas convenientes para identificar al conjunto entero. Pero para nombrar estos atributos hay que tener un poco de cuidado. El nombre tiene que hacer referencia al contenido del elemento, y no a la apariencia.

Esto es porque las apariencias pueden cambiar en un futuro, y ya no tendrian sentido sus nombres. Imaginate que queres colorear un bloque donde estan tus redes sociales de naranja, entonces le pones `class="orange"`, pero si luego lo queres cambiar a azul, ya no va a tener sentido.

Un nombre con mas sentido seria "social" por ejemplo, ya que hace referencia al contenido.

```html
<!-- Division -->
<div class="social">
  <p>I may be found on...</p>
  <p>Additionally, I have a profile on...</p>
</div>

<!-- Span -->
<p>Soon we'll be <span class="tooltip">writing HTML</span> with the best of them.</p>
```

-----

###### Comments

Lo que se ve arriba son comentarios en HTML. Cumplen la funcion de todo comentario, documentar tu codigo, y no son vistos cuando se ejecuta el codigo.

Los comentarios en HTML se realizan con `<!-- -->`, y en css se hacen con `/* ...  */`.

-----

#### Text-Based Elements

En la web hay mucho contenido en diferentes formatos, pero sin duda el que predomina es el texto. En HTML hay varios elementos para imprimir texto, pero vamos a ver por ahora lo mas basicos, que son los *headings*, *paragraph*, *bold text* para importancia y *italics* para enfasis. Despues en la lesson 6 vamos a ver como trabajar con tipografia.

##### Headings

Los headings son elementos en bloque, porque separan con saltos de linea y funcionan como titulos o separador de seccion en una pagina. Viene en seis diferentes tipos, desde `<h1> hasta <h6>`, y  establecen herarquia en una pagina. Ademas, ayudan a los search engines a identificar mejor el contenido de una pagina.

El elemento `<h1>` esta hecho para representar el texto mas importante en la pagina, y luego le siguen de los `<h2>, <h3>, ...`. Algo que no se debe hacer para mantener el valor semantico del documento, es usar los headings como un texto en negrita o algo asi, para intensificar algo. No es necesario ya que hay otras alternativas.

<h1>Heading Level 1</h1> <h2>Heading Level 2</h2> <h3>Heading Level 3</h3> <h4>Heading Level 4</h4> <h5>Heading Level 5</h5> <h6>Heading Level 6</h6> 



##### Paragraphs

Por lo general los headings estas seguidos de parrafos, para poder poner todo el contenido de la pagina. Los parrafos se utilizan con el elemento en bloque `<p>`. Es por esta razon que entre parrafos hay saltos de linea. Los parrafos pueden aparecer uno atras del otro para contener la informacion deseada. 

```html
<p>Steve Jobs was a co-founder and longtime chief executive officer at Apple. On June 12, 2005, Steve gave the commencement address at Stanford University.</p> 
<p>In his address Steve urged graduates to follow their dreams and, despite any setbacks, to never give up&ndash;advice which he sincerely took to heart.</p>
```

Esto temina imprimiento ambos parrafos con una linea entre medio.

##### Blod Text with Strong

Para darle importancia al texto usamos *bold* text, o negrita. Para esto utilizamos el elemento en linea `<strong>`, pero en realidad hay dos, el `<strong>` y el `<b>`. Esta bueno entender la diferencia semantica de estos dos elementos. 

Esto lo saque de otra pagina. Incluye algunos elementos mas, pero da su valor semantico:

- **`<i>`** — was italic, now for *text in an “alternate voice”*, such as transliterated foreign words, technical terms, and typographically italicized text ([W3C:Markup](http://dev.w3.org/html5/markup/i.html), [WHATWG](http://www.whatwg.org/specs/web-apps/current-work/multipage/text-level-semantics.html#the-i-element))
- **`<b>`** — was bold, now for *“stylistically offset” text*, such as keywords and typographically emboldened text ([W3C:Markup](http://dev.w3.org/html5/markup/b.html), [WHATWG](http://www.whatwg.org/specs/web-apps/current-work/multipage/text-level-semantics.html#the-b-element))
- **`<em>`** — was emphasis, now for *stress emphasis*, i.e., something you’d pronounce differently ([W3C:Markup](http://dev.w3.org/html5/markup/em.html), [WHATWG](http://www.whatwg.org/specs/web-apps/current-work/multipage/text-level-semantics.html#the-em-element))
- **`<strong>`** — was for stronger emphasis, now for *strong importance*, basically the same thing (stronger emphasis or importance is now indicated by nesting) ([W3C:Markup](http://dev.w3.org/html5/markup/strong.html), [WHATWG](http://www.whatwg.org/specs/web-apps/current-work/multipage/text-level-semantics.html#the-strong-element))

Pasado a español, el elemento `<b>` se usa para destacar del resto, pero solo con propositos de diseño o esteticos. Por eso es que dice *stylistically offset*, que si lo descomponemos, *offset* significa que se distingue de los demas, y *stylistically* que es lo opuesto de semantico, o sea, que no tiene ningun significado en la semantica de la frase o palabra, si no que tiene propositos esteticos.

En cambio, el elemento `<strong>` se utiliza para verdadera importancia relativa del texto. Dice que se suele anidar, para destacar su importancia. Total esto no hace que baje la linea, porque es un elemento "en linea".

Para mas informacion y una explicacion mas detallada sobre cada uno: http://html5doctor.com/i-b-em-strong-element/.

Aca es cuando uno se da cuenta de que, no es simplemente una escritura de texto asi nomas, si no que tiene su significado semantico potente. No es cualquier cosa la escritura de texto en la web. Claro que se puede hacer de una forma sencilla, pero un documento escrito de forma semanticamente correcta es otra cosa. Ni hablar de los beneficios que debe traer.

Pero volviendo, `<strong>` para importancia semantica, y `<b>` para destaque en diseño. 

```html
<!-- Strong importance -->
<p><strong>Caution:</strong> Falling rocks.</p>

<!-- Stylistically offset -->
<p>This recipe calls for <b>bacon</b> and <b>baconnaise</b>.</p>
```

Que imprime:

<p><strong>Caution:</strong> Falling rocks.</p> <p>This recipe calls for <b>bacon</b> and <b>baconnaise</b>.</p>               



##### Italicize Text with Emphasis

Esto seria para italizar texto, y dar enfasis a una palabra. Para esto usamos el elemento `<em>`, que tambien es un elemento en linea. Pero al igual que antes hay dos formas en realidad de hacerlo, una es con `<em>` y la otra se hace con `<i>`, y es equivalente a la negrita. El primero se usa para dar enfasis semantico, y el segundo para una letra italica por el lado del diseño.

En conclusion, uno por lo general utiliza `<strong>` y `<em>`, porque por lo general si estas cambiando la forma de imprimir una palabra es porque le queres dar mas importancia o enfasis. Pero hay casos es que esto no es asi, y pasa mas con la letra italica en citas o palabras en otros idiomas, cosas asi. Son texto que no necesariamente tienen enfasis, pero se quieren distinguir de los demas, y es por eso que necesitas una letra italica sin significado semantico.

La utilizacion de esto es a nuestro criterio, pero siempre dandole el valor semantico correspondiente a lo que lo debe tener.

```html
<!-- Stressed emphasis -->
<p>I <em>love</em> Chicago!</p>

<!-- Alternative voice or tone -->
<p>The name <i>Shay</i> means a gift.</p>
```

Que imprime:

<p>I <em>love</em> Chicago!</p>

<p>The name <i>Shay</i> means a gift.</p> 



Pero ademas de texto, tambien se le debe dar estructura a una pagina. Es por esto que existen otro tipo de elementos diseñados para este proposito, como pueden ser los *headers*, *articles*, *footers*, y siguen. Vamos a verlos.

#### Building Structure

