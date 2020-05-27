## HTTP Tutorial

### Overview

El Hypertext Transfer Protocol es un protocolo distribuido y colaborativo de transferencia de datos, llamados hipermedia. Define un sistema de comunicacion entre clientes y servidores, para la correcta transferencia de datos como por ejemplo, archivos HTML, imagenes, resultados de queries, etc.

Hay tres caracteristicas que hacen a HTTP un protocolo simple, pero potente. Estas son:

- Es **connectionless**: Esto hace referencia a que el cliente y el servidor no mantienen conexion entre si entre ciclos de request y response. Cuando el cliente, digamos el web browser, envia un request al server, se establece una conexion entre ellos, y al finalizar la transferencia de datos, esta se cierra. Luego, ninguno sabe del otro, y el proximo ciclo sucede como si nunca hubieran hecho una conexion.

- Es **media independent**: Esto significa que la trasferencia de datos puede ser de cualquier tipo, se puede enviar cualquier tipo de dato con HTTP. Esto es siempre y cuando ambos, el cliente y el servidor sepan como manejar los datos que se pasan. Es necesario que ambos especifiquen el tipo de contenido con un MIME-type, que es el standard para especificar la naturaleza y formato de un archivo.

- Es **stateless**: Lo de arriba, que sea conectionless, es una consecuencia de esto. Los estados, por decirlo de alguna manera, no se almacenan cuando se usa este protocolo. El cliente y el servidor comparten informacion solo durante el ciclo de request response que se hacen, y luego de eso no guardan informacion sobre los requests. Se borra todo. Por eso se dice que no guardan conexion entre si.

  

##### Basic architecture

Este es un diagrama que muestra una aplicacion web basica y en donde entra HTTP como protocolo:

![HTTP Architecture](https://www.tutorialspoint.com/http/images/cgiarch.gif)

Es decir, se ve claramente que el protocolo hace de intermediario entre la conexion entre las partes de una aplicacion web. Esto se hace mediante requests/responses entre los clientes, que son web browsers, search engines, robots, y el servidor, que es un web server. Es decir, es un modelo de arquitectura cliente/servidor.

Se puede ver que un cliente no es solo el navegador, si no que es toda entidad que pueda realizar o emitir solicitudes al servidor. Por ejemplo, estan los robots o crawlers, que recopilan informacion.

##### Client

El **HTTP client** envia un request al servidor en forma de un request method, URI, y una version del protocolo, seguido de un mensaje MIME (el estandar que vimos) que contiene modificadores de ese request, informacion del cliente y posiblemente contenido de la conexion TCP/IP.

##### Server

El **HTTP server** responde con una status line, es decir, con un codigo que indica el estado de la response. Ademas, la version del protocolo, un mensaje de error o success dependiendo, y un mensaje MIME con informacion del setvidor y diferentes datos del cuerpo de la pagina, posiblemente. Digo posiblemente porque una response no siempre significa que te pasa una pagina, hay muchos metodos diferentes.



### Parameters

Vamos a ver aca algunos parametros y sintaxis que utiliza HTTP para enviar sus request y responses. Esto va a ayudar a empezar a entender como funcionan los requests, y como hacerlos de cero.

Estos parametros son informacion adicional que se agrega al request.

##### HTTP Version

HTTP usa un esquema de numeros **<major>.<minor>**, con esa forma, que indica las versiones del protocolo. Es decir, <major> indica la version mayor, mas representativa, y <minor> la version menor.

Esto se indica con un campo **HTTP-Version**, asi se indica que vas a poner la version. Esta es la sintaxis:

```
HTTP-Version   = "HTTP" "/" 1*DIGIT "." 1*DIGIT
```

Por ejemplo:

```
HTTP/1.0

or

HTTP/1.1
```

##### URI (Uniform Resource Identifiers)

El URI es una string que es case-insensitive, que se usa para dar informacion o identificar a un sitio web, un servicio we, etc. proporcionando datos sobre este, como nombre, ubicacion, y demas. La sintaxis general es:

```
URI = "http:" "//" host [ ":" port ] [ abs_path [ "?" query ]]
```

Es como una especie de identificador o URL, pero especificado en la aplicacion. En donde, si no se pone un **port**, esta por defecto el port 80 de HTTP. Ademas, un **abs_path** vacio, que es el path absoluto del URI, es equivalente a un "/". Es decir, como es usual en los URL al final. Por otro lado, caracteres dentro de los conjuntos reservados y no seguros, tienen que codificarse con el caracter "% hex hex". 

Por ejemplo, estos tres URI son eqivalentes:

```
http://abc.com:80/~smith/home.html
http://ABC.com/%7Esmith/home.html
http://ABC.com:/%7esmith/home.html
```

Como dijimos, no distingue mayusculas de minusculas.

##### Date/Time Formats

Las estampas que se ponen de fecha y hora deben estar si o si en Greenwich Mean Time (GTM). Estan avaladas las siguientes representaciones:

```
Sun, 06 Nov 1994 08:49:37 GMT  ; RFC 822, updated by RFC 1123
Sunday, 06-Nov-94 08:49:37 GMT ; RFC 850, obsoleted by RFC 1036
Sun Nov  6 08:49:37 1994       ; ANSI C's asctime() format
```

##### Content Encoding

La codificacion del contenido indica que debe ser usado un algoritmo de codificacion antes de pasar el contenido por la red. La codificacion se usa para caracteres especiales, para que no pierdan identidad al ser comprimidos. 

Estos son esquemas permitidos:

```
Accept-encoding: gzip

or

Accept-encoding: compress

or 

Accept-encoding: deflate
```

##### Media Types

HTTP usa Internet Media Types en los headers Content-Type y Accept. Todas estas cosas despues se van a ver mejor. La sintaxis que se usa es:

```
media-type     = type "/" subtype *( ";" parameter )
```

Esto por lo que entiendo tiene que ver con los tipos de datos avalados y demas. Un ejemplo puede ser:

```
Accept: image/gif
```

##### Language tags

Tambien HTTP usa etiquetas indicando el lenguaje en los campos Accept-Language y Content-Language. 

```
language-tag  = primary-tag *( "-" subtag )
```

Como por ejemplo:

```
en, en-US, en-cockney, i-cherokee, x-pig-latin
```



Todas estas cosas son enviadas en requests, dentro de headers y distintas partes del protocolo que luego vamos a ver. Todo es necesario para una correcta interpretacion del servidor.



### HTTP Messages

El protocolo HTTP esta basado en un modelo de arquitectura cliente servidor, en donde se envian requests/responses sin estado intercambiando mensajes por medio de una conexion TCP/IP de confianza.

Los mensajes de los que vamos a hablar son precisamente estos request/responses.

El cliente, que es un programa encargado de transferir datos hacia el server, envia mensajes HTTP request. El server, que acepta la conexion del cliente, envia mensajes de la forma HTTP responses.

Es decir, en otras palabras, se le llama HTTP message a la forma general de la transferencia de informacion, que es en request y responses.

HTTP hace uso del URI para establecer una conexion. Luego de establecida, se envian HTTP messages, que incluyen request del cliente al servidor, y responses del server al client. Es decir, los mensajes es la forma general.

```
HTTP-message   = <Request> | <Response> ; HTTP/1.1 messages
```

Cada HTTP request y HTTP response tiene un formato establecido. Consiste en los siguientes items:

- Una Start-line (que puede ser Request-line o Response-line).
- Cero o mas campos headers
- Una linea vacia indicando el final de los headers.
- Un mensaje opcional.



Todas estas partes van a ser explicadas en las siguientes secciones. Estos mensajes son los mismos que se pueden ver al ver el developer tools. Siempre te muestra codigos, headers, y otras cosas.

##### Start-line

La start-line del HTTP message tiene esta sintaxis:

```
start-line = Request-Line | Status-Line
```

Vamos a ver despues bien la Request-line y la Status-line, cuando veamos la seccion especifica de los request y responses. 

Por ejemplo:

```
GET /hello.htm HTTP/1.1     (This is Request-Line sent by the client)

HTTP/1.1 200 OK             (This is Status-Line sent by the server)
```

No estoy seguro si esto es un ejemplo simplificado de una HTTP request, pero si es asi parece bastante simple. Como se puede ver, la request hace un GET del path /hello.html, y seguido, la version de HTTP. Luego la status-line, que es el codigo que indica la respuesta del server.

##### Header Fields

Los headers indican informacion requerida sobre la request o response, o sobre los objetos que se envian. Hay cuatro tipos de headers:

- **General-header**: Tienen aplicacion general para requests y responses.
- **Request-header**: Solo aplicabilidad para el request.
- **Response-header**: Solo aplicacion para la response.
- **Entity-header**: Define meta informacion sobre el entity-body, o si no esta presente, sobre el recurso que identifica el request.

Por ejemplo, estos son varios campos de headers:

```
User-Agent: curl/7.16.3 libcurl/7.16.3 OpenSSL/0.9.7l zlib/1.2.3
Host: www.example.com
Accept-Language: en, mi
Date: Mon, 27 Jul 2009 12:28:53 GMT
Server: Apache
Last-Modified: Wed, 22 Jul 2009 19:15:56 GMT
ETag: "34aa387-d-1568eb00"
Accept-Ranges: bytes
Content-Length: 51
Vary: Accept-Encoding
Content-Type: text/plain
```

O sea, los headers son solo forma de enviar informacion. No estoy seguro de si son preterminadas, si ya estan definidas. O cambian para cada request y response en particular.

Supongo que ya lo vamos a ver cuando veamos los headers.

##### Message Body

El cuerpo del mesaje es opcional, pero si es usado es para cargar el entity-body del request o response. Por lo general si se usa el entity-body este, los headers **Content-Type** y **Content-Length** especifican las caracteristicas de este cuerpo. 

En particular, el primero indica el tipo de datp del contenido del mensaje, y el otro el largo.



### HTTP-Requests

El HTTP client envia un HTTP request al server en la forma de un **request message**, que tiene la sintaxis que vimos antes para los mensajes en general. La Start-line que se usa se llama Request-line. Entonces queda:

- Una Request-line
- Cero o mas headers (solo estan disponibles el General, Request, y Entity. Claramente el Response no)
- Una linea vacia
- Un message-body opcional

Esplicaremos cada una de estas entidades.

##### Request-Line

La Request-line empieza con un metodo HTTP, luego un Request-URI y la version del protocolo.

```
Request-Line = Method SP Request-URI SP HTTP-Version CRLF
```

Ese CRLF es como una bajada de linea, para diferenciar las cosas.

Veamos cada parte de la Request-Line.

##### Request methods

El method indica la forma de enviar la request, es decir, indica el proposito que se usa al enviarle la request al servidor. Esto es necesario porque no siempre se va a querer ingresar a una pagina, hay veces que suceden cosas sin necesidad de refrescar la pagina y demas. 

Los metodos de request siempre van en mayuscula, son case-sensitive.

Esta es una lista de los metodos soportados por HTTP:

| Method and Description                                       |
| ------------------------------------------------------------ |
| **GET**: Este metodo es usado para recuperar informacion de un server, dado un cierto URI. Solo es usado para recuperar datos, no tiene ningun otro efecto en ellos. |
| **HEAD**: Igual a GET, pero solo se recupera la status-line y los headers. |
| **POST**: El POST request hace lo contrario al GET. Solo envia datos al server, como informacion del usuario, actualizacion de archivos, etc. usando formularios HTML. |
| **PUT**: Reemplaza todas las representaciones del recurso con el contenido actualizado. |
| **DELETE**: Borra todas las representaciones del recurso dado por el URI. |
| **CONNECT**: Establece un tunel al servidor identificador con el URI. |
| **OPTIONS**: Describe las opciones de comunicacion para el recurso. |
| **TRACE**: Performs a message loop back test along with the path to the target resource. |

Realmente el request method que mas se suele usar es el GET. Es el que se ve la mayor parte del tiempo, ya que cada vez que uno clickea en un nuevo link, se necesita recuperar datos del servidor para que el cliente pueda imprimir en pantalla lo necesario.

El segundo mas importante y usado es el POST. El POST se utiliza en todo llenado de formulario, acceso a paginas, etc. Tambien se usa cuando una barra o algo dinamico aparece sin necesidad de refrescar la pagina. Es decir, se usa en el momento en que el cliente quiere enviar datos hacia el servidor o para iniciar alguna accion en el servidor.

Los POST requests son muy utiles tambien para enviar datos sensibles, como usuarios y contraseñas. Y ademas sirve para enviar datos mucho mas largos. Digo esto porque tambien podriamos hacer un GET y mandar datos dentro de una query string, pero seria inseguro.

Con un **inspector**, como el developer tools, se puede ver , cada vez que realizas algo en una pagina, como el cliente envia diferentes tipos de requests. Tiene que haber si o si una columna en la DevTools que muestre los methods. 

Otra columna que aparece es la del **status**, que nos cuenta el estado de esa recuperacion de los datos. 

##### Sobre el POST

Pensa que los POST methods tambien pueden llevar un body como cualquier request, y en ese body puede haber varios tipos de informacion. Entre ellas podrian ser el usuario y contraseña de un formulario, por ejemplo.

Esto nos dice que cuando uno llena un formulario, lo que esta pasando por dentro es que el cliente esta enviando en un POST request toda la informacion que vos pusiste, para que el servidor la utilice para recuperar cierta informacion de una base de datos.

##### Sobre headers

Como ya sabemos, los headers se utilizan para enviar informacion adicional en el ciclo de requests y responses. Algunos de los headers mas usados son:

| Field Name      | Description                                 | Example                                                      |
| :-------------- | :------------------------------------------ | :----------------------------------------------------------- |
| Host            | The domain name of the server.              | Host: [www.reddit.com](http://www.reddit.com/)               |
| Accept-Language | List of acceptable languages.               | Accept-Language: en-US,en;q=0.8                              |
| User-Agent      | A string that identifies the client.        | User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_9_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/38.0.2125.101 Safari/537.36 |
| Connection      | Type of connection the client would prefer. | Connection: keep-alive                                       |

No es necesario memorizar nada. Solo saber que forma parte de un HTTP request, igualmente.

##### Request headers fields

Vamos a ver ahora al Request-header. Nosotros ya vimos que hay tres headers disponibles para un request. Los otros dos que faltan los vamos a estudiar despues es la parte especifica de headers, que son el General-header y el Entity-header. 

El Request-header lo que hace es enviar informacion adicional sobre el request y sobre el cliente en si, hacia el server. Estos campos actuan como modificadores de requests. Por ejemplo, esta es una lista de headers usuales:

- Accept-Charset
- Accept-Encoding
- Accept-Language
- Authorization
- Expect
- From
- Host
- If-Match
- If-Modified-Since
- If-None-Match
- If-Range
- If-Unmodified-Since
- Max-Forwards
- Proxy-Authorization
- Range
- Referer
- TE
- User-Agent

En casos en donde se construya nuestro propio cliente y servidor, podemos crear nosotros headers a nuestras necesidades.

Igualmente, esto tampoco es para que te los memorizes, ya que no tiene ningun sentido. Primero porque se nos va a olvidar, y segundo porque no lo vamos a usar ahora. Esto seguramente se ve devuelta y se usa a la hora de hacer una API.

##### Poniendo todo junto

Vamos a ver un ejemplo de un request hecho por el cliente al servidor de la pagina tutorialspoint.com, queriendo acceder al path /hello.htm. Este es el request que mandaria:

```
GET /hello.htm HTTP/1.1
User-Agent: Mozilla/4.0 (compatible; MSIE5.01; Windows NT)
Host: www.tutorialspoint.com
Accept-Language: en-us
Accept-Encoding: gzip, deflate
Connection: Keep-Alive
```

Notar que en la primera linea tenemos la Request-line, con el metodo usado, donde queremos acceder, y la version. Luego todas las demas lineas son headers, que dan informacion sobre el User-Agent (o sea, el browser), el host (o sea la pagina), los lenguajes que aceptan, la codificacion y la conexion.

Aca el unico header general es el de Connection, todos los demas son Request-headers. Ademas, notar que no enviamos nada de datos al servidor, ya que no lo necesitamos. Solo queremos que nos de permiso a ver un doc HTML plano.

Este otro request envia data de un formulario:

```
POST /cgi-bin/process.cgi HTTP/1.1
User-Agent: Mozilla/4.0 (compatible; MSIE5.01; Windows NT)
Host: www.tutorialspoint.com
Content-Type: application/x-www-form-urlencoded
Content-Length: length
Accept-Language: en-us
Accept-Encoding: gzip, deflate
Connection: Keep-Alive

licenseID=string&content=string&/paramsXML=string
```

Notar que cambia el URL a /cgi-bin/process.cgi, que es quien procesa la data y envia una response. Despues, Content-type le esta diciendo al servidor que la data que le pasamos es de un formulario simple, y Content-length indica el tamaño de esa data.

Tambien se podria enviar por ejemplo un document XML. Aunque tampoco nos vayamos mucho porque no nos sirve de mucho saber eso.



### HTTP Response

Luego de que el cliente envie una HTTP request al server, este devuelve una HTTP response. Esta response contiene lo siguiente:

- A Status-line
- Zero or more header (General|Response|Entity) fields followed by CRLF
- An empty line (i.e., a line with nothing preceding the CRLF)  indicating the end of the header fields
- Optionally a message-body

Es decir, es igual que una request, pero en este caso devuelve un codigo que muestra un estado. Este estado pertenece a la respuesta que da el servidor a tu solicitud. 

##### Status-line

La satuts-line que devuelve la response message del servidor, es una linea que tiene una version de HTTP, un numero que indica el estado, y una frase indicando algo por parte del servidor.

```
Status-Line = HTTP-Version SP Status-Code SP Reason-Phrase CRLF
```

##### Status Code

Hay varios codigos posibles que puede devolver un servidor. Estos codigos son numeros de 3 digitos, en donde el primer digito indica la clase de estado, y los otros dos numeros no indican nada en particular. 

Cada numero tiene un significado particular, asociado a un grupo de cosas parecidas, segun su primer digito:

| Code and Description                                         |
| :----------------------------------------------------------- |
| **1xx: Informational**: Significa que el request se recibio y su procesamiento continua. |
| **2xx: Success**: Significa que la accion fue recivida, entendida y aceptada de forma exitosa. |
| **3xx: Redirection**: Significa que otras acciones deben ser hechas para terminar el request. |
| **4xx: Client Error**: Significa que el request contiene mala sintaxis o que no puede ser ejecutado con exito. |
| **5xx: Server Error**: Significa que el server fallo al querer completar un request aparentemente valido. |

De aca salen muchos de los codigos mas populares, como 404 que es de error, y 200 que es de success. Igualmente, mas alla del primer codigo, hay varios de cada tipo. Pero simplemente hay que saber que, si es 2xx salio bien, si es 4xx el error lo tiene el cliente, ya sea por un mal URL o algo asi, si es 5xx el error esta en el servidor, que no esta funcionando bien o esta actualizandose. El 3xx te redirecciona, y el 1xx esta bien, pero tira informacion.

##### Response headers

Por otro lado, tenemos los headers del response, que no son iguales al del request. Estos son Response-headers, y dan informacion adicional por parte del server, hacia el cliente. Se encargan de pasar informacion que no se puede poner en la status-line, como informacion del server o sobre un proximo acceso al indentificador del recurso con Request-URI. Algunos headers usuales pueden ser:

- Accept-Ranges
- Age
- ETag
- Location
- Proxy-Authenticate
- Retry-After
- Server
- Vary
- WWW-Authenticate

##### Ejemplos

Veamos cual podria ser la response del request del anterior ejemplo, para acceder al hello.htm del server de tutorialspoint.

```
HTTP/1.1 200 OK
Date: Mon, 27 Jul 2009 12:28:53 GMT
Server: Apache/2.2.14 (Win32)
Last-Modified: Wed, 22 Jul 2009 19:15:56 GMT
Content-Length: 88
Content-Type: text/html
Connection: Closed
```

```
<html>
<body>
<h1>Hello, World!</h1>
</body>
</html>
```

Es decir, devuelve la status-line encima de todo, que en este caso es 200, con un mensaje de OK. Luego alguna info adicional con los headers, como una fecha, el servidor (apache, un servidor muy usado), y demas. Ademas, un message body, en donde se encuentra el documento HTML que luego el cliente va a procesar.

En cambio, si el servidor por ejemplo, no ubiera podido encontrar lo que le pide el cliente, tiraria algo asi:

```
HTTP/1.1 404 Not Found
Date: Sun, 18 Oct 2012 10:36:20 GMT
Server: Apache/2.2.14 (Win32)
Content-Length: 230
Connection: Closed
Content-Type: text/html; charset=iso-8859-1
```

```
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html>
<head>
   <title>404 Not Found</title>
</head>
<body>
   <h1>Not Found</h1>
   <p>The requested URL /t.html was not found on this server.</p>
</body>
</html>
```

Devuelve un status 404, que significa error por parte del cliente, no se encontro el URL. Por eso un mensaje de Not Found. Luego los mismos headers. Lo curioso es que igualmente devuelve un message body, que corresponde a la pagina predefinida que envia en caso de error 404.

Pensa que, generalmente, las paginas dentro de todo decentes tambien crean un documento con estilos y todo para informarte errores, para que no se pierda parte de la experiencia de usuario.

O por ejemplo, tambien podria enviar un status 400, que significa Bad Request. Esto es porque no esta hecho bien el request por parte del cliente, ya sea porque tiene errores de sintaxis o mal uso del protocolo.

##### Respecto a los status codes

Se supone que un desarrollador debe tener en claro cual es cada uno de estos status. Pero realmente no es tan importante, basta con memorizarse los mas importantes y usuales. Total se pueden buscar. Pero lo mas claro es que se pueden ir memorizando con la practica, en el momento que empecemos a hacer APIs o aplicaciones web. Porque ahi es cuando te topas mas con eso.

Algunos comunes son:

- 302 Found: se encontro, se proceso el request, pero te esta redirigiendo a otro URL. Esto pasa porque probablemente antes ese era el request que funcionaba, pero ahora cambio de lugar o de recurso, y eso el server lo sabe, por eso es que te hace un redirect.

  Lo que hace el server es ver ese 302 y luego ver al header Location, que le dice a donde redirigir.

- 500 Internal Server Error: Te informa que hay un error con la aplicacion del servidor. Puede ser desde un error de configuracion, hasta una coma que este dando vueltas por ahi. 



### Stateful Web Aplications

Como ya vimos antes, HTTP es un protocolo que se considera stateless, es decir, que entre ciclos de request/responses, el cliente y el servidor no guardan datos sobre lo enviado. Por lo tanto, todos los ciclos son independientes unos de otros, como si en cada ciclo el cliente y el servidor se volvieran a conocer.

Este atributo de HTTP es lo que lo hace dificil de controlar, y lo que vuelve dificil el trabajo del desarrollador web, cuando debe hacer **stateful** Web Apps.

Si te pones a pensar, cunado entramos a una pagina, digamos Facebook, y nos logeamos, hay un estado. Es decir, nosotros estamos dentro de Facebook con nuestro usuario puesto, y si ahora hacemos un nuevo request para entrar a otra parte del sitio, FB no nos saca si no que el usuario sigue estando. Este es el concepto de stateful que hablamos.

En esta parte vamos a ver algunas de las tecnicas que usan los desarrolladores para simular una experiencia con estado en una pagina. Tambien vamos a ver algunas de las tecnicas utilizadas en el cliente para que imprima contenido dinamico. Vamos a estar tratando:

- Sessions
- Cookies
- Asynchronous JavaScript calls, o AJAX.

##### Una stateful app

Pensa esto. Vamos a la pagina que quieras, que tenga un sistema de logeo. Iniciamos sesion con nuestro usuario, y ahora, reiniciamos la pagina. Se salio el usuario? La respuesta es no. 

Como es esto posible? No era que HTTP es stateless? Que no guarda informacion entre ciclos request/response? Bueno, asi es como funcionan todas las webs modernas. Asi es como,  por ejemplo, una pagina de compras puede agregar cosas al carrito y que cuando vayas a comprar otra no se te salga, hasta incluso por dias lo recuerda. Vamos a ver algunas cosas para que esto sea posible.

##### Sessions

Claramente se ve que HTTP usa algun tipo de estension para poder dar la impresion de un estado, de una conexion que se mantiene entre el cliente y el servidor. Esto se consigue haciendo que el servidor le envie al cliente una especie de token unico. Esto hace que, en cualquier request que envie el cliente al servidor, use este token y lo ponga como parte del request, haciendo que el servidor reconosca al cliente, por causa de este identificador. En el desarrollo web este token que va y viene se llama **session identifier**.

Esto hace que, aunque cada request/response permanesca independiente, se guarde un `session id`, y haga esta conexion. Es decir, el protocolo se mantiene stateless, al igual que el cliente y el servidor, pero como mantiene el server un indicador de este token, puede reconocerlo.

Aunque esto claramente añade bastantes consecuencias a lo que debe hacer el server. Pensa que, cada vez que el cliente le envia el token, el server tiene que hacer lo mismo. Primero se fija si el request contiene un token. Si esto se cumple, se fija si todavia es valido, basado en una serie de reglas que se ponen claramente, para decidir cuanto tiempo puede quedar una sesion abierta o para determinar como almacenar los datos de la sesion. Tercero, el server tiene que ir a buscar esos datos asociados con ese id. Y por ultimo, el servidor tiene que volver a recrear las condiciones de ese documento HTML con esa session, y darselo al cliente.

Ahora quiero que pienses lo caro que es para el servidor tener que hacer esto cada vez (me rediero caro en cuanto a recursos), aunque hasta la pagina no haya cambiado en nada casi. Es un trabajo extra realmente para el servidor, mantener una experiencia stateful. 

Imaginate el trabajo que tiene que hacer el servidor de Facebook ponele, una terrible pagina, con un documento HTML carisimo, con miles de cosas por hacer. Vos le pones like a una foto, y el servidor tiene que hacer todo el laburo devuelta, mantener sesion, ejecutar cosas en la aplicacion del servidor para hacer que suba el numero de likes, que el  pulgar azul, y muchas cosas mas, y devuelve una response casi identica a la original, teniendo que hacer todo devuelta.

Bueno, por suerte existe AJAX para esto, algo completamente necesario para abaratar recursos, y poder hacer todo eso de arriba, sin necesidad de volver a dar una response y un nuevo documento.

Claro que todo esto lo mencionamos por encima, pero requiere de mucho conocimiento.

De otra cosa que vamos a hablar es de la forma de almacenar informacion de una session: con cookies.

##### Cookies

Las HTTP cookies son pedazos de informacion, pequeños archivos, que almacenan datos por parte de la session que se guardan en el browser. La mayoria de los navegadores tienen activadas las cookies. 

Estas cookies estan hechas para mejorar la experiencia de usuario, posibilitando a que guarden tu sesion en una pagina, hasta cuando uno se va de la pagina y vuelve, tambien guardan informacion sobre tu usuario, y todo lo que desee la pagina. Puede almacenar tambien tus gustos, las cosas que ves, todo lo que quiera de tu sesion. No es para robarte ni nada por el estilo, si no que es para mejorar tu experiencia y no tener que hacer las cosas varias veces.

El request que envia el cliente no posee cookies la primera vez, pero si lo hace la response. Esto se puede ver en el DevTools, entre los headers de la response, que puede aparecer uno llamado **set-cookie**. Este header esta hecho para setear las cookies. Luego, si te fijas en los proximos request, ahi si va a tener el cliente, porque ya se guardaron de antes. Ahora aparecen con el nombre del header **cookie**.

Estas cookies las almacena el browser, y se las pasa al server para mantener todo como estaba. Fijate que si apagas apagas la compu, despues cuando te fijas en el browser la cookie sigue estando.

##### Donde se almacena la data de la session?

La respuesta es en el servidor, en alguna parte. Puede ser en memoria, o en una "persistent storage", como una base de datos o un key/value store. 

Lo mas importante igualente es que la session id se almacena en el cliente, el cual usa como una llave para acceder a los datos que guarda el servidor. Este es el funcionamiento basico de una aplicacion web stateful.

Tambien es importante saber que esta session id expira luego de un tiempo, y se pierde de la memoria del browser. Ahi es cuando hay que registrarse denuevo.

Tambien algo loco es que, si queremos podemos entrar al inspector y borrar manualmente la session id. Esto nos cierra la sesion, que es el equivalente a lo que hace cuando apretamos el boton de log out. 

##### AJAX

AJAX viene de Asynchronous JavaScript and XML. Es una tecnica que le permite al browser poder hacer request y procesar responses sin necesidad de refrescar la pagina. Es decir, sin tener que hacer otro GET request.

Esto es muy util, porque tener que hacer un GET request cada vez que algo cambia en una pagina, ademas de ser lento y una mala experiencia de usuario, es muy costoso para el seridor, consume muchos recursos.

Cuando se usa AJAX todos lo request que hace el cliente se hacen de forma asincronica. Asi se mejora la velocidad y usabilidad de las aplicaciones. Notar que, AJAX no es una herramienta ni libreria, nada de eso, si no que solo es una forma de usar JS y XML de forma asincronica, es deicr, la pagina no refresca. 

Pensa que cuando googleas algo, por ejemplo, google no refresca la pagina por cada letra que pones, pero por detras hace request asincronicos y utiliza callback functions para manejar todo.

En algun momento vamos a ver como funciona esto mejor.



### Security

Como ya mencionamos antes, los atributos que posee HTTP lo hacen un protocolo dificil de manejar para los desarrolladores. Y tanto como es dificil de manejar, tambien cumple un rol importante la seguridad aca, que no es un tema menor.

Supongamos que yo ingreso a mi cuenta en una pagina. Otra persona puede obtener mi session id? O ver mis cookies y hacerse pasar por mi? Bueno estas cosas son parte de la seguridad de HTTP, de la que vamos a hablar en esta seccion. No va a ser claramente una lista exaustiva de seguridad informatica, ya que para eso hay una rama de estudio entera. Solo vamos a ver algun que otro topic general.

##### Secure HTTP (HTTPS)

Como ya sabemos, un cliente y un servidor se envian request y responses, en donde los mensajes se transfieren en forma de strings. Si un hacker, una persona con conocimiento en redes, usa herramientas como el *packet sniffing*, que es una tecnica para leer la informacion en un request, de forma maliciosa, lo que podria hacer por ejemplo es leer tu session id. 

Recorda que la session id es un token que envia el cliente, y asi el server sabe que sos vos. Ahora pensa que pasaria si una persona lo toma. Ahora podria saber cual es tu session id, y hacer un request personalizado, en donde envie manualmente este token. Asi la persona podria acceder a tu cuenta sin necesidad siquiera de saber tu usuario ni contraseña.

Aca es cuando entra HTTPS, que son las siglas de Secure HTTP. El resource que utiliza tiene al principio el squema `https://` en vez de `http://`, y usualmente tienen un candado verde que indica que es seguro.

Lo que hace el HTTPS es encriptar las request y responses. De forma que si una persona intercepta un request en la red, el mensaje no podria usarse porque esta encriptado. Quedaria inutil ese mensaje.

HTTPS lo que hace es mandar los mensajes pasandolos antes por un protocolo de encriptacion que se llama TLS. Antes se usaba otro protocolo que se llamaba SSL. Lo que hace es agarrar las strings e intercambiarlas por una encriptacion. Si uno toca en el candado verde, se pueden ver las configuraciones de la pagina, y las cosas que suceder. 

##### Same-origin policy

Esta politica que se implementa, llamada same-origin, lo que hace es permitir una interaccion libre entre resources del mismo tipo, y restringir ciertas interacciones si las resources son de diferente origen. 

Con origen se refieren a que las resources tienen el mismo scheme, port y host. Es decir, si entre dos URL, ambos coinciden en su scheme, port y host, entoces la interaccion entre ellos esta permitida. Por ejemplo, entre los URL `http://mysite.com/doc1` y `http://mysite.com/doc2` la politica se cumple, porque ambos path pertenecen al mismo site. Pero entre `http://mysite.com/doc2` y `https://mysite.com/doc2` no se cumple.

Igualmente no todo esta restricto entre URLs de diferentes origenes, porque si no no se podrian hacer redirecciones, transferencia de datos, etc. Lo que si restringen es cuando los URL son accedidos de forma programada con una API como `XMLHttpRequest` o `fetch`. No vamos a explicar bien que son porque se escapa del libro.

Este tipo de politica es muy util para la seguridad de una pagina web. Previene contra varios tipos de ataques.

##### Session Hijacking

Ya hablamos de lo que es una session y las cookies, uno es un token, una key almacenada por el servidor y el browser, de manera que cuando el cliente le envie requests, este coincida con la key que tiene el server y este no tenga que volver a hacer la autenticacion. Lo mismo pasa con las cookies, que se almacenan en el browser para mantener ciertas cosas como estan.

Por lo general esto es lo que pasa con las aplicaciones web, lo que suelen hacer. El usuario pone un usuario y contraseña, y estas coinciden con una session id que esta almacenada en el browser, asi no se vuelve a hacer la autenticacion.

A lo que se le llama **session hijacking** es al robo de un session id, interceptando un request, y utilizandolo para iniciar sesion en una cuenta sin necesidad de un usuario ni contaseña.

##### Medidas tomadas contra el session hijacking

- Una de las medidas que se toman es el de reiniciar la sesion. El website lo que hace es borrar el session id almacenado, de forma que se debe volver a hacer la autenticacion. Ahi es cuando al ladron le queda obsoleto la session id robada. Esto se suele hacer en las partes mas sensibles de una aplicacion web, como por ejemplo cuando se va a poner informacion sobre una tarjeta de credito o cuando se va a borrar la cuenta. Para cualquier tipo de estas acciones, la mayoria de las webs lo que hacen es volver a pedirte que inicies sesion.
- Otra forma es seteando un tiempo de expiracion de sesion, de forma que el robo de la sesion sea mas dificil. Es decir, si no le seteas un tiempo, el ladron tiene una cantidad indefinida de tiempo para poder hacer la intercepcion de la session id. En cambio, si le poner un timer de 30 minutos, el usuario debe iniciar sesion devuelta cada ese tiempo, y el robo se hace mas dificil. Esto hace por ejemplo, evernote, cuando pasa un tiempo.
- La ultima es, como ya vimos, usar HTTPS como protocolo seguro, y que se minimizen las posibilidades de robo.



##### Cross-Site Scripting (XSS)

Esto es un concepto muy importante para todo desarrollador web. El XSS ocurre cuando uno deja a un usuario de una pagina llenar un formulario o introducir input que sea HTML o JavaSript, y este se imprime en pantalla o se mete dentro del documento HTML de la pagina en si.

Es decir, para explicarlo mejor. Suponete que una pagina te permite hacer un comentario en un espacio en blanco, es decir, te deja poner input. Ese input, cuando lo pones, luego se imprime en el sitio.

Si este input es simplemente un tag HTML normal de la forma `<textarea>`, lo que va a pasar es que no hay ninguna restriccion para lo que podes poner dentro. Entonces si quisiera podria poner algo asi: `Hello World <script>alert("Hello World ...")</script>`

Osea, metes algun tag HTML que este estrategicamente pensado, y si el codigo del server no tiene ningun handling para eso, podes llegar a hacer mierda todo. 

Podes hasta modificar todo un documento. Hay casos en los que se las ingenian para robar todos los session id de todos los usuarios de la pagina. 

##### Potenciales soluciones contra cross-side scripting

- La primer solucion es asegurarte de poner una limpieza del input, en caso de que se pongan tags html. Es decir, como programador podes hacer que no esten permitido el codigo JS y HTML. 
- Lo otro que se puede hacer es, permitir que se ponga codigo HTML y JS, pero hacer que no lo tome como parte del codigo. Esto se llama hacer "escape".

El *escaping* significa reemplazar un caracter HTML con una combinacion de caracteres ASCII. Esto hace que el cliente muestre los caracteres como son, y no los interorete y procese como codigo. Estos caracteres ASCII se llaman *HTML entities*, que son como codificaciones de cada caracter que se usa en HTML. Por ejemplo, el caracter < es &lt;. 

Jajajaj fijate como funciona, que el archivo este lo toma como el caracter que es. En realidad esta codificado como entidad, si te acercas te muestra en gris lo que vale.

Por ejemplo, esto `<p>Hello World!<\p>` se convierte en esto `&lt;p&gt;Hello World!&lt;\p&gt;`. Si lo pongo sin comillas me lo toma codificado. Fijate &lt;p&gt;Hello World!&lt;\p&gt;.

### Conclusion

Este es una rama de la informatica gigante. Nosotros solo la repasamos por encima, pero te imaginaras que hay miles de problemas mas, y todos los dias deben salir nuevas formas de acceder y burlar los sistemas de seguridad.

Por otro lado, ya concluimos el libro y el tutorial, y yo creo que nos dio un buen panorama.

La idea del libro no era una guia extensiva sobre HTTP ni mucho menos, si no que era mas o menos darnos un pantallaso de lo que es, sus componentes principales, y de que forma funcionan. La idea era hacernos ver el funcionamiento de una aplicacion web un poco por debajo de lo que usualmente uno se acostumbra.

Es un muy buen comienzo al desarrollo web aprender como funciona la web y sus protocolos. Pero si se quiere meterse mas adentro hay que profundizar mas.