# Writing Your Best Code

Hasta ahora estuvimos viendo un monton de cosas sobre HTML y CSS. Descubrimos que hay un monton para aprender, y no es tan simple como parece. Son muchos conceptos que hay que entender, ademas de saber como usar la sintaxis de ambos, como pueden ser sus elementos, atributos y propiedades. Todas las lecciones hasta ahora tenian estre proposito en general, explicar como funcionan este tipo de conceptos.

En esta leccion vamos a volver un paso atras, para ver un lado un poco mas abstracto de estas dos tecnologias. Vamos a estar viendo las mejores practicas a la hora de escribir codigo, cosa que siempre tienen que tomarse en cuenta. 

Esto no solo nos va a servir para escribir HTML y CSS, si no que aplica a cualquier lenguaje que sea para programar. Ya que son practicas que siempre estan bien vistas.

### HTML Coding Practices

Las buenas practicas en HTML no difieren mucho de lo que se considera una buena practica en cualquier lenguaje de programacion. Esto es, mantener un codigo limpio y bien organizado, con una buena estructura y siguiendo los estandares de compilacion propuestos por el W3C. Esto que vamos a ver no es para nada una explicacion exaustiva, ya que eso tomaria mucho tiempo. 

##### Write Standards-Compliant Markup

Cuando uno escribe codigo en HTML, y este funciona y se renderiza correctamente, aun asi esto no significa que nuestro codigo sea semanticamente correcto o que nos garantize que cumpla con los estandares de compilacion que se sugieren. Resulta que en este sentido HTML es bastante permisivo, porque nuestro codigo puede funcionar aunque sea un desastre. Es por esto que a HTML se le suele decir que es un "forgiving-language", porque aunque nuestro codigo sea incorrecto, va a funcionar. Esto se debe a que el browser hace una correccion del codigo. Si queres probarlo, intenta escribir un parrafo sin cerrar el tag, va a funcionar igual. 

Por lo tanto, cuando uno escribe HTML tiene que prestar atencion a las diferentes practicas, como abrir y cerrar elementos correctamente, usar IDs y clases apropiadas para el elemento, y siempre validar nuestro codigo.

Mal codigo:

```html
<p id="intro">New items on the menu today include <strong>caramel apple cider and breakfast crepes</p>.</strong>
<p id="intro">The caramel apple cider is delicious.
```

Buen codigo:

```html
<p class="intro">New items on the menu today include <strong>caramel apple cider and breakfast crepes</strong>.</p>
<p class="intro">The caramel apple cider is delicious.</p>
```

Esto es bastante basico igualmente. Notar que el primer codigo usa ids para dos elementos diferentes, cosa que nunca se debe hacer. Los ids estan hechos para que se usen en un unico elemento. Por lo tanto, si se quieren poner con el mismo indicador, se deberia poner mejor un class, que si admite repeticion. 

Por otro lado, hay un mal cierre de los elementos. En el primero cierra en diferente orden, y en el segundo ni siquiera lo cierra al elemento.

Yo creo que los standard-compliant son muchos mas que estos.

##### Make Use of Semantic Elements

Realmente no es una tarea sencilla la de elegir que elementos hay que utilizar a la hora de darle estructura a una pagina, ya que existen un poco mas de 100 elementos dedicados a la semantica. Pero igualmente es una tarea necesaria e importante la escribir un codigo que tenga sentido. Esto no solo provee de estructura y sematica, si no que tambien de mayor facilidad para darle estilo a las cosas.

La forma de saber si estas utilizando los elementos correctos es siempre estar verificando tu codigo, o pidiendole a otras personas que le den un vistazo por vos. Eso puede hacer que otro encientre errores o cosas que pueden mejorarse.

Estos dos son ejemplos de codigos. El primero, usa elementos sin ningun tipo de valor semantico, y el segundo usa beunas practicas. Ambos producen lo mismo:

```html
<span class="heading"><strong>Welcome Back</strong></span>
<br>
It has been a while. What have you been up to lately?
```

```html
<h1>Welcome Back</h1>
<p>It has been a while. What have you been up to lately?</p>
```

Realmente ambos funcionan de maneras parecidas, pero el segundo tiene mucho mas sentido semantico, y ademas te ahorra el tener que realizar saltos de linea manuales con `<br>`, ya que usa todos elementos en bloque.

##### Use the Proper Document Structure

