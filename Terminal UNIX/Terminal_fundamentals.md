### UNIX 1 - Terminal Fundamentals

Aca empieza esta serie de cursos que vamos a hacer en esta pagina. Les tengo una re fe. Estan re bien estructurados.

Este curso nos introduce al Terminal y a UNIX, dos herramientas fundamentales para cualquier desarrollador. Es bastante largo y nos lleva por un proceso desde principiante a avanzado en el uso del terminal. 

**1 Terminal Fundamentals**

**Navigating in Terminal**

Se le llama **Terminal** a una aplicacion que nos provee una **command line interface** (**CLI**) o una interfaz de linea de comandos, que es una forma de comunicarnos con la computadora. Cualquier cosa que puedas hacer en el explorador de archivos o Finder se puede hacer aca. 

Se le llama Finder a la GUI o grafical user interface de las computadoras con sistema operativo macOS. Es el relativo a cualquier explorador de archivos. 

El terminal es una herramienta mucho mas conveniente y rapida, al no tener que lidiar con una interfaz grafica. 

La CLI es un metodo, y no un programa informatico, que nos permite comunicarnos y darle instrucciones a un programa informatico como tal por medio de una linea de texto. Hay que diferenciarla de una shell o emulador del terminal, ya que estos son programas informaticos, y la CLI es un metodo.

Segun stack overflow, una **shell** es un programa que procesa comandos y retorna output al usuario. Ademas la mayoria de las shells manejan procesos visibles y no visibles (mejor dicho foreground y background) como puede ser la command history y editing. La shell mas comun en los sistemas linux modernos es los que se llama **Bash**. Ademas nosotros vamos a usar **zsh** (Z Shell), que es un potente bash de los sistemas basados en Unix como GNU/Linux.

Un **terminal** refiere a un programa que hace de envoltorio que corre una shell. Antes era un dispositivo fisico que consistia de un monitor y un teclado. Como los sistemas unix y linux añadieron nuevas y mejores tecnologias, termino siendo un software.

En Windows hay un software que se llama Babun, que emula una shell del estilo de Mac o LInux, y es buena para aprender sin necesidad de cambiar de OS.

En la terminal, todos los archivos empiezan con el **root directory**, que es denotado con un ( / ). El root directory es el directorio de mayor nivel en un sistema de archivos, y esa barra denota que estas partiendo de ese directorio principal. Dentro de este root directory hay archivos que son esenciales para la maquina que esta los necesita. Tambien dentrp hay un folder que se llama **Users** que contiene todas los directorios de los usuarios en tu computadora. Si te moves al directorio de tu usuario, vas a estar en lo que se llama **home** directory, que tambien se denota con ( **~** ). Por ejemplo, mi ruta es /Users/Tomas, que se representa en el bash con el ~. 

Una de las cosas mas comunes en el terminal es aprender a moverse entre directorios. El comando que se utiliza para hacerlo es **cd**, que es el nombre corto para "*change directory*".

Para moverte a un directorio dentro de la ruta en donde estas, usas cd junto con el nombre del directorio que queres. Si queres meterte varios directorios dentro, usas el path completo desde el directorio en donde estas. 

Por ej. si estas en el home directory y te queres mover al escritorio:

{ ~ } >> cd Desktop

{ ~ } >> cd Desktop/TrabajoMadre

Si se quiere ir para atras en el directorio, o mover para arriba se dice, usas **cd . .**

Mencionamos que podemos especificar el path en el comando cd, pero no sabemos que es un path. 

Un path es la forma de obtener un archivo o directorio. Es la direccion o camino hacia lo que queres obtener. 

Se llama absolute path a una ruta que arranca desde el root directory ( / ). Por ejemplo, si estoy ahora en el home ~, y quiero ir al directorio Desktop, lo puedo hacer de dos maneras:

{ ~ } >> cd Desktop

{ ~ } >> cd /Users/Tomas/Desktop

El primero se llama **relative path**, porque es relativo al current path. El segundo es el **absolute path**, porque pone el path entero desde el root directory.

Algunas preguntas: 

- Cual es la diferencia entre / y ~? 

- - El simbolo / indica el root directory, el directorio de mayor nivel en la computadora y que contiene a todos los demas directorios. El simbolo ~ representa el home directory, es decir, /Users/Tomas.

- Que comando se usa para cambiar directorios? 

