# Creating Lists

HTML ofrece tres clases de listas para utilizar. Estas son, las listas ordenadas, las no ordenadas y las descriptivas. Elegir una sobre la otra, o elegir una lista basicamente, depende del contenido y de la semantica mas apropiada para mostrar ese contenido.

Ademas, CSS ofrece varias formas de darle estilos a las listas. Como por ejemplo cambiar el indicador de cada item, ponerlo en forma circular, cuadrada, o usar numeros, letras, o sacarlo directamente. Tambien permite cambiar la orientacion de la lista, si queremos que aparesca de forma vertical u horizontal.



### Unordered List

Una lista no ordenada (unordered) es una lista en la cual no nos importa el orden de los elementos. Se puede definir con el elemento en bloque `<ul>`, y cada item en la lista se coloca con el elemento `<li>`, que viene de "list item".

Por defecto el browser lo que hace es colocar un margen superior, para separar la lista un poco del elemento de arriba, y tambien lo que hace es agregar un padding en la parte izquierda. El marcador que utiliza por defecto en este tipo de lista es un punto, que luego se puede cambiar en CSS.

Seria lo mismo que pasa aca, cuando hago una lista:

- Esto es un item de la lista no ordenada.

Notar que pone un margen que separa del parrafo de arriba, y coloca un padding a la izquierda.

```html
<ul>
  <li>Orange</li>
  <li>Green</li>
  <li>Blue</li>
</ul>
```

El resultado de esto es la siguiente lista:

- Orange
- Green
- Blue



### Ordered List

La lista ordenada es muy parecida a la no ordenada, salvo que aca si importa el orden. Es por esta razon que en vez de haber puntos como marcador, se utilizan numeros en su forma default. Se utiliza el elemento `<ol>` para definirla.

```html
<ol>
  <li>Head north on N Halsted St</li>
  <li>Turn right on W Diversey Pkwy</li>
  <li>Turn left on N Orchard St</li>
</ol>
```

El resultado de esta lista es el siguiente:

1. Head north on N Halsted St
2. Turn right on W Diversey Pkwy
3. Turn left on N Orchard St

Ademas las listas no odenadas admiten dos atributos, que son `start` y `reversed`.

##### Start Attribute

El atributo `start` indica el numero entero con el cual empieza la numeracion de los items de la lista. Por defecto esta seteado a 1, pero se puede poner cualquiera que convenga.

```html
<ol start="30">
  <li>Head north on N Halsted St</li>
  <li>Turn right on W Diversey Pkwy</li>
  <li>Turn left on N Orchard St</li>
</ol>
```

El resultado de esto es una lista como esta:

30. Head north on N Halsted St
31. Turn right on W Diversey Pkwy
32. Turn left on N Orchard St

##### Reversed Attribute

El atributo `reversed` indica simplemente si se quiere que los indices de la lista esten en orden inverso. Es un atributo que se coloca solo, no lleva valor. 

Por ejemplo, si se pusiera una lista del `1` al `5`, con este atributo asignado iria del `5` al `1`.

```html
<ol reversed>
  <li>Head north on N Halsted St</li>
  <li>Turn right on W Diversey Pkwy</li>
  <li>Turn left on N Orchard St</li>
</ol>
```

##### Value Attribute

El atributo `value` pertenece al elemento list item `<li>`, dentro de una lista ordenada. Lo que hace es definir el valor del indice de ese elemento de la lista, y hacer que todos los demas valores por debajo de ese elemento sigan a partir de ese valor. 

```html
<ol>
  <li>Head north on N Halsted St</li>
  <li value="9">Turn right on W Diversey Pkwy</li>
  <li>Turn left on N Orchard St</li>
</ol>
```

Lo que va a pasar en este ejemplo es algo asi:

1. Head north on N Halsted St

9. Turn right on W Diversey Pkwy

10. Turn left on N Orchard St



### Description List

Otro tipo de lista que suele aparecer, aunque no tan seguido como las listas ordenadas y no ordenadas, es la llamada "description list". Esta lista permite contornar terminos y sus descripciones, como en un glosario.

