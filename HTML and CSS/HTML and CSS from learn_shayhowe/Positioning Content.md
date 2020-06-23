# Positioning Content

Algo muy interesante de CSS es que nos da la posibilidad de posicionar los elementos en una pagina casi de cualquier manera imaginable. Esto permite darle estructura a una pagina y poder empezar a crear capas de personalizacion un poco mas digestibles.

Vamos a estar viendo en este capitulo las diferentes formas de posicionamiento de los elementos.

### Positioning with Floats

Una forma de posicionar elementos en una pagina es con la propiedad `float`. Esta propiedad se puede usar de varias formas diferentes. 

Lo que nos permite hacer esta propiedad es, agarrar un elemento, removerlo del flujo normal de la pagina, y posicionarlo a izquierda o derecha de su elemento parent. Ademas, todos los demas elementos en la pagina van a fluir alrededor del elemento con esta propiedad.

Por ejemplo, si le pones un `float` a una imagen, y su elemento parent es un parrafo, el parrafo se va a acomodar al tamaño de la imagen y la va a rodear.

Tambien podes usar la propiedad `float` con varios elementos a la vez, creando asi en cada uno una columna. Termina siendo una pagina con columnas.

Esta propiedad acepta varios valores, pero los mas comunes son `left` y `right`.

```css
img {
  float: left;
}
```

#### Floats in Practice

Bien, creemos una estructura simple para una pagina, que tenga un header en la parte superior, dos columnas en el centro, y un footer en la parte inferior.

```html
<header>Header</header>
<section>Section</section>
<aside>Aside</aside>
<footer>Footer</footer>
```

Esto va a crear cuatro elementos en bloque, uno debajo del otro. Pero el tema es que nosotros queremos que la pagina tenga dos columnas en el centro, por lo tanto deberiamos correr `<section>` para la izquierda y `<aside>` a la derecha.

Por lo tanto, asignemosle la propiedad `float` de esa forma:

```css
section {
  float: left;
}
aside {
  float: right;
}
```

Lo que hace un elemento floted es correrse al borde de su elemento parent, y si no tiene elemento parent, al borde de la pagina. 

Ademas, cuando corremos un elemento, lo que sucede es que este rompe el flujo de la pagina. Por lo tanto, se termina acomodando el ancho del elemento a su contenido. Pero esto a veces no se quiere asi, y se soluciona añadiendo un ancho fijo al elemento, normalmente. Por ejemplo, suponete que estamos creando unas columnas para poder hacer una capa de diseño que podamos reusar durante las paginas. Bueno en ese caso, probablemente, usariamos el float con un `width` fijo para que se mantenga el diseño por todas las paginas.

Otro problema que suele suceder es que los elementos a los que se le aplica el `float`, suelen terminar tocandose entre si, causando que el contenido del elemento este muy pegado.  Es aca donde podemos hacer uso del `margin`, para separar un poco los elementos unos de otros.

Por lo tanto, añadamos un `width` y un `margin` a los elementos, asi quedan con una mejor forma.

```
section {
  float: left;
  margin: 0 1.5%
  width: 63%
}
aside {
  float: right;
  margin: 0 1.5%;
  width: 30%;
}
```

Acordate que, en la propiedad `margin`, el primer valor hace referencia al top y al bottom, y el segundo al left y right. Por lo tanto, le esta diciendo al primero que se ponga a la izquierda y que ocupe un 63% del elemento parent, o sea, del `<body>`. Y al segundo, solo un 30% a la derecha. Esto lo que hace es dejar un poco de espacio a los extremos, porque no suma un 100%, y ademas con el margen, hace que se separen un poco mas entre si.

----------

###### Floats May Change an Element's Display Value

Cuando se hace un float a un elemento, hay que tener en cuenta la forma en que este trabaja, que es removiendo al elemento del flujo normal en la pagina, y hay posibilidades de que cambie la forma en que se imprime en pantalla el elemento. La propiedad `float` funciona con elementos en bloque, por lo tanto puede que altere la propiedad `display` de un elemento, si este no es un elemento block-level.

Por ejemplo, si queremos hacerle floating a un elemento `<snpan>`, el cual sabemos que es un elemento en linea sin posibilidad de cambiar su ancho y alto, lo que va a pasar es que automaticamente se va a cambiar su valor de display a block. Esto luego da la posibilidad de cambiar su ancho y largo. 

