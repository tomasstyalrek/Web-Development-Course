Building Forms

Los formularios son una parte muy importante de toda pagina web. Estan presentes en muchas de ellas, ya que es la principal forma de obtener input por parte del usuario que entra a la pagina. Con esa informacion que nos da el usuario nosotros somos capaces de procesarla y devolverle un output. Ademas, hoy en dia los formularios ofrecen controles para casi cualquier tipo de aplicacion que se quiera crear. Desde una aplicacion muy chica, en donde solo se requiera un usuario y contraseña, hasta aplicaciones entreras.

En esta leccion vamos a aprender a darle estructura a los formularios, que elementos podemos usar para capturar diferentes tipos de datos, y como darles un estilo a los formularios con CSS. Lo que no vamos a ver por ahora es como manejar esos datos por la parte de atras, es decir, en la aplicacion del servidor. Se nos va un poco del alcance en este momento.



### Initializing a Form

Para añadir formularios a una pagina, tenemos que utilizar el elemento `<form>`. Este elemento le da la ubicacion al formulario e indica en donde tienen que aparecer los controles. Ademas, encierra a todos los elemetnos que pertenecen dentro del formulario, como pueden ser los  divs. 

```html
<form action="/login" method="post">
  ...
</form>
```

Hay dos atributos que utilizo que son muy comunes dentro de los formularios. El primero es `action`, e indica el URL de la pagina a donde va a ser enviada la informacion del usuario, es decir, es una pagina hosteada por el servidor en donde se encuentra la aplicacion que procesa la informacion. El segundo es el atributo `method`, que indica el HTTP method que se enviara en el request al servidor. 

Este elemento no es el unico que hay que utilizar para crear formularios, pero es necesario para poder inicializarlo.



### Text Fields & Textareas

Hay diferentes campos que se pueden agregar para especificar que tipo de string se va a poner en el input que de el usuario. Esto no solo que es importante a nivel semantico, si no que ayuda a toda la interfaz realmente.

##### Text Fields

Para obtener un input por parte del usuario, uno de los elementos mas utilizados es el `<input>`. Uno de sus atributos mas recurridos es el `type`, que se encarga de especificar que tipo de informacion va a ser capturada por ese input. El valor mas comun es `text`, que indica que en el input se va a colocar texto.

Probablemente, si el browser es medio viejo, el valor que va a tener el type es el text. Ya que antes los browsers solo tomaban ese valor. Ademas, es el que van a tomar por defecto en caso de que no encuentre el tipo que especificas. Este valor funciona bien realmente, pero los otros le dan un poco mas de semantica al formulario, y ademas, el browser puede proveer una mejor experiencia.

Otro atributo que se considera una buena practica colocarlo junto con `type` es el atributo `name`. Este atributo se usa para darle un nombre al control y ademas se envia junto con los demas datos al servidor. Mientras que el type muestra que tipo de dato, o para que se va a utilizar esa informacion, esto muestra el nombre del campo.

```html
<input type="text" name="username">
```

Como podras ver, `<input>` es un elemento auto contenido, esto es, no necesita cerrarse ni de ningun contenido dentro. 

En realidad, los browsers antes solo soportaban los valores del `type` que eran `text` y `password`, solo para lo que indica. Es decir, no habia ningun tipo de forma de diferenciar contenido. En cambio en HTML5 se añadieron muchos tipos nuevos, que son `color`, `date`, `datetime`, `email`, `month`, `number`, `range`, `search`, `tel`, `time`, `url`, `week`.

Algo muy positivo de utilizar el correcto tipo es que el browser se va a acomodar, por lo menos en celulares, a poner el teclado que necesita segun el tipo. Por ejemplo, estos son los diferentes tipos en IOS.