- - Se utiliza el comando " cd ", corto para change directory.

- Cual es la diferencia entre el path relativo y absoluto? 

- - El path relativo empieza desde el directorio actual en el que estoy. En cambio, el path absoluto indica toda la ruta a seguir desde el root directory.

**Working with Files and Folders**

Ahora que ya vimos como navegar por el Terminal y visualizar directorios, vamos a ver como crear nuevos archivos y directorios ahora.

Para crear una nueva carpeta o directorio tenemos que usar el comando **mkdir**, que es un corto para "*make directory*", seguido del nombre del directorio que queremos crear o los nombres separados por coma de todos los que queramos. Por ejemplo:

{ ~ } >> cd /Users/$USER/Desktop

{ ~ } >> mkdir first_folder

Esa cosa que aparece arriba (**$USER**) es una variable de entorno o environment variable, de esas que uno tambien puede crear y se le dice añadir al path. Bueno, esta ya viene predefinida en el sistema operativo y lo que hace es tener un seguimiento de quien es el actual usuario de la shell. 

Para ver quien es el $USER, podes imprimirlo en pantalla con **echo $USER**, o con el comando **whoami**.

Ahora que ya tenemos creado nuestro directorio que llamamos *first_folder*, ahora podemos ingresar a el con el comando *cd*. Si estas fuera del Desktop, ingresas a el con el absolute path, pero si ya estas en el Desktop, solo necesitas poner el nombre del folder.

Notar que pusimos la condicion de "si estas en el Desktop". Como sabe uno si esta en el Desktop o no? Bueno, esta el comando **pwd**, que lo que hace es imprimir el absolute path de donde estas parado. Este comando es un corto para "*present working directory*".

{ ~ } >> pwd

/home/Tomas/Desktop/first_folder

Ahora que estamos en el folder que creamos, podriamos crear un nuevo archivo. Una manera muy simple de crearlo es con el **touch** command, que lo que hace es crear un archivo vacio. Asi, si estamos en el directorio first_folder ya, podemos crearlo con un relative path, si no con absolute. 

{ ~ } >> touch /Users/$USER/Desktop/first_folder/first_file

{ ~ } >> touch first_file

Y ahora que creamos el archivo, podemos asegurarnos de que esta ahi con el comando **ls**, corto para "*list*". Lo que hace este comando es enlistar todos los directorios y archivos dentro del directorio.

Hay un comando muy comun para imprimir en pantalla todo el contenido de un archivo, que es el comando **cat**. Si se pone en el terminal *cat name_of_folder*, se puede ver facilmente desde ahi todo el contenido del archivo.

Pero el comando cat no muestra nada si es que el archivo esta vacio. Por eso, vamos a añadir texto al archivo asi podemos usarlo al cat.

{ ~ } >> echo "Hello World" > first_file

El comando **echo** lo que hace es imprimir texto en el terminal. El ***>\*** se llama **redirect**. Lo que hace el redirect es dirigir el output desde el comando en la izquierda el simbolo a lo que esta a la derecha. O sea, como que le dice, lo que esta a la izquierda se dirige a lo de la derecha. Asi el comado echo se ejecuta dentro del archivo que creamos.

Ahora si intentamos devuelta con cat, si va a imprimir en el terminal el texto del archivo, ya que le ingresamos el hello world con echo.

Otra forma de navegar por dentro del contenido de un archivo es con el comando **less**. Lo que hace less es permitirte navegar por el archivo y su contenido, bajando y subiendo podes acceder a las distintas partes. Para salir del modo ese, apretas **q**.

NOTA: El bash de linux no solo es un terminal de comandos, si no que tambien permite la creacion de scripts y es un lenguaje de programacion en si. O no estoy seguro de si lo es bien, pero ofrecen un monton de caracteristicas como estructuras de control y demas para hacer consultas y varias cosas dentro de sistemas operativos UNIX.

Por esto es que cuando pones bash online te salen entornos en donde uno puede programar un archivo .sh, que corresponde a un script de de shell.

Siguendo con los comandos.

Si se quiere abrir un archivo dentro del directorio actual en donde estas, usas el comando **open**. Por ejemplo, dentro de first_folder, podes hacer *open first_file*.

En windows el comando se llama *start*. Para abrir todos los archivos dentro de un directorio se utiliza el punto ( . ), de la forma **open .** .

