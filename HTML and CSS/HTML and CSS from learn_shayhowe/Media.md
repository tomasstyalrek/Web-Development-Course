# Adding Media

Cuando buscamos en internet tenemos acceso a una cantidad gigante de informacion, y mucha de ella viene en forma de texto plano (plain text). Pero para acompañar a este texto, HTML provee una forma de introducir media en forma de imagenes, videos y audios, como tambien meter en tu pagina contenido de otra pagina por medio de un cuadro en linea.

Hoy en dia las imagenes y los cuadros en linea son soportados por todos los browsers en general, mientras que los videos y los audios, aunque tambien tienen una buena covertura, el proceso es un poco diferente todavia. 

Pero podriamos decir que se pueden utilizar con libertad relativamente en todos los browsers, hoy en dia, todo lo que refiere a media.



### Adding Images

Para añadir imagenes a una pagina tenemos que utilizar el elemento en linea `<img>`. Este elemento es auto contenido, es decir, no necesita cerrarse ni encerrar a otro contenido para que exista como tag. Es decir, no necesita texto dentro ni nada por el estilo.

Este atributo necesita de un atributo `src` para su funcionamiento. Este atributo especifica el source o fuente en donde se encuentra el archivo. Por lo general hace referencia a un archivo en tu computadora, o a un URL, que tipicamente es relativo al server en donde esta contenida una pagina.

Y adicionalmente esta el atributo `alt`, que viene de "alternative text". Este atributo deberia ponerse siempre, ya que es un texto que describe a la imagen. Lo usan los buscadores para saber de que trata tu imagen y tambien es el texto que se va a imprimir en pantalla en lugar de la foto, si esta no se renderiza por alguna razon.

```html
<img src="dog.jpg" alt="A black, brown, and white dog wearing a kerchief">
```

Por otro lado, las imagenes poseen diferentes tipos de formatos, y los browsers pueden o no soportarlos. Pero hay tres tipos de formatos que son los mas usados, ya que son aceptados por todos los browsers. Estos son los formatos `gif`, `jpg` y `png`.

De estos tres los que mas suelen usarse son el `jpg` y el `png`. El `jpg` ofrece un rango mayor de colores y mantiene un tamaño dentro de todo manejable, por eso es que se suelen usar para fotografias dentro de la web. El `png` es mejor para transparecias y fotografias con poca cantidad de colores, y es por eso que se suele usar para iconos y patrones de fondo.

##### Sizing Images

Es importante darle un tamaño a la imagen que uno coloca en el documento, para darle a entender al browser de que tamaño va a tener que renderizar esa imagen antes de que carge la pagina. Asi el browser puede reservar espacio para la imagen, y cargar todo mas rapido.

Una opcion para especificar el tamaño de la imagen es utilizando los atributos `width` y `height`, dentro del tag `<img>` directamente.

La otra opcion es colocar las propiedades en CSS, y en ese caso, la prioridad la tienen ellas. Ya que los estilos primero se cargan en CSS y despues en HTML.

En caso de colocar el alto o ancho de la imagen, el otro valor se va a ajustar automaticamente para mantener el aspecto de la imagen. Es decir, si ponemos un `width` de 200px, el height se va a cambiar solo para mantener la forma original de la imagen.

Uno puede cambiar los dos, y cada uno se va a manejar por separado, pero corre el riesgo de que la imagen quede rara, con un cambio en su forma original.

```css
img {
  height: 200px;
  width: 200px;
}
```

Es comun usar los atributos `width` y `height` dentro de HTML directamente, esto provee algun valor semantico adicional. Pero en caso de tener que manejar una cantidad grande de imagenes, y querer que todas tengan el mismo tamaño, lo mejor es usar CSS por simplicidad.



#### Positioning Images

Las imagenes por defecto son posicionadas en una pagina como elementos en linea, pero podemos cambiar su posicion con cualquiera de las maneras que ya vimos, que son especificando las propiedades `float`, `display`, o sus propiedades del box model como el `padding`, `margin` y el `border`. Es decir, cualquiera de las formas ya vistas, ya que una imagen se comporta de la misma manera que cualqueir elemento.