Como ya mencionamos, HTML es un forgiving language, esto es, la pagina va a renderizar aunque no usemos los elementos `<!DOCTYPE html>`, `<html>`, `<head>` o `<body>`. Hay como una especie de autocompletado de elementos por parte del brower. Pero el problema esta en que no todos los browsers tienen esta funcionalidad, por lo tanto, si no se ponen estos elementos puede que tu documento no se renderize en todos los browsers por igual.

Es por esta razon que siempre debemos incluir estos elementos estructurales cuando escribimos nuestro ocumento. Asi el codigo puede renderizarse bien y ser completamente semantico.

Mala practica:

```html
<html>
  <h1>Hello World</h1>
  <p>This is a web page.</p>
</html>
```

Buena practica:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Hello World</title>
  </head>
  <body>
    <h1>Hello World</h1>
    <p>This is a web page.</p>
  </body>
</html>
```

Bueno, y asi como es importante ponerlo siempre, tambien podemos aprovechar esta funcionalidad del browser y no ponerlo en algunos casos. Los casos a los que me refiero son aquellos en que solo queremos probar algo rapido o hacer un ejemplo. En ese caso no es necesario ponerlo, no tendria sentido. Solo hay que tener en cuenta que en caso de no poner toda la estructura, todo lo que pongas se va a renderizar como si estuviera dentro del body.

##### Keep Syntax Organized

A medida que nuestros documentos crecen, se hace cada vez mas dificil mantener una buena organizacion en nuestro elemento. Esto hace que las actualizaciones en nuestro documento sean dificiles de hacer, y da varios problemas.

Es por esto que es aconsejable seguir ciertas practicas a la hora de escribir nuestro codigo, que incluyen:

- Escribir todos los elementos del documento en minusculas, como tambien los atributos y los valores. 
- Usar una indentacion que se mantenga igual durante todo el documento.
- Usar siempre comilla doble, no simple.
- No usar tag de cierre si el elemento es self-closing.
- No poner valores en caso de que el atributo sea booleano.

En realidad son cosas bastante intuitivas, en caso de que vengas leyendo todo hasta aca. Con practica esto se vuelve natural.

Fijate estos dos codigos. Hay uno de los dos que es mucho mas sencillo de digerir a la vista.

```html
<Aside>
<h3>Chicago</h3>
<H5 HIDDEN='HIDDEN'>City in Illinois</H5>
<img src=chicago.jpg alt="Chicago, the third most populous city in the United States" />
<ul>
<li>234 square miles</li>
<li>2.715 million residents</li>
</ul>
</ASIDE>
```

```html
<aside>
  <h3>Chicago</h3>
  <h5 hidden>City in Illinois</h5>
  <img src="chicago.jpg" alt="Chicago, the third most populous city in the United States">
  <ul>
    <li>234 square miles</li>
    <li>2.715 million residents</li>
  </ul>