Para poder utilizarla, usamos el elemento en bloque `<dl>`, y en vez de usar un `<li>` para describir los items, tenemos que utilizar dos elementos en bloque mas. Uno es el elemento "description term" `<dt>`, y el otro es el "description element" `<dd>`.

Estos dos terminos son necesarios porque la lista en este caso no tiene marcadores, si no que es una lista de terminos, con sus descripciones debajo. Una termino puede contener mas de una descripcion, y al mismo tiempo una descripcion puede contener mas de un termino.

```html
<dl>
  <dt>study</dt>
  <dd>The devotion of time and attention to acquiring knowledge on an academic subject, especially by means of books</dd>
  <dt>design</dt>
  <dd>A plan or drawing produced to show the look and function or workings of a building, garment, or other object before it is built or made</dd>
  <dd>Purpose, planning, or intention that exists or is thought to exist behind an action, fact, or material object</dd>
  <dt>business</dt>
  <dt>work</dt>
  <dd>A person's regular occupation, profession, or trade</dd>
</dl>
```

Lo que va a hacer esto es poner como termino, que es un titulo para la descripcion, y separar con un margen izquierdo la descripcion de ese termino. 



### Nesting Lists

Una propiedad que poseen las listas es que pueden ser anidadas. Esto es algo que hace a las listas una herramienta muy potente. Pero aun asi eso no significa que se puedan usar asi nomas, si no que siempre hay que pensar en su valor semantico. Todo tiene un porque.

Cuando se quiere anidar una lista, lo que hay que hacer es ponerla dentro de uno de sus `<li>`. Asi va a aparecer una segunda lista dentro de uno de los elementos de la anterior. Se suele usar para listar ordenadas y no ordenadas.

En cuanto al porque de su uso, puede ser porque un elemento tiene mas de una posibilidad, o se quieren enlistar varios casos para un elemento dentro de la lista. Es la decicion de uno si estos tienen orden de importancia o no.

```html
<ol>
  <li>Walk the dog</li>
  <li>Fold laundry</li>
  <li>
    Go to the grocery and buy:
    <ul>
      <li>Milk</li>
      <li>Bread</li>
      <li>Cheese</li>
    </ul>
  </li>
  <li>Mow the lawn</li>
  <li>Make dinner</li>
</ol>
```

Ademas, segun el nivel de anidado en que este la nueva lista, tal vez le cambien los marcadores que usa. En el ejemplo de arriba, utiliza unos marcadores blancos, en vez de negros. Estos corresponden a la segunda anidacion de una lista como aca:

- Primera lista
- Primera lista
  - Segunda lista

Claro que tenemos el control sobre estos marcadores, en nuestra hoja de estilos.



### List Item Styling

Por lo general las listas ordenadas bienen con numeros como marcadores por defecto, y las listas no ordenadas vienen con puntos solidos. Estos valores pueden ajustarse desde CSS.

##### List Style Type Property

La propiedad `list-style-type` te permite elegir un marcador para una lista. Hay muchos tipos diferentes de marcadores disponibles, desde puntos, cuadrados y otras figuras, hasta numeros y numeros armenios. 

Esta propiedad no distingue por tipo de lista, por lo tanto puede ser aplicada a ambas, ordenada y no ordenada. Esto quiere decir que, le podriamos asignar un marcador no numerico a una lista ordenada, y uno numerico a una no ordenada.

```html
<ul>
  <li>Orange</li>
  <li>Green</li>
  <li>Blue</li>
</ul>
```

```css
ul {
  list-style-type: square;
}
```

##### List Style Type Values

