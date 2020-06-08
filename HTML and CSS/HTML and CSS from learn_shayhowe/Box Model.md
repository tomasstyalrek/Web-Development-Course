# Opening the Box Model

Hasta ahora estuvimos familiarizandonos un poco con HTML y CSS, ya sabemos como se ven y como conseguir algunas cosas basicas. Ahora vamos a ir un poquito mas profundo para ver como los elementos son impresos en una pagina y como son medidos dentro.

Vamos a hablar sobre lo que es el box model y como funciona con ambos. Ademas, vamos a ver algunas propiedades mas en CSS y a usar los valores de los largos que vimos antes.

### How Are Elements Displayed?

Antes de pasar a ver el "box model", vamos a ver como se imprimen los elementos en pantalla. 

Ya vimos antes lo que son los elementos "block-level" y los "inline-level". Pero para refrescar un poco, los elementos en bloque son aquellos que ocupan todo el ancho disponible en una pagina, independientemente de su contenido, y ademas estos contienen cortes de linea antes y despues. Son usados principalmente para contenido largo y tal vez con mas importancia o presencia, como headings, parrafos, y otros elementos estructurales. En cambio los elementos en linea son aquellos que solo ocupan el largo que su contenido necesita, y estan contenidos entre lineas. Por ejemplo, cuando uno referencia a un link, o pone en negrita un texto lo esta haciendo entre la misma linea, no hay saltos ni nada por el estilo.

##### Display

La forma en que un elemento es impreso viene determinado por default por la propiedad `display` que poseen. Claro que, como toda propiedad de un elemento, esta puede ser sobreescrita. Hay varios tipos de valores para esta propiedad, pero los mas comunes son `block`, `inline`, `inline-block`, y `none`.

Podemos cambiar esta propiedad poniendo un selector del elemento que queremos, asi se le sobreescribe la propiedad a todos. Lo hacemos de la forma que ya conocemos.

```css
p {
  display: block;
}
```

El valor `block` para esta propiedad vuelve al elemento un elemento en bloque, mientras que el valor `inline` lo vuelve en linea. 

Por otro lado, el valor `inline-block` hace que el elemento se comporte como un elemento en bloque, aceptando todas las propiedades del box model (que ya vamos a ver). Sin embargo, el elemento va a ser impreso en linea son otros elementos, y no va a comenzar en una nueva linea por defecto. Es como una especie de elemento en bloque, que se presenta en linea.

```css
p {
  display: inline-block;
}
```

![Inline vs. Block vs. Inline-Block: CSS – Danielle Developer](data:image/png;base64,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)

Esta foto lo muestra bastante bien. El que es en bloque, se presenta en cajas separados por cortes de lineas. El elemento en linea esta uno al lado del otro. Y el inline-block es una combinacion de ambos.

----

###### Space Between Inline-Block Elements

Una distincion que tienen estos tipos de elementos es que no estan siempre tocandose, no se imprimen uno al lado del otro. Usualmente existe un espacio pequeño entre estos elementos. Este estacio suele ser un poco molesto, pero es normal. Luego vamos a ver porque este espacio existe y como removerlo.

