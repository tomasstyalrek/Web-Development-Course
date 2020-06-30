# Tables

Las tablas en HTML son una forma de orgaizacion de datos que es util para presentar relaciones entre los mismos. Hay columnas y filas como en cualquier tabla, y entre ellas se disponen celdas en donde se pueden colocar datos.

En un momento, cuando CSS no existia, las tablas se utilizaban para darle estructura y posicionar contenido en una pagina. Es algo muy curioso, ya que no se disponia en ese momento de propiedades para elegir la ubicacion de los elementos en la pantalla, por lo tanto se debian crear tablas y asi asignar en las celdas los elementos. Esto funcionaba, claro, pero no es para lo que se crearon las tablas en un principio, y por eso llevaban a muchos otros problemas.

Pero hoy en dia, las cosas son un poco mejores. Las tabla se utilizan por lo general para lo que se diseñaron. Para presentar un arreglo de datos.



### Creating a Table

Las tablas estan compuestas por datos contenidos dentro de filas y columnas. En HTML una tabla basica debe estar formada por el elemento `<table>`, para definir su estructura. Luego tenes el elemento `<tr>` (table row), el `<td>` (table data), para definir su contenido y estructura interna. Y luego para una mejor estructura y un mayor valor semantico, se puede incluir el `<th>` (table header) y otros elementos mas, y asi formar una tabla solida.

##### Table

El elemento `<table>` es el inicializador de la tabla. Usando este elemento le indicamos al documento que dentro se va a disponer la informacion en forma de tabla, es decir, en columnas y filas.

```html
<table>
  ...
</table>
```

Este elemento solo conforma la inicializacion, y no representa ningun tipo de tabla grafica.

##### Table Row

Una vez definida o inicializada la tabla, se pueden ir agregando filas a la tabla utilizando el elemento `<tr>`. La cantidad de filas que se puede crear son bastantes.

```html
<table>
  <tr>
    ...
  </tr>
  <tr>
    ...
  </tr>
</table>
```

##### Table Data

El elemento `<td>` crea los datos en cada celda de la tabla, asi creando columnas por cada dato que se añade. Este elemento se coloca dentro de la fila, y de esta manera va enlistando las celdas una al lado de la otra.

```html
<table>
  <tr>
    <td>Don&#8217;t Make Me Think by Steve Krug</td>
    <td>In Stock</td>
    <td>1</td>
    <td>$30.02</td>
  </tr>
  <tr>
    <td>A Project Guide to UX Design by Russ Unger &#38; Carolyn Chandler</td>
    <td>In Stock</td>
    <td>2</td>
    <td>$52.94 ($26.47 &#215; 2)</td>
  </tr>
  <tr>
    <td>Introducing HTML5 by Bruce Lawson &#38; Remy Sharp</td>
    <td>Out of Stock</td>
    <td>1</td>
    <td>$22.23</td>
  </tr>
  <tr>
    <td>Bulletproof Web Design by Dan Cederholm</td>
    <td>In Stock</td>
    <td>1</td>
    <td>$30.17</td>
  </tr>
</table>
```

Hay que tener en cuenta que para que la informacion que pones en la tabla sea realmente legible, debemos darle un estilo con CSS antes. Porque si probas el anterior ejemplo en el browser, se imprime una tabla blanca, sin ningun tipo de lineas divisoras que marquen las filas y columnas ni nada.

##### Table Header

Un header se puede asignar para una columna o fila para aclarar y organizar mejor el contenido de una tabla. Ademas añade valor semantico a la tabla. Esto se puede lograr con el elemento `<th>`.

Hay dos maneras de utilizar este elemento, y estas son para darle un heading a una columna o a una fila. Si se quisiera darle un header a las columnas, entonces uno tendria que crear una fila superior que sea solo de elementos header. Poniendo la misma cantidad de headers que de columnas haria que cada uno se asigne a cada columna.

La otra forma poner el elemento por encima de los elementos `<td>`, y asi crear en la primer columna, una columna solo de headers que asignen a cada fila un header.