##### Inline Positioning Images

Consideremos este ejemplo:

```html
<p>Gatsby is a black, brown, and white hound mix puppy who loves howling at fire trucks and collecting belly rubs. <img src="dog.jpg" alt="A black, brown, and white dog wearing a kerchief"> Although he spends most of his time sleeping he is also quick to chase any birds who enter his vision.</p>
```

El elemento `<img>` es un elemento en linea, esto quiere decir que se va a colocar exactamente en la posicion que le indicas dentro de un texto. Tambien podes colocarlo dentro de un parrafo como arriba.

Lo que termina pasando en un caso de esos es que el alto de la linea se termina acomodando al alto de la imagen. De esa manera permite incrustar a la imagen alrededor del texto. Realmente no es algo muy estetico, pero bueno. 

Es mucho mas comun tratar a la imagen como un elemento en bloque, y haciendo un floating, tirarla hacia un costado haciendo que el texto que acomode a ella, formando un contorno alrededor.

##### Block Positioning Images

Forzar a la imagen a ser un elemento en bloque, especificandolo en su propiedad `display`, hace que la imagen se comporte como un bloque que aparece en una nueva linea, rodeado por contenido en la parte superior o inferior.

```css
img {
  display: block;
}
```

##### Positioning Images Flush Left or Right

A veces cambiarle la propiedad `display` a un elemento no es la mejor opcion para posicionarlo. Y mas con imagenes, en donde algo muy comun que se quiere conseguir es lograr que la imagen se posicione a un costado, y que el contenido que lo rodea lo encierre.

Bueno este es el funcionamiento principal de la propiedad `float`, es decir, para esto fue diseñada principalmente. Para utilizarlo con imagenes. Esto se logra dandole a la propiedad del selector de la imagen, el valor left o right, dependiendo de donde quieras colocarla dentro de su elemento contenedor. Lo que va a hacer esto es colocar a la imagen a un costado, tomando como referencia al elemento que contiene a todo el contenido. 

Luego uno arregla a la imagen como desee, añadiendo un margen si es que la imagen toca al contenido, o un borde para encerrarla en algo. Eso ya esta bastante evidente.

##### Cuando usar un elemento Image vs un Background Image

Si uno lo piensa, ambas formas funcionan de la misma manera. Una crea un elemento que directamente es una imagen, y el otro pone de fondo en el elemento a una imagen. Es decir, con un div y una imagen de fondo, se podria alcanzar lo mismo que con una imagen.

Pero en realidad tienen diferentes propositos, y, como seguramente ya te diste cuenta, son semanticos. 

El elemento `<img>` es recomendable usarlo cuando la imagen contiene dentro algo que importa y es relevante al contenido de la pagina, es decir, que posee contenido con valor semantico. 

Es cambio la propiedad `background` o `background-image` se utiliza mas para propositos de diseño en una pagina y de interaz de usuario. No tiene que estar directamente relacionada al contenido de la pagina. 



### Adding Audio

HTML5 provee ademas una forma de añadir a una pagina un archivo de audio. Esto se hace con el elemento `<audio>`, que al igual que el elemento `<img>` necesita de un atributo `src` en donde se especifica el archivo de audio o el url del archivo. Pero a diferencia de las imagenes, este elemento tiene que cerrar el tag.

```html
<audio src="jazz.ogg"></audio>
```

##### Audio Attributes

Los atributos mas populares al usar audio son `autoplay`, `controls`, `loop` y `preload`.

Los atributos `autoplay`, `controls` y `loop` son atributos booleanos, es decir, basta con poner su nombre para que se tomen como atributos del elemento. No llevan true o false ni nada por el estilo.

Por defecto, el elemento audio no se imprime en pantalla, no es un elemento que sea visible. Con el atributo `autoplay` el audio se va a escuchar de fomra automatica, va a empezar solo, pero igualmente no se va a ver en pantalla.

```html
<audio src="jazz.ogg" autoplay></audio>
```

Con el atributo `controls` lo que logramos es que el audio se imprima en pantalla, utilizando los controles basicos que provee el browser. Este controlador viene con boton de play y pausa, volumen, y una barra de desplazamiento.

