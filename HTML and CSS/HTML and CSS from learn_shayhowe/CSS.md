# CSS

CSS es un lenguaje complejo y bastante potente. Nos permite añadir una plantilla y un diseño a nuestras paginas, y poder compartirlo por todas las paginas de un sitio web. 

Pero primero, para poder realizar las cosas mas interesantes que tiene disponible, necesitamos poder entender ciertos conceptos basicos, como el de renderacion de los estilos, como funcionan los selectores, y muchas otras propiedades comunes, escenciales para poder utilizar el lenguaje correctamente.

### The Cascade

Empecemos descomponiendo un poco como los estilos  son renderizados, mirando a algo que se llama cascada.  Dentro de CSS, los estilos estan dispuestos en forma de cascada, de manera que se colocan desde la parte superior a la inferior, y pueden añadirse nuevos estilos y solaparse otros.

Por ejemplo, supongamos que queremos añadirle un background color naranja a los elementos p de nuestro documento, y un tamaño de fuente de 24 pixeles. Pero despues volvemos a definir su color de fondo como verde. 

```css
p {
  background: orange;
  font-size: 24px;
}
p {
  background: green;
}
```

Lo que va a pasar en este caso es que, el background verde va a tomar precencia antes que el naranja, porque asi se dispone la jerarquia en CSS. Los elementos que se ponen ultimos, son los que toma en cuenta. Pero por otro lado, el tamaño de fuente sigue siendo 24, porque no se sobreescribio por otra fuente.

Por lo tanto, recordar que siempre un documento CSS va en forma de cascada, uno abajo del otro, y se sobreescriben los estilos, en caso de una repeticion, tomando en cuenta al ultimo estilo puesto.

##### Cascading Properties

Ademas de haber como una jerarquia dentro de la cascada, tambien la hay dentro del selector mismo.

Supongamos que, devuelta, le ponemos el color de fondo naranja a los elementos p, e inmediatamente debajo lo volvemos a setear en verde. 

```css
p {  
  background: orange;  
  background: green; 
} 
```

Lo que pasa aca es que la propiedad que se vuelve a setear, toma el valor del ultimo dado. En este caso, los parrafos van a quedar en verde.



### Calculating Specificity

Todo selector en CSS tiene un "specificity weight", es decir, un peso de especificidad. Esta propiedad del selector, junto con su posicionamiento en la cascada, van a determinar como se renderizaran los estilos.

Mas especificamente, el selector `type` es el que tiene el menor peso de especificidad, y tiene un valor de  `0-0-1`, sea lo que sea eso. Luego, el selector `class` tiene un valor medio, con valor `0-1-0`. Y por ultimo viene el `id` con una especificidad alta y un valor de `1-0-0`.

Estos valores se imprimen asi, con guiones, porque no se quiere que la maquina los interprete en decimal. Despues vamos a ver mejor que representan estos valores.

Esta especificidad en un selector es lo que define la importancia que se le dara a un selector en caso de que ocurra un conflicto. Por ejemplo, si uno quiere darle un estilo a un parrafo que contiene el atributo id, y hace esto:

```html
<p id="food">...</p>
```

```css
#food {
  background: green; 
} 
p {  
  background: orange; 
} 
```

Lo que toma precedencia aca es el selector de id, y no de type, aunque este ultimo este puesto debajo de la cascada. Esto se debe al peso que tiene un selector de id por sobre uno de type. Por lo tanto, el color del parrafo va a ser verde.

Por lo tanto, por ahora solo va a ser necesario que recordemos eso. El selector `id` tiene mas peso que un selector `class`, y que estos tienen mas peso que un `type`.

Luego vamos a seguir indagando un poco mas en esto porque es un tema importante. 



### Combining Selectors

Hasta ahora vimos como usar diferentes tipos de selectores de forma individual, pero tambien necesitamos saber como usarlos juntos. Combinando selectores se puede ser mas especifico sobre que elemento o grupo de elementos queremos seleccionar.

Por ejemplo, imaginate que tenemos un conjunto de elementos que son parrafos, los cuales estan todos dentros de un div con class="hotdog", y queremos poner todos los elementos p dentro de color marron, pero le decimos que en caso de que alguno de los parrafos tenga class="mustard" lo ponga en amarillo. Bueno, seria algo asi.