| List Style Type Value       | Content                                 |
| :-------------------------- | :-------------------------------------- |
| `none`                      | No list item                            |
| `disc`                      | A filled circle                         |
| `circle`                    | A hollow circle                         |
| `square`                    | A filled square                         |
| `decimal`                   | Decimal numbers                         |
| `decimal-leading-zero`      | Decimal numbers padded by initial zeros |
| `lower-roman`               | Lowercase roman numerals                |
| `upper-roman`               | Uppercase roman numerals                |
| `lower-greek`               | Lowercase classical Greek               |
| `lower-alpha / lower-latin` | Lowercase ASCII letters                 |
| `upper-alpha / upper-latin` | Uppercase ASCII letters                 |
| `armenian`                  | Traditional Armenian numbering          |
| `georgian`                  | Traditional Georgian numbering          |

##### Using an Image as a List Item Marker

Hay casos en que no queremos utilizar los marcadores disponibles, y en cambio queremos uno personalizado. 

Esto se puede lograr asignando una imagen de fondo al elemento `<li>`, y ademas sacandole su marcador por default. Es decir, la propiedad `list-style-type` tiene que estar en `none`. Ademas le tenes que poner un padding al elemento. Recordar que la imagen no se ve afectada por el padding del elemento, por su valor por default para cubrir el padding.

```html
<ul>
  <li>Orange</li>
  <li>Green</li>
  <li>Blue</li>
</ul>
```

```css
li {
  background: url("arrow.png") 0 50% no-repeat;
  list-style-type: none;
  padding-left: 12px;
}
```

Notar que le agrega la imagen del background, la posiciona y le dice que no se repita. Luego saca el marcador por defecto y le pone un padding. El resultado termina siendo un marcador con una flecha.

##### List Style Position Property

Hay tres posibles valores para la propiedad `list-style-position`, que son `outside`, `inside` y `inherit`. El valor `outside` es el que esta por defecto en las listas, y lo que hace es imprimir el marcador a la izquierda del elemento, dejando el contenido a la derecha. Todo el contenido se mantiene en una misma linea vertical, es decir, nada puede envolver al marcador.

En cambio, el valor `inline` lo que hace es permitir que el contenido recubra al marcador, pudiendo estar tambien debajo de este. Esto es rara vez usado, ya que da mucha mas prolijidad y organizacion el valor outline. Deja ver mucho mas el concepto de que eso es una lista. En cambio el segundo parece como si fuera un texto normal, pero con un punto al principio.

##### Shorthand List Style Property

Y la propiedad para darle estilos a las listas tambien tiene su version en shorthand, de la forma `list-style`. El orden de los valores corresponden al `list-style-type` y `list-style-position`. 

Realmente esta es la propiedad que vas a estar usando constantemente, ya que rara vez uses la propiedad para cambiar la posicion. Por lo tanto, al final terminas usando esta propiedad `list-syle` como equivalente a la `list-style-type`. Aunque tenes que tener en cuenta que siempre admite un segundo valor.

```css
ul {
  list-style: circle inside;
}
ol {
  list-style: lower-roman;
}
```



### Horizontally Displaying List

Hay veces en que surge la necesidad de presentar los elemtos de una lista de forma horizontal, ya sea porque, por ejemplo, queres crear una lista de navegacion, o queres poner los elementos uno al lado de otro en una fila. Esto ultimo suele pasar cuando los elemetnos son chicos, y suelen entrar mas de uno por fila.

Dependiendo que se quiera lograr hay varias formas de hacerlo. Una es cambiando la propiedad `display` de los elementos list item a `inline` o `inline-block`, o si no tambien haciendoles floating.

##### Displaying List

Una de las formas principales para lograr poner los elementos de forma horizontal es poniendo su propiedad `display` en `inline` o `inline-block`. Con este valor, lo que hace es setear a los elementos `<li>` en una linea sola, con un espacio separandolos entre ellos.

Parece ser una forma muy simple de poder hacer una barra de navegacion. Le pones un margen izquierdo y ya esta, los separas  queda. Realmente es muy simple.

Acordate que las propiedades de lista van sobre el elemento de la lista `<ul>` o `<ol>`, pero el display va sobre los list item `<li>`.

Si los espacios entre elementos son problematicos, los podemos eliminar como ya vimos antes.