```html
<audio src="jazz.ogg" controls></audio>
```

Ademas, el atributo `loop` va a hacer que el audio se repita una y otra vez, de principio a fin.

Por ultimo, el atributo `preload` sirve para dar informacion que necesite ser cargada antes que el audio comience. Es decir, son metadatos sobre el audio que tal vez necesite. Tiene tres posibles valores, que son `none`, `auto` y `metadata`. El valor `none` no va a cargar ningun tipo de dato sobre el audio antes de que este se ejecute, mientras que `auto` va a cargar la informacion del archivo de audio. Y el `metadata` es como que esta entre medio de los otros dos, no carga todos los datos, solo el largo del clip y otras cosas mas.

Resulta que el atributo `preload` ya esta por default en `auto`. Esto es, va a cargar todos los datos que posee el archivo. Por lo tanto, poder cambiar el valor del atributo es una herramienta util en caso de que el audio no sea esencial a la pagina, ya que esto ahorraria ancho de banda y el tiempo de cargado de la pagina tal vez seria menor.

##### Audio Fallbacks & Multiple Sources

Los principales formatos de audio que admiten los browsers son `ogg`, `mp3` y `wav`. 

Ya que, como siempre, segun el browser el cargado de las cosas puede fallar, es bueno tener audios de reserva, o darle al browser mas de un formato de audio del mismo audio, por las dudas. Esto lo podemos lograr asignando varios sources a los audios dentro del contenido del elemento audio. 

Esto se logra, primero, sacando el atributo `src` del elemento `<audio>`, y luego utilizando los elementos `<source>` dentro del mismo. 

Estos elementos `<source>` llevan dos atributos, uno es el `src` para identificar la ruta del archivo, y el otro es `type`, que le indica al browser identificar rapitadamente cuales archivos de audio estan disponibles. En caso de que puede cargar uno, los demas ya los descarta. Solo termina sonando uno.

```html
<audio controls>
  <source src="jazz.ogg" type="audio/ogg">
  <source src="jazz.mp3" type="audio/mpeg">
  <source src="jazz.wav" type="audio/wav">
  Please <a href="jazz.mp3" download>download</a> the audio file.
</audio>
```

Notar que, como ultimo caso puso un link para descargar el archivo de audio, en el caso de que el browser no pudiera ejecutarlo. 

Tambien notar que los atributos para el audio siguen en el mismo lugar. Solo sacamos de los atributos al `src`.



### Adding Video

De la misma manera que ponemos audio en una pagina, se puede colocar un video con el elemento `<video>`. Este elemento admite los mismos atributos y los fallbacks que el elemento de audio. 

La diferencia es que aca, aunque no pongamos el atributo `controls`, el video se va a imprimir en pantalla, pero no se si es una muy buena practica. Ya que el video solo se va a reproducir, sin dejar al usuario controlarlo. Por eso es que se suele usar siempre el atributo controls en este elemento, a menos que se tengan rasones para no dejar al usuario controlar la reproduccion del video.

Tambien es una buena practica utilizar en CSS las propiedades `width` y `height`, para darle una dimension fija a los videos. De esta forma el browser ya sabe de antemano cuanto espacio reservar para renderizar el video, y ademas el video no toma las dimensiones que quiere. Es decir, funciona de la misma manera que las imagenes.

```html
<video src="earth.ogv" controls></video>
```

Intenta hacer lo mismo en un ejemplo, con un video que encuentres. Lo que va a pasar es que te va a aparecer un controlador que provee por defecto el browser. 

Una realidad tambien es que, a medida que la personalizacion de tu pagina crece, uno tal vez quiera cambiar el aspecto del controlador por default que ofrece el browser. Pero hay que saber que esto puede ser hecho, pero se necesita un poco de trabajo con JavaScript.

##### Poster Atributte

Un atributo adicional del elemento `<video>` es el atributo `poster`. Este nos permite asignarle al video una imagen para que sea impresa como presentacion del video, es decir, antes de que este se reprodusca. 