</aside>
```

Hay que asegurarse tambien de siempre mantener una buena practica, no solo para que uno mismo no se confunda, si no para tener una forma de escribir mas universal. Hay que seguir las practicas propuestas.

##### Use Practical IDs & Class Values

Asignar IDs y clases a los elementos no es una tarea facil. Ya que un ID o clase no debe hacer referencia a un estilo o al diseño del elemento, si no a su contenido. Si le pones una clase o id a un elemento haciendo referencia a su color rojo, si en algun momento lo queres cambiar a azul, no solo que tenes que cambiar CSS si no que tambien HTML en cada instancia en donde pusiste la clase rojo.

Si el parrafo menciona un mensaje de alerta de un error, mejor usar eso como clase o id, ya que dificilmente se cambie en un futuro.

```html
<!-- Bad Code -->
<p class="red">Error! Please try again.</p>
<!-- Good Code -->
<p class="alert">Error! Please try again.</p>
```

##### Use the Alternative Text Attribute on Images

El atributo `alt` siempre deberia ser puesto en las imagenes, ya que provee una descripcion de la imagen y ayuda a lectores y software de accesibilidad a entender mejor las cosas.

El atributo `alt` siempre deberia ser muy descriptivo de la imagen, a menos que la misma no sea relevante para nada. En ese caso el atributo se deja vacio. Esto es mejor, ya sea porque no hay nada que poner, como tambien para que el usuario no pierda el tiempo en algo innecesario.

Por ultimo, si la imagen no tiene ningun sentido en el contenido de la pagina, como por ejemplo el caso de una imagen que solo se use para la interfaz de una pagina, entonces deberia ser puesta solo en CSS en la propiedad `background-image`, y no como un elemento `<img>` en HTML. Esto es porque el elemento tiene un valor semantico, que en ese caso no seria necesario darle a esa imagen.

```html
<!-- Bad Code -->
<img src="puppy.jpg">
<!-- Good Code -->
<img src="puppy.jpg" alt="A beautiful, two-year-old hound mix puppy">
```

##### Separate Content from Style

Nunca uses estilos dentro de elementos. Esto no es para nada una buena practica, ya que hace que tu codigo sea dificil de mantener, y que el browser renderize lentamente las paginas. Pensa que, poniendo estilos dentro de cada elemento hace que no puedas reutilizar estilos, si no que vas a tener que ponerle a cada elemento por separado el propio.

 Los estilos siempre se colocar en un documento externo al documento HTML, que tiene contenido todos los estilos. Y lo mejor es siempre utilizar clases, si es que hay varios elementos iguales, y llamarlas con un selector desde CSS.

Asi ademas, haces posible la reutilizacion y la asignacion de estilos a mas de un elemento.

```html
<!-- Bad Code -->
<p style="color: #393; font-size: 24px;">Thank you!</p>
<!-- Good Code -->
<p class="alert-success">Thank you!</p>
```

En vez de poner todo ahi con el atributo style, le pones una clase y le asignas estilos en otro archivo.

##### Avoid a Case of "Divitis"

La "divitis" hace referencia a inundar la pagina de elementos `<div>`. Se que son convenientes para poner estilos a una pagina, y hacer que todo quede mas organizado.  Pero un exceso puede hacer que tengas divs que ni siquiera sepas que realizan.

La sugerencia es siempre mantener el codigo lo mas limpio posible, utiizando la menor cantidad de `<div>` posibles, solo los necesarios para realizar lo qiue necesitas. Ademas, es bueno priorizar antes que un div, un elemento que le provea estructura y valor semantico, si es que se puede situar en ese caso.

Recorda que, si dos cosas realizan lo mismo, pero una es mas sencilla de leer y es mas reducida que la otra, entonces siempre elegi la segunda.

```html
<!-- Bad Code -->
<div class="container">
  <div class="article">
    <div class="headline">Headlines Across the World</div>
  </div>
</div>
<!-- Good Code -->
<div class="container">
  <article>
    <h1>Headlines Across the World</h1>
  </article>
</div>
```

Acordate que un elemento estructural puede realizar el trabajo del div tranquilamente, ya que es un elemento en bloque. Por lo tanto, si lo podes usar, priorizalo antes que el div.

##### Continually Refactor Code

Cuando un website y una codebase crece, cada vez se va dejando mas de lado codigo que se acumula y no sirve para nada. Acordate de siempre mantener las cosas limpiar. Volver a revisar el codigo para ver si algo se puede reducir o eliminar, si es que quedo obsoleto. Siempre intentar volver las cosas mas manejables.



Por ultimo, recorda que en todo se puede profundizar. Hay libros completos de style guides, y asi para cada cosa que estuvimos viendo. 

Hay que practicar mucho, muchisimo. Hay que tener bien en claro las cosas basicas para poder pasar a algo mas potente. Luego de esto vamos a estar viendo un poco mas sobre como posicionar mejor elementos, luego se vienen cosas mas avanzadas dentro de HTML y CSS. Tambien vamos a estar viendo JS. Para ese momento, con la correcta practica, vas a estar hecho bastante bestia como para poder conseguir un laburo tranquilo aunque sea. 

Pero la realidad es que no se termina ahi, faltan muchas cosas mas. Ver algunos frameworks importantes, y seguir viendo conceptos que son necesarios si se quiere ser un desarrollador en front end. Hay que entender en mayor profundidad como funciona la web, y mas que nada sus protocolos para poder hacer web apis. 



### CSS Coding Practices

Al igual que HTML, las mejores practicas en CSS son parecidas. Se concentran siempre en mantener un codigo limpio y bien organizado. Ademas, CSS tiene ciertos principios sobre como trabajar con las complejidades de este lenguaje.

##### Organize Code with Comments

Los codigos que escribimos en CSS se pueden volver realmente muy grandes, con cientos y cientos de lineas. Es por esto que es bueno, primero, separar nuestro codigo en bloques logicos, como por ejemplo, las secciones de nuestra pagina, y segundo, colocar comentarios en todo el codigo, indicando a que le estas dando estilo en cada caso.

Esto va a hacer posible que accedas mas rapidamente al codigo cuando tengas que mantenerlo, y no tener que buscar y leer detalladamente de que se trata lo que vez.

```css
/* bad code */
header { ... }
article { ... }
.btn { ... }

