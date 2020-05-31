## HTML Fundamentals

HTML viene de HyperText Markup Language. Es uno de los pilares basicos para la construccion de todas las paginas web, junto con otras tecnologias como CSS y JavaScript. 

El estudio de HTML es realmente muy extenso. Vamos a ir recopilando informacion de diferentes fuentes, y a centrarnos en el aprendizaje teorico y en la practica.

Para mas informacion, hay que visitar [MDN docs](https://developer.mozilla.org/en-US/docs/Web/HTML) u otros tutoriales. Tambien puede ayudar mucho el articulo de [Wikipedia](https://en.wikipedia.org/wiki/HTML#History). 

FreeCodeCamp tambien tiene un excelente tutorial practico. Poca teoria y mucha practica. Esta bueno para complementar al mismo tiempo. Aprender teoria fuerte por un lado, y practicar por el otro. 

#### Structure of HTML

Un documento HTML se compone de tags o etiquetas, en donde cada una se identifica con un nombre especifico y realiza algo dentro de la estructura de una pagina. Generalmente los tags se deben abrir, con <> y cerrar con </>. 

Este es un documento HTML basico:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>My first HTML page!</title>
</head>
<body>
  <h1>Here's some important text!</h1>
  <div>Here's some content.</div>
  <div>See ya later!</div>
</body>
</html>
```

Aca se pueden ver varios tags diferentes, como <html>, <head>, <meta>, <title> y mas. Vamos a ir aprendiendo que son estos y muchos mas.

Todos los tags en HTML estan estructurandos en forma de una herarquia entre ellos. Por ejemplo, se puede ver que <meta> y <title> estan dentro del tag <head>, y que <h1> esta dentro de <body>, y que todo se encuentra dentro de <html>.  

Asi podemos decir que, por ejemplo, <h1> es *child* de <body>, y que a su vez <body> es *parent* de <h1>. Ademas, elementos con el mismo parent se llaman *siblings*.

Asi todo el documento se podria visualizar como un arbol, en donde los tags superiores son parents de los inferiores, y los inferiores child de los superiores. 

![alt="html tree structure"](https://www.rithmschool.com/content/html_css_fundamentals/html_graph.png)



##### Doctype and essential tags

Un tag que es esencial para un documento HTML el el doctype. El doctype lo que hace es especificar el tipo de escritura del documento. Nosotros vamos a estar usando el doctype <!DOCTYPE html>, que le dice a la pagina que estamos usando HTML5. Siempre se coloca en la primer linea de un documento. 

Luego del tag DOCTYPE se ven algunos tags que tambien son esenciales para todos los documentos html. Estos son:

<html> - este tag contiene todo el documento entero, es decir, todos los demas tags deben ser children de este.

head> - en  este tag se situan los elementos que tienen un contenido que no se quiere imprimir en pantalla, como metadata, titulo, scripts o stylesheets.

meta> - este es un tag para proveer metadatos, es decir, datos sobre los datos. Esto se utiliza para especificar que conjunto de caracteres queremos utilizar o para cosas de SEO.

title> - este es el titulo de la pagina, que se muestra en la tab de la pagina.



