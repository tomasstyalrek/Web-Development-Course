### UNIX 3 - Environment, Process and Finding

**Terminal Environment**

El entorno del terminal es una lista de configuraciones, de settings que pueden ser referenciados por programas. Para ver el terminal's environment se puede poner en el terminal el comando env. Se deberia poder ver un output como el siguiente:

rvm_bin_path=/Users/tim/.rvm/bin

TERM_PROGRAM=Apple_Terminal

GEM_HOME=/Users/tim/.rvm/gems/ruby-2.3.1

TERM=xterm-256color

SHELL=/bin/bash

CLICOLOR=1

IRBRC=/Users/tim/.rvm/rubies/ruby-2.3.1/.irbrc

TMPDIR=/var/folders/5s/zstwqxy52pl_lq_lr3b5v7nc0000gn/T/

Apple_PubSub_Socket_Render=/private/tmp/com.apple.launchd.Q7TcyOvK4P/Render

TERM_PROGRAM_VERSION=361.1

OLDPWD=/Users/tim

TERM_SESSION_ID=281162A1-5C58-4285-9A35-AC9306923C34

USER=tim

__CF_USER_TEXT_ENCODING=0x1F5:0x0:0x0

LSCOLORS=GxFxCxDxBxegedabagaced

PATH=/usr/local/bin:/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin:/Users/tim/.rvm/bin

PWD=/Users/tim/Projects/Rithm/prework

.

.

.

Yo creo que este es mas el caso de los sistemas basados en UNIX, ya que el del tutorial tiene una mac. 

Cada uno de los elementos a la izquierda del =, en el output de arriba, representan las **variables de entorno** o **environment variables**.

Dada una variable de entorno que quieras saber que representa, o su valor, podes usar el comando echo, junto con la variable de entorno. Toda variable debe ir con el prefijo $. Por ejemplo, si quisieras imprimir la variable PWD:

echo $PWD

Lo que hace esto es mostrarte el output de esa variable.

Ahora pasemos a crear nuestra propia variable de entorno. Por ejemplo, podriamos crear un directorio en el Desktop llamado Projects. Y luego de eso, podriamos hacer una variable llamada PROJDIR, que mantiene un seguimiento del path del nuevo directorio que creamos. 

Es que esta es la funcion de una variable de entorno. Lo que hace una variable es almacenar en memoria el path a un cierto lugar que vos le des. Asi cada vez que llames a esa variable, vas a ir a ese path o ejecutar el archivo que pedis.

Para crear una variable nueva, podemos usar el comando export, seguido de la declaracion de la variable.

export PROJDIR=/Users/Tomas/Projects

Notar que el simbolo $ no se usa en este caso, porque no es para declaracion de variables, si no para cuando se quiere referenciar el valor de una variable.

Y ahora que esta declarada, podes usarla normalmente:

cd $PROJDIR

Ahi si usas el $.

El problema es que, ahora, si cerramos el terminal, la variable se borra. No se queda guardada. 

Para poder guardar las variables de entorno y que cada vez que entremos al terminal este disponible para su uso, tenemos que modificar algunas cosas en el archivo de configuracion del shell. Este archivo se encuentra en el directorio home, y cambia segun la shell que se tenga. Si estas usando oh-my-zsh, el archivo de configuracion deberia llamarse .zshrc, y si estas usando bash el archivo se llama .bash_profile.

Estos archivos de configuracion contienen todas las variables de entorno. Por lo tanto, si queres definir una nueva tenes que definirla dentro de la misma manera que antes: Abris el archivo .zshrc o .bash_profile y pones:

export PROJDIR=/Users/$USER/Projects

Ahora se guarda el archivo, se cierra todo y se vuelve a abrir. Cuando se pone devuelta el comando echo $PROJDIR, deberia imprimir el path al directorio.

Lo bueno de las variables de entorno es que tambien se pueden usar como atajo para un path. Por ejemplo:

export PYTHON_DIR=$PROJDIR/python

Se puede notar que para acortar el path a la variable, se utiliza la otra de la misma forma que antes.

Por ultimo, vamos a ver una variable muy comun que es la variable de entorno PATH. La funcion de esta variable es encontrar programas para ejecutar. 

Es por esta variable que la mayor parte de los comandos funcionan. Ya que los comandos son programas en si, son como funciones que ya estan programadas por el shell, y estan almacenadas por lo general en el directorio bin. Estos comandos son programas en si ya programados, y qie cada ves qie se ejecutan, es posible hacerlo porque estan seteadas en la variable PATH. 

Podes darte cuenta de esto porque si cambias la declaracion de la variable path, no vas a poder acceder a la mayoria de los comandos. 

**Processes**

