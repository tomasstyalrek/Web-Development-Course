## Git

La idea de esta nota es hacer una introduccion a Git, que es y sus comandos basicos. No tiene sentido verlo en profundidad porque se nos va a olvidar claramente. Es mejor ver lo junto y necesario y en caso de que necesitemos hacer algo en especial en su momento, lo googleamos y podemos dejar esto como anotaciones.

-----

Este capitulo introduce a Git, un sistema de control de versiones fundamental para todo desarrollador.

**Git** es un sistema de control de versiones, es gratis y open source, y esta diseñado para manejar de todo, desde pequeños projectos a projectos de gran escala, con rapidez y eficiencia. 

Es decir, git es simplemente un administrador de versiones de software, diseñado para que un desarrollador pueda trabajar en conjunto, y poder administrar su projecto, guardando todo en git. Asi se implementa una forma de organizacion muy eficiente.

Lo que hace git es tomar "snapshots" del software en cada version del mismo, e ir guardando todos en paralelo. Es como si usaras archivos como siempre, pero en vez de guardar sobre el archivo, cada guardado es un copia aparte. De forma que si tenes que volver atras por alguna razon, podes acerlo sin inconvenientes. 

Cuando se empieza a apredender sobre git, se ven muy seguido unas siglas que son **VCS**. Estas siglas son de la palabra Version Control System. Git es un VCS porque lo que hace es dejarte crear diferentes versiones del software que estas haceindo, y luego darte la posibilidad de navegar entre versiones anteriores y posteriores cuando lo desees. Git no es el unico VCS que existe.

Antes de poder empezar a utilizar git, hay que acegurarse de que esta instalado. Para saber que version de git tenemos instalada, podemos ejecutar el comando git --version. Si aparece un error, es porque no esta instalado en el sistema. 

En la pagina principal de git hay un libro gratuito que se llama **Pro Git**. Creo que debe ser un libro fundamental para leer en algun momento, porque el uso de git es muy habitual y saber usarlo a la perfeccion debe ser una herramienta muy util. El link es https://git-scm.com/book/en/v2

Algo excelente de git es que al instalarlo viene incluida una "git bash". Esto hace posible tener la shell de linux en windows.

Para empezar a usar Git tenemos que inicializar un repositorio en Git. Creemos el directorio learn_git y hacemos cd dentro de el.

Ahora dentro del directorio learn_git, tenemos que **inicializar** un nuevo repositorio. Para esto, vamos a ejecutar el comando:

- git init

Y deberia aparecer algo asi en el terminal: Initialized empty Git repository in /Users/YOUR_USERNAME/Desktop/learn_git/.git/. 

Ahora el tema es que, si vos pones ls en el directorio, no vas a ver nada, va a aparecer vacio. Esto es porque el directorio nuevo que se creo .git, es un directorio escondido. Esto es por el punto antes del archivo.

NOTA: Aprender que significa el . y el .. antes de un directorio o archivo.

Pero aunque este directorio este escondido, siempre te tenes que asegurar que fue creado ya que sin el ninigun comando de git funcionaria. Por otro lado, dificilmente tengas que utilizarlo alguna vez.

En caso de que te confundas, y ponele que inicializas un repositorio de git en un directorio que no querias, como ponele el Desktop o el home (cosa que no queres que pase), podes eliminar el repositorio con el comando remove:

- rm -rf .git.

En donde, en el comando de arriba, la flag **-f** es para un remove a la fuerza. Y la flag **-r** es para un remove recursivo, es decir, para que borre directorios y archivos dentro de los directorios y asi siga.

Ahora, para hacer un **commit** de tu codigo, es decir, tomar una foto o snapshot del codigo, primero el codigo debe pasar por un area que se llama **staging area**. Esta area existe porque git no quiere que vos mandes snapshots asi nomas y porque si, entonces lo que hace es dejarlo en esta area antes de que sea *committed*. Para ver en que estado o en que area esta el codigo, se puede usar el comando **git status** .

Git esta compuesto como por capas, que despues vamos a ver cuales son cada una. Esto hace posible que vos puedas ir moviendo tus archivos desde el directorio de trabajo capa por capa, por las diferentes instancias de tu version.

En caso de que no hayas añadido, modificado o eliminado nada, y quieras hacer un commit del directorio, te va a avisar que no hay nada para hacerle el snapshop y tu directorio no tiene ninguna modificacion. O sea, git se da cuenta y no hace commits al pedo.

Por ejemplo, hagamos un directorio nuevo, o el mismo de antes, el learn_git. Este directorio ya estaba inicializado, por lo tanto ya tiene la carpeta .git dentro. 

Pero como no se hizo nada ni se añadio nada nuevo al directorio, si te fijas el status con git status, te va a decir "*on brach master*" (en este caso, porque estas en el area master), "*no commits yet*" y "*nothing to commit*". 