Esto es solo para saber y tenerlo en cuenta, en caso de que no quieras que se cambie el display del elemento.

------

##### More Than Two Elements

Con dos elementos, es bastante sencillo e intuitivo darles valores, ya que uno se va a la izquierda y el otro a la derecha, pero con mas de dos columnas cambia un poco. Entonces, para hacer esto, modifiquemos un poco nuestro documento, de forma que en vez de tener dos columnas, tengamos tres, entre el header y el footer. Le vamos a poner a las tres `<section>`.

```html
<header>...</header> 
<section>...</section> 
<section>...</section> 
<section>...</section> 
<footer>...</footer> 
```

Entonces lo que vamos a hacer es, en lugar de colcarles posicion a cada uno por separado, las ponemos las tres para un mismo lado, digamos `left`. De esta manera pone un elemento al lado del otro. Tambien, de esta forma, habria que ajustar un poco el ancho de los elementos para que se impriman bien.

```css
section {
  float: left;
  margin: 0 1.5%;
  width: 30%;
}
```

Lo que sucede aca, es que intenta poner uno al lado del otro. Pero el tema es que si el ancho de cada uno es mas de lo que deberia, te los acomoda uno abajo del otro. Es como si no encontrara espacio, y los termina colocando a los que no entran debajo. Por lo tanto, hay que poner un buen tamaño.



#### Clearing & Containing Floats

Seguramente, probando los anteriores ejemplos, notaste que hay superposiciones y esta quedando todo mal.

Esto ocurre porque la propiedad `float` fue originalmente diseñada para envolver el contenido alrededor de una imagen. Es decir, con este proposito funciona perfecto. Intenta agarrar y colocar una imgagen seguido de un parrafo, y separalos. Vas a ver que el parrafo se coloca alrededor de la imagen naturalmente.

Pero el tema es que al no estar diseñado para posicionamiento, tiene algunas fallas. Hay veces que los estilos de un elemento no se renderizan cuando a ese elemento lo ponemos al lado de un elemento con floating, o si el elemento es parent de otro con floating. Los estilos de ese elemento pueden ser cambiados negativamente.

Tambien las propiedades `margin` y `padding` hay veces que no son bien interpretadas, causando una combinacion dentro del elemento floted. O, debido a esto de que el elemento se elimina del flujo normal, los otros elementos a su alrededor tienden a querer ocupar todo el espacio posible, y terminan opacando partes indeseadas.

Esto ultimo te debio haber pasado en el ejemplo de las dos columnas. El elemento `<footer>` termina ocupando todo el espacio horizontal disponible, haciendo que opaque a los elementos `<section>` y `<aside>`.

Bien, para evitar todo esto tenemos que realizar dos cosas. Una es *clear floats*, o sea, limpiar a los elementos, y el otro se llama *contain floats*. Esto se utiliza para devolver a la pagina su flujo normal.

##### Clearing Floats

El proceso de limpieza de floats se realiza con la popiedad `clear`, que acepta varios valores. Los principales son `left`, `right` y `both`.

```css
div {
  clear: left;
}
```

Lo que hace el valor `left` es limpiar los floats izquierdos, es decir, los elementos que posean la propiedad `float: left;`. Y el valor `right` realiza la limpieza para los valores derechos. Aunque el valor mas ideal suele ser el valor `both`, ya que limpia tanto los derechos como los izquierdos.

Entonces, si volvemos a nuestro ejemplo principal con dos columnas, y agregamos la propiedad `clear: both;` al elemento `<footer>`, lo que va a realizar es como una limpieza, sacando al footer de atras y poniendolo debajo. 

Notar que se lo tenemos que colocar a footer, porque es el elemento que cambio su flujo o posicion. Es decir, recordemos que cuando le agregamos la propiedad `float` a un elemento, este cambia su posicion en la pagina alterando el flujo. Por lo tanto, cuando limpiamos un float, lo que hacemos es volver ese flujo a la normalidad. Si antes el elemento `<footer>` estaba debajo de `<section>` y `<aside>`, y cuando cuando cambiamos sus flujos el `<footer>` cambio su lugar, entonces queremos devolverselo.

Notar tambien que la limpieza siempre es aplicada al elemento que viene despues, y no antes.

```css
footer {
  clear: both;
}
```

##### Containing Floats

La segunda opcion para resolver los problemas de renderizado y posicionamiento de elementos se llama *containing*. Esta opcion asegura que todos tus estilos se van a renderizar de manera correcta.