```html
<div class="hotdog">
  <p>...</p>
  <p>...</p>
  <p class="mustard">...</p>
</div>
```

```css
.hotdog p {
  background: brown;
}
.hotdog p.mustard {
  background: yellow;
}
```

Cuando uno combina selectores, estos se leen de derecha a izquierda. Es decir, desde el selector que esta pegado a la llave, llamado *key selector*, hasta el ultimo elemento de la izquierda, el cual funciona al igual que todos los anteriores que no son el key selector, como precalificadores.

Es decir, lo que hacen estos selectores es anidarse uno dentro del otro, dandole instrucciones de como encontrar el elemento especifico dentro del documento.

El primer selector combinado es el `.hotdog p`. Este esta formado por dos selectores. El primero es un `type` selector, que al ser de esta forma toma a todos los parrafos y le aplica las propiedades que se indican. Luego el `.hotdog` es un `class` selector, que le dice que esas propiedades solo van a ser aplicadas a los elementos p que esten anidados dentro del elemento con clase hotdog, que en este caso en un div.

El segundo selector contiene tres selectores en realidad. Dos selectores de class, y uno de type. Lo que le dice es que necesita a todos los `<p>` con `class="mustard"`, que esten metidos dentro del elemento con `class="hotdog"`.

Notar que aca esta ocurriendo una sobreescritura en el estilo de uno de los parrafos, porque al principio se les da a todos sin excepcion el color marron, pero luego se le vuelve a indicar que haga una excepcion si ocurre lo que pide.

Esta sobreescritura sucede debido al peso del segundo selector combinado, que es la suma de los pesos de cada selector que lo compone. Si el peso ubiera sido menor, no lo tendria en cuenta.

-----

###### Spaces Within Selectors

Hay que notar la importancia del uso de los espacios cuando se utilizan selectores. 

Se puede ver que el segundo selector, por ejemplo, contiene la combinacion de selectores `.hotdog p.mustard`. La forma de elegir los espacios aca no es trivial. El espacio denota que estas usando un nuevo selector, que te estas refiriendo a otro elemento. Mientras que cuando no se pone un espacio, uno se refiere al mismo elemento. Es por esto que lo anterior se interpreta primero como los elementos con clase hotdog, que dentro tienen un parrafo con clase mustard.

Si por ejemplo, sacariamos el p de ahi, quedando solo `.hotgod .mustard`, lo que haria seria tomar todos los elementos con clase mustard que encuentre dentro del elemento con clase hotdog, sin diferenciar por tipo.

-------

Entonces, finalmente podemos decir que, combinando selectores uno puede seleccionar cualquier elemento que quiera dentro de un documento HTML. 

Veamos como afecta al peso de la especificidad esta combinacion de selectores.

##### Specificity Within Combined Selectors

Cuando los selectores son combinados, tambien se combina la especificidad de cada uno. Esta especificidad se puede calcular contando cada selector diferente dentro de un selector combinado. 

La forma de contar es la siguiente. Tomemos como ejemplo al primer selector combinado de mas atras, el selector `.hotdog p`. Este esta formado de dos selectores, uno de clase, que dijimos que tenia el valor medio `0-1-0` y el otro es de type, que tiene el valor mas chico `0-0-1`. Por lo tanto, combinandolos seria el valor `0-1-1`, que se forma sumando cada uno de los puntos de cada selector.

Cada uno de estos puntos representa cuantos selectores hay de cada tipo. La primer posicion es para selectores `id`, la segunda para los `class` y la tercera para los `type`. Por lo tanto, los puntos de arriba nos estan diciendo que tenemos uno de class y uno de type.

El el segundo selector combinado tenemos dos de class, y uno de type. Por lo tanto, podemos concluir sin hacer la suma que los puntos seran `0-2-1`, que representa 0 de id, 2 de class, y 1 de type. Esto claramente se ve que es superior al anterior, por lo tanto va a tomar mas importancia a la hora de asignar estilos.

Tambien podemos concluir que, lo que cuenta realmente a la hora de ver la jerarquia en una cascada es la cantidad de peso en la especificidad que tengan los selectores. Por lo tanto, si cambiariamos de lugar estos dos selectores, no pasaria nada.