Creemos un archivo nuevo, por ejemplo, example.txt. Ahora cuando pongamos devuelta git status te va a decir que este nuevo archivo todavia no esta *rastreado* o *tracked.* Lo que tenes que hacer en git al añadir un nuevo archivo es trackearlo, de manera que lo pueda utilizar. 

Lo que aparece cuando creas el archivo example.txt es: 

$ git status

On branch master

No commits yet

Untracked files:

 (use "git add <file>..." to include in what will be committed)

​    example.txt

nothing added to commit but untracked files present (use "git add" to track)

Te muestra lo mismo de antes. En que branch estas, si hay commits hechos y en este caso te muestra los **untracked files**. Como se puede ver y te señala Git, te dice que para añadirlos ejecutes ese comando, esto va a hacer que ese archivo quede listo para hacerle el commit.

Entonces vamos a trackearlo. Para hacerlo, ejecutamos el comando:

- **git add example.txt.**

Otra cosa que podes hacer es, en vez de especificar el archivo en especifico que queres hacerle el commit, podemos hacerselo a todos los archivos que estan en el directorio con:

- git add . 

El punto ( . ) como siempre actua para indicar "todo". Ademas de esta hay varias formas para añadir archivos. 

Ahora cuando estes listo, y luego de haber añadido tu archivo al staging area, podes hacer el commit. Esto se hace con el comando git commit y la flag -m . Ademas el commit siempre te pide un comentario obligatorio. Es como para mantener un indicador de lo que hiciste al hacerle el commit al archivo:

- **git commit -m "initial commit"**

Notar que el commit no te pide que especifiques el archivo con lo que lo queres hacer, ya que va a hacerselo a todo archivo que este en el staging area, que vos hayas añadido.

Para ver el historial de commits que hiciste, podes ejecutar el comando **git log**. Esto te va a mostrar todos los commits que hiciste con sus mensajes. Para salir de esa pantalla, presionas **q**. Ademas podes hacer que el log ese se vea un poco mejor poniendo la flag git log --oneline, esto muestra los commits en una linea sola. 

Entonces, haciendo un resumen de lo que vimos hasta ahora. 

Git es un sistema de control de versiones. Con el podes mantener el control y administrar cada una de las partes del desarrollo del software. Para inicializar un directorio como un repositorio de Git, tenes que usar el comando git init. Para ver el estado de los archivos y otros directorios en ese directorio, tenes que usar git status. Para poder agregar un archivo a la staging area, usas git add. Para poder hacer un commit de un archivo, tenes que usar git commit. Para ver un historial de todos los commits hasta el momento, usas git log.

Ahora lo que vamos a ver es la configuracion de git. 

Una de las cosas que no se ven a la hora de usar el comando *git log* y ver el historial, es el autor y el email del archivo. Esto va a ser de mucha ayuda en el futuro, porque al usar github uno quiere estar seguro que el mail con el que esta asociado el commit es el mismo que el de tu cuenta en github. 

Para poder cambiar esto, tenemos que hacer uso del comando:

git config --global user.name "YOUR NAME"

git config --global user.email "YOUR EMAIL"

En realidad lo que hace esto es setear el nombre de usuario y el email del propietario de la sesion de git. Esto esta bueno hacer todo el tiempo, para asegurarse de que seas vos el usuario y todo salga bien.

Otra cosa que se puede cambiar, por ejemplo, es lo de apretar q cada ves que queres salir del git log. Se hace con el comando:

git config --global --replace-all core.pager cat

Todas estas configuraciones que uno hace viven en un archivo que se llama .gitconfig que por lo general esta el directorio home. Si ejecutas cat ~/.gitconfig se ven todas las configuraciones actuales que tiene git. 

Resulta que yo ya tengo de antes la configuracion de que mi usuario preterminado es tomas, y mi mail es [tomasstylarek@gmail.com.](mailto:tomasstylarek@gmail.com.)

Esto es porque ya se quedo guardado el archivo anterior donde estaba guardado git en el home. 

Otra cosa bastante util es hacer lo que se llama **alias**. Un alias es un atajo hacia un comando que uses mucho. Son convenientes porque vas a estar tecleando mucho en el futuro los comandos mas comunes, es decir, git init, git add, git status, etc. 

Para crear un **alias temporal**, haces:

git config alias.KEYBOARD_SHORTCUT COMMAND

Por ejemplo, si ponemos mucho git status, lo podriamos setear como git s de esta forma:

git config alias.s status

Notar que no es necesario añadir el git.

Si quisieras que se vuelva un comando global, es decir, que lo reconsca en cualquier sesion, tenes que añadir el comando --global. Este es el mismo que se usa por ejemplo, para setear el usuario. Por esto es que se setea una vez sola. 

Por ejemplo, si queres que git init sea git i para siempre, podes poner git config --global alias.i init.