Bien. Esto requiere un poco mas de codigo y de explicacion de algunas cosas adicionales que no vimos. Vamos a intentar ver todo asi no queda nada suelto y sin entender.

Lo primero que hay que tener en cuenta es que, esta forma de limpieza de floats es mas efectiva porque no interrumpe con el flujo de la pagina. No hay forma de que haya problemas en la renderizacion de cosas, o en superposiciones. Nada de eso va a pasar, y esto es porque estamos usando a un elemento como contenedor. De aca sale el nombre de esto, que es mas una tecnica que otra cosa.

Lo que hacemos es utilizar un elemento (que supongo ya te imaginas cual es), que solo vamos a utilizar con el proposito de contener a nuestros elementos, que queremos ponerle la propiedad `float`. Este elemento es el `<div>`, por lo general, ya que sirve mucho en estos casos. Provee una caja en donde podemos meter cosas, solo con propositos de diseño y no semanticos. 

Este elemento `<div>` debe ser elemento parent de nuestros elementos float. Y lo que vamos a hacer es ponerle, es este caso y para este ejemplo, la clase `group`, ya que nos permite tener mayor flexibilidad al darle un estilo, antes que directamente referenciarlo con un type selector.

Y para lograr limpiar los elementos anidados dentro, tenemos que aplicarle lo siguiente:

```css
.group:before,
.group:after {
  content: "";
  display: table;
}
.group:after {
  clear: both;
}
.group {
  clear: both;
  *zoom: 1;
}
```

Lo que hace esto es limpiar a los elementos child del elemento div, que lo referenciamos por medio de su clase. Asi, te terminan quedando tus elementos de la forma que queres, y contenidos dentro de un elemento en bloque (el `<div>`), haciendo que todo se comporte con normalidad, y nada afecte el curso de las cosas.

Por lo tanto, pasamos a tener dos opciones muy buenas. Si se quiere mover elementos de esta forma, sin que nada pase por los costados, y sin que nada afecte el flujo, usa un contenedor. Ahora si tu idea es la contraria, como por ejemplo, separar en columnas una pagina, o poner una imagen rodeada de texto, es mejor usar clearing.

Pero bueno, volviendo atras, hay que explicar como funciona el codigo. 

Las dos palabras que se ven, que son `:before` y `:after` son pseudo-elementos. Es decir, son una clase diferente de elementos, utilizados para dar estilos a algunas partes especificas de los elementos, como puede ser la primer letra de un texto, o la primer linea de un elemento, o para insertar contenido antes o despues de un elemento. Estos dos pseudo-elementos son elementos generados de manera dinamica por encima y debajo del elemento, que en este caso del ejemplo, es el `<div class="group">`.

Estos elementos no incluyen ningun contenido dentro y son impresos como elementos `table-level`. Esta es otra forma de presentacion de los elementos, parecida al display en bloque. No hay que preocuparse mucho por esta clase de elemento, porque cuando veamos como hacer tablas va a quedar bastante claro.

Por lo tanto, el primer selector, compuesto por estos dos pseudo-elementos, lo que esta haciendo es asignarle un contenido vacio a los mismos, y que se impriman como tabla. 

Luego los otros dos selectores se encargan de limpiar los floats. El primero, se encarga de limpiar los elementos dentro del `<div>`, ya que al ser el elemento que viene despues del div, limpia a los anteriores, que serian su contenido. El segundo referencia al div en si, y lo que hace es asegurarse de limpiar cualquier otro elemento que haya quedado por encima de este. Esto lo tiene que hacer en caso de que encima haya elementos float que no esten contenidos en un div, de forma que el mismo div no caiga en lo mismo que caia el footer en el anterior ejemplo. Es decir, que no opaque a los de arriba.

Por ultimo, la propiedad `*zoom: 1;` indica que el factor de escala es normal.

Entonces, apliquemos todo esto que vimos en el ejemplo de antes, poniendo dentro de un contenedor a los elementos `<section>` y `<aside>`.

```html
<header>...</header>
<div class="group">
  <section>...</section>
  <aside>...</aside>
</div>
<footer>...</footer>
```

```css
.group:before,
.group:after {
  content: "";
  display: table;
}
.group:after {
  clear: both;
}
.group {
  clear: both;
  *zoom: 1;
}
section {
  float: left;
  margin: 0 1.5%;
  width: 63%;
}
aside {
  float: right;
  margin: 0 1.5%;
  width: 30%;
}
```