Es mas usual que le pongamos el valor `inline-block` a los elementos, antes que el valor `inline`, ya que de la primer forma, tenemos la posibilidad de colocarle margenes superior e inferior, cosa que con el valor inline no es posible.

Ademas, cuando cambiamos el display de los elementos, los marcadores desaparecen solos. No es necesario sacarselos.

```html
<ul>
  <li>Orange</li>
  <li>Green</li>
  <li>Blue</li>
</ul>
```

```css
li {
  display: inline-block;
  margin: 0 10px;
}
```

##### Floating List

Cambiar la propiedad `display` de los elementos es algo muy rapido y sencillo si, por ejemplo, se quiere hacer una barra de navegacion. Pero en caso de que se quieran conservar los marcadores, no podemos usar este metodo porque se borran. Por lo tanto, en estos casos en que se quieren conservar los marcadores, es mejor hacerles floating a los elementos.

Esto se hace, como ya vimos (floating para mas de dos elementos), poniendo un float left para todos los elementos. Esto hace que los ponga uno al lado del otro en una linea horizontal, dejando sus marcadores intactos.

Puede que los marcadores superpongan al texto del anterior elemento, por lo tanto, un margen o padding tiene que añadirse si o si.

```html
<ul>
  <li>Orange</li>
  <li>Green</li>
  <li>Blue</li>
</ul>
```

```css
li {
  float: left;
  margin: 0 20px;
}
```

Recorda que, hacer floating sobre un elemento corta el flujo de los elementos en la pagina. Por lo tanto, podrias hacer un clearfix, es decir, utilizar un elemento contenedor div, hacer el floting dentro, y hacer un clearing con el elemento `:after`. Y luego hacer clearing por fuera.

Si no lo recordas bien, es comun, volve a la leccion que lo vimos y pasale una leida.



#### Example

Muy seguido se ven a menus de navegacion hechos mediante una lista no ordenada, es muy comun. Se podria hacer esto con las dos tecnicas que vimos, sacandole el estilo a la lista.

Este ejemplo esta hecho poniendo a los elementos en `inline-block`.

```html
<nav class="navigation">
  <ul>
    <li><a href="#">Profile</a></li><!--
    --><li><a href="#">Settings</a></li><!--
    --><li><a href="#">Notifications</a></li><!--
    --><li><a href="#">Logout</a></li>
  </ul>
</nav>
```

```css
.navigation ul {
  font: bold 11px "Helvetica Neue", Helvetica, Arial, sans-serif;
  margin: 0;
  padding: 0;
  text-transform: uppercase;
}
.navigation li {
  display: inline-block;
}
.navigation a {
  background: #395870;
  background: linear-gradient(#49708f, #293f50);
  border-right: 1px solid rgba(0, 0, 0, .3);
  color: #fff;
  padding: 12px 20px;
  text-decoration: none;
}
.navigation a:hover {
  background: #314b60;
  box-shadow: inset 0 0 10px 1px rgba(0, 0, 0, .3);
}
.navigation li:first-child a {
  border-radius: 4px 0 0 4px;
}
.navigation li:last-child a {
  border-right: 0;
  border-radius: 0 4px 4px 0;
}
```

Yo pense que los elementos tenian un gradiente lineal de top a bottom, y un gradiente radial en hover, pero no resulta que es un box shadow pero en forma inline, es decir, se mete a dentro del elemento. Ambas opciones eran viables.

Notar tambien que a los anchor solo le pone un borde a la derecha, para hacer la division. Pero luego le indica al ultimo a que ese borde sea nulo, para que no quede feo al final. Esto lo hace agregandole al selector un `:last-child`. Luego le pone un radius solo en la parte derecha, arriba y abajo, que es lo mismo que hace en la parte iquierda, con el primer anchor.

El resultado es una barra de navegacion muy linda, con anchor que parecen realmente botones. Esto se logra con el hover, y cambiando los gradientes. Aca se puede ver cuanto afecta un buen gradiente a la profundidad y el diseño de una pagina.