Igualmente existe un atributo que siempre se suele usar, que es `scope`. Esto nos permite colocarle el valor `col` y asi hacer referencia a una columna, o el valor `row` y hacer referencia a las filas. Son solo valores para asignar el contenido.

Usar este atributo del elemento `<th>` es algo muy valioso para la semantica de la pagina.

```html
<table>
  <tr>
    <th scope="col">Item</th>
    <th scope="col">Availability</th>
    <th scope="col">Qty</th>
    <th scope="col">Price</th>
  </tr>
  <tr>
    <td>Don&#8217;t Make Me Think by Steve Krug</td>
    <td>In Stock</td>
    <td>1</td>
    <td>$30.02</td>
  </tr>
  <tr>
    <td>A Project Guide to UX Design by Russ Unger &#38; Carolyn Chandler</td>
    <td>In Stock</td>
    <td>2</td>
    <td>$52.94 ($26.47 &#215; 2)</td>
  </tr>
  <tr>
    <td>Introducing HTML5 by Bruce Lawson &#38; Remy Sharp</td>
    <td>Out of Stock</td>
    <td>1</td>
    <td>$22.23</td>
  </tr>
  <tr>
    <td>Bulletproof Web Design by Dan Cederholm</td>
    <td>In Stock</td>
    <td>1</td>
    <td>$30.17</td>
  </tr>
</table>
```

El browser por defecto le va a poner al heading una letra negrita y va a centrar el contenido.

Otra manera de asignar headers es hacerlo desde la celda hacia el header, con el atributo `headers`. Es decir, si se quiere asignar una celda, ya sea un elemento `<td>` o `<th>`, a un header, se puede utilizar este atributo. Este atributo necesita que le pasemos el valor del id del header al que queremos asociar la celda.



### Table Structure

Entender el funcionamiento de una tabla, y como organizar datos dentro, es una herramienta muy potente. Claro que, como todo en este mundo, se puede seguir adentrandose en mas teoria sobre como utilizar a la perfeccion las tablas. 