Entonces al final, termina quedando todo como antes, pero usas un contenedor para meter a los elementos que le haces floating dentro y asi mantener el flujo de la pagina. Lo unico que se agrega es la limpieza por parte del contenedor, que utiliza estos pseudo-elementos para que la realizen.

Esta tecnica es la que se ve tanto en los documentos de las paginas. O capas no es esta en especifico, pero uno puede ver cuando entra a ver el documento HTML de otra pagina que esta repleta de divs. Ahora queda mas claro que esos divs son para hacer separaciones de bloques, poder darles un diseño por separado y para poder posicionar el contenido con mayor facilidad.

Por lo general en las paginas a esta tecnica le suelen poner "clearfix", porque se puede encontrar con ese nombre en algunas paginas, en la definicion de sus clases.



### Positioning with Inline-Block

Ademas de usar floats para posicionar elementos, tenemos la opcion de utilizar el valor `inline-block` dentro de la propiedad `display`. Esto lo que nos permite es poder poner a los elementos formando una linea de bloques.

Lo bueno de esta forma de hacerlo es que no hay que preocuparse por hacerles float o clearing a los elementos, y ademas, todos se comportan como en el box model. Por lo tanto, podemos modificar todas sus partes.

##### Inline-Block in Practice

Empecemos por dejar el documento HTML como el de antes, del ejemplo de las tres columnas:

```html
<header>...</header>
<section>...</section>
<section>...</section>
<section>...</section>
<footer>...</footer>
```

Entonces ahora en vez de darles un floating a los elementos, vamos a cambiarle su propiedad `display` de esta manera.

```css
section {
  display: inline-block;
  margin: 0 1.5%;
  width: 30%;
}
```

Lo que hace es cambiar el display a `inline-block`, y deja los margenes y el ancho como antes.

El tema es que lo que hace esto es imprimirnos los bloques, pero tira uno para la linea de abajo. No lo hace entrar con los otros dos en la misma linea. Esto se debe a que, cuando se hace la suma de los anchos de los elementos, mas sus margenes, el tamaño se termina pasando de lo que tiene la linea y lo tira para abajo.

Pero si te acordas hablamos de algo que ocurria en este tipo de valor de display, que era que aparecian unos espacios entre medio de los bloques. Bueno, para que todo funcione habria que remover este espacio.

##### Removing Spaces Between Inline-Block Elements

Hay varias formas de eliminar ese espacio. Algunas mas complejas que otras, pero nosotros vamos a ver solo dos, que son las mas simples. Estas ocurren dentro de HTML.

La primer solucion es poner cada section uno al lado del otro. Es decir, abris y cerras un section, y el siguiente se le pega al anterior.

```html
<header>...</header>
<section>
  ...
</section><section>
  ...
</section><section>
  ...
</section>
<footer>...</footer>
```

Esto va a hacer que ese espacio desaparesca, dejando que los bloques puedan imprimirse bien.

El problema de ese espacio es que es adicional, y es molesto porque no lo podes medir. Es decir, no es parte del margen, por lo tanto muchas veces uno no lo tiene en cuenta en el elemento, pero porque no es parte del box model. Entonces al final termina molestando y haciendo que las cosas no queden como uno quiere. 

Pero sacandolo, te termina quedando un espacio que corresonde solo al margen. A los valores de margen que vos colocaste.

La segunda forma es igual a la primera en teoria, pero se ve diferente. Lo que se hace es poner un comentario que empiece al final del elemento, y termine en el inicio del siguiente. Asi te estas comiendo todo posible espacio que haya, y termina siendo lo mismo que antes.

```html
<header>...</header>
<section>
  ...
</section><!--   comment
--><section>
  ...
</section><!--
--><section>
  ...
 </section>
 <footer>...</footer>
```

Tal vez los comentarios sea una mejor opcion para la organizacion.



### Creating Reusable Layouts

Cuando uno realiza una pagina, muchas veces es muy conveniente realizar capas que puedas reutilizar durante la pagina. Esto te facilita las cosas, ya que siempre se repite el mismo documento y los mismos estilos.

Estos *layouts* pueden ser creados tanto usando floats o elementos inline-block. Dice que todavia la utilizacion de uno u otro esta en debate, pero que a el le parece una mejor y mas simple opcion usar inline-block elements. Los floats son solo para lo que se inventaron, para hacer un wrap, para que el flujo de la pagina se corte, cambies de posicion el elemento, y otro elemento se acomode a el. 

