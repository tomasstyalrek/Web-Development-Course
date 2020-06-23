# Backgrounds & Gradients

Los fondos o backgrounds tienen un impacto muy significativo en el diseño de un sitio web. Ayudan a mostrar lo que uno quiere que se vea y que el usuario sienta al entrar a la pagina, establecen grupos, asigna prioridades a la vista, y tienen mucha influencia en la usabilidad del sitio web.

En fin, cumple todas las reglas de lo que estudia el diseño, y no es aleatoria ni la eleccion de colores ni su distribucion. Todo tiene un sentido. Pero realmente es otra rama de estudio completa.

Nosotros vamos a limitarnos un poco mas a lo que es la definicion de estos colores en la pagina. En CSS los fondos pueden ser de un color solido, una imagen o un gradiente, hasta una combinacion de estos.



### Adding a Background Color

La forma mas rapida y sencilla para declarar un fondo a un elemento es añadiendole un color. Para hacer esto podemos utilizar las propiedades `background` o `background-color`.

Mientras que la primera es la version en shorthand del atributo, en donde uno puede poner colores o imagenes, la segunda es la version longhand mas especifica, solo usado para colores solidos. 

```css
div {
background-color: #b2b2b2;
}
```

En cuanto a como elegir esos colores, podemos utilizar cualquier valor de los que vimos. Ya sea una keyword en especifico, un valor hexadecimal, RGB o HSL. Con transparencia o sin ella.

-----

###### Sobre Backgrounds Transparentes

Es una buena idea setear siempre un doble valor de fondo cuando se utilizan colores con transparencia. Ya que debido al soporte de los navegadores, hay ocaciones en que estos colores no se renderizan.

Especialmente con Internet Explorer 8. Este browser no suele renderizar bien los colores transparentes.

Por esta razon es que lo mejor es asignar a un elemento que posea transparencia, primero un color "seguro", y luego el transparente. De manera que primero renderize el ultimo de la cascada, pero si falla vaya al seguro.

```css
div {
  background-color: #b2b2b2;
  background-color: rgba(0, 0, 0, .3);
}
```

------



### Adding a Background Image

La asignacion de una imagen a un fondo funciona de una forma muy similar a la de un color solido. Solo que las imagenes admiten algunas propiedades adicionales para añadir algunas cosas mas. Para setear una imagen podemos usar, devuelta, la propiedad `background` en su version shorthand, o una mas especifica en version longhand que es `background-image`. Pero sin importar cual usemos, tenemos que utilizar siempre un identificador de la fuente de donde viene esa imagen, usando la funcion `url()`.

Esta funcion `url()` no acepta realmente un URL, si no que necesita el path a la imagen que esta de forma local en tu computadora. Asegurate de ponerlo bien, poniendo de forma explicita las carpetas.

```css
div {
  background-image: url("alert.png");
}
```

Aunque usar esta propiedad sola con el valor `url` puede devolver resultados no deseables. Ya que la imagen, para llenar todo el espacio del elemento, se va a repetir a si misma desde la parte superior izquierda. Pero para que esto no ocurra tenemos disponibles dos propiedades muy utiles. Una de ellas es `background-repeat`  y la otra es `background-position`.

##### Background Repeat

Por defecto una imagen se va a repetir en un elemento, tanto de forma vertical como horizontal, hasta llenarlo por completo. La propiedad `background-repeat` cambia la forma en que una imagen se repite, si es que se repite.

```css
div {
  background-image: url("alert.png");
  background-repeat: no-repeat;
}
```

Esta propiedad admite cuatro valores. Estos son: `repeat`, `repeat-x`, `repeat-y`, y `no-repeat`. El valor por defecto para toda imagen es `repeat`, y es por esta razon que la imagen se repite en ambas direcciones.

Te recomiendo que pruebes esto con una imagen cualquiera. Setea el ancho y alto del elemento a un tamaño mayor al de la resolucion de la imagen, y vas a ver como se repite por defecto.

Luego cambia los valores. Vas a ver que con el valor `no-repeat`, la imagen se va a imprimir una vez sola, y lo demas  del elemento va a seguir normal. Tambien tenes la posibilidad de que se repita solo en el eje horizontal con `repeat-x` y solo en el vertical con `repeat-y`.

##### Background Position

Cuando se setea una imagen, por defecto se posiciona en el extremo superior izquierdo del elemento. Por esa razon existe esta propiedad `background-position`, para poder mover la imagen en relacion al elemento que la contiene. Ya sea que el elemento es un div o algo asi, o el mismo body.