Pero bueno, nosotros solo vamos a ver algunos elementos mas que nos van a ayudar a estructurar mejor las tablas. Si se quiere seguir viendo mas cosas, (este)[https://www.456bereastreet.com/archive/200410/bring_on_the_tables/] es un buen blog sobre eso.

Entre estos elementos, vamos a ver a `<caption>`, `<thead>`, `<tbody>` y `<tfoot>`.

##### Table Caption

El elemento `<caption>` se utiliza para darle a la tabla un titulo o anotacion. Se utiliza para que el usuario sepa de que se trata la tabla o que tipo de datos puede encontrar ahi. El elemento se coloca luego del elemento `<table>`, es decir, luego de inicializar la tabla. Ademas, se coloca por defecto en la parte superior, como un titulo para la tabla.

```html
<table>
  <caption>Design and Front-End Development Books</caption>
  ...
</table>
```

##### Table Head, Body & Foot

Ademas, una tabla puede ser descompuesta en su estructura en tres partes, que son un head, un body y un foot. Los elementos correpondientes a estructurar cada parte de la tabla son el `<thead>` (table head), el `<tbody>` (table body), y el `<tfoot>` (table foot).

El elemento `<thead>` es utilizado para agrupar todas las celdas que componen el encabezado de la tabla, ya sea la fila principal con los headers de cada columna, o todo lo que se considere parte del encabezado de una tabla. Va situado por debajo del elemento `<caption>` y por encima del elemento `<tbody>`.

Luego, los elementos `<tbody>` y `<tfoot>` deben situarse por debajo del header de la tabla. En algun momento, el `<tfoot>` debia estar estrictamente debajo del `<thead>`, pero en HTML5 dejo de ser asi. Ahora hay libertad para ponerlo como quieras.

Aunque por lo general, el `<tbody>` es utilizado para contener el cuerpo o contenido principal de la tabla, mientras que el `<tfoot>` se usa para contener los datos que describen el contenido de la tabla.

```html
<table>
  <caption>Design and Front-End Development Books</caption>
  <thead>
    <tr>
      <th scope="col">Item</th>
      <th scope="col">Availability</th>
      <th scope="col">Qty</th>
      <th scope="col">Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Don&#8217;t Make Me Think by Steve Krug</td>
      <td>In Stock</td>
      <td>1</td>
      <td>$30.02</td>
    </tr>
    ...
  </tbody>
  <tfoot>
    <tr>
      <td>Subtotal</td>
      <td></td>
      <td></td>
      <td>$135.36</td>
    </tr>
    <tr>
      <td>Tax</td>
      <td></td>
      <td></td>
      <td>$13.54</td>
    </tr>
    <tr>
      <td>Total</td>
      <td></td>
      <td></td>
      <td>$148.90</td>
    </tr>
  </tfoot>
</table>
```

Realmente esto no provoca un cambio visual, si no que esta destinado a la semantica.

##### Combining Multiple Cells

Hay ocaciones en que se necesita combinar celdas de datos en una sola celda, ya sea por propositos de estilo, o porque hay celdas nulas o con los mismos datos mas de una vez. 

Para realizar esto se utilizan los atributos `colspan` y `rowspan`, que funcionan en los elementos `<td>` y `<th>`. Recorda que estos dos elementos son los unicos que crean realmente las celdas, ya que el `<tr>` es mas estructural que otra cosa. Es por esto que estos atrivutos no funcionan con este ultimo.

El atributo `colspan` se utiliza para expandir o combinar una celda a travez de multiples columnas en una tabla, mientras que el atributo `rowspan` se utiliza para expandir la celda a travez de multimples filas. Estos atributos aceptan un valor entero, que indica la cantidad de celdas a expandirse. Esta por defecto en 1.

En otras palabras, el `colspan` extiende la celda de forma horizontal, mientras que la otra de forma vertical.

```html
<table>
  <caption>Design and Front-End Development Books</caption>
  <thead>
    <tr>
      <th scope="col" colspan="2">Item</th>
      <th scope="col">Qty</th>
      <th scope="col">Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Don&#8217;t Make Me Think by Steve Krug</td>
      <td>In Stock</td>
      <td>1</td>
      <td>$30.02</td>
    </tr>
    ...
  </tbody>
  <tfoot>
    <tr>
      <td colspan="3">Subtotal</td>
      <td>$135.36</td>
    </tr>
    <tr>
      <td colspan="3">Tax</td>
      <td>$13.54</td>
    </tr>
    <tr>
      <td colspan="3">Total</td>
      <td>$148.90</td>
    </tr>
  </tfoot>
</table>
```

Lo que se hizo aca fue sacar uno de los headers, quedando la celda del header vacia en esa columna. Por lo tanto, se puso el colspan=2, y ahora rellena dos columnas el anterior header.

SI lo corres en el doc, vas a ver como se centra el contenido para abarcar ambas columnas.



### Table Borders

Un correcto uso de bordes en las tablas puede lograr una organizacion y entendimiento mejor de los datos en ella. Cuando se tienen que modificar los bordes con CSS, hay dos propiedades que son muy utiles: `border-collapse` y `border-spacing`.

##### Border Collapse Property

Las tablas, como ya vimos, estan formadas por un elemento parent `<table>` y luego, sus datos formados por `<td>` y `<th>`. Cuando uno le asigna un tamaño a los bordes, por ejemplo, lo que va a pasar es que lo va a asignar a todos los bordes de las celdas, por lo tanto el contorno de la tabla va a quedar bien, pero entre celdas no. Entre celdas los que va a pasar es que se van a sumar ambos bordes, quedando un borde del doble del ancho que los bordes de la tabla asignados.

Por esto es que existe la propiedad `border-collapse`, para poder indicarle a los bordes que se unan, asi lo que se asigna es lo que termina poniendose en la tabla. Tiene tres valores posibles, `collapse`, `separate` y `inherit`. Por defecto esta puesto el `separate`, que deja los bordes separados entre si, acumulando los anchos. Pero, por otro lado, el valor `collapse` va a condensar los bordes de las celdas en uno solo.

```css
table {
  border-collapse: collapse;
}
th,
td {
  border: 1px solid #cecfd5;
  padding: 10px 15px;
}
```

Como se puede ver, la propiedad se asigna a toda la tabla, y es aplicada a cada borde de toda celda. El padding que pone se aplica en cada celda para distanciar el contenido del borde.

##### Border Spacing Property

Al contrario de la propiedad `border-collapse`, que junta los bordes en uno solo, la propiedad `border-spacing` determina el espacio entre celdas.

Aca pasa lo mismo que antes. Si lo quesieramos hacer manualmente, lo de asignar un margen para separar las celdas, se acumularian los espacios. En cambio, si usamos esta propiedad se asigna exactamente lo que queremos.

```css
table {
  border-collapse: separate;
  border-spacing: 4px;
}
table,
th,
td {
  border: 1px solid #cecfd5;
}
th,
td {
  padding: 10px 15px;
}
```

Lo que termina haciendo esto es, tener un borde principal de contorno de la tabla, y por separado cada celda tiene su borde y se separa de los bordes. Por lo tanto terminan quedando todas casillas separadas.

Una cosa a notar es que, solo podemos usar esta propiedad si la propiedad `border-collapse` esta en `separate`. Pensa que si colapsas los bordes, se vuelven uno solo y no hay forma de separarlos.

Ademas hay que tener en cuenta que se pueden asignar los bordes en dos partes. Una corresponde al espacio horizontal y el otro al vertical. Como por ejemplo en la declaracion `border-spacing: 5px 10px;`.

##### Adding Borders to Rows

Si quisieramos poner un borde entre filas, hay algunas cosas que tenemos que hacer, ya que no es posible asignar bordes a elementos estructurales como el `<tr>`. 

Lo primero que tenemos que hacer es poner a la tabla entera la propiedad `border-collapse`, para asegurarnos de que no se repitan los bodes. Luego lo que hacemos es asignarle a cada celda, sea elemento `<td>` o `<th>`, un borde inferior con `bprder-bottom`. Asi solo se le asigna el borde de abajo y no los demas.

Por ultimo, si queremos, podriamos sacar el borde inferior de todo asignandolo a 0. La forma de hacer esto es indicando el `:last-child`, que hace que se lo asigne al ultimo elemento `<td>` de la lista.

Esto lo mostramos solo porque es muy comun hacer esto en las paginas. Solo dejar una linea divisora de filas. Ademas, hace que la tabla no se vea tanto como una tabla, si no mas como unas filas. Puede llegar a quedar muy bien si se les aplican diferentes tipografias y tamaños a las letras.



### Table Striping

Algo que tambien se suele hacer mucho es agregar un diferente color de fondo a las tablas, que se le llama "stripe", es decir, rayar la tabla de diferentes colores. Esto se suele hacer con el encabezado de la tabla, para proveerle de una diferente organizacion y la distincion del encabezado. Otra cosa que se suele hacer es separar cada fila con un color que difiere muy poco del anterior, como por ejemplo, blanco y gris. Asi haces un alternado entre filas.

Una forma de realizar esto es poniendole a todos los elementos `<tr>` que quieras cambiarle el color, una clase en particular que sea la misma para todos. Asi luego le asignas un background color y se les aplican a todos los seleccionados. Esta es la forma mas directa.

La otra es usando la pseudo-clase `:nth-child`. Esta pseudo clase admite un argumento, que puede ser `even` o `odd`. Lo que hace es seleccionar de un conjunto de elementos solo los que esten en posiciones pares o impares. Entonces, les asignas ahi el color y se lo cambia.

```css
table {
  border-collapse: separate;
  border-spacing: 0;
}
th,
td {
  padding: 10px 15px;
}
thead {
  background: #395870;
  color: #fff;
}
tbody tr:nth-child(even) {
  background: #f0f0f2;
}
td {
  border-bottom: 1px solid #cecfd5;
  border-right: 1px solid #cecfd5;
}
td:first-child {
  border-left: 1px solid #cecfd5;
}
```

Notar que en este ejemplo, le asigna al `<thead>` un color azul, y esto pone a toda la fila del encabezado de ese color. Esta es una forma de hacerlo mas conveniente, antes que seleccionar la fila. Luego le dice que dentro del tbody, selecciones solo los elementos fila pares, y les asigna color gris. 

Otras cosas a notar es que se le puso a la tabla el border-colapse en separate, y un espacio de 0. Esto se hizo porque las celdas contienen bordes, pero los elementos `<th>` no tienen borde. Entonces, si se pone un colapse y se le da un cierto borde, terminan sobresaliendo los bordes del cuerpo de la tabla. Entonces lo que se hace es setearlo a separado, pero se pone una separacion nula.

Lo que hace esa separacion nula es sacar cualquier borde interno, y es por eso que despues le pone borde abajo y a la derecha a cada celda. Asi creando como un collapse.

Parece algo simple de hacer, pero al momento de hacerlo siempre surgen dificultades. Ya sea porque no se sabe que poner, o que hacer. Muchas cosas se nos van olvidando. La solucion a eso es practicar mucho, copiar trabajos de otros, inventar los tuyos. Asi hasta que se te grabe en la cabeza cada elemento, propiedad y funcionamiento de las cosas, o al menos los mas importantes. De manera que, si tener que hacer una tabla, no lo tengas que pensar tanto y las cosas salgan de manera natural.



### Aligning Text

El aliniamiento de texto juega tambien un rol importante en las tablas. Tanto el aliniamiento horizontal como el vertical. Loa nombres y descripciones son por lo general tirados para la izquierda, mientras que los numeros se suelen tirar para la izquierda. Tambien puede que otros elementos, dependiendo del contenido, esten centrados, como puede ser el caso de los headings.

Para mover de forma horixontal, tenemos la propiedad `text-align`, que ya vimos en otras lecciones.

Por otro lado, tambien podemos hacer un aliniamiento vertical, utilizando la propiedad `vertical-align`. Esta propiedad solo funciona con elementos en linea, o con celdas de tablas, pero no funciona con elementos en bloque o inline-block. 

La propiedad `vertical-align` tiene varios valores disponibles distintos para utilizar, pero los mas usados suelen ser `top`, `middle` y `bottom`. Lo que hacen estos es centrar el texto dentro de la celda en referencia a esa celda, o en caso de no poder hacerlo, en referencia al elemento en linea mas cercano. No va a tomar nunca en cuenta a los elementos en bloque y inline-block.

Entonces, hagamos un ejemplo con la tabla de los libros con la que ya venimos trabajando. Vamos a hacer aliniamientos, asi se organiazan mejor las cosas.

```html
<table>
  <thead>
    <tr>
      <th scope="col" colspan="2">Item</th>
      <th scope="col">Qty</th>
      <th scope="col">Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <strong class="book-title">Don&#8217;t Make Me Think</strong> by Steve Krug
      </td>
      <td class="item-stock">In Stock</td>
      <td class="item-qty">1</td>
      <td class="item-price">$30.02</td>
    </tr>
    <tr>
      <td>
        <strong class="book-title">A Project Guide to UX Design</strong> by Russ Unger &#38; Carolyn Chandler
      </td>
      <td class="item-stock">In Stock</td>
      <td class="item-qty">2</td>
      <td class="item-price">$52.94 <span class="item-multiple">$26.47 &#215; 2</span></td>
    </tr>
    <tr>
      <td>
        <strong class="book-title">Introducing HTML5</strong> by Bruce Lawson &#38; Remy Sharp
      </td>
      <td class="item-stock">Out of Stock</td>
      <td class="item-qty">1</td>
      <td class="item-price">$22.23</td>
    </tr>
    <tr>
      <td>
        <strong class="book-title">Bulletproof Web Design</strong> by Dan Cederholm
      </td>
      <td class="item-stock">In Stock</td>
      <td class="item-qty">1</td>
      <td class="item-price">$30.17</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <td colspan="3">Subtotal</td>
      <td>$135.36</td>
    </tr>
    <tr>
      <td colspan="3">Tax</td>
      <td>$13.54</td>
    </tr>
    <tr>
      <td colspan="3">Total</td>
      <td>$148.90</td>
    </tr>
  </tfoot>
</table>
```

```css
table {
  border-collapse: separate;
  border-spacing: 0;
  color: #4a4a4d;
  font: 14px/1.4 "Helvetica Neue", Helvetica, Arial, sans-serif;
}
th,
td {
  padding: 10px 15px;
  vertical-align: middle;
}
thead {
  background: #395870;
  color: #fff;
}
th:first-child {
  text-align: left;
}
tbody tr:nth-child(even) {
  background: #f0f0f2;
}
td {
  border-bottom: 1px solid #cecfd5;
  border-right: 1px solid #cecfd5;
}
td:first-child {
  border-left: 1px solid #cecfd5;
}
.book-title {
  color: #395870;
  display: block;
}
.item-stock,
.item-qty {
  text-align: center;
}
.item-price {
  text-align: right;
}
.item-multiple {
  display: block;
}
tfoot {
  text-align: right;
}
tfoot tr:last-child {
  background: #f0f0f2;
}
```

Vamos a descomponer el codigo entero. Por un lado tenemos la estructura de la tabla, que como un repaso rapido, esta usando todo lo que vimos. Inicializa con `<table>`, estructura con `<thead>`, `<tbody>` y `<tfoot>`, crea filas con `<tr>` y dentro de ellas, segun quiera un header o no, usa `<th>` o `<td>`. 

Luego, utiliza el atributo colspan para expandir las celdas horizontalmente, e indica el numero segun cuantas quiera tomar. Utiliza tambien el elemento `<strong>` para dar titulos mismo dentro de las celdas. 

Por otro lado, tenemos la parte de CSS. Primero, a toda la tabla le asigna un `border-collapse` de `separate`, con un `border-spacing` de 0. Esto ya vimos porque lo hace, es para juntar todos los bordes de todas las celdas, y hacerlos cero. Esto lo hacia para que no termine siendo el body mas grande que el encabezado. Ademas, le pone un color de texto y una fuente a toda la tabla. Termina quedando una tabla sin contorno.

Luego a todas las celdas, le agrega un padding para separar el texto interior de los bordes, y hace un `vertical-align` en `middle`. Esto hace que el texto dentro de la celda se centre de forma vertical.

Le agraga un color al header medio azulado, y el color del texto en blanco.

Luego, el `th:first-child`, vendria a ser el primer elemento th dentro del header. Le asigna un `text-align` a `left`. Esto lo hace porque quiere que solo el encabezado de la primero columna este tirado a la izquierda. 

Despues, a todo el tbody, solo las filas que sean pares, les mete un color diferente de fondo para hacer un "striping". 

Luego, a cada celda le agrega un borde inferior y derecha, para poder completar todas las lineas interiores, que se sacaron antes con el border collapse. Y a cada celda que sea td y este primera dentro del elemento parent, osea el tr, le agrega un borde izquierdo. Esto lo hace porque cuando uso el border collapse, la tabla quedo sin bordes. Entonces termina dandole todos los bordes inferiores y derechos a las celdas, y la tabla queda con bordes, menos en la parte izquierda. Y es por eso que tiene que realizar esto ultimo.

Por ultimo, asigna a todos los elementos de clase block-title, que serian los titulos de los libros, un color azul y que sean elementos en bloque. Esto hace que separen la linea entre el titulo y el autor. Asi nunca se van a tocar como si estuvieran en linea. Luego a los dos headers del medio, los centra en la celda, y prefiere poner al header del precio hacia la derecha. 

El item-multiple es un solo elemento, que corresponde al precio. Lo pone en bloque para que separe la linea. Luego mete a todo el tfoot a la derecha, y a la ultima fila le cambia el color. Esto lo hace con la pseudo-clase last-child.

##### Otro ejemplo

Agregemosle algunas cosas para modificar el texto de adentro. Cambiar algunos tamaños e intensidades del texto, y redondear algunos bordes.

```html
<table>
  <thead>
    <tr>
      <th scope="col" colspan="2">Item</th>
      <th scope="col">Qty</th>
      <th scope="col">Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <strong class="book-title">Don&#8217;t Make Me Think</strong>
        <span class="text-offset">by Steve Krug</span>
      </td>
      <td class="item-stock">In Stock</td>
      <td class="item-qty">1</td>
      <td class="item-price">$30.02</td>
    </tr>
    <tr>
      <td>
        <strong class="book-title">A Project Guide to UX Design</strong>
        <span class="text-offset">by Russ Unger &#38; Carolyn Chandler</span>
      </td>
      <td class="item-stock">In Stock</td>
      <td class="item-qty">2</td>
      <td class="item-price">$52.94 <span class="text-offset item-multiple">$26.47 &#215; 2</span></td>
    </tr>
    <tr>
      <td>
        <strong class="book-title">Introducing HTML5</strong>
        <span class="text-offset">by Bruce Lawson &#38; Remy Sharp</span>
      </td>
      <td class="item-stock">Out of Stock</td>
      <td class="item-qty">1</td>
      <td class="item-price">$22.23</td>
    </tr>
    <tr>
      <td>
        <strong class="book-title">Bulletproof Web Design</strong>
        <span class="text-offset">by Dan Cederholm</span>
      </td>
      <td class="item-stock">In Stock</td>
      <td class="item-qty">1</td>
      <td class="item-price">$30.17</td>
    </tr>
  </tbody>
  <tfoot>
    <tr class="text-offset">
      <td colspan="3">Subtotal</td>
      <td>$135.36</td>
    </tr>
    <tr class="text-offset">
      <td colspan="3">Tax</td>
      <td>$13.54</td>
    </tr>
    <tr>
      <td colspan="3">Total</td>
      <td>$148.90</td>
    </tr>
  </tfoot>
</table>
```

```css
table {
  border-collapse: separate;
  border-spacing: 0;
  color: #4a4a4d;
  font: 14px/1.4 "Helvetica Neue", Helvetica, Arial, sans-serif;
}
th,
td {
  padding: 10px 15px;
  vertical-align: middle;
}
thead {
  background: #395870;
  background: linear-gradient(#49708f, #293f50);
  color: #fff;
  font-size: 11px;
  text-transform: uppercase;
}
th:first-child {
  border-top-left-radius: 5px;
  text-align: left;
}
th:last-child {
  border-top-right-radius: 5px;
}
tbody tr:nth-child(even) {
  background: #f0f0f2;
}
td {
  border-bottom: 1px solid #cecfd5;
  border-right: 1px solid #cecfd5;
}
td:first-child {
  border-left: 1px solid #cecfd5;
}
.book-title {
  color: #395870;
  display: block;
}
.text-offset {
  color: #7c7c80;
  font-size: 12px;
}
.item-stock,
.item-qty {
  text-align: center;
}
.item-price {
  text-align: right;
}
.item-multiple {
  display: block;
}
tfoot {
  text-align: right;
}
tfoot tr:last-child {
  background: #f0f0f2;
  color: #395870;
  font-weight: bold;
}
tfoot tr:last-child td:first-child {
  border-bottom-left-radius: 5px;
}
tfoot tr:last-child td:last-child {
  border-bottom-right-radius: 5px;
}
```

Solo le agrego alguna que otra cosa, como un text-offset que le cambio el tamaño y el color a un poco menos intenso. Agrego un border-radius a las esquinas inferiores. Un gradiente al header. Y no mucho mas.

Sobre hacer un border-radius en las esquinas. En este caso lo hizo sobre la celda, y no sobre la fila ni tabla. Creo que la razon es porque la tabla y las filas son elementos estructurales, y no son visibles. Pero las celdas si lo son, y es por eso que si se redondea, se lo hace a las celdas de los extremos. Recorda usar las pseudo-classes `:first-child` y `:last-child`.

Ahora a practicar mucho.