![Removing the whitespace (Gap) between inline-block elements with ...](https://ourcodeworld.com/public-media/articles/articleocw-5a5ba34b87b7e.png)

Esta foto lo expresa bastante bien. No es una presentacion continua de bloques en linea, si no que hay un espacio entre ellos.

-------

Por ultimo, el valor `none` va a esconder el elemento y la pagina no lo va a renderizar, como si no existiera. Ademas, todo elemento que este anidado dentro de este elemento, tambien va a ser escondido. Este es el caso por defecto de un `<div>`, por ejemplo, que no representa nada, solo una division con propositos de diseño.

Saber como los elementos son impresos en pantalla, y como cambiar estas propiedades, es muy importante ya que tiene implicaciones en como es renderizado el "box model". Ademas esto da lugar a un sinfin de diferentes formas de estructurar una pagina. Vamos a ir viendo como estos diferentes valores cambian la forma en que un elemento es presentado.



### What Is the Box Model?

**Todo elemento en una pagina es una caja rectangular**. Este es un concepto que cuando uno lo entiende, le cambia el panorama por completo. 

En realidad, suelen haber tres cosas que te cambian la forma de pensar, con respecto al diseño y estructura de una pagina. Todo elemento en una pagina es una caja, se puede controlar el tamaño y posicion de esas cajas, y por ultimo, le puedo añadir un diseño a cada caja. Esto te abre el camino a un monton de posibilidades distintas. 

Todo elemento en una pagina es una caja que puede contener ancho (width), alto (height), relleno (padding), bordes (borders) y margen (margin).



![img ](https://i0.wp.com/css-tricks.com/wp-content/csstricks-uploads/thebox.png?resize=570%2C248)

En la foto se puede ver que el ancho y largo pertenecen al elemento en si. Comprenden hasta la linea punteada. Luego viene el padding, que es el relleno entre los bordes y el elemento. Luego los bordes, que es el contorno, y por ultimo el margen, que es todo lo blanco.

### Working woth the Box Model

Todo elemento es una caja rectangular, y hay varias propiedades para determinar el tamaño de la caja. 

El cuerpo o la parte principal de la caja esta definida por el ancho y largo de la misma, que puede cambiar por varios factores. Puede estar determinado por la propiedad `display`, por el contenido mismo del elemento, que hace que se agrande o achique, o especificando explicitamente el `width` y `heigth` en las propiedades del elemento. 

Luego, el `padding` y `border` espanden las dimensiones de la caja mas alla de lo que ocupa el elemento. Es decir, el ancho y largo definen cuanto ocupa el elemento en si, y el relleno y borde lo expanden mas. 

Y por ultimo viene el `margin`, que le sigue al borde.

Todas estas propiedades componen el box model, es decir, `width`, `height`, `padding`, `border`, y `margin`.

```css
div {
  border: 6px solid #949599;
  height: 100px;
  margin: 20px;
  padding: 20px;
  width: 400px;
}
```

El ancho total de un elemento (en pixeles) puede ser calculado con la siguiente formula:

```css
margin-right + border-right + padding-right + width + padding-left + border-left + margin-left 
```

Que no es mas que la suma de los pixeles horizontales que lo componen, que corresponden a dos margenes, dos bordes, dos rellenos, y el elemento en si, que seria su ancho.

Y lo mismo se puede hacer para calcular su largo, utilizando la siguiente formula:

```css
margin-top + border-top + padding-top + height + padding-bottom + border-bottom + margin-bottom 
```

Que, de la misma manera, son la suma de sus pixeles verticales, correspondientes a los dos margenes superior e inferior, dos bordes, dos rellenos y el alto del elemento en si.

![The Box Model](https://learn.shayhowe.com/assets/images/courses/html-css/opening-the-box-model/box-model.png)

Esto se muestra para que tengamos en cuenta que, ademas de que el elemento es una caja, el ancho o largo de un elemento no viene determinado solo por el ancho y largo que le pongamos en sus propiedades, si no que hay que tener en cuenta todas las demas propiedades. 

En principio, podriamos preguntarnos por que razon es que hay tantas cosas para tener en cuenta, y no basta con que haya un par. Pero es que cada una tiene  su proposito. Por esta razon es que ahora vamos a ver de forma mas detallada cada una de estas.



#### Width & Height

Todo elemento tiene un ancho y alto que esta asignado por defecto. Este depende de que tipo de elemento sea. Pero este ancho y alto puede ser modificado por varias razones. Una de ellas es la importacia que tenga ese elemento en la pagina. Segun que represente ese elemento para el contenido de una pagina, va a darsele un ancho y largo correspondiente. Esto se le asignara a los elementos que no sean en linea.

##### Width

El ancho por defecto de un elemento viene dado por el valor de su propiedad `display`. Si el elemento es en bloque, viene por defecto con un ancho del 100%, ya que ocupa todo el ancho de la pantalla. Luego, los elementos en linea y los inline-block, se expanden y contraen dependiendo de su contenido. Un elemento en linea no puede tener un ancho o largo fijo, es decir, no se los podes asignar, porque su tamaño es relativo a su contenido. 

Habiendo dicho esto, solo le vas a poder asignar un ancho y largo, con las propiedades `width` y `height`, a los elementos "non-inline", es decir, a todos menos los elementos en linea. Y para hacerlo, se lo tenes que asignar como propiedad y darle un valor. Este valor puede ser cualquiera de los que ya vimos.

```css
div {
  width: 400px;
}
```

##### Height

El largo vertical de un elemento viene asignado por defecto dependiendo del contenido. Este se expande o contrae segun vayan creciendo las lineas del contenido. Devuelta, los elementos en linea no poseen propiedades de largo ni ancho, porque siempre se acomodan al contenido, pero para asignar el largo de un elemento que no sea en linea, podemos usar la propiedad `height`.

```css
div {
  height: 100px;
}
```



#### Margin & Padding

Dependiendo del elemento, el browser le va a asignar por defecto algun valor de margen y relleno. Por lo general siempre tienen uno establecido, por cuestiones de claridad y legibilidad. Estos valores por defecto cambian de elemento a elemento, y de browser en browser. Cada uno elige sus valores como desea.

Es por esto que vimos, hace unos capitulos atras, lo que era el CSS reset. Constaba en asignar una capa de personalizacion principal bien basica, con el objetivo de que todo tipo de diseño o estilo principal se reinicie a cero. Esto lograba que la pagina se vea igual en todos los browsers principalmente, y a partir de esa plantilla nosotros podiamos ir construyendo arriba, sobre una base cruda. 

Por esta razon es que esta bueno implementar el CSS reset a nuestras paginas. Para que no ocurra que los valores por defecto en la caja de cada elemento hagan que algo se vea diferente de browser en browser, y asi capas arruinar nuestro diseño.

##### Margin

La propiedad `margin` nos permite asignar la cantidad de espacio que rodea a un elemento. El margen de un elemento cae fuera de los bordes del mismo y es completamente transparente en color. Son usados por lo general para posicionar elementos en un lugar particular o para crear espacio entre elementos, y mantener otras cosas a una distancia segura. Es decir, asi te aseguras de que nada se este molestando entre si.

```css
div {
  margin: 20px;
}
```

Los elementos en linea aceptan margen, pero no superior e inferior. Si en los costados. Sin embargo los elementos en bloque y los inline-block si aceptan el margen arriba y abajo (`top` y `bottom`).

##### Padding

El `padding` o relleno en un elemento es similar a lo que realiza el margen, pero el relleno distancia al elemento del borde, es decir, se encuentra en la cara interna del borde. 

```css
div {
  padding: 20px;
}
```

Esta propiedad afecta a los cuatro lados de un elemento en linea, a diferencia de como lo hace el margen, que solo actua a izquierda y derecha. Probablemente, si asignamos un relleno mayor en un elemento en linea, este se va a combinar con la linea de arriba y abajo.

Luego, en los demas tipos de elementos se comporta normalmente.

##### Margin & Padding Declarations

Cuando se declaran valores para las propiedades, hay mas de una forma de hacerlo. Por ahora vimos la forma que se llama *longhand*, que consiste en enlistar todas las propiedades de un elemento, con su correspondiente valor cada una. La otra opcion se llama *shorthand*, que consiste en enlistar mas de un valor para una sola propiedad. Esta ultima alternativa no esta presente en todas las propiedades, asi que tenemos que asegurarnos de que, si la usamos, la propiedad sea la correcta con su estrucutra de valores. O sea, que lo admita.

Las propiedades `margin` y `padding` son ambas, funcionan como longhand y shorthand. Cuando por ejemplo, usamos una propiedad de estas y le asignamos un valor, en realidad lo que estamos haciendo es asignarle a los cuatro bordes el mismo valor.

```css
div {
  margin: 20px;
}
```

Pero por ejemplo, si asignamos dos valores separados por un espacio, lo que hace es asignar el primero al `top` y al `bottom`, y el otro al `left` y `right`.

```css
div {
  margin: 10px 20px;
}
```

Y por ultimo, si quisieramos asignar valores diferentes a cada uno de los lados, tendriamos que hacerlo de manera horaria empezando por el `top`. Es decir, el orden seria `top`, `right`, `bottom` y `left`.

```css
div {
  margin: 10px 20px 0 15px;
}
```

Notar que no es necesario ponerle la unidad de *px* si el valor es 0.

Estas dos propiedades, `margin` y `padding`, usadas de esta manera, son consideradas *shorthand*, ya sea que pones un valor, dos o cuatro. Esto es porque, por dentro, siempre le estas asignando a los cuatro lados un valor. 

Pero estas propiedades tambien se consideran *longhand*. Esto es porque tambien pueden usarse de forma individual con cada lado, y asi tener una propiedad con un solo valor. Esto se logra añadiendo un guion ( - ) y el nombre del lado (`top`, `right`, `bottom`, o `left`). Fijate este ejemplo:

```css
div {
  margin-top: 10px;
  padding-left: 6px;
}
```

Asi que, teniendo en cuenta estas dos formas de asignar valores, queda en cada uno la eleccion. Por lo general, si solo queres cambiar el tamaño a uno de los lados, vas a usar la forma *longhand*. Esto da un poco mas de claridad al codigo, lo hace mas explicito. Pero en caso de que quieras tener los cuatro lados diferentes o algo asi, usar *shorthand* es algo bastante mas comodo y rapido.

------

###### Margin & Padding Colors

Las propiedades `margin` y `padding` son completamente transparentes. No aceptan propiedades de color.

Igualmente, cuando uno asigna margen y relleno puede ver colores. Esto se debe a que los dos se acomodan a los colores que estan en sus elementos relativos. Al ser transparentes, el margen muestra el color de fondo de su elemento parent, y el padding muestra el color de fondo del elemento al que esta aplicado. Recorda que el margen esta tocando siempre la parte exterior del elemento, y el padding es lo mas proximo al contenido del elemento en si.

-----



#### Borders

El borde de un elemento se situa en medio del margen y el relleno, dandole al elemento un contorno. La propiedad `border` tiene tres valores disponibles, `width`, `style` y `color`.

En la forma *shorthand*, se usa la propiedad `border` y los valores van en el orden dicho anteriormente, separado por espacios, corresponden al `width`, `style` y `color`. Y en su forma *longhand*, las propiedades se separan en estos tres valores, es decir, `border-width`, `border-style` y `border-color`.

En cuanto al `width` y al `color`, estos se comportan como ya vimos. Podemos asignarlos usando las unidades de largo y los colores en algun codigo visto, como siempre.

Pero lo que es nuevo son las diferentes apariencias disponibles para un borde. Los valores mas comunes para la propiedad `style` son `solid`, `double`, `dashed`, `dotted`, y `none`, pero hay muchos mas.

![CSS/Training/borders - Web Education Community Group](https://www.w3.org/community/webed/wiki/images/a/af/Cssed_borderstyles.png)

Por ejemplo, este es un elemento `<div>` con que su borde tiene un ancho de 6px, un estilo solido, con color gris.

```css
div {
  border: 6px solid #949599;
}
```

##### Individual Border Sides

Al igual que el margen y el relleno, los bordes se pueden manipular por separado. Para hacerlo usamos las propiedades `border-top`, `border-right`, `border-bottom`, y `border-left`. Todas estas aceptan los mismos valores que `border`, es decir,  `width`, `style`, y `color`. O sea, si quisieramos podriamos setear cada borde de una forma diferente, con su propio color, ancho y estilo.

```css
div {
  border-bottom: 6px solid #949599;
}
```

Y tambien se puede ir un poco mas fino, y optar por las propiedades mas individuales. Estas se formarian añadiendo el valor que queres cambiar con un guion.

```css
div {
  border-bottom-width: 12px;
}
```

Esta bueno en estos casos tener un editor de esos que te presentan las propiedades disponibles. Nos ahorraria memorizar muchos nombres. Por eso es que todo esto sirve en realidad para que uno sepa lo que ofrece CSS, y no para saber de memoria todo. Esto se queda en la memoria con tiempo de practica.

##### Border Radius

La propiedad `border-radius` te permite redondear los bordes de un elemento.

Esta propiedad acepta unidades de longitud, como porcentajes y pixeles. Ademas, se puede redondear por separado los bordes. Si se ingresa un solo valor, redondea todos. Si ingresas dos valores, el primero redondea el `top-left/bottom-right` y el segundo el `top-right/bottom-left`. Y por ultimo, si pones cuatro valores va en orden horario, arrancando desde el `top-left`. Es decir, `top-left`, `top-right`, `bottom-right`, y `bottom-left`.

```css
div {
  border-radius: 5px;
}
```

Por ejemplo, si queremos hacer un circulo, una forma es poner los bordes en un 50%. Pero en cambio, si solo se quiere redondear los bordes un poco, solo basta con poner un porcentaje chico o pocos pixeles.

Algo que esta bueno es ponerse a jugar un poco con elementos, y fijarse de que manera van cambiando. Asi ademas te vas familiarizando con lo que vamos aprendiendo. 

Tambien los bordes tienen su propiedad en version *longhand*. Esto se formaria usando la propiedad `border`, luego el extremo vertical (`top` o `bottom`), luego el extremo horizontal (`left` o `right`), y por ultimo la propiedad `radius`. Por ejemplo:

```css
div {
  border-top-right-radius: 5px;
}
```



#### Box Sizing

Hasta ahora el tamaño de una caja tiene un diseño que es aditivio, es decir, vos definis el ancho como 400px, el padding de 20px y los bordes de 10px, y pasas a tener un elemento que ocupa 460px. Es bastante intuitiva esta forma de conseguir el tamaño de un elemento.

Pero sin embargo, el box model se puede cambiar para poder aceptar diferentes calculos. En CSS3 se añadio una propiedad llamada `box-sizing`, esta te deja cambiar como el box model trabaja y como se calcula el tamaño de un elemento. Esta propiedad acepta tres valores primarios, que son `content-box`, `padding-box`, y `border-box`. Cada uno de estos hace una diferencia grande en la forma de calcular el tamaño de un elemento.

##### Content Box

El `content-box` es el valor que contiene por defecto la propiedad `box-sizing`, y hace que el box model tenga este diseño aditivo. Si directamente no usamos esta propiedad, este va a quedar como el valor por defecto para todos los elementos. Con este valor, el tamaño de un elemento empieza con sus propiedades `width` y `height`, y luego se le añade cualquier propiedad de `margin`, `border` o `padding` de las que estuvimos viendo.

```css
div {
  -webkit-box-sizing: content-box;
     -moz-box-sizing: content-box;
          box-sizing: content-box;
}
```

-----

###### Browser-Specific Properties & Values

Ese `-webkit` o `-moz` que se ve arriba, son los llamados *vendor prefixes*. Referencian a un browser en especifico. 

Cuando CSS3 fue introducido, este vino con varias nuevas propiedades y valores que, en un principio, no son soportados por los browsers al menos que estos vayan sacando actualizaciones para poder hacerlas compatibles. Por esta razon es que se añadieron estos prefijos a las propiedades, incluyendo la propiedad `box-sizing`, para que estos browsers puedan utilizar las nuevas propiedades disponibles. Esto aparecio con la salida de CCS3, y se utilizo para mantener esta experiencia con las nuevas propiedades mientras que los browsers encontraban una manera de actualizar el software.

Es decir, probablemente estos prefijos ya no sirvan mucho en browsers actualizados, pero a veces es una buena idea usarlos para que browsers mas viejos soporten las propiedades.

Si una propiedad o valor necesita de un prefijo del browser, este debe ir al principio siempre. Para una referencia, estos son los principales:

- Mozilla Firefox: `-moz-`
- Microsoft Internet Explorer: `-ms-`
- Webkit (Google Chrome and Apple Safari): `-webkit-`

----------

##### Padding Box (Obsoleto)

El valor `padding-box` lo que hace es incluir la propiedad `padding` dentro de los valores del ancho y largo. Es decir, es como si lo escondiera al padding dentro, como parte de su `width` y `height`. 

Por ejemplo, si ponemos un `width` de 400px, y un `padding` de 20 px, el ancho total va a seguir siendo de 400px. Ademas, el contenido se encoje proporcionalmente a medida que se agranda el relleno. Esto sucede porque el relleno se agrega, pero queda dentro del contenido entonces se termina expandiendo para adentro, en vez de hacerlo como relleno y expandir los bordes hacia afuera.

Pero en cambio, si añadimos un borde o margen, estos si van a ser añadidos al ancho o largo de un elemento. 

```css
div {
  box-sizing: padding-box;
}
```

Por lo tanto, mientras que el valor `content-box` mide todo de forma aditiva, el valor `padding-box` no toma en cuenta al padding.

Actualizacion: Este valor esta obsoleto y no debe usarse.

##### Border Box

Por ultimo, el valor `border-box` altera el box model de forma que todo valor añadido a la propiedad `border` y `padding` se van a añadir al `width` y `height` del elemento. Es decir, funciona de la misma manera que el anterior, pero añadiendo tambien el borde.

Por lo tanto, si ponemos un width de 400px, un padding de 20px, y un borde de 10px, el tamaño total se va a quedar en 400px.

Pero si le ponemos un valor al `margin`, este si va a ser sumado al del contenido. Cualquiera sea el valor del `box-sizing`, va a sumarsele el valor del margen.

```css
div {
  box-sizing: border-box;
}
```

##### Picking a Box Size

Ahora, uno se pregunta para que me sirve saber esto. Bueno, resulta que es extremadamente util.

Por lo general lo mejor es usar el valor `border-box`. Esto es porque hace que todo, excepto el margen, se contenga dentro del rectangulo que queremos. Nos da una mayor facilidad para manipular el tamaño de un elemento. Nosotros seteamos el ancho de un elemento a 400px, por ejemplo, y ya no tenemos que preocuparnos por los bordes ni por el padding, porque se van a acomodar ellos solos dentro del ancho. Es como si le dijeras, tenes este ancho o largo disponible, vos acomodate ahi adentro. 

De la manera `content-box`, tendrias que manipular vos manualmente el tamaño. Si queres un ancho de 400px, tendrias que ir haciendo la suma con los paddings y los borders para que te de del tamaño que uno quiere.

Y en cuanto al margen, esta es la razon por la que no hay un `box-sizing` para el. No tendria sentido porque le margen no forma parte del contenido de un elemento, si no que forma mas parte del exterior del mismo.

Pero no todo es perfecto. La desventaja del uso del `box-sizing` es que, al ser una especificacion de CSS3, no todos los browsers lo soportan. Si lo hacen los browsers mas comunes, porque estan actualizados, pero hay otros que no lo hacen. O tambien puede ser que haya personas que aun conserven una version anterior de un browser, y sea esta la razon por la que no le funciona esto. Pero realmente, las chances estan de nuestro lado para el uso de la propiedad, pero en caso de que haya problemas, es nuestro trabajo identificar que browser esta teniendo porblemas, y tal vez poner un prefijo sea la solucion.



### Developer Tools

La mayor parte de los browsers poseen una *Developer Tools*. Esta herramienta nos permite inspeccionar los elementos de la pagina y ver en donde vive ese elemento dentro del documento HTML, ademas de poder ver cuales son las propiedades y valores de CSS aplicadas a el. La mayoria de estas herramientas tambien contienen un diagrama que muestra el box model de un elemento.

Por ejemplo, el developer tools de Chrome se situa en las opciones de arriba a la derecha, "Mas herramientas" y "Herramientas para desarrolladores". Tambien lo podes activar com Ctrl + Mayus + I.

Aca dentro podes ver absolutamente todo lo que pasa. Si clickeas en la herramienta que esta arriba, en la parte izquierda del panel que se abrio, esto te deja seleccionar los elementos que quieras. Seleccionando uno te va a permitir ver como esta compuesto. Se ve por un lado su estructura en el codigo HTML, y en la parte de abajo se ven los estilos del elemento. 

En la parte de los estilos, si entras a "Computed" vas a ver una caja que representa el box model de ese elemento. Y con un color diferente te muestra cada parte del elemento. Estos son los colores que aparecen cuando vas a seleccionar el elemento con la herramienta mencionada.

Cuando uno quiere seleccionar un elemento, va pasando por encima de ellos y se ponen de colores. Estos representan las diferentes partes del box model. Por lo general, en azul esta el contenido del elemento, es decir, su `width` y `height`, y luego en verde el `padding`, en una especie de naranja el `border` y en marron el `margin`. Te recomiento jugar un poco con esto.

El Developer Tools es una excelente herramienta para aprender tambien. Porque ahi esta todo. Podes poner en practica todo lo aprendido, y a medida que vayas aprendiendo mas, lo que antes no entendias en el DevTools, ahora empieza a tener sentido.

Es una muy buena practica ver el contenido de las paginas, y de que manera otros construyen sus estructuras y diseños. Ver patrones y jugar un poco con las cosas te va a aclarar muchas ideas.

![Google Chrome Developer Tools](https://learn.shayhowe.com/assets/images/courses/html-css/opening-the-box-model/developer-tools.png)



##### Summary

Espero que las cosas empiecen ya a tomar un poco de sentido. Claro que hay cosas que uno no se imagina todavia como hacerlas. Pero a medida que sigamos avanzando todo va a cerrar. Como por ejemplo, tal vez ya empezaste a crear tus documentos, a darles algunos estilos y jugar un poco, pero no estas logrando hacer que las cosas se posicionen en lugares de la pagina. Bueno, esto lo vamos a ver en la proxima leccion.

En cuanto a esta seccion, lo que vimos primero fue la forma de imprimir o presentar los elementos en una pagina por parte del browser. Vimos que hay tres tipos de formas en que los elementos se presentan, que son en linea, en bloque, y ambos al mismo tiempo.

Tambien introducimos al modelo de cajas en CSS, diciendo que todo elemento es una caja. Todo elemento posee dentro de esa caja diferentes propiedades que pueden ser cambiadas. Estas son su anchoy largo que afectan a su contenido, el padding, que corresponde al relleno del elemento anterior a los bordes. Luego vienen los bordes en si, que son el contorno del elemento, y por ultimo la parte exterior del elemento llamada margen, que es la que interactua y posiciona al elemento.

Vimos que hay mas de una forma de asignar propiedades a elementos. Esto se podia hacer en la forma *shorthand*, separando con espacios los valores, o de la forma *longhand*, poniendo cada valor individualmente.

Cada uno de estos valores tiene diferentes propiedades que podemos ir cambiando. Ya sea correspondiente a los estilos o al largo, podiamos cambiar cada estilo diferente por separado o cada lado del elemento individualmente.

Luego vimos como cambiar la forma en que los elementos cuentan su tamaño, que al final solo son dos. O contas de forma aditiva, o mantenes de forma estatica el tamaño y todo se acomoda a ese tamaño fijo.

Vimos que hay propiedades que no son soportadas por todos los navegadores y por eso hay que agregar prefigos. Y por ultimo, vimos las DevTools que proveen los browsers, para inspeccionar diferentes aspectos de una pagina, como sus elementos, estilos, estructura, y mucho mas.

En la proxima leccion vamos a empezar a ver el posicionamiento de los elementos dentro de una pagina.

