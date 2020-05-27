### Como funciona la web?

En esta seccion vamos a ver varios conceptos relacionados con la web y su funcionamiento. Al finalizarlo deberiamos tener en claro que es el internet, como se transfieren los datos en el internet, entender la diferencia entre una web page, un web server, etc. Ademas, saber un poco que es un cliente, un servidor, un DNS, y mas.

Vamos a tener que hacer varios assignments en esta seccion.



Lo que llamamos internet es realmente una read o network, una conexion entre una cantidad muy grande de computadores en todo el mundo, para poder hacer posible la transferencia de informacion entre ellos. 

La forma en que los computadores realizan intercambios de informacion la define un protocolo, que es una serie de "reglas" a seguir para la transferencia de datos. Asi el protocolo define como debe hacerse la transferencia, y se envian packages entre las partes. 

Un paquete contiene informacion sobre la transferencia, como por ejemplo, el destino y el remitente. 

Cada computador tiene un numero que lo identifica, llamado IP. Tambien este IP se puede camuflar en algo que es un dominio.

El dominio es el nombre que recibe una pagina web.

Esto es muy por encima.

##### A simple network

Cuando, por ejemplo, dos computadoras necesitan intercambiar informacion entre si, lo pueden hacer conectandose de forma fisica o inalambrica. Supongamos que es de forma fisica.

A esta conexion entre computadores se le llama red o network. Pero una red no solo esta limitada a dos computadoras, en realidad pueden estar conectadas una infinidad.

El problema esta que en una conexion fisica las cosas se ponen complicadas, ya que por ejemplo, si se quisieran conectar 10 computadoras tendrian que haber 45 cables y 9 puertos por cada pc. Esto haria muy dificil la transferencia de datos entre ellas. y mas si el numero sube.

Para este proposito es que se invento lo que se llama **router**, que es una computadora mas chica y con menos componentes claramente, porque su unica funcion es la de hacer de intermediario entre la conexion entre las computadoras. Asi, para conectar las computadoras A y B, la A le envia la señal al router, y este la redirige hacia B.

De esta forma el router solo necesita 10 conexiones para 10 computadoras, y cada computadora necesita un solo conector.

##### A network of networks

Pero que pasa si quisieras conectar millones de computadoras juntas, para que todas se transfieran datos entre si? Ya que los routers son tamvien computadoras, nada nos limita de conectarlos juntos. Asi es posible la extension de la conexion entre las computadoras, conectando routers juntos, y estos a otros routers, y cada uno de ellos conectados a computadoras.

Esta conexion entre computadoras y routers es muy cercano a lo que seria el internet. El internet es una conexion a nivel mundial. Para que esta conexion sea posible, es necesario un medio de transferencia particular, que pueda transformar los datos enviados por la computadora en dats manejables por el cable o conector, y asi pueda alcanzar distancias mas largas de transferencia. Para este proposito existe el **modem**, un dispositivo encargado de hacer la conversion entre el tipo de dato que recibe desde la computadora, y un tipo de dato que maneje el cable telefonico. 

Asi en todo el mundo hay un cantidad gigante de subnetworks, redes mas chicas que se conectan entre si por todo el mundo, dandote la posibilidad de intercambiar informacion con computadoras en cualquier parte. Estas sebredes las manejan las **Internet Service Provider** (**ISP**), que no es otra cosa que un proveedor de conexiones entre routers de su autoria, que se conectan entre si con otros, y asi construyen redes gigantes.

Por lo tanto, las computadoras se conectan con routers, los routers con modems, y estos transfieren la informacion hacia los ISP, que tienen routers mas robustos.

##### Finding Computers

Para realizar una transferencia de datos a una computadora, se necesita una direccion para poder conectarse con ella, llamada **IP** (**Internet Protocol**). Son una serie de numeros separados por puntos, como por ejemplo, 192.168.2.10.

El tema es que recordar numeros para el humano no se le da bien, por eso es que existe lo llamado **domain name**. Esto es un alias que se le da al IP, y claramente es unico, solo un alias puede representar a un IP. Por ejemplo, google.com es el alias del IP 173.194.121.32.

##### Internet y la Web

Hay una diferencia entre estas dos. La internet solo representa una infraestructura. Mientras que la web es solo un servicio que esta provee, al igual que email y IRC son otros servicios.

#### How The Web Works

##### Clients and Servers

Como dijimos antes, lo que se llama web es un servicio que provee o que surge gracias a la infraestructura que ya vimos llamada internet. Esta avala la conexion entre dos entidades que se les llama **client** y **server**.

