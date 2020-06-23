# Typography

Elcampo de la tipografia crecio mucho ultimamente. Antes la tipografia que uno podia utilizar solo era la que estaba contenida dentro de tu computadora, y no habia forma de poder trabajar con otras que no sean esas. Hoy en dia lo que se peude hacer es importar o meter dentro del documento las tipografias que nosotros queremos utilizar, dandonos una cantidad gigante de diferentes tipografias de donde elegir.

Pero aun asi, auque simplemente puedas importar tipografias y listo, necesitamos tener un conocimiento de los principios basicos en la tipografia. 

Por si estan interesados en un conocimiento mas profundo en tipografia, podes ir [aca](http://webtypography.net/toc/).

---------

###### Typeface vs Font

Estos dos conceptos se suelen usar de manera intercambiable, pero no son iguales. *Typeface* hace referencia a la tipografia en si, su impresion artistica, como se ve, sinte y se lee. Una *font* es un archivo que contiene una typeface. Este archivo es el que le premite a la computadora acceder a la tipografia.

Una buena analogia entre las dos es la comparacion entre una cancion y un mp3. La cancion es la expresion artistica en si, mientras que el mp3 es un archivo.

---------



### Adding Color to Text

Una de las primeras cosas en que uno piensa para empezar a darle un estilo a su pagina es añadir una fuente diferente a la del browser y un color, y que esto es una de las principales cosas que hacen que una pagina empiece a tomar su escencia.

La unica propiedad que necesitamos para poder cambiar el color de texto en general es `color`. Y para setearla usamos los valos que ya vimos antes, que por lo general es el hexadecimal, pero vimos otros como el RGB, RGBa, HSL y HSLa.

```css
html {
  color: #555;
}
```

De esta manera se setea un mismo color a todo el texto de la pagina.



### Changing Font Properties

Todas las diferentes propiedades que podemos utilizar para editar texto recaen en dos tipos: las font-based y las text-based. Es decir, una categoria hace referencia solo a la fuente, y la otra solo al texo. 

Para usar cada categoria se utiliza un prefijo, que es `font-` para la de fuente, y `text-` para la de texto. Nosotros vamos a arrancar por las propiedades de la categoria fuente.

##### Font Family

La propiedad `font-family` se utiliza para separar por comas todas las fuentes que queremos incluir en el documento. La primer fuente de esta lista es la fuente principal, que se utilizara en caso de que este disponible. 

Luego, si esta no esta disponible para su uso, toma las siguentes fuentes que se declararon, de izquierda a derecha. Como te podras imaginar, la ultima fuente especificada es la principal del sistema, que suele ser `sans-serif` o `serif`.

```css
body {
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
}
```

La razon por la que la fuente "Helvetica Neue" esta encerrada en comillas es porque consiste en mas de dos palabras. Toda fuente con mas de dos palabras se debe encerrar entre comillas. Notar que, el browser va a utilizar esta fuente, pero en caso de que no este disponible o no se halla instalado, va a utilizar la "Helvetica" y asi.

##### Font Size

La propiedad `font-size` te permite setear un tamaño de fuente, uilizando cualquier unidad de medida, ya sea pixeles, em, porcentajes, puntos o `font-size` keywords.

```css
body {
  font-size: 14px;
}
```

##### Font Style

La propiedad `font-style` se utiliza para italizar texto, o para prevenirlo de ser italizado. Tiene cuatro valores, que son `normal`, `italic`, `oblique` y `inherit`. Pero de estos cuatro, los que se suelen usar son el `normal` para devolverle su estado normal al texto, y tambien `italic` para volver el texto a italica.

```css
.special {
  font-style: italic;
}
```

##### Font Variant

No se si pasa todo el tiempo, pero ocacionalmente se cambia el texto a una variante en mayusculas pero mas chica, tambien llamada *small caps*. Son, literalmente, letras mayusculas pero mas chicas de lo normal, como estas:

- sᴍᴀʟʟ ᴄᴀᴘs, SMALL CAPS. Se nota la diferencia.

Vienen tres valores para la propiedad `font-variant`, que son `small-caps`, `normal` y `inherit`. Aunque las mas usadas son las primeras dos, que ya sabras para que son.

```css
.firm {
  font-variant: small-caps;
}
```

##### Font Weight

Hay veces que queremos cambiar una fuente a un estilo en negrita o **bold**. Para esto podemos usar la propiedad `font-weight`, que viene con los valores `normal`, `bold`, `bolder`, `lighter` y `inherit`, como tambien con valores numericos. 

Lo recomendable es utilizar solo los valores `normal` y `bold` para cambiar entre negrita y normal, y en caso de que se quiera cambiar el "peso" del texto, utilizar numeros para tener mas control.

Los numeros utilizados van del `100` al `900`, de cien en cien. Representando el numero 100 al peso mas pequeño, y el 900 al mas grande. La letra `normal` ya viene con un peso de 400, para darse una idea, y la `bold` es de 700. Por esto es que tenes la opcion de usar lighter, que te pone algo menor a 400, y bolder que te lo sube de 700.

Igualmente, antes de poder usar esta propiedad tenemos que fijarnos si nuestra fuente viene con diferentes espesores. Ya que si no viene de esta manera, claramente no va a funcionar, y nos va a tirar al valor mas cercano.

Por ejemplo, la Times New Roman viene solo en 400 y 700, por lo tanto cualquier otro valor lo va a tirar al mas cercano.

##### Line Height

La propiedad `line-height` nos permite cambiar el alto de la linea de texto. Acepta todas las unidades ya vistas.

Una buena practica, para mantener la legibilidad, es la de setear el tamaño de la linea a una vez y medio la de la fuente. Es decir, el mismo tamaño de la fuente, sumado la mitad. 

```css
body {
  line-height: 22px;
}
```

Otro uso que esta bueno para esta propiedad es para centrar el texto (si es que tiene una sola linea) en la mitad de un elemento. Esto se logra seteando el alto del elemento al mismo valor que el alto de la linea de esta manera:

```css
.btn {
  height: 22px;
  line-height: 22px;
}
```

Es muy usado en botones. Notar que, aunque el alto de la linea sea del mismo tamaño que el elemento, no significa que el texto ocupe todo. El texto sigue teniendo su mismo tamaño de siempre, pero al tener el ancho el mismo que el del elemento, lo termina centrando en el medio.

##### Shorthand Font Properties

Una opcion que esta disponible al usar las propiedades de las fuentes es la de usar su version shorthand. Es decir, se puede hacer uso de solo la propiedad `font`, y enlistar separando con espacios cada valor.

De izquierda a derecha, los valores corresponden a `font-style`, `font-variant`, `font-weight`, `font-size`, `line-height`, y `font-family`. 

Todo se separa por espacios, menos claro, la parte de `font-family`, que tiene sus comas pertenecientes al elemento. Ademas, entre la propiedad `font-size` y `line-height` va un " / ". 

```css
html {
  font: italic small-caps bold 14px/22px "Helvetica Neue", Helvetica, Arial, sans-serif;
}
```

##### Font Properties All Together

Este ejemplo usa todas las propiedades que acabamos de ver. Muestra mas o menos el uso que se le podria dar a cada una.

```html
<h2><a href="#">I Am a Builder</a></h2>

<p class="byline">Posted by Shay Howe</p>

<p>Every day I see designers and developers working alongside one another. They work intelligently in pursuit of business objectives. They work diligently making exceptional products. They solve real problems and take pride in their work. They are builders. <a href="#">Continue&#8230;</a></p>
```

```css
h2,
p {
  color: #555;
  font: 13px/20px "Helvetica Neue", Helvetica, Arial, sans-serif;
}
a {
  color: #0087cc;
}
a:hover {
  color: #ff7b29;
}
h2 {
  font-size: 22px;
  font-weight: bold;
  margin-bottom: 6px;
}
.byline {
  color: #9799a7;
  font-family: Georgia, Times, "Times New Roman", serif;
  font-style: italic;
  margin-bottom: 18px;
}
```

El ejemplo se puede ver [aca](https://codepen.io/shayhowe/pen/KfmBz).

-----

###### CSS Pseudo-Classes

Habras notado un selector que nunca antes habias visto, que es ese `a:hover`. El `:hover` que se ve al lado del selector se llama *pseudo-class*, que es una keyword usada en los selctores para añadir un estilo o estado unico. 

En este caso, la keyword `hover` se utiliza para aplicar el diseño correspondiente a cuando uno para por encima del elemento con el cursor. Por esta razon se llama hover (flotar). Cuando el elemento es un hipervinculo, muchas veces lo que se suele hacer es que cuando uno pasa con el cursor por encima, se le cambia el color.

En el caso del ejemplo anterior, se le dio a todos los anchor elements un color celeste, pero cuando pasas por encima del elemento se vuelve naranja. La forma de lograr eso es con el *hover*.

Ademas de ese hay muchas otras pseudo-classes que ya vamos a ir viendo.

------

En cuanto a paginas de fuentes, una de las mas recomendadas para utilizar es [Google Fonts](https://fonts.google.com/), ya que ofrecen fuentes gratiutas y open source. Eso quiere decir que no estan atadas a licencias y las podes descargar y usar para lo que quieras. En cambio, hay fuentes en otras paginas que estas sujetas a licencias, por lo tanto tenes que pagar por ellas para utilizarlas con total libertad.



### Applying Text Properties

Ahora nos vamos a centrar en las propiedades relacionadas al texto en si, y no a la fuente.

##### Text Align

La propiedad `text-align` ajusta un texto dentro de un elemento. Esta tiene cinco valores, que son `left`, `right`, `center`, `justify` y `inherit`. 

Creo que la mayoria son bastantes obvios, menos el valor `justify`. Este ultimo funciona de la misma forma que un texto alineado a la izquierda, pero pone un distanciamiento conveniente entre las palabras de forma que todas entren desde el principio hasta el final del elemento. Termina quedando un texto que rellena todo el espacio disponible por el elemento. En cambio con left, puede que la linea no complete hasta el final, porque si una palabra no entra en la misma linea, baja la linea y continua debajo.

Por ejemplo, este archivo funciona con un alineamineto a la izquierda, y se puede ver porque hay lineas que cortan antes que otras, y los espacios no se ajustan solos.

```css
p {
  text-align: center;
}
```

##### Text Decoration

La propiedad `text-decoration` le da ciertos añadidos a un texto para decorarlo. Entre los valores disponibles estan `none`, `underline`, `overline`, `line-through` y `inherit`. 

Lo que hacen todos estos es añadirle una linea al texto. Esta puede ser debajo del texto, sobre el texto, y por encima. Entre las utilizaciones de esto, una de ellas se me ocurre que puede ser para negar algo, o mostrar ejemplos que estan mal planteados. En ese caso se podria usar el `line-through`. Otra posibilidad es cuando una palabra tiene faltas ortograficas, y el editor te pone una linea roja que esta `underline`, y que ademas esta curvada.

![text-decoration | Codrops](https://codropspz-tympanus.netdna-ssl.com/codrops/wp-content/uploads/2014/12/text-decoration-example.png)

```css
.note {
  text-decoration: underline;
}
```

Ademas, se le pueden añadir varias decoraciones a un texto en una misma propiedad, separando con espacios los valores.

##### Text Indent

El indentado de texto con la propiedad `text-indent` te permite separar texto en la primer linea de un parrafo, o de cualquier elemento que contenga texto, al igual que se suele hacer en las publicaciones impresas.

La propiedad toma todas las unidades que ya vimos. Y para valores positivos, toma una indentacion hacia adentro, mientras que con valores negativos, la toma hacia afuera.

```css
p {
  text-indent: 20px;
}
```

##### Text Shadow

La propiedad `text-shadow` te permite añadirle sombras a un texto. Por lo general esta compuesto de cuatro valores separados por espacios. Entre esos cuatro, tres de ellos representan medidas de la sombra, y el cuarto representa el color de esa sombra.

En cuanto a los primeros tres, el primero representa la compensacion de la sombra horizontal, y el segundo el de la sombra vertical. El tercero por otro lado, determina el radio de difuminacion de la sombra. El cuarto valor, como ya dijimos, representa el color, que puede estar en cualquier sistema ya visto anteriormente.

```css
p {
  text-shadow: 3px 6px 2px rgba(0, 0, 0, .3);
}
```

Te recomiendo ir ahora y probar alguna que otra sombra, para ver como funcionan estos numeros.

Algo a mencionar es que, cuando el valor es positivo respecto a la linea vertical, se proyecta hacia la derecha. En cambio, si lo pones negativo lo tira para la izquierda. Lo mismo pasa con la sombra horizontal, que si esta seteada en positivo la tira hacia abajo, y negativo hacia arriba.

Por defecto el color ya viene seteado a negro creo, y dependiendo de la difuminacion se va a volver mas grizaceo. Es cuestion de ir probando. Los valores no son obligatorios para que la propiedad funcione. Pero es recomendable poner aunque sea los primeros tres porque sino ni siquiera se ve como una sombra.

##### Box Shadow

Aunque no tenga relacion con el texto, lo mencionamos ahora a esta propiedad porque funciona exactamente como lo hace la de arriba. Tenes cuatro valores, dos para posicionamiento, el otro para difuminacion y el ultimo del color. Pero ademas acepta un valor mas que corresponde al estiramiento de la sombra.

Y por ultimo, tambien tiene un valor opcional, que se puede situar al inicio de los valores, que es `inset`. Este valor pone a la sombra del lado de adentro del elemento antes que del de afuera.

##### Text Transform

Esta propiedad `text-transform` funciona con el mismo sentido que la propiedad ya vista `font-variant`. Esta hecha para hacer un cambio en el texto entre lineas si necesidad de cambiar de *typeface*. Hay cinco valores posibles para esta propiedad, los cuales son `none`, `capitalize`, `uppercase`, `lowercase` y `inherit`.

El valor `capitalize` lo que va a hacer es poner la primer letra de cada palabra en mayusculas. Luego la `uppercase` y `lowercase` va a setear todo a mayusculas o todo a minuscula. 

```css
p {
  text-transform: uppercase;
}
```

##### Letter Spacing

Esta propiedad `letter-space` nos permite manipular el espaciamiento entre letras. Un valor positivo va a alejar las palabras entre si, y un valor negativo las va a juntar, el valor `none` las va a poner en su estado normal.

```css
p {
  letter-spacing: -.5em;
}
```

Esto hace que las letras se junten la mitad del espacio de lo que estaban.

##### Word Spacing

Al igual que la anterior propiedad, esta propiedad `word-spacing` setea un valor de separacion pero entre las palabras esta ves. Funciona de la misma manera que antes.

```css
p {
  word-spacing: .25em;
}
```

##### Text properties All Together

Hagamos lo mismo que antes. Pongamos todo junto en un ejemplo.

```html
<h2><a href="#">I Am a Builder</a></h2>

<p class="byline">Posted by Shay Howe</p>

<p class="intro">Every day I see designers and developers working alongside one another. They work intelligently in pursuit of business objectives. They work diligently making exceptional products. They solve real problems and take pride in their work. They are builders. <a href="#">Continue&#8230;</a></p>
```

```css
h2,
p {
  color: #555;
  font: 13px/20px "Helvetica Neue", Helvetica, Arial, sans-serif;
}
a {
  color: #0087cc;
}
a:hover {
  color: #ff7b29;
}
h2 {
  font-size: 22px;
  font-weight: bold;
  letter-spacing: -.02em;
  margin-bottom: 6px;
}
h2 a {
  text-decoration: none;
  text-shadow: 2px 2px 1px rgba(0, 0, 0, .2);
}
.byline {
  color: #9799a7;
  font-family: Georgia, Times, "Times New Roman", serif;
  font-style: italic;
  margin-bottom: 18px;
}
.intro {
  text-indent: 15px;
}
.intro a {
  font-size: 11px;
  font-weight: bold;
  text-decoration: underline;
  text-transform: uppercase;
}
```

Termina en algo como [esto](https://codepen.io/shayhowe/pen/tBazc). Notar que le agrega un poco de sombra al texto principal. Un poco de indentacion a la primer linea del texto. Ademas le pone al texto "continue" una linea por debajo y todo en mayuscula.

Notar que la propiedad `text-decoration` es buena para usarla con links o elementos anchor, porque por defecto vienen con una linea por debajo.

Hay muchas utilizaciones realmente con todo esto, y hay que ir viendolas y usandolas con el tiempo, a medida que realizamos diferentes proyectos. Siempre es bueno volver aca para recordar las propiedades disponibles, o en todo caso recurrir a internet. Es imposible que se te queden todas en la cabeza de una, eso solo se logra con repeticion y practica. Pero aunque sea esto te vuelve mas conciente de las cosas que se pueden realizar, y que estan disponibles para su uso. Ese es, al fin y al cabo, el sentido de todo esto.



### Using Web-Safe Fonts

Hay una serie de fuentes que ya vienen pre instaladas en todo dispositivo capas de correr un browser en el. Ya sea una computadora, tablet, smart-phone u cuaquier otro. Por eso es que, hay una lista de alginas fuentes con las que nos podemos quedar tranquilos y asegurarnos de que todo dispositivo las va a renderizar de manera correcta. Esta lista fue titulada con el nombre de "web-safe fonts", porque son todas las fuentes seguras para utilizar. Estas son:

- Arial
- Courier New, Courier
- Garamond
- Georgia
- Lucida Sans, Lucida Grande, Lucida
- Palatino Linotype
- Tahoma
- Times New Roman, Times
- Trebuchet
- Verdana



### Embedding Web Fonts

Algo que se puede hacer tambien cuando se quiere utilizar una fuente en especifico es subirla a un servidor e incluirla dentro de tu documento con un CSS `@font-face` at-rule. Esto nos añade la capacidad de incluir tipografia de diferentes fuentes, de forma que esa tipografia no viva en la computadora del usuario, si no que lo haga de forma online. Asi, asegurandonos de que siempre va a ser renderizada.

Asi es como se llama este tipo de declaracion en CSS, *at-rule*. No solo esta esta, si no que hay muchas otras, y todas se tienen una funcion de comportamiento o para realizar instrucciones. No vamos a ver ahora todas las disponibles, pero en el momento en que hagamos una referencia completa le vamos a dar un pantallazo a todas.

Pero por ahora, solo quedemosnos con que la declaracion `@font-face` nos permite declarar dentro nuestra `font-family` como siempre, e incluirle un `src`, es decir, un source file en donde se encuentre el archivo de la tipografia que queremos utilizar. 

```css
@font-face {
  font-family: "Lobster";
  src: local("Lobster"), url("lobster.woff") format("woff");
}
body {
  font-family: "Lobster", "Comic Sans", cursive;
}
```

Notar que la propiedad `font-family` dentro de esta declaracion `@font-face` no representa la fuente que sera utilizada en el cuerpo del documento, si no que solo indica cual es la fuente que se va a importar. 

Luego, uno tiene que poner igualmente las fuentes que la pagina utilizara, y tambien las fuentes basicas que necesita para los casos en que no puede renderizarlas.

Pero aun asi, aunque podamos subir fuentes a nuestra pagiana, esto no significa que podamos hacerlo con total libertad. Recorda que las fuentes se consideran expresiones artisticas, o piezas de arte. Es decir, estan diseñadas por una persona y le pertenecen a ella o el. Por eso es que antes de poder utilizar una fuente tenemos que ver que tipo de licencia posee. 

Hay sitios web pagos, en donde con una subscripcion se puede acceder a las licencias de una gama de funtes, como tambien hay sitios gratuitos con licencias libres como Google Fonts, que ya hablamos de el mas arriba. 

Por lo tanto, lo recomendable es agarrar fuentes de un lugar en donde sean libres de uso. Y en su defecto, ver a cual licencia estan sujetas.

##### @font-face at-rule

Le quiero dedicar un poco mas a esta declaracion, porque no se entiende muy bien su propiedad `src`. 

Lo que permite hacer `@font-face` es especificar fuentes online para que puedan ser visualizadas en una pagina. Esto permite poder proporcionar a la pagina nuestras propias fuentes, eliminando la necesidad de depender de solo las fuentes que se encuentran instaladas en la computadora del usuario.

Su sintaxis, de forma mas detallada, es la siguiente:

```css
@font-face {
  font-family: <un-nombre-de-fuente-remota>;
  src: <origen> [,<origen>]*;
  [font-weight: <peso>];
  [font-style: <estilo>];
}
```

Se puede ver que la primer propiedad es `font-family`, que recibe un valor que corresponde al nombre que le damos a la fuente. Este nombre luego sera el que tomara todas las propiedades de la fuente que importamos.

Luego en la propiedad `src` se coloca un `<origen>`, correspondiente a la direccion URL de la ubicacion remota del archivo que necesitamos (con `url("URL de la fuente")`), o en su defecto el nombre de la fuente en nuestra computadora, que la referenciamos de la forma `local("Nombre de Fuente")`. Es decir, tenes dos opciones, o llamas directamente al URL en donde se encuentra la fuente, o la descargas y la tenes de forma local.

Luego te da la opcion de especificar en el momento que peso y que estilo de la fuente queres importar. Esto es lo mismo que ya vimos antes, el primero seria el `font-weight` (bold, bolder, ...), y el otro el ``font-size`.

Por ejemplo:

```html
<html>
<head>
  <title>Web Font Sample</title>
  <style type="text/css" media="screen, print">
    @font-face {
      font-family: "Bitstream Vera Serif Bold";
      src: url("http://developer.mozilla.org/@api/deki/files/2934/=VeraSeBd.ttf");
    }
    
    body { font-family: "Bitstream Vera Serif Bold", serif }
  </style>
</head>
<body>
  This is Bitstream Vera Serif Bold.
</body>
</html>
```

Notar como la importa del url en donde se encuentra con la funcion `url()`. 

##### Otra forma de importar fuentes

Hay una forma mas (y tal vez haya otras), que tiene el mismo resultado, pero en lugar de utilizar CSS para importarlo, se importa directamente dentro del documento HTML. Esto se puede hacer usando un `<link>`, en donde el atributo `href` se pone el url de la pagina, y en `rel` se pone stylesheet. Igualmente, Google Fonts te especifica como hacerlo en la parte derecha. Asi que se puede seguir las instrucciones que proveen ellos.



### Including Citations and Quotes

Hay ocaciones en que uno necesita colocar una cita de alguna otra fuente o autor, y como las citas tienen su propio estilo de tipografia, vamos a cubrirlo aca en esta seccion.

Las citas pueden colocarse y distinguirse del texto restante usando HTML semantico solamente, con los elementos `<cite>`, `<q>` y `<blockquote>`. 

Por lo general, para saber que elemento usarne cada caso, hay que seguir estas reglas:

- `<cite>`: Esta diseñada para referenciar un trabajo creativo, un autor o un recurso.
- `<q>`: Este elemento se utiliza para citas cortas en la misma linea (inline).
- `<blockquote>`: Como su nombre lo indica, es un elemento en bloque. Se utiliza para citas mas largas y externas.

##### Citing a Creative Work

El elemento `<cite>` es un elemento en linea, utilizado para citar un trabajo creativo de alguien, incluyendo el titulo de su trabajo, el nombre del autor, o el URL de referencia. Por defecto el texto que rodeas con este elemento se va a poner en italica.

Adicionalmente se pueden incluir links a la pagina correspondiente. Por ejemplo, en este caso se cita a un libro de una autora, y se pasa un link referenciando a su pagina.

```html
<p>The book <cite><a href="http://www.amazon.com/Steve-Jobs-Walter-Isaacson/dp/1451648537">Steve Jobs</a></cite> is truly inspirational.</p>
```

##### Dialogue & Prose Quotation

Generalmente, los dialogos y las prosas son puestas como citas inline. Para estos se debe usar el elemento `<q>` (de quote, o sea, cita), que indica una cita de dialogo o una prosa. No deberia usarse con otros propositos. Solo para citaciones a otro texto, de forma corta y en linea con el resto del texto.

```html
<p>Steve Jobs once said, <q>One home run is much better than two doubles.</q></p>
```

No hay que preocuparse por añadir comillas, ya que el browser las mete por nosotros. Es por esto que lo mejor es usar estos elementos para citar cosas, ya sea por comodidad y ademas por motivos semanticos.

##### Dialogue & Prose Citation

El elemento `<q>` admite adicionalmente un atributo que es `cite`, que lo que hace es dejarte colocar la referencia al URL de la cita. Esto no altera la apariencia del elemento, solo es para añadir un valor para los lectores.

##### External Quotation

El elemento `<blockquote>` es utilizado para referenciar citas grandes que sean externas a la pagina. Este es un elemento en bloque, y que ademas se le pueden poner otros elements anidados dentro de el, como headings y parrafos, ya que estas citando tal vez a una partegrande de una pagina. 

```html
<blockquote>
  <p>&#8220;In most people&#8217;s vocabularies, design is a veneer. It&#8217;s interior decorating. It&#8217;s the fabric of the curtains, of the sofa. But to me, nothing could be further from the meaning of design. Design is the fundamental soul of a human-made creation that ends up expressing itself in successive outer layers of the product.&#8221;</p>
</blockquote>
```

##### External Citation

Al igual que con el elemento `<q>`, el elemento `<blockquote>` tambien admite el mismo atributo `cite`, y adicionalmente, al ser un elemento en bloque, tambien se le puede anidar otro elemento `<cite>`. 

El primero, el atributo, recordar que solo es para referenciar el URL de la cita, pero no tiene ningun cambio en la apariencia. Es solo por cuestiones semanticas o para dejar una referencia al URL de la cita dentro del documento. Se me ocurren que esos pueden ser los casos. El segundo esta buen, porque tal vez no queres dejar un link a la otra pagina, pero si te queres recordar para vos que la cita viene desde esa pagina.

El elemento tambien es para cuestiones semanticas realmente. Porque ya todo el bloque se pone en forma de cita, y porque le pongas otro elemento cite dentro, no hace diferencia en apariencia. Pero asi podrias mostrar que hay una cita dentro de otra cita tal vez.

Por ultimo, decir que para el uso de `<cite>` el browser no agrega comillas, solo es una letra italica. En cambio para los otros dos si se utilizan comillas.

##### Summary

Bien, ya sabemos como trabajar con tipografia. Vimos todas las propiedades disponibles para la fuente y el texto. Ademas vimos como utilizar diferentes fuentes y como importar fuentes externas de forma online dentro de nuestro documento.

Tambien vimos como hacer citaciones a diferente tipo de contenido.