/* good code */
/* Primary header */
header { ... }

/* Featured article */
article { ... }

/* Buttons */
.btn { ... }
```

##### Write CSS Using Multiple Lines & Spaces

Hay un standard de como se tiene que escribir el codigo en CSS. Es importante seguirlo, primero, porque es como se escribe a nivel global, y ademas porque va a hacer que vos y los demas puedan leer el codigo de forma muy prolija.

Cuando usamos mas de un selector, estos se ponen separados por coma, y bajando linea. Asi se enlistan todos los selectores a los que se les aplican las propiedades. Luego se abren dos llaves `{}` y se baja la linea entre ellas. Antes de la llave hay un espacio, entre medio de la llave y el selector. Entre medio se enlistan los pares ``propiedad: valor`` que se escriben separados por coma, y el lineas distintas. Cada uno se compone de una propiedad, un : seguido, un espacio, el valor, y un ;.

```css
/* bad code */
a,.btn{background:#aaa;color:#f60;font-size:18px;padding:6px;}

/* good code */
a,
.btn {
  background: #aaa;
  color: #f60;
  font-size: 18px;
  padding: 6px;
}
```

##### Use Proper Class Names

Como ya lo hablamos antes para HTML, las clases deben hacer referencia al contenido de un elemento y no a su apariencia. Y por convencion, los nombres deben escribirse en minuscula y se separan por guiones, y no por guiones bajos.

```css
/* bad code */
.Red_Box { ... }

/* good code */
.alert-message { ... }
```

##### Build Proficient Selectors

Los selectores en CSS se nos pueden ir de las manos si no los mantenemos. Pueden volverse muy largos o muy especificos. 

Mientras mas largo es un selector, mas precalificadores continene, y es cada vez mas especifico. Y si cada vez se vuelve mas especifico, eso significa que es mas probable que el codigo se rompa por diferentes causas.

La idea cuando se usan selectores es ser lo mas breve posible, para que todo quede bien organizado y facil de leer. Como mucho se puede anidar dos o tres elementos para adentro, no mucho mas.

Otra cosa es no usar el ID de los elementos en selectores anidados. No es una buena idea. Los ids solo se utilizan para darle estilo a uno solo, en especifico. Recorda que los IDs son atributos unicos.

```css
/* bad code */
#aside #featured ul.news li a { ... }
#aside #featured ul.news li a em.special { ... }

/* good code */
.news a { ... }
.news .special { ... }
```

Notar que los selectores que estan primero son demasiado especificos, al punto en que se vuelve innecesario. Si vos ya tenes un atributo con su clase, podes seleccionarlo a partir de ahi. Luego anidar dos o tres veces como mucho. No es necesario incluir cada uno de los elementos que se anidan hasta llegar al que queres.

Solo es necesario cuando puede haber confuciones entre elementos. Pero siempre recorda que los atributos class y id estan hechos para esto. Uno para seleccionar grupos que compartan los mismos estilos, y el otro para cuando el estilo es unico.

##### Use Specific Classes When Necessary

Hay casos en que los selectores de los elementos se vuelven muy largos y demasiado especificos, al punto en que ya no se entienden mas y son dificiles de manejar. En esos casos, esta permitido y se considera una buena practica la de aplicarle una clase a ese elemento, aunque esta sea unica y no agrupe a otros. 

Esto solo se hace por cuestiones de eficiencia a la hora de escribir y entender el codigo, y ademas para que renderize mas rapido, al no haber tantas iteraciones. 

Por ejemplo, imaginate un selector largo y muy especifico, al cual en un futuro a alguno de sus elementos se los cambia de lugar. El selector ya no haria efecto. Esto es algo que puede solucionar una clase especifica. 

```css
/* bad code */
section aside h1 em { ... }
/* good code */ 
.text-offset { ... }
```

##### Use the Sorthand Version of the Properties

Siempre es una mejor practica la de establecer los valores a una propiedad, eligiendo su forma shorthand, si es posible. Igualmente se deja siempre a criterio de uno mismo.

Si solo se tiene que aplicar algo a un lugar especifico del elemento, usamos longhand, pero en este momento nos estamos refiriendo a algo como esto:

```css
/* bad code */
img {
  margin-top: 5px;
  margin-right: 10px;
  margin-bottom: 5px;
  margin-left: 10px;
}
button {
  padding: 0 0 0 20px;
}

/* good code */
img {
  margin: 5px 10px;
}
button {
  padding-left: 20px;
}
```

En este caso, el primer codigo utiliza valores longhand para especificar los cuatro margenes de un elemento,  la shorthand para solo especificar uno. La idea es aprovechara estas cosas qie ofrece CSS para poder facilitarnos las cosas.

##### Use Shorthand Hexadecimal Color Values

Por convencion y facilidad, se suele usar siempre los valores shorthand de los valores hexadecimales de los colores. Usarlos no va a ser siempre posible, pero en los casos en que se pueda utilizar, lo mejor es hacerlo. Esto es por cuestiones de prolijidad.

Si no lo recordas, los valores shorthand hexadecimales se forman solo cuando hay dos valores iguales de cada digito. Recorda que el valor hexadecimal tiene 6 digitos, y si se van formando de dos en dos que son iguales, podes reemplazarlos por tres letras en vez de seis. 

Ademas, la convension es usar letras minusculas siempre que usemos este valor.

```css
/* bad code */
.module {
  background: #DDDDDD;
  color: #FF6600;
}

/* good code */
.module {
  background: #ddd;
  color: #f60;
}
```

##### Drop Units form Zero Values

Se considera una buena practica en CSS no ponerle unidades al valor 0. Al ser un valor nulo, no hay necesidad de añadir unidades que no son necesarias, lo unico que hacen es alargar el codigo mas. Entonces en ese caso, lo que hacemos es quitar la unidad, sea cual sea, asi acortamos el codigo y todo queda mas prolijo.

```css
/* bad code */
div {
  margin: 20px 0px;
  letter-spacing: 0%;
  padding: 0px 5px;
}

/* good code */
div {
  margin: 20px 0;
  letter-spacing: 0;
  padding: 0 5px;
}
```

##### Group & Align Vendor Prefixes

Cuando utilizamos prefijos de los diferentes browsers, que ya los vimos en lecciones anteriores, tambien es importante seguir ciertos estandares. No son escenciales para que funcionen ni nada por el estilo, si no que solo es una cuestion de organzacion y lectura.

Lo que se intenta hacer siempre es alinear entre las lineas a la propiedad o al valor que lleve a el prefijo. Recordar que los prefijos se pueden colocar en la propiedad y en el valir tambien.

Por lo tanto, lo que hacemos es indentar las propiedades o valores lo necesario como para que queden alineadas entre si.

```css
/* bad code */
div {
  background: -webkit-linear-gradient(#a1d3b0, #f6f1d3);
  background: -moz-linear-gradient(#a1d3b0, #f6f1d3);
  background: linear-gradient(#a1d3b0, #f6f1d3);
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}

/* good code */
div {
background: -webkit-linear-gradient(#a1d3b0, #f6f1d3);
background:    -moz-linear-gradient(#a1d3b0, #f6f1d3);
background:         linear-gradient(#a1d3b0, #f6f1d3);
-webkit-box-sizing: border-box;
   -moz-box-sizing: border-box;
        box-sizing: border-box;
}
```

Notar que el `linear-gradient()` se alinea cuando se baja la linea, y lo mismo para la propiedad `box-sizing`.

Por ultimo, es una buena practica dejar siempre la propiedad sin prefijos al final, abajo de todas. 

##### Modularize Styles for Reuse

CSS provee la funcionalidad de escribir codigo que sea reutilizado entre los elementos, con el uso de clases. El funcionamiento consiste en darle la misma clase a todos los elementos que esten relacionados entre si, es decir, que sus estilos sean parecidos, y asi podemos usar un mismo codigo para varios elementos. 

Si por ejemplo, hay una seccion en nuestra pagina que es de noticias y tiene un fondo, un borde y un radio particular, entonces tal vez un buen nombre de clase seria `news`. Pero en caso de que, por ejemplo, haya otra seccion con eventos proximos que tiene los mismos estilos, para reutilizar deberiamos usar otro nombre, como por ejemplo, `feat-box`. En realidad puede ser cualquier nombre que identifique a todo el contenido que este dentro.

```css
/* bad code */
.news {
  background: #eee;
  border: 1px solid #ccc;
  border-radius: 6px;
}
.events {
  background: #eee;
  border: 1px solid #ccc;
  border-radius: 6px;
}
/* good code */
.feat-box {
  background: #eee;
  border: 1px solid #ccc;
  border-radius: 6px;
}
```

Lo que nos quiere indicar esto es que, siempre es bueno agrupar contenido si tienen los mismos estilos. Solo lo escribis una vez, y lo vas usando para mas de un elemento.