Yo creo que estoy de acuerdo con el. Porque usar floats parece un poco mas tedioso, por el tema del clearing. Por eso tal vez sea mejor usar los float solo para imagenes y cosas asi, y elementos inline-block para estructurar y posicionar.

Ademas tiene sentido esta segunda forma, porque creando conteiners siempre alrededor de los elementos que queres cambiar de lugar, todo va a ir bien y se facilitan las cosas. Ahora cierra un poco mas todo. 

Es por eso que las paginas deben usar siempre un div principal, que contiene todo el flujo normal de la pagina, con elementos en bloque. Y luego empieza a subdividir con divs para poder cambiar de posicion los elementos. Asi ponele podrias tener un div gigante que vaya desde abajo del header hasta arriba del footer, y tener una division para hacer barras laterales y muchas mas cosas.

Asi que para mi es cuestion de ver a todos como una caja de cajas anidadas, que cada una se controla como quiere, y cada elemento dentro se controla independientemente. 

Por ultimo, tambien hay algunas especificaciones mas de CSS, especificamente la `flex-` y la `grid-`, vale la pena ver.



### Uniquely Positioning Elements

Antes que nada, muy recomendada la pagina A List Apart, creo que es el blog mas importante en el desarrollo web. Tiene todos topics por separado que responden muchas preguntas, de diferentes dudas que nos van quedando por el camino. 

Y de esto se va a tratar esta parte, de ver otra forma para posicionar. Porque probablemente hasta ahora estas entendiendo de que forma se posiciona, pero lo llevas a la practica y a veces es todo medio desastroso. Terminas probando con numeros hasta que las cosas te cuadran bien. Al corto plazo, esto te arregla y hace lo que necesitas, pero no es una buena practica para realizar siempre.

Vamos a estar viendo para esto la propiedad `position` y varios de sus valores.

Muchas veces pasa que queremos tener un control preciso de la posicion de un elemento, ya que usando floating las cosas salen mal muchas veces, no se renderizan bien y se superponen, y usando los elementos inline-block, podemos crear columnas pero a veces es incomodo poner cada cosa en su lugar. Para estas situaciones aparece la propiedad `position`.

La propiedad `position` identifica como un elemento es posicionado en una pagina y si va a aparecer o no dentro del flujo normal del documento. Esta propiedad se utliza en conjunto con las propiedades de compensacion (box offset), que son `top`, `right`, `bottom`, y `left`, que identifican en donde va a ser posicionado. 

Es decir, con la propiedad `position` indicas el *como*, y con las direcciones indicas el *donde*.

Los elementos tienen por defecto esta propiedad seteada a `static`, lo que significa que el elemento fluye de forma normal dentro del documento y no acepta ninguna propiedad que les de direcciones. Este valor `static` suele ser sobreescrita por los valores `relative` y `absolute`, que vamos a ver ahora.

##### Relative Positioning

El valor `relative` de la propiedad `position` permite que el elemento aparesca en el flujo normal de la pagina, dejando espacio para un elemento al lado, pero no dejando que otros elementos lo rodee al elemento. Tambien permite que la posicion del elemento sea especificada con una de las propiedades *box offset*. 

Estas propiedades son individuales, y especifican la posicion del elemento. Se usan directamente diciendo la posicion. Fijate este ejemplo:

```html
<div>...</div>
<div class="offset">...</div>
<div>...</div>
```

```css
div {
  height: 100px;
  width: 100px;
}
.offset {
  left: 20px;
  position: relative;
  top: 20px;
}
```

Lo que esta haciendo es, primero dandole a todos los elementos un tamaño de 100x100, y luego decirle que su posicion sea relativa. Esto le permite utilizar las propiedades para cambiar su posicion. Entonces lo que hace es cambiarsela como quiere, le pone 20px arriba y 20 a la izquierda.

Este posicionamiento lo que hace es mover al elemento desde el lado que le indicas. Es decir, si le decis `top`, lo saca la cantidad de pixeles indicada del top, es decir, mueve hacia abajo. Asi con todos los lados, mueve desde el lado, hacia el contrario. Hace un pushing desde el lado indicado.

Ademas, como estamos usando `relative`, esto hace que los demas elementos alrededor no se puedan mover. Es decir, no tienen bloqueado el cambio en el flujo. Por lo tanto, estan quietos en su lugar, y el elemento que se puede puede hacer lo que quiera. Se puede hasta superponer, que los otros elementos se quedan es su lugar.

