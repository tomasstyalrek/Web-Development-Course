### UNIX 4 - Advanced Terminal Commands

**SSH**

Estos ya son tutoriales mas potentes. **SSH**, o **S**ecure **Sh**ell, es un proveedor de un canal seguro para la comunicacion con otras computadoras. Se puede usar para ingresar y conectarse de forma segura a otros servidores. 

Yo creo que en un futuro vamos a tener que verlo con mayor profundidad, porque ya es un tema bastante complejo. 

Lo que hace este tutorial es enseñarte a como setear una instacia EC2. Para esto hay unos cuantos pasos a seguir, como tener una cuenta en Amazon Web Services, crearse un IAM user, crear una clave, un VPC, un Security Group y otras cosas. 

No vamos a ver como hacerlo ahora, ya que ni siquiera sabemos que es un servidor ni para que sirve todo esto. Lo vamos a dejar para un futuro.

**Cut, Sed, Awk, and Xargs**

El comando **cut** es util para hacer splitting sobre strings. Asi por ejemplo, podriamos agarrar un texto y separar o filtrar las partes que queremos solamente. 

Estos son varios ejemplos del uso de cut en el archivo languages.txt:

Java,James

Ruby,Matz

Lisp,John

Bash,Brian

Self,David

lenguages.txt

Podriamos por ejemplo, decirle que corte de cada linea del caracter 1 al 4. El flag -c le dice que lo que viene despues referencia caracteres y no bytes.

- cut -c 1-4 languages.txt

Java

Ruby

Lisp

Bash

Self

Podriamos separar por la coma, y tomar lo que esta a la derecha. En donde el flag -d es para mostrar el delimitter (en este caso la ,) y -f le dice cual de las partes quiere agarrar (la 1 o 2).

- cut -d, -f2 languages.txt  {toma la segunda parte}
- cut -d, -f1 languages.txt  {toma la primera}

Notar que es mucho mas util cortar por la coma, que cortar por la cantidad de caracteres, ya que si tenemos diferentes cantidades, corta las palabras por la mitad.

Y tambien podemos usar piping con el comando cut, como por ejemplo:

- cut -d, -f2 languages.txt | sort | head -n 2

Tambien otro de los comandos que vamos a ver es el comando **sed**. El comando sed, o **Stream EDitor**, es un comando muy complejo que tiene muchas utilizaciones. No vamos a ver todas, porque es bastante largo, pero se puede seguir aprendoendo con el tiempo.

El comando sed es usualmente usado para encontrar texto y reemplazarlo, y editar texto en un archivo. Tambien para imprimir ciertas partes de un archivo.

Por ejemplo, podriamos reemplazar cada coma en el archivo que ya usamos arriba, langueges.txt, con un dos puntos:

sed 's/,/:/g' languages.txt

Separemos las partes del comando. Tenemos el comando sed a la izquierda. Seguido de una s, que indica sustitucion, la , es el valor viejo, los : es el nuevo valor, g es para hacerlo de forma global, no solo en el primer match. 

Entonces, lo que hace este comando es sustituir todas las comas que encuentre por ( : ). El output deberia ser:

Java:James

Ruby:Matz

Lisp:John

Bash:Brian

Self:David

Pero el tema es que esto lo que hace es hacer un cambio superficial. El archivo original queda intacto. Para poder modificar al archivo original en el lugar, tenemos que usar el flag -i, cosa que termina en problemas porque estamos usando argumentos adicionales. Por eso es qe tambien tenemos que agregarle el flag -e, que supongo que significa, dejame poner ademas argumentos adicionales.

sed -ie 's/,/:/g' languages.txt 

O sea, lo que hace eso es hacer lo de arriba pero modificar al archivo original.

Ahora si haces devuelta cat languages.txt el archivo se modifico. 

Esto es recien una punta de lo que puede hacer este comando.

Otro comando util es el comando **awk**, que es una herramienta de procesado de texto parecida a sed. Por ejemplo, una de las utilizaciones de awk es para imprimir partes de un texto. 