El unico momento en donde la jerarquia se da por orden de abajo hacia arriba de la cascada, es para cuando usamos exactamente el mismo selector. En ese caso necesita darle importancia a uno mas que al otro, y elige hacerlo de abajo hacia arriba.

Por ultimo quiero destacar que el peso de la especificidad va en orden de peso individual. Es decir, ya sabemos que `id > class > type`. Por lo tanto, por mas de que tengas muchos class y type en un selector combinado, la prioridad se le va a dar al type por mas de que sea uno solo. O sea, dados dos selectores, uno con los puntos `0-4-5` y el otro con el peso `1-0-0`, gana el segundo.



### Layering Styles with Multiple Classes

Una forma de mantener los pesos de nuestros selectores lo mas bajo posible es siendo tan modular como sea posible, compartiendo estilos similares de elemento en elemento. Y una forma de ser lo mas modular posible es poniendo capas en diferentes estilos usando clases mutiples.

Los elementos en HTML pueden tener mas de un atributo de clase. Esto se hace separando con espacios los valores del atributo, y puede ser tan largo como querramos. Esto nos permite asignar ciertos estilos a todos los elementos de un tipo mientras que podemos asignar otros estilos mas especificos a algunos elementos del mismo tipo.

Lo que se puede hacer es ir atando estilos que queremos reutilizar continuamente todos a una clase y añadir estilos individuales a cierto elemento o grupo de elementos, referenciando a las clases multiples que se diferencian unas de otras.

Pensa en este caso. Tenemos diferentes links, y cada uno se dirige a un lugar diferente. Queremos que todos los links tengan el mismo tamaño de fuente, pero queremos diferenciar su color segun a donde se dirigan. Una solucion muy buena para esto es usar clases multiples, porque asi podes asignarle a los elementos clases iguales que compartan, pero otras que no lo hagan, y asi poder asignar diferentes estilos a cada uno pero manteniendo uno en comun. Fijate este caso:

```html
<a class="btn btn-danger">...</a>
<a class="btn btn-success">...</a>
```

```css
.btn {
  font-size: 16px;
}
.btn-danger {
  background: red;
}
.btn-success {
  background: green;
}
```

Notar que asigna a ambos links una misma clase que es `btn`, pero ademas le pone a cada uno una diferente porque los quiere diferenciar. Esta clase se la añade con un espacio. Por lo tanto, eso le da la posibilidad de utilizar selectores para cada clase con libertad. Asi elige para una clase la fuente de 16 pixeles, y eso se comparte entre los dos links. Pero despues diferencia en el color poniendo la clase individual.

La ventaja de esto es que los pesos siempre son los mismos en los selectores, todos son de `0-1-0`. O sea, terminas manteniendo pesos bajos y no hay confusiones. Esto es posible porque al ser un solo atributo con multiples clases, igualmente es un atributo solo, por lo tanto, por mas de que tenga mil clases dentro va a seguir con un peso de `0-1-0`. 

Esta es una caracteristica muy util que maneja CSS. Cada clase se puede utilizar con selectores como si fueran todas de atributos diferentes, cuando en realidad estan metidas todas juntas dentro de un mismo valor.

En conclusion, la clave es ir manejando de forma estrategica las clases que comparten los elementos, y tambien las que no comparten, de forma que podamos manipular los estilos de la manera que queramos hacerlo.



### Common CSS Property Values

Antes ya estuvimos viendo algun que otro valor de propiedad, como pueden ser los colores verde y rojo, y alguna otra cosa mas. Pero no se indago mucho en eso.

Ahora vamos a ver bien todas las propiedades y sus valores que vimos atras, e introduciremos nuevas. Nos vamos a centrar mas que nada en colores y medidas.

#### Colors

Todos los colores en CSS estan definidos en sRGB (standard Red, Gren and Blue). Esta es la manera de hacer los colores de forma digital, de la misma manera que funciona un monitor. Se mesclan diferentes tonalidades y se pueden formar casi todos los colores existentes. 

Por ahora existen cuatro formas de representacion de los colores de sRGB en CSS, y estas son las keywords, notacion hexadecimal, y los valores RGB y HSL.

##### Keyword Colors

Las keywords son nombres ya predefinidos para cada color. Estan los colores mas comunes que se suelen utilizar.