![iOS7 Date Control](https://learn.shayhowe.com/assets/images/courses/html-css/building-forms/ios-date.png)

Esto es con un valor `type` que es `date`.

![iOS7 Time Control](https://learn.shayhowe.com/assets/images/courses/html-css/building-forms/ios-time.png)

Esto es con valor `time`.

![iOS7 Email Control](https://learn.shayhowe.com/assets/images/courses/html-css/building-forms/ios-email.png)

Valor `email`.

![iOS7 Telephone Control](https://learn.shayhowe.com/assets/images/courses/html-css/building-forms/ios-tel.png)

Valor `tel`.

```html
<input type="date" name="birthday">
<input type="time" name="game-time">
<input type="email" name="email-address">
<input type="url" name="website">
<input type="number" name="cost">
<input type="tel" name="phone-number">
```

Aca se pueden ver los posibles nombres que podrias darle a cada tipo. Esto depende de que sea el input.

##### Textarea

El elemento `<textarea>` se utiliza para porciones mas largas de texto. Es decir, funciona de la misma forma que el input, pero se usa para poner una cadena de texto larga, y es por eso que el cuadrado que forma es mas ancho. Solo acepta el atributo `name`, ya que el `type` siempre es de texto. Por lo general, siempre lo usamos como una caja de comentarios.

```html
<textarea name="comment">Add your comment here</textarea>
```

<textarea name="comment">Add your comment here</textarea>

Ese es un ejemplo de como se imprime en pantalla el area de texto.

Ademas, posee dos atributos utilizados para darle tamaño al area. Uno de ellos es `cols` que especifica la cantidad de columnas que acepta el cuadro, refiriendose a cada caracter de ancho. Y lo mism el atributo `rows`, que hace referencia a las filas de lineas de caracteres. Entonces, el primero especifica cuantos caracteres entran por linea, por lo tanto agranda el ancho, y el otro cuantas lineas entran en total.

Pero claro que tambien podemos cambiarle la apariencia y el tamaño en CSS. Ademas le podemos cambiar los bordes y demas.



### Multiple Choice Input & Menus

Tambien se ofrecen diferentes formas para mostrar opciones dentro de los formularios, que pueden ser botones de opcion multiple que puedas tocar, o tambien listas que se extiendan y dejen ver mas opciones. 

##### Radio Buttons

Los radio buttons son una forma de permitirle al usuario que haga una eleccion entre varias opciones, pero solo le permite tomar una de ellas.

Para crear un radio button, hay que utilizar el elemento `<input>` junto con el atributo `type` seteado al valor `radio`. Ademas, hay que poner cada opcion con el musmo valor en el atributo `name`, para que el browser entienda que todos pertenecen a los mismos tipos de opciones.

Ademas, necesitamos agregarle un texto, para que el usuario pueda saber cuales son las opciones a elegir. Esto se hace colocando un contenido a la derecha del input, pero poniendo dentro de elemento el `value` que corresponde. Esto es mas algo semantico que otra cosa.

```html
<input type="radio" name="day" value="Friday" checked> Friday
<input type="radio" name="day" value="Saturday"> Saturday
<input type="radio" name="day" value="Sunday"> Sunday
```

Notar que hay un atributo booleano que no mencionamos, que es `checked`. Este atributo indica cual opcion debe estar marcada por defecto.

##### Check Boxes

Las check boxes funcionan de misma manera que los radio buttons, solo que en este caso hau dos excepciones. Una es que el atributo `type` debe ir seteado en `checkbox`, y el otro es que este admite multiples opciones marcadas. Luego, se comporta de la misma manera, y tiene los mismos atributos que el anterior.

```html
<input type="checkbox" name="day" value="Friday" checked> Friday
<input type="checkbox" name="day" value="Saturday"> Saturday
<input type="checkbox" name="day" value="Sunday"> Sunday
```

Proba ponerlo en el documento. El estilo segun el browser cambia, pero es bastante decente.

##### Drop-Down Lists

Una lista es lo mismo que un radio button, en el sentido de que solo se puede elegir una opcion. La lista esta pensada para poder acultar una larga lista de opciones bajo una pestaña, asi ahorrando espacio y legibilidad. 

Para poder usar listas, usamos los elementos `<select>` y `<option>`. El elemento `<select>` encierra todas las opciones para colocar en la lista, y el elemento `<option>` representa a cada una de esas opciones. 

El atributo `name` le corresponde al elemento `<select>`, mientras que el atributo `value` le corresponde a cada elemento `<option>`. Cada uno de los valores que se le de al atributo `value` debe hacer referencia al name del select que los encierra.

Ambos, el `<select>` y el `<option>` son elementos que deben cerrarse a si mismos. El select porque tiene que encerrar a los options, y los option encierran un contenido, qye es lo que se le muestra al usuario. 

Por ultimo, al igual que el atributo booleano `checked` de antes, aca esta el atributo `selected`.

```html
<select name="day">
  <option value="Friday" selected>Friday</option>
  <option value="Saturday">Saturday</option>
  <option value="Sunday">Sunday</option>
</select>
```

Esto va a mostrar una lista desplegable con tres opciones, siendo "Friday" la que ya viene seleccionada por defecto.

##### Multiple Selections

Este caso es un poco mas particular. Funciona en las listas desplegables, pero te permite elegir mas de una opcion. Esto se hace colocando el atributo booleano `multiple` en el elemento `<select>`, y ademas, la consecuencia es que podes usar el atributo `select` en los option mas de una vez.

El tamaño del elemento `<select>` lo podes ir modificando en CSS para que te aparescan mas o menos opciones. La forma de utilizar este tipo de listas es presionando shift y eligiendo mas de una opcion. Asi te permite seleccionar sin perder las anteriores. Es una forma bastante inusual de lista.

```html
<select name="day" multiple>
  <option value="Friday" selected>Friday</option>
  <option value="Saturday">Saturday</option>
  <option value="Sunday">Sunday</option>
</select>
```



### Form Buttons

Luego de que el usuario haya llenado el formulario, necesitamos una manera de que este pueda enviar esa informacion. Para esto usamos un submit input o un submit button.

##### Submit Input

La primer forma de poder crear un boton con el cual el usuario pueda enviar la informacion es utilizando un elemento `<input>`. Esto se hace colocando el atributo `type` con el valor `submit`. Ademas admite un name, que es lo de siempre, y aca el atributo `value` contiene el texto que muestra el boton.

```html
<input type="submit" name="submit" value="Send">
```

##### Submit Button

Si, en cambio, se necesita un mayor control sobre la estructura y el diseño de un boton, el elemento `<button>` es mejor en este caso. Y que el input no puede contener nada mas, es auto contenido.

Lo que tiene el `<button>` es que al ser especificamente un boton, no es necesario colocarle un `type` que diga `submit`, porque ya lo tiene por defecto. Funciona igual que un `<input>` en realidad, solo que este tiene la posibilidad de contener texto u otros elementos, por lo tanto eso deja mas posibilidades a el diseño del boton. 

Aca, en vez de usar el atributo `value` para colocar el texto que va a aparecer en el boton, lo ponemos directamente como el contenido.

```html
<button name="submit">
  <strong>Send Us</strong> a Message
</button>
```



### Other Inputs

Hay un par de usos mas para los inputs que no vimos, que incluyen pasar datos escondidos y adjuntar archivos en el procesamiento del formulario.

##### Hidden Input

El input escondido provee una forma de pasar datos al servidor sin que se impriman al usuario. Son utiles para trackear codigos, keys y otra informacion que es de interes para el usuario pero es necesaria para el procesamiento del formulario. 

Pero aunque la informacion no se imprime en pantalla, puede ser encontrada en el source code de la pagina, por lo tanto no es util para pasar informacion sensible.

Para usar hidden input, tenemos que especificar el valor `hidden` en el atributo `type`. Y como siempre, usar el name y value adecuados.

```html
<input type="hidden" name="tracking-code" value="abc-123">
```

##### File Input

Para adjuntar archivos junto a un formulario, hay que usar el valor `file` en el atributo `type`. 

```html
<input type="file" name="file">
```

Este tipo de input imprime un boton en pantalla, con un texto que indica que adjuntes un archivo. Al apretarlo, el solo te abre el explorador de archivos de la computadora del usuario para buscar el archivo que se quiere adjuntar.

Cuando el archivo se adjunta, este aparece a la derecha con su nombre y formato.

Algo que no es tan bueno sobre esto es que los browsers no permiten mucho el cambio de diseño para elementos input, y hay que implementar algunas soluciones mas dificiles con JavaScript. 



### Organizing Form Elements

Saber como capturar datos mediante input es la mitad del trabajo. La otra mitad es la parte en que se tiene que organizar todo para que sea entendible para el usuario. Es importante entender de que forma mostrar el contenido del formulario, para que el usuari sepa que poner en cada caso.

Para estos casos se usan los labels, fieldsets, y legends.

##### Label

Los labels o etiquetas proveen subtitulos o headings para los controles de los formularios, atando a ellos una etiqueta para asistir al usuario y hacer que entienda de que se trata el campo que debe rellenar.

Se crea con el elemento `<label>`, el cual debe contener texto que describe al input o al control que pertenece la etiqueta.

El elemento `<lebel>` lleva siempre un atributo `for`, al cual se le asigna el mismo valor del atributo `id` del elemento al que corresponde. Asi lo que logras es atar el label al elemento.

```html
<label for="username">Username</label>
<input type="text" name="username" id="username">
```

O tambien se puede omitir el uso de los atributos `for` y `id` si se encierra a los elementos a los que se les quiere asignar la etiqueta. 

```html
<label>
  <input type="radio" name="day" value="Friday" checked> Friday
</label>
<label>
  <input type="radio" name="day" value="Saturday"> Saturday
</label>
<label>
  <input type="radio" name="day" value="Sunday"> Sunday
</label>
```

Lo que hace esto es poner un heading a la izquierda de los elementos, indicando asi a que hace referencia el input que hay que colocar.

##### Fieldset

El elemento `<fieldset>` actua como un contenedor estructural, al igual que lo hace por ejemplo el elemento `<section>`, pero este esta dedicado a separar y organizar contenido dentro de formularios. Es un elemento en bloque que contiene a elementos que estan relacionados. Ademas incluye por defecto un borde que puede ser modificado en CSS.

En otras palabras, es un contenedor que se usa para formularios. Dentro pones todo lo relacionado a lo que queres hacer con el formulario. Añade estructura, organizacion y semantica.

```html
<fieldset>  
  <label>    
	Username    
	  <input type="text" name="username">
  </label>  
  <label>    
    Password    
      <input type="text" name="password">  
  </label> 
</fieldset>
```

##### Legend

El elemento `<legend>` provee un heading para el elemento `<fieldset>`. Tiene la funcion de proveer de un titulo al formulario. Esta leyenda va a aparecer en la parte superior del contenedor del formulario.

```html
<fieldset>
  <legend>Login</legend>
  <label>
    Username
    <input type="text" name="username">
  </label>
  <label>
    Password
    <input type="text" name="password">
  </label>
</fieldset>
```

Lo que hace esto es colocar entre la linea del borde un heading al formulario. Pero se coloca en el borde del fieldset por defecto.



### Form & Input Attributes

Aca se disponen algunos de los atributos mas comunes que se usan a la hora de hacer formularios.

##### Disabled

Este es un atributo booleano, y cuando se lo usa hace que el elemento o control se vuelva inutil. Ya no hay forma de interactuar con el y no envia ningun valor al servidor para procesamiento del formulario.

Por ejemplo, en caso de ponerlo en el elemento `<fieldset>`, lo que va a hacer es poner a todo el unput que haya de color gris por defecto, y sin poder acceder a ellos. 

Esto se utiliza mucho en formularios cuando uno llena una opcion de las que hay, y se desabilitan otras debido a que no tiene sentido rellenarlas. Es decir, una de las opciones bloquea a las demas. Esto seguramente se hace utilizando JS para dar la condicion, junto a esta propiedad.

##### Placeholder

El atributo `placeholder` puede colocarse dentro de un elemento `<input>` o `<textarea>` para asi colocar un texto dentro del espacio para colocar el input, que desaparece cuando uno se centra en el espacio o escribe algo. Es muy comun verlo, ya que provee una forma de aclararle al usuario, o de proveerle mayor informacion, sobre el dato que tiene que colocar ahi.

```html
<label>
  Email Address
  <input type="email" name="email-address" placeholder="name@domain.com">
</label>
```

La diferencia entre estre atributo y el atributo `value` es que, en el segundo lo que le indicas viene por defecto en el formulario. Es decir, no se va cuando te paras encima, si no que lo tenes que borrar vos. Sirve en los casos en que ya queres dejar algo por defecto desde un principio.

##### Required

El atributo booleano `required` hace que un input del formulario sea obligatorio para poder continuar. Se usa en los casos en que el dato debe ser enviado al servidor para que funcione, o sea, es critico para el funcionamiento del formulario. 

En caso de que no se rellene ese campo, salta un mensaje de error por parte del browser. Este mensaje no es posible darle un estilo, ya que lo maneja el browser, pero por otro lado, elementos invalidos y controles si se les puede dar un estilo con las pseudo-classes `:optional` y `:required`.

Ademas, esto provee una forma de indicar que, no solo el campo tiene que estar, si no que tiene que ser correcto tambien. Por ejemplo, si tenes un input del tipo email, se necesita no solo llenar el input del email, si no que tambien sea un email valido.

```html
<label>
  Email Address
  <input type="email" name="email-address" required>
</label>
```

##### Additional Attributes

Ademas de los anteriores, hay muchos mas atributos. Estos son varios otros, aunque hay mas. Algunos de estos son: `accept`, `autocomplete`, `autofocus`, `formaction`, `formenctype`, `formmethod`, `formnovalidate`, `formtarget`, `max`, `maxlength`, `min`, `pattern`, `readonly`, `selectionDirection`, `step`.

Para mas informacion sobre cada uno, hay que googlearlos. Tambien se trata de eso, de rebuscarsela uno solo y buscar informacion cuando se presenten los problemas.



### Login Form Example

Este es un ejemplo de un formulario que utiliza todo lo que vimos hasta ahora.

```html
<form>
  <fieldset class="account-info">
    <label>
      Username
      <input type="text" name="username">
    </label>
    <label>
      Password
      <input type="password" name="password">
    </label>
  </fieldset>
  <fieldset class="account-action">
    <input class="btn" type="submit" name="submit" value="Login">
    <label>
      <input type="checkbox" name="remember"> Stay signed in
    </label>
  </fieldset>
</form>
```

```css
*,
*:before,
*:after {
   box-sizing: border-box;
}
form {
  border: 1px solid #c6c7cc;
  border-radius: 5px;
  font: 14px/1.4 "Helvetica Neue", Helvetica, Arial, sans-serif;
  overflow: hidden;
  width: 240px;
}
fieldset {
  border: 0;
  margin: 0;
  padding: 0;
}
input {
  border-radius: 5px;
  font: 14px/1.4 "Helvetica Neue", Helvetica, Arial, sans-serif;
  margin: 0;
}
.account-info {
  padding: 20px 20px 0 20px;
}
.account-info label {
  color: #395870;
  display: block;
  font-weight: bold;
  margin-bottom: 20px;
}
.account-info input {
  background: #fff;
  border: 1px solid #c6c7cc;
   box-shadow: inset 0 1px 1px rgba(0, 0, 0, .1);
  color: #636466;
  padding: 6px;
  margin-top: 6px;
  width: 100%;
}
.account-action {
  background: #f0f0f2;
  border-top: 1px solid #c6c7cc;
  padding: 20px;
}
.account-action .btn {
  background: linear-gradient(#49708f, #293f50);
  border: 0;
  color: #fff;
  cursor: pointer;
  font-weight: bold;
  float: left;
  padding: 8px 16px;
}
.account-action label {
  color: #7c7c80;
  font-size: 12px;
  float: left;
  margin: 10px 0 0 20px;
}
```

Realmente la estructura del formulario es muy simple. Solo se compone por dos inputs con labels, un boton que lo pone en forma de input, y un ultimo checkbox para mantener la sesion cada vez que ingresas a la pagina.

Notar que el formulario en dos secciones, y asi queda un poco mas prolijo. Ademas le permite asignarle dos colores diferentes al background.

