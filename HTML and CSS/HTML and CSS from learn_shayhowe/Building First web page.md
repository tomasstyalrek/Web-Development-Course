## Intro and building our first web page

**HTML** o *HyperText Markup Language*, es un leguaje de marcado o de etiquetas, que cumple la funcion de darle a las parginas la estructura de su contenido, y su contenido mismo. **CSS** o *Cascading Style Sheets* es un lenguaje de presentacion creado para añadir apariencia  al contenido, usando por ejemplo fuentes y colores.

Los dos lenguajes son independientes uno de otro y deben seguir siendo de esa manera. CSS no deberia escribirse dentro de un documento HTML. HTML solo representa estructura y contenido, y CSS solo representa apariencia. 

Asi, entendiendo esta diferencia podemos pasar a explicar mejor HTML.



#### HTML Common Terms

HTML tiene muchos terminos, que se van a ir aprendiendo con el paso del tiempo. Pero los tres principales que se deben aprender son el de *element, tag*, y *attribute*. 

##### Elements

Los elementos son designadores que definen la estructura y el contenido de un objeto en una pagina. Algunos de los mas conocidos son los headings `<h1>,  ..., <h6>`, los paragraphs `<p>`, y la lista sigue con otros como `<a>, <div>, <span>, <strong>, <em>, ...`, y muchos mas.

Los elementos se definen con los simbolos mayor y menor <>. 

##### Tags

En un elemento hay una parte que destaca llamada tag. Un tag es un nombre encerrado entre dos <>, como por ejemplo el tag `<div>`. 

Se le llama *opening tag* al tag que abre y cierra con un simbolo mayor y menor, este abre el elemento. Como el ejemplo anterior. Y se le llama *closing tag* al tag que cierra el elemento, que se escribe con un /, como es el caso de `</div>`. Lo que va entre medio de estos es el contenido del elemento. 

Por ejemplo, un *archor link* es un elemento que referencia a un hipervinculo externo a la pagina. Para usarlo se utiliza el tag de apertura y cierre `<a> ... </a>`, y entre medio se coloca el nombre de ese hipervinculo, que seria el contenido.

##### Atributtes

Los atributos son propiedades que añaden informacion a un elemento. Los mas conocidos son *id*, para identificar un elemento, *class* para clasificarlo, *src* que especifica el source, la fuente del contenido incrustado ahi, y *href* que referencia a un hipervinculo.

Los atributos se colocan en el opening tag, y por lo general son pares de la forma 

`attribute-name="attribute-value"`

Como por ejemplo:

```html
<a href="http://shayhowe.com/">Shay Howe</a>
```

Lo que hace eso es solo mostrar el texto "Shay Howe", pero hacerlo clickeable para acceder a un hipervinculo.