La lista completa de todas las palabras esta en [CSS specification](https://www.w3.org/TR/css3-color/). Pero para que nos agamos una idea, cualquier color simple que podamos escribir en ingles esta en esta lista. Por lo tanto, si se quiere usar un color estandar sin mucha modificacion, estos son una buena opcion.

Aca le estamos poniendo a todos los elementos con `class="task"` el color bordo (maroon), y a los `class="count"` el amarillo (yellow).

```css
.task {
  background: maroon;
}
.count {
  background: yellow;
}
```

Una desventaja muy clara de esto es que son opciones limitadas. Aunque hay varios en la lista, no te da la libertad que te da crear un color por tu cuenta.

##### Hexadecimal Colors

Esta es una notacion en hexadecimal para formar colores. Recorda que el hexadecimal contiene los numeros del ``0`` al``9`` y de la ``a`` a la ``f``. En vez de 10, es una a, 11 es una b, 12 es una c, etc. Este codigo se escribe con un `#`, y tres o seis caracteres en hexadecimal. 

Realmente no interesa tanto, aunque sea para nosotros, de que manera se forman los numeros. Simplemente hay que saber que es una notacion posible, y que cuando uno forma colores suele aparecer. 

Lo bueno de esta notacion es que te permite formar varios millones de colores. Para ser exactos, 16.7 millones de colores. 

Hagamos lo mismo que arriba, pero en hexadecimal.

```css
.task {
  background: #800000;  /*maroon*/
}
.count {
  background: #ff0;     /*yellow*/
}
```

Esta forma de usar los colores puede ser complicada igualmente. O sea, no es algo que hagamos por nuestra cuenta, es decir, pensar en el color y escribir su codigo. Si no que por lo general esta bueno usar un software de combinacion de colores. Hay uno excelente, que es [Adobe Kuler](https://kuler.adobe.com/), que te deja hacer mesclas y encontrar relaciones entre colores. 

Y si no, por lo general las aplicaciones para dibujar o editar contienen un panel de colores, en donde se ponen todos los codigos. Ejemplo, el Photoshop o el Paint.

##### RGB & RGBa Colors

Los colores representados en RGB se tienen que colocar utilizando la funcion **rgb( )**, que recibe tres valores separados por coma. Cada uno de ellos puede tener un valor desde 0 a 255. El 0 es negro puro, y el 255 es blanco puro.

Como es de esperarse, el primer numero representa el rojo, el segundo el verde y el tercero el azul. Por ejemplo, el color naranja es `rgb(255, 102, 0)`.

```css
.task {
  background: rgb(128, 0, 0);     /*maroon*/
}
.count {
  background: rgb(255, 255, 0);   /*yellow*/
}
```

Otra posibilidad es usar la funcion **rgba( )**, que es igual pero contiene un canal alfa, o de transparencia. Este numero adicional va de 0 a 1, siendo 0 una transparencia total y 1 la opacidad total. Es el equivalente a manejar con un porcentaje la opacidad del color. 

```css
.task {
  background: rgba(128, 0, 0, .25);    /*maroon 25%*/
}
.count {
  background: rgba(255, 255, 0, 1);    /*yellow 100%*/
}
```

##### HSL & HSLa Colors

HSL viene de Hue (color), Saturation (saturacion) y Lightness (luminosidad). Funciona muy parecido al RGB, pero con la funcion **hsl( )**, la cual toma tres valores.

El primer valor va de 0 a 360, que representa un circulo de colores. Los otros dos valores son un porcentaje que va de 0 a 100%. Usa el simbolo `%`.

```css
.task {
  background: hsl(0, 100%, 25%);
}
.count {
  background: hsl(60, 100%, 50%);
}
```

Y lo mismo. Tambien acepta transparencia con un campo adicional, que va de 0 a 1. La funcion que se utiliza es **hsla( )**.

Este tipo de codigo es relativamente nuevo, y tal vez no tenga tanto soporte como los demas. Es por eso que hoy en dia se sigue optando por el codigo en hexadecimal, para colores normales, y el RGBa para transparencia. Esos son los dos que se usan generalmente.

#### Lengths

Los largos en CSS son un tipo de dato muy util, que posee varios valores diferentes, todos para diferentes propositos. Los largos vienen en dos diferentes formas, absoluta y relativa, en donde cada una usa diferentes unidades de medida.

Solo vamos a ver los valores mas comunes por ahora, ya que valores mas complejos tienen mas poder del que necesitamos por ahora.

##### Absolute Lengths

Los largos absolutos son los valores mas simples, ya que son unidades de medida fisicas, como pueden ser la pulgada, centimetro o el milimetro. La unidad de medida absoluta mas popular es el pixel, representada con la unidad `px`.

###### Pixels

El pixel equivale a 1/96 de pulgada, es decir, en una pulgada hay 96 pixeles. Pero esto puede cambiar segun la densidad de pixeles que tenga un despositivo. 

Los pixels se utilzan hace bastante tiempo, y son usados en muchas propiedades diferentes. Por ejemplo, la que ya vimos varias veces, para ponerle un tamaño a una fuente.

```css
p {
  font-size: 14px;
}
```

Pero el problema de los pixeles es que son una unidad absoluta, por lo tanto no se ajustan a los diferentes tipos de dispositivos. Para una pantalla mas grande o de mayor densidad de pixeles, al ser absoluta se queda siempre de la misma manera. Es por esta razon que ya no son tan utilizados los pixels como unidad de medida, pero aun asi sigue siendo una buena unidad para usar como principiante.

##### Relative Lengths

Los largos relativos utilizan unidades que no son fijas, si no que se mueven en torno a otra unidad. Esto presenta una ventaja a la hora de acomodar tu documento a cualquier pantalla, pero tambien son un poco mas dificiles de usar.

###### Percentages

Los porcentajes son una de los valores relativos mas utilizados. Para usarlo se usa el simbolo de porcentaje `%`, y hay que tener en cuenta que el porcentaje se define en relacion al elemento parent. Es decir, por ejemplo, si ponemos en un selector la propiedad de que queremos un largo de un 50%, le estamos diciendo que queremos que sea la mitad del tamaño que su elemento que lo contiene.

```css
.col {
  width: 50%;
}
```

Los porcentajes son muy utiles a la hora de declarar el largo y alto de las cosas, cuando estamos diseñando nuestra pagina. Vamos a volverlos a ver en el futuro.

###### Em

Esta es otra unidad muy popular, representada por la unidad de medida `em`. Su largo se calcula basandose en la font size de un elemento. Es decir, referencia directamente a un tamaño de fuente.

Esto es, si tenemos un elemento con un tamaño de fuente de 14 px, y su largo es de 5em, entonces su largo va a ser de 70px (14 * 5). 

```css
.banner {
  font-size: 14px;
  width: 5em;
}
```

Que pasa si el `font-size` no esta asignado en ese selector? Bueno, en ese caso el selector se va a basar en el elemento parent mas cercano que posea un tamaño de fuente.

Como era de esperarse, esta unidad se suele usar para darle estilo a un texto. Ya sea su tamaño de fuente, el espacio entre el texto, los margenes y muchas otras cosas, que vamos a ver mas adelante.

Por otro lado, hay una cantidad muy grande de unidades de medida, pero estas tres que vimos son las mas comunes. Ademas, dificilmente uses todas, o las recuerdes, porque son muchas. Asi que no se si tiene mucho sentido verlas todas. La idea es que te quedes con la mas conveniente y listo.

### Summary

Bien, vimos muchas cosas hasta ahora y ya estamos avanzando bastante. Las cosas empiezan a tomar mas sentido. Asi que repasemos lo que vimos en esta seccion para terminar.

Primero hablamos un poco sobre lo que se llama la cascada en CSS, y la forma en que esta se renderiza. Dijimos que lo hace desde abajo hacia arriba, y que tiene en cuenta las superposiciones de selectores de esta manera. Pero esto es siempre y cuando los pesos de su especificidad sean iguales. Vimos luego como se manejan estos pesos, y porque es bueno usar atributos de clase con multiples valores.

Tambien vimos como combinar selectores de manera normal, y como trabaja su peso a medida que se añaden combinan. Por ultimo, vimos algunas propiedades comunes en CSS, como es el color y el largo. Varias formas de combinar y usar colores, y diferetes unidades de medida para cambiar la forma de nuestros elementos.

Todavia nos faltan ver un monton de cosas, pero lo fundamental ya esta empezando a tomar su lugar. Cuando uno entiende como funciona todo por abajo, lo de arriba se entiende mucho mejor.