awk '{print}' languages.txt.

Esto lo que va a hacer es simplemente imprimir el archivo de texto ese. Pero con awk podemos setear un delimitador, para decirle que queres imprimir el textp desde cierta parte. Para poner un delimitter usamos el flag -F. Ponele que ponemos a ( : ) como delimitter y le decimos que solo queremos la primer parte de lo que separa eso, con $1

awk -F ':' '{print $1}' languages.txt

Por ahi es medio choto porque tenes una sintaxis diferente para cada comando casi. Pero bueno. Aca la F significa el delimitador. Luego de eso va el delimitador, y luego pones el print para imprimir y junto con $ la parte que quedo.

Por ultimo esta el comando xargs. Hay veces que se quiere ejecutar un comando para una serie de archivos. En este caso esta bueno este comando. Estos son algunos ejemplos de su uso.

find . -name *.html | xargs grep "elie" - busca por el texto "elie" dentro de cada uno de los archivos con extension html. Es bastante potente. Notar que usa piping, y por un lado tiene el find cada html. Por el otro, la repeticion de los comandos para cada uno, con un grep que busca el texto dentro del archivo. O sea, sin el xargs, solo seria una busqueda individual en un archivo.

ls | xargs wc -l - cuenta el total de lineas para cada archivo en el directorio

find . -name "*" | xargs open - abre todo en el directorio actual.

find . -name "*.css" | xargs open - abre todos los archivos css.

find . -name "*.html | xargs rm - elimina todo archivo html.

ls | xargs -t -I {} mv {} {}.md - añade una extension a todos los archivos. 

Cada uno de estos comandos que vimos, los vimos muy por encima. Todos tienen varias utilizaciones mas, que en caso de querer usarlas alguna vez, vamos a tener que adentrarnos un poco mas y hacer otro tutorial.

**Shell Scripting and Vim**

El shell scripting exite por la necesidad de comandos dinamicos. Pensa que nosotros usamos comandos para realizar diferentes tipos de cosas dentro del shell, pero estos comandos no pueden ser reutilizados ni nada por el estilo. Si queres usar el mismo comando para otro archivo, tenes que reescribir todo devuelta. 

El shell scripting nos da una herramienta para dejar programados y hechos los comandos que no existan, creados por el usuario para realizar una accion que tal vez es muy comun para el, y quiere reutilizarla. 

Es como una forma de hacer modulos dentro del shell. Para hacer esto, vamos a usar un lenguaje llamado bash.

Por ejemplo, podemos hacer un script del shell de esta forma. Guardamos en un archivo first.sh el comando echo "Hello World".

Pero luego si lo ejecutamos asi ./first.sh, nos va a dar permiso denegado. Esto es porque no lo hicimos ejecutable. Lo que hacemos entonces es cambiar los permisos, para que sea ejecutable por todos: chmod 755 first.sh. Y ahora si lo podemos ejecutar como ./first.sh.

Hay una forma, por ejemplo, de hacer scripts dinamicos. Esto es usando un $1. Por ejemplo, podriamos hacer un archivo que se llame second.sh que tenga el contenido: 

echo Hello $1

Luego cambiamos sus permisos con chmod igual que antes. Ese $1 lo que nos avala es a poder decirle que es lo que sigue. Si ejecutamos ./second.sh normalmente, nos va a dar Hello. Pero si lo ejecutamos como ./second.sh World le va a meter la palabra atras e imprime Hello World.

Asi podemos hacer scripts mas complejos. Es mas, esto es un lenguaje entero asi que necesitamos estudiar Bash para poder entender bien como hacer scripts.

Vim es un editor de texto basado en la terminal. Puede ser muy intimidante, pero si se estudia te podes volver terriblemente eficiente en el desarrollo. Para abrir algo en el editor Vim tenes que poner vi NAME_OF_FILE. 

Hay una pagina con un tutorial muy grafico que se llama vim-adventures. Es para aprender vim. https://vim-adventures.com/