Es mas, eso es lo que esta pasando en el ejemplo de arriba. El elemento del medio esta tapando al de abajo.

##### Absolute Positioning

El valor `absolute` de la propiedad `position` difiere de la posicion relativa en que el elemento no aparece en el flujo normal del documento, y el espacio y posicion original del elemento no se preserva.

Tambien los elementos con posicion absoluta se mueven en relacion al elemento parent mas cercano que tenga posicion relativa. Y si este elemento parent que es relativo no existe, el elemento toma la referencia del `<body>`. 

```html
<section>
  <div class="offset">...</div>
</section>
```

```css
section {
  position: relative;
}
div {
  position: absolute;
  right: 20px;
  top: 20px;
}
```

La diferencia entre este y el anterior es que, primero, setea un elemento con posicion relativa para que contenga a otro que le va a poner posicion absoluta. Mientras que el elemento `<section>` esta metido en el flujo del documento, y su posicion puede cambiar para el lado que quieras dentro del espacio disponible, el otro elemento esta en una posicion absoluta. Esto significa que toma como referencia a su elemento contenedor, que es `<section>`, y se mueve con respecto a el. Es decir, cuando le pone al `<div>` posicion absoluta y lo mueve, en realidad le esta diciendo que se mueva con respecto a su lugar dentro de este elemento. Toma como referencia ese lugar. Por lo tanto, si le decis que se mueva 20px a la derecha, se va a mover 20px a partir de su posicion en el elemento `<section>`.

Ademas, esta posicion absoluta hace como que solo tome en cuenta a su elemento parent relativo. Como si ahora el elemento existiera dentro de esa caja nomas. Por eso es que no esta contenido en el flujo normal, y puede solapar a otros elementos porque no los tiene en cuenta.

##### Aclarando un poco

En realidad, si lo pensas, la posicion absoluta puede funcionar igual que la relativa, nada mas que hace que veas las cosas de otro lugar.