Esta propiedad admite dos valores. El primero hace referencia al movimieto horizontal y el otro al vertical. Si agregas dos valores, el primero lo va a correr la cantidad que le decis desde el lado izquierdo, es decir, hacia la derecha, y el segundo lo mueve desde el top, osea, hacia abajo. Si se pone solo un valor, tira de ambos lados un 50% del valor. 

```css
div {
  background-image: url("alert.png");
  background-position: 20px 10px;
  background-repeat: no-repeat;
}
```

Por ejemplo, esto lo que haria es poner a la imagen a 20px del extremo izquierdo, y a 10px del superior.

Tambien se pueden usar como valores las keywords `top`, `right`, `bottom`, `left`, y `center`. Asi como tambien porcentajes y cualquier unidad de medida.

Por ejemplo, al usar porcentajes, tenes de la misma manera que antes dos valores para indicar. El valor `0 0` va a hacer referencia a la posicion original de la imagen, que seria el extremo superior izquierdo. Luego, por ejemplo, el `0 100%` lo tira al extremo inferior izquierdo. El `100% 100%` lo va a tirar al extremo inferior derecho, y por ultimo el `100% 0` te lo tira al superior derecho.

![CSS Background Positions](https://learn.shayhowe.com/assets/images/courses/html-css/setting-backgrounds-and-gradients/background-position.png)

##### Shorthand Background Image Values

Veamos como es la disposicion de estas cuatro propiedades para las imagenes en su version shorthand. Como ya mencionamos, la version shorthand de esto es la propiedad `background`, y el orden de los valores que toma van en `background-color`, `background-image`, `background-position`, y luego `background-repeat`.

```css
div {
  background: #b2b2b2 url("alert.png") 20px 10px no-repeat;
}
```

Es decir, esta es la forma de meter todas juntas en una misma propiedad. Si no, se pueden usar todas por separado claramente. 

Todas se separan por espacios, como en cualquier valor shorthand.

##### Example

Veamos un ejemplo de como se pueden usar todas estas propiedades, junto con algunas otras, para hacer una especie de barra en donde haya una imagen pegada.

```html
<div class="notice-success">
  Woo hoo! Congratulations, you did it!
</div>
```

```css
.notice-success {
  background: #67b11c url("tick.png") 20px 50% no-repeat;
  border: 2px solid #467813;
  border-radius: 5px;
  color: #fff;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  padding: 15px 20px 15px 50px;
}
```

Podes ver el ejemplo [aca](https://codepen.io/shayhowe/pen/filhe). Notar que esta muy bueno el ejemplo, porque combina un texto con una imagen, y la posiciona de manera que se ve todo muy natural.

Lo que mas interesa aca es la forma en que setea la imagen. Notar que le pone un color verde al background, luego le asigna la imagen y le dice que no se repita, para poder ponerla una unica vez a 20px de la parte izquierda, y a un 50% de la parte superior, que hace que se centre en el medio. 



### Designing Gradient Backgrounds

En CSS3 se introdujeron los fondos en forma de gradiente, aunque hoy en dia, claro que no son soportados por los browsers viejos, como todo estilo nuevo que salga.

Los gradientes son tratados como imagenes en CSS, por lo tanto podemos crearlos tanto con la propiedad `background` o `background-image`. Los valores para estas propiedades cambian dependiendo en que tipo de gradiente se quiera conseguir.

Si te acordas, vimos antes lo que era un "vendor prefix", un prefijo que hacia referencia a un browser, diseñado para añadirle las propiedades que los browsers mas viejos no soportaban. Sin embargo, hoy en dia los browsers eliminaron la necesidad de utilizar prefijos para que los gradientes se rendericen, pero aun asi no es mala idea usarlos por las dudas.

Asi que nosotros los vamos a estar usando en los primeros ejemplos, pero luego los vamos a elminar para que haya mas simplicidad en los ejemplos. Pero siempre recorda que estos prefijos se pueden poner para casos como estos, en donde es probable que los estilos no se rendericen correctamente debido a la antiguedad del browser, y al poco soporte a las nuevas tecnologias.

##### Linear Gradient Background

En algun momento, si se queria hacer un gradiente lo que se tenia que hacer era primero editar la imagen en algun software de procesamiento de imagenes, y luego importarla al documento. 

Te imaginaras que no parece algo muy rapido de hacer. No es un metodo muy flexible. Pero por fortuna hoy en dia se permiten hacer directamente sobre CSS los gradientes lineales, de forma que solo cambiando unos valores ya esta hecho. No se necesita acceder a un software para hacerlo.

```css
div {
  background: #466368;
  background: -webkit-linear-gradient(#648880, #293f50);
  background:    -moz-linear-gradient(#648880, #293f50);
  background:         linear-gradient(#648880, #293f50);
}
```

Como se puede ver, los gradientes lineales se declaran con la funcion `linear-gradient`, que es el valor de la propiedad `background` en este caso, aunque tambien puede ser la propiedad `background-image`, funciona con ambas.

La funcion `linear-gradient` acepta dos valores, correspondientes a el color de inicio del gradiente, y el color en el que termina. El browser maneja la transicion entre los dos colores.

Recorda que siempre es una buena practica asignarle un color antes al elemento, ya que en caso de que el gradiente lineal no sea renderizado correctamente, el color de fondo se va a imprimir sin problemas.

##### Changing the Direction of a Gradient

Los gradientes tambien pueden ser dirigidos. Por defecto un gradiente cambia empezando desde la parte superior de un elemento, hasta la parte inferior. Es decir, es un gradiente de top a bottom. Pero esto puede ser cambiado especificando una keyword como primer parametro de la funcion.

Debe haber como ocho valores disponibles, cuatro lados del elemento, y cuatro esquinas. El valor por defecto es `to bottom`, que hace el gradiente de arriba a abajo. Luego, segun para donde quieras que se diriga, colocas la direccion, es decir `to right`, `to left`, `to top`. 

Siempre se mueve desde el primer parametro de color hasta el segundo parametro.

Luego, tambien tenemos cuatro dedicados a las esquinas. Que se especifican poniendo doble lado, como en `to right bottom`, `to right top`, `to left bottom` o `to left top`. Todos lo tiran desde la esquina contraria hacia la que se indica.

```css
div {
  background: #466368;
  background: linear-gradient(to right bottom, #648880, #293f50);
}
```

Te recomiendo que vayas a un editor, crees unos cuantos divs, y veas la diferencia entre los gradientes. 

Pero no solo se pueden colocar keywords para realizar los gradientes, si no que tambien se aceptan grados. Por ejemplo, setear el valor de un gradiente a `315deg` es lo mismo que poner left top, y poner `135deg` es lo mismo que poner right bottom. Asi se puede poner cualquier grado entre `0` y `360`.

Para mas informacion en el funcionamiento de las keywords en los gradientes lineales visitar [esta pagina](http://meyerweb.com/eric/thoughts/2012/04/26/lineargradient-keywords/).

##### Radial Gradient Background

Hay veces en que uno tiene la necesidad de utilizar un gradiente radial, es decir, que se dirija en todas las direcciones. Este tipo de gradiente comparte muchas de las reglas con el gradiente lineal.

Para utilizarlo podemos utilizar las mismas propiedades, `background` o `background-image`, colocando como valor la funcion `radial-gradient()`.

```css
div {
  background: #466368;
  background: radial-gradient(#648880, #293f50);
}
```

Lo que hace el radial gradient es poner al primer color en el centro absoluto del elemento, y al segundo color en el exterior del elemento. Asi el color hace una transicion desde el centro del elemento hacia todas partes.

Los gradientes radiales son un poco mas complejos en la cantidad de cosas disponibles para su modificacion, que el gradiente lineal. Entre ellas esta la locacion del centro, el tamaño del gradiente, el radio, y mas. Para una informacion mas detallada, consultar en google cuando se necesite algo mas complejo de hacer, o visitar [esta pagina](https://dev.opera.com/articles/css3-radial-gradients/).

Aunque otra opcion es usar una herramienta como [esta](https://www.cssmatic.com/), que es una pagina que te permite realizar un gradiente a mano, y luego te da el codigo en CSS para implementarlo.

##### Gradient Color Stops

Los color stops no son mas que una serie de colores separados por comas, que se especifican dentro de la funcion de gradiente. 

Poner mas de dos colores en un gradiente va a hacer que el gradiente haga la transicion entre todos los colores que le indicas.

```css
div {
  background: #648880;
  background: linear-gradient(to right, #f6f1d3, #648880, #293f50);
}
```

Intenta probarlo. Pone un div, y mandale mas de dos colores.

El browser lo que va a hacer es una transicion de colores, y pone a todos a una distancia igual, para que niguno ocupe mas que el otro. Pero si quiesieras algun color con mas precencia que otro, necesitas mandar un porcentaje a la derecha del que queres.

```css
div {
  background: #648880;
  background: linear-gradient(to right, #f6f1d3, #648880 85%, #293f50);
}
```

Si no se especifican los demas, como en este caso, pone a los otros dos iguales, y el del medio ocupa el 85% del elemento.

##### Example

Aca hay un ejemplo de todos los tipos de gradientes en uno solo.

```html
<div class="gradientToTop">
  Linear Gradient To Top
</div>
<div class="gradientToBottom">
  Linear Gradient To Bottom
</div>
<div class="gradientToRight">
  Linear Gradient To Right
</div>
<div class="gradientToLeft">
  Linear Gradient To Left
</div>
<div class="gradientToRightTop">
  Linear Gradient To Right Top
</div>
<div class="gradientToRightBottom">
  Linear Gradient To Right Bottom
</div>
<div class="gradientToLeftTop">
  Linear Gradient To Left Top
</div>
<div class="gradientToLeftBottom">
  Linear Gradient To Left Bottom
</div>
<div class="gradientCircular">
  Linear Gradient in a Another Shape
</div>
<div class="gradientRadial">
  Radial Gradient by Default
</div>
<div class="gradientThree">
  Linear Gradient with Three Colors
</div>
```

```css
div {
  font-family: sans-serif;
  width: 100%;
  height: 50px;
  margin-bottom: 5px;
  font-size: 10px;
  color: white;
  line-height: 50px;
  text-align: center;
}
.gradientToTop {
  background: linear-gradient(to top, #10038F, #10FA8F);
}
.gradientToBottom {
  background: linear-gradient(to bottom, #10038F, #10FA8F);
}
.gradientToRight {
  background: linear-gradient(to right, #10038F, #10FA8F);
}
.gradientToLeft {
  background: linear-gradient(to left, #10038F, #10FA8F);
}
.gradientToRightTop {
  background: linear-gradient(to right top, #10038F, #10FA8F);
}
.gradientToRightBottom {
  background: linear-gradient(to right bottom, #10038F, #10FA8F);
}
.gradientToLeftTop {
  background: linear-gradient(to left top, #10038F, #10FA8F);
}
.gradientToLeftBottom {
  background: linear-gradient(to left bottom, #10038F, #10FA8F);
}
.gradientCircular {
  width: 200px;
  border-radius: 50%;
  background: linear-gradient(to left bottom, #10038F, #10FA8F);
}
.gradientRadial {
  background: radial-gradient(#F2521B, #E6253B)
}
.gradientThree {
  background: linear-gradient(to left ,#F2BF1B, #E6253B, #3A57F5)
}
```



### Using Multiple Background Images

En algun momento, solo estaba permitido el uso de una sola imagen para colocar en el background de un elemento. Hoy en dia, CSS3 permite la utilizacion de mas de una imagen, separando con comas a cada valor en la propiedad `background` o `background-image`.

La primer imagen que se dispone como valor va a ser la que esta mas adelante, la primera de todas. Mientras que la ultima va a ser la que esta atras de todo. Lo mismo pasa con la posicion de las del medio.

```css
div {
  background:  url("foreground.png") 0 0 no-repeat, url("middle-ground.png") 0 0 no-repeat, url("background.png") 0 0 no-repeat;
}
```

Recordar que al usar la propiedad `background`, se esta usando una propiedad shorthand, y sus valores iban en orden de color, imagen, posicion y repeat. En este caso, se enlistan tres imagenes, que poseen el primer valor que es el archivo de la imagen, el segundo son dos valores que representan la posicion y el tercero es el repeat.

Si no se quiesiera poner en la forma shorthand, habria que enlistar todas las imagenes separadas por comas y luego realizar lo mismo para la posicion y el repeat.

Esta funcionalidad esta bueno usarla en los casos en que queres poner una imagen y un gradiente, entre muchos otros. Porque recorda que un gradiente no es mas que una imagen, por lo tanto, puede ser puesto con otra.

Esto es, tanto en la parte de atras, es decir, que la imagen este adelante y el gradiente de fondo, como tambien puede estar adelante el gradiente y ser transparente. Ambas son posibles utilizaciones.

Por ejemplo, podriamos tener un logo, que es una imagen, y la unica forma de poder hacer un gradiente a un elemento, y agregarle un logo delante, es separar por comas. O por ejemplo, la otra vuelta vi a un flaco poner un gif de fondo en la lanfing page, y le puso un gradiente transparente adelante para hacerle como un filtro verdoso.

Ejercicio: Descargate un logo de una tilde o algo asi, y hace una barra de "success", como indicando que hiciste bien algo. Mandale un gradiente a la barra, y el logo a la izquierda, con un mensaje de que salio bien algo.



### New Background Properties

En CSS3 se añadieron tres propiedades nuevas al background. Estas son `background-size`, `background-clip`, y `background-origin`.

La propiedad `background-size` te permite redimensionar una imagen, mientras que las propiedades `background-clip` y `background-origin` te permiten controlar en donde una imagen es cortada y en donde la imagen esta contenida dentro del elemento (dentro del borde o del padding, por ejemplo).

##### CSS3 Background Size

Esta propiedad te permite asignarle un tamaño a todo el background de un elemento. Con esto quiero decir que si tenemos mas de una imagen de background, como en el ejemplo anterior, el resizing se le va a aplicar a todo.

Este size que le asignamos puede ser de cualquier unidad. Si utilizamos porcentajes, hay que tener en cuenta que estos hacen referencia no a la imagen en si, si no al elemento. Es decir, si le poner un tamaño del 75%, va a tomar el 75% del tamaño del elemento que lo contiene.

Los valores se pueden especificar separando con espacios, en donde el primer valor representa el ancho del elemento, mientras que el segundo valor representa el alto del elemento.

Si solo pones un valor, la imagen va a preservar su forma, y se va a acomodar a lo que pongas. Por ejemplo, si pones 100%, la imagen se queda con su forma y ademas se acomoda a todo el espacio disponible del elemento.

Hay otra posibilidad que es usar la keyword `auto`. Esto funciona reemplazando por el valor correspondiente del width o height. Lo que hace es indicar que queres mantener la forma original de la imagen, pero queres modificar su tamaño. La diferencia con poner un solo valor es que este te permite asignarle este tamaño en referencia a su alto o ancho. 

Por ejemplo, si pones el valor `auto 75%`, le estas diciendo que queres que la imagen conserve su forma, pero redimensionando el alto. Si en cambio pusieras `75% auto`, seria al revez, estas indicando que queres un ancho del 75% del elemento, pero manteniendo la forma.

```css
div {
  background: url("shay.jpg") 0 0 no-repeat;
  background-size: auto 75%;
  border: 2px dashed #9799a7;
  height: 240px;
  width: 200px;
}
```

##### Cover & Contain Keyword Values

Hay dos keywords mas que se pueden utilizar en lugar de poner valores numericos a la propiedad `background-size`, que son `cover` y `contain`.

El valor `cover` va a ajustar la imagen para que ocupe todo el elemento. La imagen preserva su forma original, pero es ajustada a los extremos. Esto significa que tal vez haya partes de la imagen que se cortan. Si te pones a pensarlo, solo estaria ajustando la imagen al lado mas largo del elemento, y el otro termina cortando la imagen, porque esta debe mantener su forma.

El valor `contain`, al contrario del anterior, va a achicar la imagen, preservando su forma original, hasta que esta este contenida dentro del elemento. O sea, puede que la imagen no ocupe el total del elemento, pero se va a ver entera si o si.



##### CSS3 Background Clip & Origin

La propiedad `background-clip` especifica el area de superficie que una imagen de fondo va a cubrir, y la propiedad `background-origin` especifica en donde la propiedad `background-position` se origina. 

Esto lo hacen en referencia a las partes del box model del elemento. Por eso tienen ambos tres valores disponibles, que son `border-box`, `padding-box` y `content-box`.

```css
div {
  background: url("shay.jpg") 0 0 no-repeat;
  background-clip: padding-box;
  background-origin: border-box;
}
```

Estas propiedades ya vienen seteadas a un valor por defecto. La `background-clip` ya viene con el valor `border-box` por defecto, es por esta razon que una imagen se puede extender por defecto hasta los bordes, y no los cubre. Esto es lo maximo que se puede extender. Y luego, la propiedad `background-origin` ya viene en `padding-box` por defecto, asi permite que el comienzo de la imagen se extienda por el padding.

Si queres intenta ver que pasa si pones una imagen de fondo y le aplicas padding. Vas a ver que no se mueve de su lugar, pero si tal vez lo haga el texto, si es que hay texto. Esto es por causa de la ultima pripiedad, que le dice a la imagen que tiene permitido extenderse hasta el padding.

Asi podes hacer todo tipo de combinaciones. Podrias extender la imagen hasta el borde, o ajustarla al contenido, de modo que quedaria un espacio si es que hay padding.

