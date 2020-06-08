## HTML

Ahora que ya hicimos una introduccion a los conceptos basicos sobre HTML, vamos a empezar a indagar un poco mas profundo. Es necesario conocer de una mejor manera los componentes de este lenguaje para entender y poder estructurar una pagina.

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

Anteriormente, toda la estructura de una pagina web estaba hecha con elementos `<div>`. El problema de esto es que, aunque sirve para dividir secciones, no agrega valor semantico al documento. Es decir, si por ejemplo la search engine entra a tu pagina, solo ve un monton de `<div>`, sin ninguna informacion de en donde esta parado.

Por esta razon es que en HTML5 se añadieron diferentes elementos estructurales, como son el `<header>`, ` <nav>`, ` <article>`, `<section>`, ` <aside>` y `<footer>`.

Todos estos elementos estan diseñados para dar una organizacion a nuestra pagina, mejorando su estructura semantica. Todos son elementos en bloque, y no tienen un estilo puesto por defercto. Ademas, pueden ser usados mas de una vez por pagina.

![Building Structure](https://learn.shayhowe.com/assets/images/courses/html-css/getting-to-know-html/building-structure.png)

Este es un ejemplo de una posible disposicion de los elementos.

##### Header

El elemento `<header>` se utiliza para identificar la parte superior de una pagina, articulo, seccion o un segmento. Por lo general suele contener un heading, algun texto introductorio, navegador, etc.

```html
<header>...</header> 
```

------

###### `<header>` vs `<head>` vs `<h1>` through `<h6>` Elements

Es bastante simple confundirse con estos tres terminos, ya que uno es el header, el otro el head y los demas, los headings. Pero hay que dejar en claro que cada uno tiene diferentes valores semanticos.

El `<header>` es el elemento estructuras que identifica la parte superior de una pagina. Cae dentro del `<body>`.

El `<head>` no es impreso en la pagina, y se utiliza para poner dentro metadatos, incluyendo el titulo del documento y links a archivos externos. Cae dentro del elemento `<html>`.

Y los headings `<h1>` hasta `<h6>` son para designar diferentes headings por la pagina. Titulos, subtitulos, etc.

------



##### Navigation

El elemento `<nav>` identifica una seccion mayor o la mas importante para navegacion de links en una pagina. Es decir, se reserva para navegacion primaria, como un navegador global, tabla de contenidos, links previos o siguientes, y otros.

Por lo general, este elemento solo contiene links internos, a diferentes parted del mismo sitio web. Links externos no deberian ser puestos dentro de un navegador principal, si no que tienen que ponerse en un anchor `<a>`.

```html
<nav>...</nav> 
```



##### Article

El elemento `<article>` se utiliza para identificar una seccion de contenido independiente, self-conteined, que por lo general es independientemente distribuido o reusado. Por lo que entiendo, es para separar una seccion de tu pagina, que generalmente siempre va a ser la misma, es decir, el patron se va a repetir, y dentro vas a poner el contenido de tu blog, diario, contenido cualquiera.

```html
<article>...</article> 
```



##### Section

El elemento `<section>` es usado para identificar un grupo tematico de contenido, que generalmente, pero no siempre, contiene al heading. Es decir, en el se agrupa cierto contenido que tiene contenido semantico similar.

Por lo general se utiliza para corar contenido y separar de forma jerarquica.

```html
<section>...</section> 
```

-----

###### Deciding between`<article>`, `<section>` or `<div>`

Para saber cual de los tres utilizar, lo mas facil es mirar al contenido, como se debe hacer para determinar el valor semantico de todo.

El mas facil de decidir es el elemento `<div>`. Ya que los elementos `<article>` y `<section>` son para dar estructura y significado semantico a un documento, pero en cambio el otro es solo para dar diseño. Por lo tanto, si la separacion es para fines esteticos, usas `<div>`.

Luego, si el contenido tiene valor semantico, y puede ser independientemente distribuido, usa `<article>`. Pero en cambio, si solo representa una seccion de un grupo tematico de contenido, usa `<section>`.

------



##### Aside

El elemento `<aside>` esta diseñado para contener barras laterales, cosas que se insertan, explicaciones cortas, que por lo general estan relacionadas con el contenido que rodea. Por ejemplo, cuando se usa con un elemento `<article>` el `<aside>` puede contener un indice para navegar, informacion del autor, etc.

Por ejemplo, es esta pagina, el aside es para la barra de navegacion por el indice del curso. Arriba contiene el header, y un nav para enlistar el indice.

Hay que recordar que el elemento `<aside>` es un elemento en bloque, y por lo tanto ocupa todo el largo de la pagina en su bloque. Uno pensaria que se posiciona solo a un costado, como es usual, pero no es asi. Esto se puede hacer por otra parte, que despues vamos a ver.

```html
<aside>...</aside>
```



##### Footer

El elemento `<footer>` identifica el final o cierre de una pagina, articulo, seccion u otro segmento. Por lo general se situa al fondo de su elemento parent. Es decir, un parent puede contener a muchos elementos dentro. Bueno, este suele ser el ultimo.

El contenido dentro del elemento deberia ser informacion relativa a la seccion o elemento en el que este contenido, no debe hacer referencia a otra cosa.

```html
<footer>...</footer> 
```

----

###### Caracter encoding

Hay veces en las que ciertos caracteres especiales pueden ser confundidos por otros caracteres. Es por esta razon que tienen que ser codificados. 

La codificacion de un caracter en HTML es muy simple, lleva un ' & ' antes y un ' ; ' despues del codigo del caracter. 

Por ejemplo, si quisieramos escribir la palabra "resumé", tendriamos que usar `resum&eacute;`, porque esa tilde al revez causa problemas en un documento. 

------



#### Creating Hyperlinks

Junto con el texto, los hipervinculos forman una parte esencial del internet, ya que provee la capacidad de llegar desde una pagina o resource a otra. Los hipervinculos se forman con el elemento anchor `<a>`, que es un elemento en linea, y que necesita para funcionar el atributo `href`, conocido como "hyperlink reference", para referenciar al link.

Por ejemplo, aca clickeando en "Shay", se llega a la pagina puesta en la referencia:

```html
<a href="http://shayhowe.com">Shay</a>
```

###### Wrapping Block-Level Elements with Anchors

Hay una convencion que dice que elementos en linea no deberian encerrar a elementos en bloque. Pero en HTML5 se permitio hacer esto con los anchor, como una excepcion, dado a las utilidades que provee.

El elemento anchor tiene permiso, aunque sea un elemento en linea, para encerrar ya sea otros elementos en linea, en bloque o cualquier otro elemento. Lo que se consigue con esto es hacer que un elemento entero se comporte como un link.

Este es el ejemplo de las imagenes, que encerradas por un anchor pueden ser clickeables y no solo una foto.



##### Relative & Absolute Paths

Los dos tipos de links mas comunes son aquellos que dirigen a otra pagina en el mismo sitio web, y aquellas que te dirigen a otros sitios web. Estos links se referencian en el atributo `href`, y son mas conocidos como paths.

Los links que dirigen a una pagina diferente del mismo sitio son **relative paths**, porque no se deben poner en el `href` con su dominio completo (con el .com, .org, etc). Esto es porque, al ser de la misma pagina, basta con colocar su filename, contenido en alguna carpeta de nuestro proyecto.

El atributo `href` tiene que reflejar cuando una pagina nueva e esta tomando de la carpeta que contiene todas las paginas. Lo que hace es tomarla de ahi, en vez de poner su link como si fuera una pagina externa.

En cambio, si el link te dirige hacia una pagina en otro sitio web, el atributo `href` debe contener un **absolute path**, indicando el dominio completo al que te lleva la pagina al clickear el link. 

```html
<!-- Relative Path -->
<a href="about.html">About</a>

<!-- Absolute Path -->
<a href="http://www.google.com/">Google</a>
```

Aca, clickeando en About nos dirige a la pagina que esta contenida dentro de la carpeta del documento, que es about.html. Pero clickeando en Google nos lleva a un link externo que es google.com.



##### Linking to an Email Address

Hay veces en que uno quisiera crear un hipervinculo que te permita enviar un mail a alguien, o al propietario de la pagina. Por ejemplo, podria decir "Email me!", y al clickearlo, te redirige a un cliente de emails en donde uno puede llenarlo y el email es enviado al mail correspondiente.

Para que esto sea posible, el atributo `href` debe tener un valor que comience con `mailto:`, seguido del email address de la persona a la que se lo quiere enviar.

Por ejemplo, para enviar un email a *shay@awesome.com*, tendrias que poner en el atributo `mailto:shay@awesome.com`.

Podriamos tambien enviar un asunto, cuerpo del texto, y otra informacion ligada al mail. Por ejemplo, para enviar un asunto, tenemos que incluir el parametro `subject=` al path del mail. Recorda que un mail es como un URL, pero que se envia por medio de otro protocolo. Por lo tanto puede tener parametros. El primero de ellos, siguiendo al email, debe ser un `?`, para poder conectar con parametros a la derecha del path. Si hay multiples palabras en un asunto, se requiere que los espacios en blanco entre ellas sean codificados con `%20`, porque un URL no acepta espacios.

El cuerpo del mensaje que se envia funciona de la misma manera que el asunto, pero esta vez usando el parametro `body=`. Pero en este caso, como estamos poniendo mas de un parametro, estos deben conectarse con un `&`. Y pasa lo mismo que antes, los espacios se deben codificar con `%20` y ademas, los saltos de linea con `%0A`.

Para mas codificaciones, hay que buscar una tabla en donde esten puestos. Son todos numeros hexadecimales que representan caracteres.

Entonces, pongamos todo junto y mandemosle un mail a `shay@awesome.com`, con el asunto "Que onda", y el body "Que haces pibe".

```html
<a href="mailto:shay@awesome.com?subject=Que%20Onda&body=Que%20haces%pibe">Email Me</a>
```



##### Opening links in a New Window

Por defecto, un link que clickeamos se abre en la misma pestaña en la que estamos, pero podemos modificar esto y hacer que se habra una nueva cada vez que clickeamos links.

Para poder hacer esto, en el elemento anchor tenemos que poner el atributo `target="_blank"`.

Por ejemplo, abramos `http://shayhowe.com/` en una nueva pestaña:

```html
<a href="http://shayhowe.com/" target="_blank">Shay Howe</a>
```



##### Linking to Parts of the Same Page

Hay casos en que uno clickea un link, y este nos lleva a otra seccion en la misma pagina. Es como un movimiento, que por lo general es hacia abajo, y nos lleva mas rapido al contenido que queremos. Esto suele pasar por ejemplo en libros virtuales, en donde hay un indice y nos tira hacia abajo hasta llegar al contenido.

Podemos hacer esto facilmente con un anchor, primero poniendole el atributo `id` al elemento que queremos ir, y despues dandole la referencia a ese atributo en el `href` del anchor, con un `#` y el nombre del id.

Por ejemplo, si queremos ir para el principio de la pagina podriamos hacer algo asi:

```html
<body id="top">
    ...
    <a href="#top">Back to top</a>
    ...
</body>
```

Ahora clickeas en "Back to top" y te lleva al inicio de la pagina.