El cliente es el usuario normal de la web, que realiza una busqueda usual y puede estar conectado a internet mediante una computadora o mobil. Ademas este ingresa a diferentes tipos de paginas mediante un web browser, un servicio que se encarga de hacer la transferencia de datos entre vos, el cliente, y el servidor. 

Un servidor es una computadora especial, que contiene software y hardware para poder contener en el paginas, sitios web y aplicaciones. Cuando el cliente quiere acceder a una pagina que esta contenida en un servidor, este le envia una copia de esta junto con una serie de permisos y muchas cosas mas, que las recibe el browser y la pone en pantalla.

##### Otras partes

Tambien participan de la web otros servicios y entidades que son:

- **Conexion a internet**: Es la que te permite tener acceso a la informacion y que se hagan las transferencias. 
- **TCP/IP**: Transmission Control Protocol y Internet Protocol, son solo una serie de protocolos, es decir, reglas definidas para la transferencia de informacion en la red.
- **DNS**: Domain Name Servers es el contenedor de todos los nombres o dominios en el internet. Cuando uno quiere acceder a una pagina, el web browser busca en el DNS para ver a que IP pertenece el dominio que pusiste. Y luego procede a realizar toda la transferencia.
- **HTTP**: HyperText Transfer Protocol es el protocolo que define de que panera se realiza la transferencia de datos o hipertexto. Es como la forma de comunicacion entre un servidor y un cliente. 
- **Component files**: Un sitio web esta formado por una cantidad de archivos. Estos pueden ser:
  - **Code Files**: Archivos de codigo o algun lenguaje, ya que la web esta formada por lo general de tres tecnologias que son HTML, CSS y JavaScript.
  - **Assets**: Todos los demas archivos que componen una pagina web, como pueden ser documentos docx, PDFs, imagenes, audios, videos, etc.

##### Que pasa exactamente?

Cuando uno pone un dominio en un browser, lo que pasa es lo siguiente:

1. El web browser va al DNS Server, y busca por el IP del dominio que pusiste.
2. El browser manda un HTTP request al server, pidiendo el acceso y una copia de los datos que contiene la web, como son su codigo HTML, todos sus archivos, y todo lo que la compone, junto con un paquete con diferentes permisos y protocolos. Esto se transfiere por la conexion a internet entre el cliente y el servidor, usando los protocolos TCP/IP.
3. Si todo esta bien, el server envia los datos. Entre ellos un HTTP response que es un codigo (200, 404, etc). 
4. El browser es el encargado de tomar todos los datos enviados por el servidor, e interpretarlos dentro del browser como una pagina, para imprimirla en pantalla y que el usuario lo pueda ver.

Estos contenedores de datos enviados entre las partes se llaman **packets**.



#### Diferencias entre webpage, website, web server y search engine.

Hay cuatro conceptos que se suelen usar de forma intercambiable aunque no lo son. Estos son:

- **web page**: Un documento o conjunto de ellos, que puede ser impreso por un web browser en pantalla, para mostrarlo al usuario. Tambien llamada simplemente pagina.
- **website**: Un website hace referencia a un sitio web completo, a un conjunto de paginas agrupadas que forman un mismo tema en comun. Llamado site o sitio web.
- **web server**: Una computadora especial que hace de almacenamiento de un website. 
- **search engine**: Un servicio para encontrar otras paginas web. Este posee una lista inmensa de paginas, y te permite tener una barra de busqueda de dominios, palabras clave, y mas. Estos son los ejemplos de Google, Bing, DuckDuckGo, etc. Funcionan dentro de un web browser, que es el intermediario entre el cliente y el servidor, y realiza todas las tranferencias y protocolos. Ejemplos son Chrome, Mozilla, etc.

Una web page esta formada de documentos y otros tipos de archivos. Estos pueden contener la estructura de la pagina, estilos, scripts, media, etc. Todo esto es recopilado por el browser para poder mostrarlo.

En este momento estamos usando el web browser Chrome 81. Que en su maximo detalle se escribe de esta forma: 

Mozilla/5.0 (Windows NT 10.0; ) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.138 Safari/537.36

My IP Adress es: **190.189.65.50**



Esto obviamente es una mirada muy superficial de como funciona el internet y la web. Esto en realidad es muy complejo y se compone de muchas partes. Hay una rama de estudio completa que se llama networking, que ya la vamos a tener en la facu. Ahi se ve en profundidad cada una de las partes del funcionamiento de la web.