Otra operacion muy comun es hacer copias y movimientos de files entre directorios. La operacion mover la hacemos con el comando **mv**, corto para "*move*".

Para probar como funciona, creamos un archivo text.txt en el Desktop, y lo vamos a mover dentro del first_folder.

Entonces ahora, una vez que estamos en el Desktop, en donde se puedan ver ambos el directorio y el archivo, entonces hacemos:

{ ~ } >> mv text.txt first_folder

Es decir, va primero el archivo que queremos mover, luego el destino. Si el destino no esta en el mismo folder, tenes que especificar el absolute path.

Para copiar archivos, usas el comando **cp**, corto para "*copy*". La sintaxis es asi:

cp PATH_TO_ORIGINAL_FILE PATH_TO_COPIED_FILE

Aca se puede ver que la operacion copy no es un copiado normal como el que haces con el mouse. Con el mouse uno copia y pega, como si hiciera un move de un folder a otro de un archivo, pero si moverlo del todo si no que hace una copia del mismo, y ahora tenes dos duplicados. 

En cambio aca, lo que hace copy no es hacer el move del duplicado, si no que solo lo duplica en otro archivo. Por eso uno especifica el archivo original, y el archivo copia. 

En caso de querer hacer un move de una copia, vas a tener que hacer ambas operaciones. Primero copias en un archivo de nombre diferente al original, luego lo moves.

En caso de que se quiera copiar un directorio entero, no se puede usar cp, ya que da error. Tenes que modificarlo con un **-r**. 

cp -r first_folder first_folder_copy

Y ahi si lo hace bien. Notar que siempre por lo general van en orden el original y la copia.

Esta **-r** se llama **flag**. Una flag se puede pensar como una opcion que uno le pasa al comando para cambiar su estado. Para ver todos los flags de un comando, se coloca el comando **man**, que viene de "*manual*". En windows esto es *--help*. Por ejemplo, *man cp* te da una lista de todos los flags de cp. Con q la sacas.

Ahora vamos a ver como eliminar archivos. Para eliminar archivos, se utiliza el **rm** command, corto para "*remove*". Pero hay que ser muy cuidadosos con este comando, porque una vez que se elimina un archivo, no pide confirmacion ni nada, y tampoco va a la papelera, lo elimina de la computadora del todo. 

Asi con seguridad podemos hacer rm con los dos archivos dentro de first_folder.

rm first_file.txt

rm first_file_copy.txt

Pero devuelta va a haber un problema si intentas eliminar el directorio first_folder. Esto es porque el comando rm es solo para files. 

Para eliminar directorios (vacios) usas **rmdir**. Si el directorio no esta vacio, te va a saltar el error rmdir: first_folder: Directory not empty. 

Con **rm -rf** podes eliminar un directorio con contenido dentro.

NOTAS: 

Con mv se puede renombrar un archivo tambien. Poniendo mv archivo renombre.

**Listing Files and Flags**

Ya vimos que el comando **ls** enlista todos los files y folders de un directorio. Pero hay muchas veces en que el ls no nos muestra todos los directorios. 

Para poder lograr diferentes cosas con estos comandos hay que agregarles flags. Las **flags** pueden usarse para alterar el comportamiento de un comando. Se usan añadiendole al comando un ( **-** ), y por lo general son solo letras minusculas o mayusculas. 

Por ejemplo, pasandole a ls el flag **-a**, podemos enlistar "all", todos los archivos y directorios, incluyendo los que estan escondidos. 

Hay otro flag que es **-l** que nos da mas informacion sobre cada directorio y archivo. 

Los flags pueden ser combinados para añadir mas de uno al mismo tiempo, y se pueden mandar uno al lado del otro. Por ejemplo, si se quisiera con ls el flag a y l, lo pones asi:

ls -la

El comando ls es uno de los mas usados, y mas porque despues lo vamos a usar mucho con git. 

**Excercises**

La parte uno ya la hice en el shell.

Part 2:

- Que hace el comando man? Como salis de un man rm?

- - El comando man imprime el manual de un comando. Para salir de un manual apretas la tecla q.

- Que hace el flag -l y -a en ls?

- - El flag -a muestra todo el contenido, monstrando todos los directorios y archivos, hasta los escondidos. El -l usa un formato largo de lista.

- Como se salta a la ultima linea del terminal? 

- - Usando **ctrl+e**

- Como te moves al principio del terminal? 

- - Con **ctrl+a**.