Un proceso es un programa en la computadora que esta siendo ejecutado. Por ejemplo, el google chrome que esta abierto ahora es un proceso. Todo programa, incluyendo hasta un comando de la shell, que es un programa, se denomina proceso.

Lo bueno de los sistemas operativos y su manejo de los procesos es que, uno puede asegurarse de que la memoria utilizada por un proceso no puede ser accedida por otro proceso. Esto te asegura de que si un proceso falla, esto no tiene ningun efecto en el resto del sistema.

Lo que vamos a ver es como uno puede saber que procesos estan ejecutandose en estos momentos en la computadora, y como cerrarlos desde el terminal.

El comando **ps**, corto para "*processes"*, es un comando muy util para ver que procesos estan ejecutandose en ese momento en la maquina. El comando ps se puede usar solo, pero es muy comun usarlo de la forma **ps aux**. Este aux no es un comando, si no que cada letra significa algo. 

La a en aux indica que queres all todos los procesos, no solo los que esta ejecutando tu usuario actual. La u hace que se imprima el owner del proceso. Por ultimo, x hace que sea posible cer toda la lista de procesos, y no solo los que estan relacionados con el terminal. La razon por la que se escribe aux y no -aux, es historica, una convension particular.

Si pones el comando, sale algo como esto:

USER   PID  %CPU %MEM      VSZ    RSS   TT  STAT STARTED      TIME COMMAND

tim  74874   8.3  1.7  3408348 139912   ??  S     3:34PM   6:39.74 /Applications/Google Chrome.app/Contents/Versions/53.0.2785.116/Google Chrome Helper.app/Contents

tim  74858   6.2  2.8  3224740 233060   ??  S     3:34PM   8:34.62 /Applications/Google Chrome.app/Contents/MacOS/Google Chrome

tim  61431   2.5  0.6  2698840  53728   ??  R     9:46AM   0:59.49 /Applications/Utilities/Terminal.app/Contents/MacOS/Terminal

Algunas columnas importantes son las USER, PID, y COMMAND. La columna USER es el nombre de usuario del usuario ejecutando el proceso. La columna PID es el numero que identifica de forma unica al proceso. 

Hay veces que un proceso sigue ejecutandose, aunque uno ya dio la orden de que debia cerrarse. Estos casos en donde el programa no responde, es util el comando kill, que hace un cierre forzoso del programa.

Los dos comandos estos funcionan en windows tambien. Lo que hice fue crear un archivo hola.txt, lo abri. Luego con ps vez todos los procesos, aunque de una forma un poco dirente que en linux. Cuando lo identificas, pones kill y el id y muere.

Esta es la forma de hacerlo siempre. Identificas el ID o PID number, y ejecutas por ejemplo:

kill 10011

Hay otro comando que se suele usar, que en realidad es una flag adicional, y es kill -9. Este es otro comando que aparece en los tutoriales. 

La diferencia con el anterior es que ese manda una señal al programa para que se cierre, y esa señal se llama TERM . Esta señal cierra el programa efectivamente, pero hay veces que el programa se queda congelado. En esos casos se usa el kill -9, que lo que hace es mandal una señal KILL, que significa "non-ignorable kill", o sea no hay forma de ignorarla.

**Finding Files and Folders**

Vamos a introducir el comando **find**, uno de los comandos mas utilizados, ya que te deja encontrar un archivo o directorio especificando su nombre. 

Si queres buscar el nombre de un directorio, va a encontrar al directorio y mostrar su contenido. 

Por ejemplo, si quiesieramos encontrar todas nuestras descargas, podemos hacer:

find Downloads

Esto nos da todo el contenido de la carpeta Downloads.

Hay dos formas de usar el comando file. Una es con un filepath, es decir, la ruta del archivo. La otra es con una expresion. Podemos usar **regular expressions** para encontrar archivos. Esto es muy conveniente para encontrar coincidencias.

Por ejemplo, ingresemos al directorio views suponiendo que lo tenemos en nuestra computadora. Ahora vamos a buscar todos los archivos con el nombre first.txt dentro de directorio:

find . -name "first.txt"

Esto lo que haria es encontar todos los archivos con el nombre first.txt. No se si tiene mucha utilidad en verdad. 

Pero eso solo te sirve en caso de que te sepas exactamente el nombre del archivo que queres buscar. El tema aparece cuando uno no sabe el nombre, o hay varios nombres que tienen ciertas coincidencias pero no todas. En esos casos es muy bueno usar regular expressions. 

Por ejemplo, podriamos hacer uso de wildcards coomo pueden ser *, que significa cualquier numero de caracteres, ?, que es un caracter y [] que simboliza cualquiera de los caracteres entre los corchetes. 

Estos son otros ejemplos:

- Encontrar dentro de el directorio views cualquier cosa que termine con .html, es decir, cualquier archivo con extension html. Por lo tanto, hacemos cd dentro de views, y luego ponemos el comando: find . -name "*.html"
- Encontrar dentro de views, todo archivo que termine con una extension de tres letras, como por ejemplo .txt o .css. Entonces hariamos find . -name "*.???". Porque le estas diciendo, * cualquier cantidad de caracteres, un punto . y luego tres caracteres, que lo pones con ? para simbolizar cada uno un caracter cualquier.
- Encontrar cualquier archivo dentro de views que empiece con las letras f, t o s. Hacemos find . -name "[fts]*". Los caracteres dentro de los corchetes simbolizan un espacio solo en donde pueden estar esos caracteres.
- Encontrar todos los archivos que tengan un main en algun lado de su nombre. Hacemos find . -name "*main*". Le mandamos * antes y despues para denotar que pueden ir cualquier cantidad de caracteres.

En conclusion, con find podemos encontar archivos o directorios buscandolos por nombre, path o una expresion. El metodo mas util es el de la expresion, ya que busca por coinsidencias. 

Recorda que * simboliza una cantidad indefinida de caracteres. El simbolo ? simboliza un solo caracter que puede tomar cualquier valor. Y los corchetes [ ] simbolizan cualquiera de los caracteres que esten dentro de ellos. 

Seguramente se puedan usar muchas mas expresiones y otras cosas. Pero esto me parece bastante bien, no creo que se necesite mucho mas. En caso de no poder hacer tu expresion por falta de algo, hay que consultar por regular expressions. 

Otro comando utilizado con un proposito parecido es el comando **grep**, que ya lo vimos antes. Este comando sirve muy bien, no para archivos y directorios, si no para hacer busqueda de valores especificos en una string de un archivo de texto.

Ademas grep se puede usar con piping y cat, esto añade utilidades.

Por ejemplo, ya vimos que podiamos hacer cosas como estas: cat people.txt | grep Elie. O sea, agarrar y decirle que abra el texto y busque por coincidencias en el nombre Elie. Esto es posible de hacer usando piping.

Vamos a usar este archivo names.txt como ejemplo:

Lisa

Mark

Elie

Beth

Tim

Elizabeth

Tom

Matt

Liza

Janey

Jane

Shana

Agreguemos algunas utilidades al comando **grep**, introduciendo algunas flags:

- -i es para busquedas que no distingan mayusculas. Por ej. 
- - - grep -i "elie" names.txt => Elie

- -w para busqueda de palabra entera. En cambio antes buscaba todo lo que coincidia con lo que ponias. Si ponias Eli tambien la encontraba seguro.
- - - grep -i "beth" names.txt
    - grep -iw "beth" names.txt => Beth  {combinando ambas}

- -A para imprimir una dada cantidad de lineas despues. O sea, encientra la coincidencia y la cantidad de lineas que pones despues tambien.
- - - grep -A 3 "Beth" names.txt

Beth

Tim

Elizabeth

Tom

- -B lo mismo que -A pero con la cantidad de lineas antes. O sea, el nombre en este caso esta ultimo.
- - - grep -B 3 "Beth" names.txt

Lisa

Mark

Elie

Beth

- -C imprime una dada cantidad de lineas alrededor. Con alrededor se refiere arriba y abajo.
- - - grep -C 3 "Beth" names.txt

Lisa

Mark

Elie

Beth

Tim

Elizabeth

Tom

- -v invertir la busqueda. O sea, busca todo lo que no estas buscando.
- - - grep -v "Jane" names.txt

Lisa

Mark

Elie

Beth

Tim

Elizabeth

Tom

Matt

Liza

Shana

- -c count. Cuenta las coincidencias. 
- - - grep -c "Jane" names.txt => 2

- -n mostrar el numero de linea.
- - - grep -ni "Jane" names.txt

10:Janey

11:Jane

Para mas flags, ver el manual.

Resulta que antes con find, lo que usabamos en las expresiones no eran regular expressions, eran simbolos definidos en el find nomas. 

Ahora, la diferencia es que en el grep si se usan regular expressions. Asi tenemos los simbolos:

- ( . ) cualquier caracter

- - grep -wc "...." names.txt => 7 Esto le dice cuantos nombres hay con 4 letras.

- ( * ) Coincude con 0 o mas de los caracteres precedidos. Ej. cuantos nombres empiezan con T.

- - grep -wc "T.*" names.txt => 2

- [ ]  - Caracteres especificos. Ej. cuantos nombres empiezan con L, M o E.

- - grep -wc "[LME].*" names.txt => 6

- [^] - no coinciden. Ej cuantos nombres no empiezan con T.

- - grep -wc "[^T].*" names.txt => 10