![HTML Syntax Outline](https://learn.shayhowe.com/assets/images/courses/html-css/building-your-first-web-page/html-syntax-outline.png)

Elemento se le llama al bloque entero, mientras que tag es solo lo que determina su funcion, y el atributo su propiedad. Ambos son partes de un elemento. 



#### HTML Document Structure

Los documentos HTML son plain text docuements, es decir, son documentos de texto normales, pero que poseen la extension *.html* antes que *.txt*. Por lo tanto, uno puede elegir escribirlos donde quiera, siempre y cuando lo que guarde no sea un texto enriquecido, como lo hacen el Microsoft Word y otros. Por eso es que se recomienda unar un IDE o si se quiere algo mas simple, el bloc de notas basta.

Todo documento tiene una estructura basica que necesita de estos elementos: `<!DOCTYPE html>`, `<html>`, `<head>`, y `<body>`.

La declaracion de tipo de documento, o `<!DOCTYPE html>`, le informa al web browser que version de html estamos usando. Como solo ponemos html, esto indica que queremos usar su ultima version. Siempre se coloca este elemento en el principio del documento. 

Segido de este se coloca el elemento `<html>`, el cual indica que el contenido de la pagina esta dentro de el. Dentro de el, el `<head>` incluye toda la metadata de la pagina, junto con su informacion. El contenido dentro no se imprime en la pagina, si no que es solo informacion para el web browser. Puede contener el titulo de la pagina, que se imprime en la barra de titulo del browser, links a archivos externos y otras cosas.

Y por ultimo, dentro del elemento `<body>` recae toda la estructura y contenido de la pagina, que si es visible al usuario.

Un documento basico es algo asi:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>Hello World</title>
  </head>
  <body>
    <h1>Hello World</h1>
    <p>This is a web page.</p>
  </body>
</html>
```

Si lo guardas con extension .html y lo abris en el browser, deberia verse un heading en negrita y mas grande que dice "Hello World", y un parrafo abajo que dice "This is a page."

Un elemento que se ve dentro del head es `<meta charset="utf-8">`. Esto indica la codificacion de los caracteres en UTF-8. Luego esta el titulo de la pagina con el tag `<title>`. 

Tambien se puede ver que hay indentacion entre elementos anidados. No es necesaria, pero añade legibilidad.

###### Self-Closing elements

El ejemplo de arriba, del elemento `<meta>`, es un caso de un tag que se cierra a si mismo. Es decir, que no requiere otro tag de cierre. Estos tipos de tags son la minoria. Estos son:

- `<br>`, `<embed>`, `<hr>`, `<img>`, `<input>`, `<link>`, `<meta>`, `<param>`, `<source>`, `<wbr>`

Ninguno de estos tags necesita cerrarse para cumplir su funcion.

###### Code Validator

Debido a que cuando escribimos nuestro documento vamos a cometer errores, inevitablemente, la W3C tiene un validado de nuestro codigo. Se lo pasas y verifica que todo este bien. Aca [HTML](https://validator.w3.org/), y aca [CSS](https://jigsaw.w3.org/css-validator/).



#### CSS Common Terms

Tambien hay algunos terminos esenciales que hay que conocer por parte de CSS. Estos son los *selectors*, las *properties* y *values*.

##### Selectors

A medida que se va estructurando y agregando elementos a una pagina, se pueden ir agregando estilos con CSS. Un selector designa a que elemento o elementos en el documento HTML se les va a aplicar los estilos que se especifican, como colores, fuentes, tamaños y posiciones. 

Los selectores apuntan o estan referenciados por lo general a los atributos de los elementos. Es decir, se conectan al documento HTML por medio de sus atributos , como por ejemplo, id o class que son muy usuales. O directamente se podria especificar un conjunto de elementos, poniendo su tag.

Los selectores se forman con llaves {}, en donde se ponen los estilos que seran aplicados a los elementos seleccionados. Por ejemplo, este selector esta apuntando a todos los elementos `<p>` parrafos.

```css
p { ... }
```

##### Properties

Una vez que se asignaron con los selectores al elemento o a los elementos que van a recibir el estilo, hay que usar propiedades para indicar que se va a modificar. Las propiedades van dentro de las llaves, con un nombre especifico, y seguido de un " : ". 

Hay una cantidad muy grande de propiedades, como por ejemplo `background`, `color`, `font-size`, `height`,  `width` y muchas otras. 

Por ejemplo, aca le estamos asignando un color y un tamaño de fuente a un parrafo:

```css
p {  
    color: ...;  
    font-size: ...; 
} 
```

Por lo general se suelen poner una debajo de la otra para mayor legibilidad.

##### Values

El valor es lo que toma una propiedad. Va entre un : despues de asignar la propiedad, y antes de un ; para cerrarla. Por ejemplo, aca estamos asignando el color naranja al parrafo, con un tamaño de 16 pixeles.

```css
p {  
	color: orange;  
	font-size: 16px;
} 
```



#### Working with selectors

Entonces, como ya vimos, los selectores son los encargados de indicar a que elementos HTML se les dara estilo. Por esta razon es importante tener una buena base de como se usan los selectores. 

Vamos a empezar por los selectores mas comunes, que son *type*, *class* y *id*.

##### Type selectors

Estos tipos de selectores seleccionan a los elementos por su tipo. Es decir, si quisieras todos los elementos *division*, el selector se llamaria *div* y haria referencia a todos los tags `<div>` en el documento.

```css
div { ... }
```

Hace referencia a:

```html
<div>...</div>          
<div>...</div>
```

##### Class selectors

Los selectores que seleccionan por clase, lo que hacen es aplicarle el estilo indicado a todos los elementos con atributo *class*. 

Esta es una forma un poco mas especifica de especificar a un grupo de elementos, antes que aplicarselo a todos los de un mismo tipo. Ya que podes ponerle la misma clase a todos los elementos que queres que tengan lo mismo, y asi despues especificarselo en el documento css.

Para hacer esto, necesitamos el operador dot ( . ), seguido del valor del attributo class. Esto es:

```css
.awesome { ... }
```

Referencia a:

```html
<div class="awesome">...</div>
<p class="awesome">...</p>
```

##### ID selectors

Los selectores que seleccionan por id son mas precisos todavia que los de clase, ya que solo se aplican al id de un unico elemento. 

Hacen referencia al valor del atributo id que se le pone al elemento. Ademas, solo pueden ser usados una vez por pagina estos atributos, es decir, no pueden haber dos id iguales en una misma pagina.

Para poder referenciarlos, se utilza un hash sign (#), seguido por el valor del atributo id. Por ejemplo:

```css
#shayhowe { ... } 
```

Referencia a:

```html
<div id="shayhowe">...</div>
```

##### Additional selectors

Estos tres tipos de selectores son los mas comunes, pero en realidad hay muchos mas. Todos estan disponibles para su uso, y se recomienda que cuando ya se este bien con estos selectores, se empiece a indagar mas en el uso de otros mas avanzados.



Ahora que ya vimos las cosas basicas de HTML y CSS, vamos a ver como unir los documentos para que empiecen a trabajar juntos.

#### Referencing CSS

Para poder hacer que CSS se conecte con HTML, hay que referenciar a CSS en el documento HTML. La mejor practica que uno puede hacer es la de incluir un archivo CSS de forma externa, o sea, no directamente dentro del documento HTML. Luego este archivo se referencia desde el `<head>` de nuestro documento. Esto es mucho mejor ya que usando un solo archivo css para toda la pagina, nos permite escribirlo una vez sola y que se mantenga durante todo el sitio.

Otra opcion podria ser la de incluir el codigo css entre lineas en el mismo documento HTML, pero esto no se recomienda para proyectos serios, si no que es solo para hacer cosas rapidas y ejemplos, o cosas asi.

Entonces, para crear un archivo CSS necesitamos crear un documento de texto como antes, pero ahora le ponemos extension `.css`. Este archivo debe guardarse en el mismo directorio de nuestro proyecto, junto al archivo .html.

Luego lo que hacemos es poner dentro del `<head>` un link al archivo css, por eso es que usamos el elemento `<link>`, que es un tag self-closing. 

Dentro de este tag, vamos a poner dos atributos. El primero es `rel="stylesheet"`, que es lo que indica la referencia, que en este caso le decimos que es hacia una hoja de estilos. Y el segundo es el atributo `href="main.css"`, que es lo que indica cual es el hipervinculo que relacionamos, que es el archivo .css.

```html
<head>
  <link rel="stylesheet" href="main.css">
</head>
```

Notar que en el href se debe colocar la ruta al archivo en nuestra pc, pero como lo pusimos en la misma carpeta que el doc html, no es necesario poner el path.

Pero si, por ejemplo, estuviera dentro de la carpeta stylesheets, entonces el href seria `href="stylesheets/main.css"`.

Otra cosa que esta bueno remarcar, es que aunque nosotros no hayamos usado css todavia, la pagina talvez ya venga con algun color predefinido, un tipo de fuente, y un tamaño. Todo muy basico. Esto es porque el browser ya posee su propia capa que esta seteada por default, y que renderiza siempre que no haya css incluido.



#### Using CSS resets

Como dijimos, el browser ya posee su propia capa por default, para que los documentos si css puedan ser impresos de igual manera. Pero el tema es que cada browser tiene su propio estilo inicial.

Es por esto que es muy comun usar algo que se llama CSS resets, que son plantillas iniciales para que tu documento HTML se vea de igual forma en todos los browsers. Es una manera basica de hacer tu pagina compatible con todos los navegadores disponibles.

Hay varios resets disponibles para su uso, aunque uno de los mas populares es este [Eric Meyer’s reset](http://meyerweb.com/eric/tools/css/reset/). Y hay otro que se llama [Normalize.css](https://necolas.github.io/normalize.css/), que requiere un poco mas de conocimiento.

El tema del cross-browser es algo importante y que se debe tener en cuenta para testear tu aplicacion. No todo se tiene que ver exactamente igual en todos los browsers, pero es bueno que no difieran mucho unos de otros.