```html
<video src="earth.ogv" controls poster="earth-video-screenshot.jpg"></video>
```

Esto seria como lo que hace YouTube con los videos, que tienen colocado una imagen de presentacion. Esta imagen se puede poner al azar, o la puede elegir el usuario. Lo que realmente esta asignando es este atributo.

##### Video Fallbacks

Al igual que con los audios, podemos utilizar los elementos `source` para indicar los archivos de video a los que va a recurrir el browser. Los archivos que son aceptados por lo general son `mp4` y `ogg`.

Aunque otra posibilidad es elegir a un servicio de hosting de video como la pagina que contiene a tu videos almacenados, y mediante un link inctrustar ese video en tu pagina. Los servicios de hosting elegidos suelen ser YouTube o Vimeo, ya que solo tendriamos que subir nuestros videos ahi, y hacer un embedded video en nuestra pagina con un inline frame.



### Adding Inline Frames

Una forma muy util de imprimir contenido en tu pagina es utilizando un inline frame. Esto permite agregar contenido de otro documento HTML, a tu documento, metiendolo entre medio. Esto se puede lograr con el elemento `<iframe>`, colocando el atributo `src` con el valor del URL en donde esta contenido lo que queres.

Una posibilidad es recurrir a un URL relativo a la pagina en donde esta el elemento `<iframe>`, es decir, para que tome como referencia el iframe de la otra pagina y lo ponga en la tuya, o tambien se puede asignar el URL absoluto a la pagina externa.

Realmente esto no es solo para videos, si no que es para cualquier servicio que se quiera utilizar, como por ejemplo el Google Maps. 

Estoy seguro, igualmente, que el tema es un poco mas complejo que esto, y es necesario conocer como funciona la API del servicio que queres utilizar. Esto es para utilizar videos, mapas, servicios de pagos, y mucho mas seguramente.

Al conocer como funciona la aplicacion que provee el servicio, o creo que podes hacer incrustaciones de forma correcta en tus paginas.

Para mas informacion siempre es una buena idea recurrir a las APIs de los servicios. Todos deberian tener una.



### Semantically Identifying Figures & Captions

En HTML5 se introdujeron los elementos `<figure>` y `<figcaption>`, dos elementos para poder identificar de forma semantica a media dentro de una pagina. Antes se hacia con una lista ordenada, y aunque funcionaba, no tenia un buen valor semantico.

##### Figure

El elemento en bloque `<figure>` se utiliza para identificar y encerrar contenido "media", como pueden ser imagenes, videos, audios, bloques de codigo, diagramas, ilustraciones y otros. Puede contener mas de un elemento dentro. 

```html
<figure>
  <img src="dog.jpg" alt="A black, brown, and white dog wearing a kerchief">
</figure>
```

##### Figure Caption

El elemento `<figcaption>` es usado siempre dentro de un elemento `<figure>` para añadir un subtitulo a una figura. Un subtitulo cumple la funcion de tener una referencia a lo que pasa en la figura, es una anotacion. 

No importa en que parte de la figura se coloque, si arriba de todo, o abajo o en cualquier parte, porque siempre se coloca al fondo del contenido. Solo se puede poner una vez sola.

Ademas, es posible reemplazar el atributo `alt` de la imagen si es que el caption describe bien a la imagen. Es decir, puede que haya una repeticion con el alt y el caption, y por eso tla vez lo pueda reemplazar.

```html
<figure>
  <img src="dog.jpg">
  <figcaption>A beautiful black, brown, and white hound dog wearing kerchief.</figcaption>
</figure>
```

Notar que no es absolutamente necesario colocar una figura en los archivos media del documento. Solo es necesario incluir a aquellos que son self-conteines, es decir, que su contenido no depende de los demas. 

Ya estamos terminando mas o menos con esto. Nos quedan un par de cosas mas, como formularios y tablas. Pero ya casi que estamos. Con todo esto ya tenemos las herramientas para hacer una interfaz, por lo menos, que sea muy completa. Solo se necesita imaginacion y mucha practica. Lo mas importante de todo es practicar, porque si no se te van olvidando las cosas.