Igual empecemos un poco de mas atras. Primero que nada, cuando la posicion de un elemento es estatica, todos siguen lo que se llama *normal flow*. Esta es la propiedad que tienen todos los elementos por defecto. Si pones tres divs por ejemplo, uno abajo del otro, vas a obtener esto. Un bloque abajo del otro de forma normal. [Ejemplo 1](https://alistapart.github.io/code-samples/css-positioning-101/example_a.html).

Ahora, la posicion cuando es relativa, en realidad tambien se puede comportar igual que la estatita. Si uno setea todos los bloques con la posicion relativa, y los deja como estan, siguen siendo bloques estaticos. Pero ahora, que sea relativo te da la posibilidad de cambiar la posicion de estos bloques, haciendo que lo demas quede estatico. Todo continua con su flujo normal, y si cambias algo de lugar nada se acomoda a los cambios. [Ejemplo 2](https://alistapart.github.io/code-samples/css-positioning-101/example_c.html).

Por lo tanto, termina moviendose algo y todo se queda en su lugar. Ahora, pensa que pasaria si anido el segundo bloque dentro del primero. Es decir, hago algo asi:

```html
<div id="box_1"> 	
  <div id="box_2"></div> 
</div>
```

Lo que va a pasar es que va a haber dos bloques superpuestos en el primer bloque, y el tercero se pega al primero. Ahora pensa que pasaria si lo corro para la derecha. Tendriamos una posicion absoluta (hecha con una relativa). El tema es que este bloque lo movemos de forma independiente. Sigue siendo relativo. [Ejemplo 3](https://alistapart.github.io/code-samples/css-positioning-101/example_d.html).

Esto es lo mismo que se podria hacer con un bloque que es absoluto, dentro de otro bloque relativo. Lo que haces es moverlo con respecto al contenedor. Si ese contenedor es el cubo de arriba, podes lograr lo mismo que en ejemplo 3, diciendole que se mueva con respecto a ese cubo.

El tema es que uno lo esta pensando con cubos chicos, pero imaginate que lo podes hacer con referencia al `<body>`, es decir, los cubos terminan siendo como cubos reales con un coso de belcro atras, los agarras y los pegas donde queres. Porque no estan ligados a nada, a ningun flujo. Son independientes. Por ejemplo podes agarrar cuatro cubos anidados en el `<body>` y asignarles:

```css
#box_1 { 
	position: absolute;
	top: 0;
	left: 0;
	width: 200px;
	height: 200px;
	background: #ee3e64;
}
#box_2 { 
	position: absolute;
	top: 0;
	right: 0;
	width: 200px;
	height: 200px;
	background: #44accf;
}
#box_3 { 
	position: absolute;
	bottom: 0;
	left: 0;
	width: 200px;
	height: 200px;
	background: #b7d84b;
}
#box_4 { 
	position: absolute;
	bottom: 0;
	right: 0;
	width: 200px;
	height: 200px;
	background: #ebde52;
}
```

Todos son absolutos, entonces los podes mover por toda la pantalla controlando su ubicacion con las propiedades offset. [Ejemplo 4](https://alistapart.github.io/code-samples/css-positioning-101/example_e.html). Ahi los pone en cada esquina de la pantalla. Hace la prueba de redimensionar la pantalla y fijate que pasa.

Lo que va a pasar es que se mueven con la pantalla, porque estan pegados. No siguen el flujo del documento. Estan en una posicion absoluta dentro del documento. Muevas como muevas, van a seguir ahi. Esto se logra poniendolos absolutos con respecto a su elemento parent (el `<body>`, que representa a toda la pantalla).

Esto que se crea se llama sistema de coordenadas, es decir, se crea un sistema, un mundo propio alrededor del elemento que los contiene. Por ejemplo, aca mete cajas con posicion absoluta dentro de las cajas, y que pasa, se quedan absolutas dentro de la caja. [Ejemplo 5](https://alistapart.github.io/code-samples/css-positioning-101/example_f.html).

Este comportamiento te da lugar a implementar muchas cosas mas, y a jugar con cosas relativas y absolutas. Asi por ejemplo, podemos poner algo en la pantalla y que se redimensione cuando esta se mueva. [Ejemplo 6](https://alistapart.github.io/code-samples/css-positioning-101/example_g.html). Y esto se hace muy facil, porque solo definis dos divs, uno dentro del otro, y los dos dentro del body. Y ya esta, si tienen posicion absoluta, se mantienen siempre en la misma posicion. Se mueve el cuadrado exterior con respecto a la pantalla, y el interior con respecto al exterior.

```css
#box_a { 
	position: absolute; 
	top: 10px;
	right: 10px;
	bottom: 10px;
	left: 10px; 
	background: red; 
}
#box_b { 
	position: absolute; 
	top: 20px;
	right: 20px; 
	bottom: 20px; 
	left: 20px; 
	background: white;
}
```

O ponele, podes hacer una barra lateral que se quede estatica siempre. [Ejemplo 7](https://alistapart.github.io/code-samples/css-positioning-101/example_h.html). Y es lo mismo, pero aca ambos divs con posiciones absolutas con respecto al body. La barra tiene un 20% del body para un costado, y todos los demas en 0 porque ocupan todo el body, y el otro div seria lo que queda, igual que el anterior, pero el lado opuesto con un 80%.

```css
#box_1 { 
	position: absolute;
	top: 0;
	right: 20%; 
	bottom: 0;
	left: 0;
	background: #ee3e64;
}

#box_2 { 
	position: absolute; 
	top: 0; 
	right: 0; 
	bottom: 0; 
	left: 80%; 
	background: #b7d84b;
}
```

Ojo, igual esto no significa que sea la mejor aproximacion a un *two-columns layout*, pero muestra un poco del poder que tiene.

##### Fixed Positioning

Ahora, no son los unicos esos dos. Hay dos mas.

El valor `fixed` para la propiedad `position` tiene las mismas relgas que se cumplen para un elemento con posicion absoluta. La unica diferencia es que la posicion fija deja al elemento inmovil en la pantalla, sin importar si uno scrollea.

Por ejemplo, hay paginas que poseen barras de navegacion en la parte superior que estan fijas. Es decir, po mas de que escrollees hacia abajo, la barra se mantiene en el mismo lugar. 

```css
#box_2 {
	position: fixed; 
	bottom: 0; 
	left: 0; 
	right: 0; 
}
```

Las propiedades `left` y `right`, seteandolas a 0, hacen que el ancho del elemento ocupe toda la pantalla, adaptandose a cualquier estilo. Ademas, el `bottom` en 0 le dice que lo quiere siempre pegado al fondo, porque es un footer. Es decir, en este caso funciona para aportar informacion de copyright. [Ejemplo 8](https://alistapart.github.io/code-samples/css-positioning-101/example_i.html). Nota que te moves y se queda fijo abajo.

Otra cosa a tener en cuenta es que la posicion fija no funciona en las versiones mas viejas de los navegadores, porque los toma como estaticos. En ese caso, el footer seguiria abajo, pero cuando te moves se queda en su lugar. Aunque hay soluciones para hacer que funcione es estos browsers. 

Otro ejemplo en [esta pagina](https://developers.google.com/), en donde si vas a la DevTools y clickeas en la barra de arriba (elemento `<devsite-header ...>`), asi se puede ver en los estilos que tiene puesta la posicion en `fixed`.

##### Inherit Positioning

Este valor es simplemente para indicar que queres que el elemento herede el mismo valor de la propiedad `position` de su elemento parent. Es decir, es lo mismo usar este valor a poner el mismo valor del elemento parent.

##### IN ACTION

Bueno, finalmente para dar una conclusion a todo esto, vamos a mostrar un ejemplo de una pagina que reune cada una de las posiciones que vimos en esta seccion.

Este [Ejemplo 9](https://alistapart.github.io/code-samples/css-positioning-101/example_j.html) muestra un tipico layout de una pagina que contiene un header, un navegador, contenido y un footer. 

Empecemos por el elemento `#container`, que simplemente tiene la funcion de centrar el contenido dentro de la ventana que se ve en la pagina. El elemento que le sigue es el `#nav` que representa el navegador de la pagina, es decir, el lugar en donde se encuentran los hipervinculos mas importantes. A este elemento no se le necesita asignar un valor a la posicion, y por lo tanto su valor queda por defecto en `static`. Esto ocurre porque la barra esta bien en el lugar donde esta, manteniendo el flujo normal de la pagina.

Ahora, si entramos dentro del elemento `#nav` podemos ver que estan todos los hipervinculos. Y si clieckeamos en uno de ellos, vemos que la forma que utilizaron para colocarlos uno al lado del otro fue haciendo floating. Agarra y le pone a todos los a dentro de #nav un float left, como ya vimos que se hacia para mas de dos elementos.

Luego sigue el contenido principal `#content`, que le pusieron posicion relativa. En realidad esa posicion relativa no tiene ninguna diferencia a una estatica, porque no tienen offsets, solo se pone para que sea elemento con posicion relativa contenedor del elemento `#callout`, que se puede ver que esta anidado dentro. Se pone para crear un nuevo sistema de coordenadas. Por lo tanto, ese elemento callout se setea a una posicion absoluta, asi se crea ese nuevo sistema y se puede controlar el callout solo haciendo referencia al content.

Es muy loco que ese elemento #callout sea en realidad parte del contenido, pero lo que hacen es empujarlo desde la izquierda hacia el costado 80px. Como tiene posicion absoluta con respecto al content, este se mueve 80px para la derecha en referencia a el contenido. Esto se logra poniendo un offset `right: -80px`, de forma que tire desde la derecha, para la derecha. Resultado final, lo terminan sacando de su elemento parent.

Otra cosa piola es que, para darle ese tamaño vertical, lo empuja al elemento 100px por arriba y por abajo, tomando el mismo tamaño que su elemento parent, que es el contenido, menos los 100 de cada lado.

Ademas, como el #callout es absoluto, no afecta nada de lo que toca. Tambien, le meten un padding derecho al contenido, para que el callout no lo tape. 

Por ultimo, meten un footer y le ponen posicion fija, para que cuando se scrollee quede en el mismo lugar. Esto lo hacen poniendo un div de manera normal para diferenciar el bloque de los demas, y lo pegan al fondo con bottom: 0. Ademas, tienen que levantar un poco el padding del contenido para que no quede abajo del footer.

Por ultimo, lo que quiero notar es que ningun elemento div necesita toquetear los espacios laterales, ya que como esta metido dentro de un container que tiene seteado el margen como ellos quieren. Entonces, todo elemento anidado se acomoda a los limites que setearon. Asi te ahorras centrar a todos los elementos.

Esta es la razon por la que siempre se usan tantos divs en las paginas, para poder meter todo en cajas y organizar mejor.



### Conclusion

Espero que todo esto nos haya dejado mejor parados en lo que es el layout de CSS. Ya estan cerrando mas las cosas. Ahora la idea es tener mucha practica, y con tiempo vamos a manejar todos estos conceptos muy bien.