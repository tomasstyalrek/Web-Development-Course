### UNIX 2 - Permissions, Redirection and Piping

**Permissions and Links**

Muchas veces cuando se trabaja en el terminal, aparecen un monton de errores y son muy comunes por lo general. Estos son errores que aparecen cuando intentas instalar algo o mover algo, y seguramente aparece el mensaje "permission denied" entre otras lineas. Entender porque ocurren estos errores es muy importante para poder manejarlos.

![listing items in home directory](https://www.rithmschool.com/content/terminal/output-of-l-in-zsh.png)

Esto es lo que suele aparecer si estas parado en el /home y apretas **ls -lah**. Recordar que -a te da todas las entradas, incluyendo las que se definieron con ( . ), -l te da la version en lista larga y -h es nuevo, significa "human readable".

Asi te tira toda una lista de todos los elementos en el home de tu computadora. No todo lo que esta aca es importante, pero vamos a ver que significa. Por ejemplo, en la linea en donde aparece el archivo .bashrc, que se muestran todos los archivos a la derecha. La linea es esta:

- -rwxr-xr-x 1 eschoppik staff 67B Aug 29 2014 .bashrc

Hay varias columnas. La tercera indica el owner del file, que en este caso es el **usuario** eschoppik. La cuarta columna especifica el nombre del **grupo** al que esta asociado, que en este caso es staff. 

Un usuario puede o no ser miembro del staff. En los sistemas Mac dice, por lo general el usuario de la pc es miembro del grupo staff. Para ver a que grupo pertenece un usuario, se pone el comando **groups**. Introducimos todo esto para poder hablar luego de permisos, ya que los permisos pueden ser asignados al poseedor del archivo, o a un usuario que no es el poseedor ni el miemro de un grupo. 

Ahora vamos a hablar de la primer columna en la lista de antes, que es -rwxr-xr-x. Estos caracteres son los permisos del archivo. Cada uno de ellos habla de un permismo diferente. Los permisos son una serie de reglas que definen que operaciones y cuales no puede realizan un usuario en un archivo o directorio. Hay tres tipos de operaciones que pueden ser permitidas o denegadas, que son:

- r - leer un archivo.
- w - escribir un archivo.
- x - ejecutar un archivo (despues lo vamos a ver).

Ahora, porque la string que ponen es tan larga, si solo hay tres operaciones? Esto es porque las **permission strings** describe a diferentes tipos de usuarios. Podes ser de algunos de estos tres tipos de usuarios:

- El owner del archivo.
- No el owner, pero miembro del grupo asociado con el archivo. 
- Otro. No owner ni asociado.

Entonces, la premission string tiene tres partes, una para el owner, otra para el group y otra para los others. Asi especifica los permisos que se le declara a cada uno. Ademas, tiene un caracter adicional para mostrar que es un directorio, archivo, etc.

![Permissions](https://www.rithmschool.com/content/terminal/permissionsDiagram.png)

Esta es la permission string de arriba, indicando todo. Notar que lo que dice es que es un archivo ( - ), que puede ser leido, escrito y ejecutado por el owner, puede ser leido y ejecutado por el grupo asociado y puede ser ejecutado por otros. 

Para cambiar permisos en los archivos o directorios, usamos el comando **chmod**. Este comando se utiliza junto con un codigo que esta en sistema octal, es decir, de base 8. En donde cada uno de los numero representa un permiso que puede tener el elemento en si.

| Number | Permission              | rwx (display in terminal) |
| ------ | ----------------------- | ------------------------- |
| 0      | none                    | ---                       |
| 1      | execute                 | --x                       |
| 2      | write only              | -w-                       |
| 3      | write and execute       | -wx                       |
| 4      | read only               | r--                       |
| 5      | read and execute        | r-x                       |
| 6      | read and write          | rw-                       |
| 7      | read, write and execute | rwx                       |

En esta tabla se representa cada uno de los numero y su representacion en el permiso correspondiente. Asi podemos ver que el permiso del archivo .bashrc esta compuesto de tres permisos, uno para cada usuario. 

El primero es un simbolo ( - ) que representa un file, luego esta seguido de los permisos rwx, r-x y r-x todo junto. 

En el caso de querer cambiar el permiso de un archivo, usamos el comando chmod, junto con los tres permisos y el file. 

- chmod 770 somefile.txt

Pero tambien se puede ser mas especifico usando **symbolic notation**. Esto es:

`chmod ug+rwx,o-rwx hi.txt`

Lo que le esta diciendo ahi es que añada a u (user) y g (group) los permisos rwx y le quite a o (other) los permisos rwx. 

En caso de querer cambiar los permisos de un **directorio**, tenes que usar el flag **-R**.

chmod -R 755 some_folder.

Por otro lado, vamos a hablar un poco de que significa el permiso "x" para un file o folder. Un permiso "x" (**executable**) te dice que podes acceder a el, por ejemplo con el comando *cd*. 

Por ejemplo, si creamos un directorio normal, deberiamos tener permiso a ingresar a el ya que por defecto los directorios que creamos tienen el permiso x puesto. 

```
mkdir test_folder
cd test_folder
cd ..
chmod 666 test_folder
cd test_folder
```

Pero en ese caso, en que cambiemos los permisos a 666, es decir, a que todo tipo de usuario solo puede leer y escribir sobre el, entonces a la hora de cambiar directorio a ese, va a dar un error.

Da un ejemplo con un shell script, haciendolo ejecutable. Lo que hace es añadirle cosas al script, y luego le cambia los permisos con chmod 755 test.sh, y asi puede acceder a el.

Volvamos a la linea del comando que pusimos que fue **ls -lah**. Lo que tiro fue esto en una de las filas:

-rwxr-xr-x 1 eschoppik staff 67B Aug 29 2014 .bashrc

Vamos a terminar de saber que es cada una de estas columnas. Ya digimos que la primer columna representa los permisos del archivo .bashrc. Luego viene la columna con el numero 1, que hace referencia al numero de archivos (que siempre es 1 para files). Luego viene eschoppik y  staff, que digimos que eran el usuario y el grupo al que pertenece el archivo o directorio, respectivamente. Luego tenemos a 67B, que es el tamaño del archivo (estoy seguro que representado en hexadecimal), Aug 29 2014 es el ultimo dia que se modifico el archivo, y por ultimo el archivo en si .bashrc.

Que pasa si no queremos que eschoppik y  staff sean el owner y el grupo del archivo? Bueno, podemos usar los siguientes comandos:

chown anotheruser:anothergroup .bashrc

Se puede ver que chown viene de "*change owner*". O tambien si queremos cambiar el grupo, usamos el "change group":

chgrp anothergroup .zshrc.

Por lo tanto, usamos chown para cambiar el usuario del archivo y chgrp para cambiar el grupo. 

Pero fijate este otro archivo:

drwxr-xr-x 6 root admin 204B Oct 20 2015 ..

Este es un poco diferente. El usuario ahora es root, y el grupo es admin. Ademas son 6 y son directorios, por la primer d. Que es el usuario root?

El usuario **root** es un usuario especial que puede hacer lo que quiera en la computadora, cambiar permisos, borrar lo que quiera y demas. Ahi es cuando entra el comando **sudo**. 

Cuando el owner del archivo es el root, y queres cambiar algo en ese archivo, tenes que usar el comando **sudo**. El comando sudo lo que hace es darte el poder del root por una linea, y te pregunta por la contraseña para poder realizar el comando. 

Por ejemplo, podrias crear un archivo y decirle que le queres cambiar el owner a root. Para esto tenes que usar sudo:

sudo chown root somefile.txt

Aca sudo hace de comando para poder ser el root. Luego usa el change owner y luego le dice que quiere que sea el root. Si despues queres eliminar el archivo, no te va a dejar porque no sos el root. Tenes que usar sudo. 

Como tenemos muchos archivos y directorios por todo el sistema, a veces se vuelve dificil saber donde estan. Por eso existe el comando **ln**, el cual nos permite crear un link hacia un archivo o directorio. 

ln path_to_link name_of_link

La estructura para hacerlo es esa. El comando ln, la ruta al link, el nombre del link.

Hay dos tipos de links que podemos hacer, los hard y symbolic links. 

Los **hard links** tienen una particularidad, pero primero hay que saber que es un link. Suponete que creamos un archivo en el Desktop que se llame learn.txt. Luego le añadimos texto con echo "texto" > learn.txt.

Ahora lo que hacemos es crear el link al archivo de texto, usando el comando ln.

ln learn.txt first_link

Lo llamamos first_link. Ahora este link es como un atajo o acceso directo al archivo. No importa si lo movemos de directorio, el link siempre te abre el mismo archivo. 

La particularidad de los **hard links** es que si el archivo se borra, el link lo sigue ejecutando como antes.

Pero en caso de que solo querramos una referencia a un archivo, y no tenerlo para siempre como copiado en un link, usamos un **symbolic link**. Para hacerlo es exactamente igual, pero usamos el flag **-s**. Ahora si tenemos un link simbolico a un archivo, podemos hacer cat link mientras exista el archivo, pero si se borra el link da error. 

Esto tambien es posible de hacer para directorios. Muy util por si no nos acordamos el path a el, o si es muy largo y queremos un atajo. 

Sumario: Aprendimos sobre permisos, root y sudo y links. Ademas, empezamos a usar los comandos chmod, para cambiar permisos, chown para cambiar owner, y chgrp para cambiar de grupo. Luego, sudo para tener permisos de root, y ln para crear links a archivos. 

**Redirection**

Hay veces que uno quiere hacer un output con un comando, y quiere enviar ese output hacia otro archivo o directorio. Para estos casos existe la redireccion. Esto es algo que ya hicimos anteriormente, y se utilizan para esto los simbolos  >> o >. 

Hagamos un ejemplo con el comando echo.

El comando echo es util para imprimir texto en el terminal, pero a veces es mas util tomar ese texto y redireccionarlo a un archivo. Podriamos poner el comando

echo Hello World > hello.txt, y lo que haria seria enviar el texto Hello World al archivo de texto hello.txt. Luego si accedieras al archivo con cat, te mostraria el output. 

Pero el tema es que si lo volves a usar con otro texto, como echo Hello Universe > hello.txt, lo que hace hace es reescribir el texto. Si ahora pones cat sobre el archivo, te va a mostrat el nuevo texo, y el viejo lo superpone. 

Capas que queres hacer esto, pero capas que no. En caso de que lo que quieras hacer sea añadir texto, hacer un append a la siguiente linea, ahi es cuando entra el simbolo >>. Por ejemplo, podriamos añadirle mas texto al archivo hello.txt de esta forma: echo Hello World >> hello.txt. Y ahora, si hacemos cat sobre el archivo, veriamos lo siguiente:

```
Hello Universe
Hello World
```

Esto es muy util en los casos en que queremos añadir cosas chicas a los archivos de texto. Ahorra mucho tiempo, ya que es poner un comando, contra abrir, escribir, y guardar el archivo. 

Otra forma de hacer redirection es con **input** en vez de output. Para esto en vez de utilizar el simbolo >, usamos <.

Hagamos algo por ahora. Supongamos que tenemos un archivo que se llama names.txt. Dentro del archivo estan los siguientes nombres: 

```
Bob
Tom
Jim
Amy
```

Hay un comando que se llama **sort**. Este comando lo que hace es ordenar en orden alfabetico texto. Por lo tanto, podemos hacer sort names.txt, y va a hacer un sorting de los nombres dentro de name.txt. 

```
Amy
Bob
Jim
Tom
```

Ahora, lo que podriamos hacer es redireccionar el input a otro archivo de la siguiente manera: sort < names.txt > sorted.txt. 

Es como si las flechas o el mayor y el menor indicaran para que lado esta dirigida la redireccion de las cosas. Es como si le digera, hacele un sort a names.txt y metelo dentro de sorted.txt.

El tema viene cuando intentamos usar otros comandos con sort. Para conectar todos los comandos que queremos poner en la redireccion, necesitamos usar algo llamado "pipes". 

Por lo tanto, en conclusion, lo que aprendimos en este apartado fue sobre redireccion. Como hacer que comandos y texto se dirigan hacia otros archivos como un output que envien, o que al revez reciban un input. 

**Piping**

Ya vimos como podemos hacerle un redirect a un archivo, de forma que se puedan realizar ms de un comando a la vez sobre algo, o hacer que el archivo realize un output e input a otro archivo. 

Pero que pasa si uno quiere encadenar mas comandos juntos? Ahi es donde estra lo que se llama "**piping**". Antes de hablar del piping, hay que introducir nuevos comandos.

- head - imprime las primeras lineas de un archivo (usando el flag -n podemos especificar cuantas lineas queremos).
- tail - imprime las ultimas lineas de un archivo (con -n especificamos cuantas).
- sort - ordena las lineas de un archivo de texto.
- uniq - elimina lineas duplicadas del archivo (pero para que funcione debe estar ordenado ya).
- wc - hace un count de las palabras, lineas, caracteres y bytes. 

Creemos dos archivos, uno first.txt, que contiene las lineas:

```
First
Second
Third
```

Y un segundo archivo second.txt:

```
Fourth
Fifth
Sixth
```

Ahora lo que hacemos es **concatenar** ambos, con el comando **cat** de esta forma:

cat first.txt second.txt

Pero que pasa si, por ejemplo, queremos concatenar ambos archivos, despues queremos ordenar lo de adentro, despues queremos mostrar las ultimas tres lineas y despues las primeras tres. Bueno, esto se hace haciendo **piping** o una tuberia. 

Es decir, el piping es una forma de unir comandos, diciendole, hace esto, despues esto y asi.

cat first.txt second.txt | sort | tail -n 3 | head -n 1

Como se puede ver, el caracter para hacer pipe es **|** character. Entonces, viendo al comando de arriba, lo que hace es concatenar los dos archivos. Luego ordena, luego muestra las tres ultimas lineas (notar el -n 3) y luego las tres primeras. 

Hay otras que no usamos, pero que pudimos usar luego de usar el sort, como puede ser uniq, que elimina duplicados, o wc, que cuenta palabras.

Otro comando muy util es **grep**. Es util para bucar texto, y funciona bien solo pero tambien si se usa con cat en un piping. 

Por ejemplo, si harias lo siguiente cat first.txt | grep First lo que pasaria es que imprime en pantalla "First". Esto es porque grep lo que hace es hacer un find de la palabra que pones, y como esta esta en first.txt, la encuentra y la imprime. Si ademas, encuentra varias coincidencias, las imprime a todas. 

Otro ejemplo, si haces esto que tira?

```
cat first.txt second.txt | grep Nope
cat first.txt second.txt | grep th
```

El primero no hace nada, porque le estas pidiendo que encuentre la palabra Nope en la concatenacion de first.txt y second.txt. Pero en la segunda si va a haber coincidencias, y van a ser 6 th.

Otro ejemplo de piping lo podemos hacer con el comando **uniq** y **sort**, que por o general van a ir juntos, ya que para poder usar uniq, tiene que estar ordenado el archivo. Suponete este archivo petnames.txt:

```
Lassie
Moxie
Whiskey
Fido
Lassie
Moxie
```

Le podemos hacer: sort petnames.txt | uniq

```
Fido
Lassie
Moxie
Whiskey
```

Lo que hace es, primero ordenar, luego borrar duplicados. 

Y ponele que queres mandar eso a un nuevo archivo petnames_sorted.txt. Bueno, podes usar redirection asi: sort petnames.txt | uniq > petnames_sorted.txt

Asi le decis que queres mandarselo a ese nuevo archivo. Si existe lo reemplaza, si no lo crea.