## Advanced Git Commands

#### Stashing

Hay casos en los que sucede que uno esta trabajando con ciertos archivos y no quiere añadirlos ni hacerles commit, pero tampoco los quiere eliminar. Suponete el caso en que estas trabajando en una actualizacion de un codigo, y te llega un nuevo codigo al upstream. En ese caso, vas a tener que hacer un pull para ver si el codigo que estas haciendo tiene algo que ver con ese, o si el tuyo sigue funcionando.

EL tema es que cuando haces un *pull* o un *merge* en tu working directory, Git no te va a dejar hacerlo si tu directorio no esta limpio. Con limpio se hace referencia a que no haya quedado nada suelto. Para poder hacer un pull o un merge de otro codigo, todo lo que tenes en el working tiene que estar con commit.

Entonces, que haces si tu directorio no esta limpio, pero tampoco estas listo para hacer el commit porque todavia tener que verificar cosas? Bueno, para esto sirve el **stashing**. Se puede pensar al stashing como una forma temporal de recordar cambios sin tener que hacer un commit oficial.

Estos son algunos comandos:

- `git stash` - stash los commits (lo mismo que *git stash save*).
- `git stash list` - muestra la lista de los stashed changes.
- `git stash apply` - mueve el ultimo stash devuelta al working directory, pero lo deja en la lista.
- `git stash pop` - lo mueve al working y lo elimina.
- `git stash show` - muestra el ultimo stash.
- `git stash show stash@{number}` - mustra un stash especifico.

Se puede aprender mas acerca del stashing en el momento en que se necesite. Solo esta bueno recordar que se utiliza para esos casos en que no estas seguro de hacer el commit, pero necesitas tu working directory limpio.



#### Rebasing

##### Merging vs Rebasing

Lo primero que tenemos que entender sobre *git rebase* es que soluciona el mismo problema que *git merge*, pero ambos funcionan de maneras muy diferentes. 

Consideremos el caso en que uno empieza a trabajar en lo suyo en una rama dedicada, y se agrega un nuevo commit en la master branch. Supongamos que este nuevo commit que se hizo es relevante a tu trabajo, por lo tanto queres que lo que esta en master este en tu branch feature. Por eso tenes dos opciones, usar git merge o rebase.

##### The merge option

La primer opcion es agarrar y hacer un merging con la master branch en la feature branch. Esto se haria de manera simple con:

```
git checkout feature
git merge master
```

Esto lo que hace es un "merge commit" que une el historial de ambas branches en la feature.

Esta opcion tiene ventajas, como por ejemplo que es una operacion no destructiva, a diferencia de el rebasing. Es decir, no le quita a una rama para ponersela a la otra, si no que copia el contenido. Pero por otro lado, ahora la branch feature va a tener modificado el historial cada vez que haga un merge commit. Va a aparecer un merge commit extraño cada vez que haya nuevos archivos en la master. Esto puede ser dificil de entender para otros desarrolladores, porque el git log se ensucia todo. A esto es lo que le llama el libro *pollute*, es decir, contamina tu historial con todos merges.

##### The rebase option

Como alternativa  a git merge podemos usar el comando *git rebase*, para, como dice el comando, rebasar la feature branch en la master. 

```
git checkout feature
git rebase master
```

O sea, lo que hace esto es mover la branch entera a la punta de la master branch, e incorpora todos los nuevos commits que estaban en la otra a la master. Pero la diferencia con *merge* es que esta reescribe todos los commits en la master, como si siempre ubieran estado ahi.

El resultado final es algo asi:

![Rebasing the feature branch onto master](https://wac-cdn.atlassian.com/dam/jcr:5b153a22-38be-40d0-aec8-5f2fffc771e5/03.svg?cdnVersion=1044)

Los beneficios de esto es que te deja un historial mucho mas prolijo, sin estar contaminado por los merge commits, ya que termina siendo como una linea recta, todo de corrido. Lo otro es que se vuelve mucho mas sencillo de visualizar en el sentido de su linealidad en el historial. 

Pero hay algunas desventajas. Primero, es un proceso que destruye una rama y la pega, hace un cut paste. Despues vamos a ver algunas reglas generales que se deben seguir para no mandarse cagadas, ya que volver a escribir el historial de un proyecto no esta muy bueno. Y lo otro, un poco menos importante, es el concepto que se pierde, que es el merge commit, que tal vez da el contexto de lo que paso. Es decir, el merge commit te dice en que momento vinieros las actualizaciones del upstream. Igualmente, si decidiste usar rebasing es porque no lo querias.

Igual esta claro que como un principiante en Git yo no lo usaria, pero porque siento que los proyectos tal vez sean un poco mas cortos. Pero cuando las cosas se vuelvan mas largas, yo creo que ahi si entran en juego estas cuestiones.

##### Interactive Rebasing

Hacer rebasing interactivo te permite alterar los commits a medida que son movidos a la nueva branch. Te permite tener un control total sobre el historial de commits, y de esta forma poder limpiar un poco las cosas antes de hacer un merging de una feature branch en la master.

Para poder hacerlo, hay que pasar la flag *i* al comando *git rebase*:

```
git checkout feature
git rebase -i master
```

Esto lo que hace es abrir un editor de texto en donde se enlisatan los commit, y uno modificando los comandos puede hacer lo que quiera.

```
pick 33d5b7a Message for commit #1
pick 9480b3d Message for commit #2
pick 5c67e61 Message for commit #3
```

Por ejemplo, suponete que el segundo commit fixea un bug muy chico del primero, entonces agarras y en vez de *pick* le mandas *fixup* entonces los une al primero y al segundo.

Cuando terminas de hacer todo, guardas el archivo y Git hace el rebasing como le indicaste.

Esto es algo muy util, porque modificar los commits de esa manera hace que tu historial se vea mucho mejor y mas entendible. A veces se vuelve necesario esto para tener un buen workflow.

##### The golder rule of rebasing

Hay una regla general que hay que tener en cuenta cuando se usa *git rebase*, ya que es un comando un poco peligroso en este sentido. Esa regla es, no se usa en ramas publicas. Con esto me refiero a que no se puede usar con branches que usen todos los desarrolladores. 

Si puede ir el rebase desde una branch secundaria personal, hacia la publica, pero no al revez.

Por ejemplo, pensa que pasaria si haces un rebasing de la master branch en tu feature branch. 

![Rebasing the master branch](https://wac-cdn.atlassian.com/dam/jcr:1d22f018-b2c7-4096-9db1-c54940cf4f4e/05.svg?cdnVersion=1044)

Lo que va a pasar aca es que se van a pegar todos los commits de la master en la tuya. Es decir, la master se va a pegar en la punta de la feature, pero aun asi la master original va a seguir existiendo. Vos vas a estar trabajando en tu master propia, y los demas desarrolladores en otra distinta. Y a partir de ahi, el historial que hagas en esa master va a ser distinto de la otra.

Por eso la unica solucion que te va a quedar es hacer un merging entre dos master, resultando en dos conjuntos de commits iguales y un merge commit. Termina siendo una situacion que se puede evitar.

Por eso, antes de ejecutar un git rebase, te tenes que hacer la pregunta, alguien mas esta mirando esta branch? Si es asi, pensa en otra forma no destructiva de hacer tus cambios (por ejemplo, un git revert).

Para mas informacion, seguir leyendo en:

- https://www.atlassian.com/git/tutorials/merging-vs-rebasing



##### Pre-reading

Entonces, vamos a respondernos algunas preguntas:

- Que significa que un merge contamina el commit history?
  - Contaminar hace referencia a los merge commits. Cada vez que uno hace un merge desde una beanch a otra, queda el registro en el historial. Esto es una desventaja que puede tener el comando merge cuando un proyecto se hace muy grande y dificil de visualizar en el historial.
- Como resuelve el rebasing el problema de este commit "extra"?
  - Ese commit extra seria el merge commit, y lo soluciona cuando hace el rebasing. Lo que hace es, a mi entendimiento y a grandes rasgos, reescribir esos commits como si fueran nuevos, y los mete en la otra branch. Terminan siendo todos commits que parecen originales de la branch a la que se los conectaste.
- Cual es la "Golden Rule"? Porque saberla es importante?
  - La golder rule te dice que no le hagas rebasing a las branches publicas. Es decir, a aquellas en las que trabaja el equipo entero como la master. Esto resulta en cagadas, y peor si nunca te das cuenta. Porque jamas se te va a actualizar esa rama, y al mergiar vas a duplicar todo.



##### Ejemplos de rebasing interactivo

Recordemos que hacer rebasing interactivo puede ser muy util para dejar prolijas las cosas antes de tirarla para una rama publica de produccion. 

Ponele que estas trabajando en tu propia rama, y haces commits, lo normal. Luego, antes de hacer el rebasing para unir todo tu progreso a la rama principal, lo mejor es toquetear un poco para entregar algo un poco mas legible.

Entonces, hagamos un ejemplo:

```bash
mkdir learn_rebase
cd learn_rebase
git init

echo first > first.txt
git add .
git commit -m "adding first"

echo second > second.txt
git add .
git commit -m "adding second"

echo third > third.txt
git add .
git commit -m "adding third"

echo fourth > fourth.txt
git add .
git commit -m "adding fourth"

echo fifth > fifth.txt
git add .
git commit -m "adding fifth"

echo sixth > sixth.txt
git add .
git commit -m "adding sixth"

git log --oneline | cat | wc -l # shows us we have 6 commits

git rebase -i HEAD~5 # let's rebase from the earliest commit possible
```

Crea un directorio, lo inicializa como repositorio, y crea seis archivos. Luego hace un log para ver los commits, y hace un rebase a la rama principal.

Tendriamos que ver algo asi:

```bash
pick 6f69a93 adding second
pick e2bb264 adding third
pick 9d46da5 adding fourth
pick dcce954 adding fifth
pick 5c040e4 adding sixth

# Rebase 77d05ef..5c040e4 onto 77d05ef (5 command(s))
#
# Commands:
# p, pick = use commit
# r, reword = use commit, but edit the commit message
# e, edit = use commit, but stop for amending
# s, squash = use commit, but meld into previous commit
# f, fixup = like "squash", but discard this commit's log message
# x, exec = run command (the rest of the line) using shell
# d, drop = remove commit
#
# These lines can be re-ordered; they are executed from top to bottom.
#
# If you remove a line here THAT COMMIT WILL BE LOST.
#
# However, if you remove everything, the rebase will be aborted.
#
# Note that empty commits are commented out
```

Ahi se enlistan algunas cosas muy buenas que podemos hacer, como editar los mensajes, juntar con otros commits, y mas. 

Por ejemplo, podriamos usar squash, para meter justos con el previo:

```bash
pick 6f69a93 adding second
squash e2bb264 adding third
squash 9d46da5 adding fourth
squash dcce954 adding fifth
squash 5c040e4 adding sixth

# Rebase 77d05ef..5c040e4 onto 77d05ef (5 command(s))
#
# Commands:
# p, pick = use commit
# r, reword = use commit, but edit the commit message
# e, edit = use commit, but stop for amending
# s, squash = use commit, but meld into previous commit
# f, fixup = like "squash", but discard this commit's log message
# x, exec = run command (the rest of the line) using shell
# d, drop = remove commit
#
# These lines can be re-ordered; they are executed from top to bottom.
#
# If you remove a line here THAT COMMIT WILL BE LOST.
#
# However, if you remove everything, the rebase will be aborted.
#
# Note that empty commits are commented out
```

Es muy util esto de juntar commits, porque hay veces que lo que cambia es insignificante. Entonces podes juntar todas las cosas que sean parecidas.



Mucho mas por aprender sobre rebasing aca: 

- https://git-scm.com/docs/git-rebase



#### Reverting

El comando *git revert* deshace o revierte un commit, a diferencia de *git reset* que elimina el commit de la existencia, hasta del historial. Lo que hace *git revert* es, sacarlo al commit, pero en realidad hace otro y lo mete en la history indicando los cambios. 

Por lo tanto, usar *git reset* cuando estas colabrando con otros desarrolladores es **muy peligroso**, porque estas alterando la historia de los commits, y hace que sea mas dificil mantener una concistencia en el historial de commits. Por lo tanto, usar *git revert* puede ser una mejor idea al trabajar en conjunto, porque asi todos se quedan consientes de lo que borraste.

Pensa en esto. Estas trabajando de forma normal, y haces varios commits. Luego, te das cuenta que algo no te gusto sobre uno anterior, entonces queres revertir los commits para poder cambiarlo. 

Entonces ahi pensas, uso git reset. Pero esto lo que ca a hacer es eliminar todos los commits que hiciste despues del que te equivocaste. Entonces ahi es cuando aparece git revert.

Por ejemplo:

```bash
mkdir learn_revert # Create a folder called `learn_revert`
cd learn_revert # `cd` into the folder `learn_revert`
git init # Initialize a git repository

touch first.txt # Create a file called `first.txt`
echo Start >> first.txt # Add the text "Start" to `first.txt`

git add . # Add the `first.txt` file
git commit -m "adding first" # Commit with the message "Adding first.txt"

echo WRONG > wrong.txt # Add the text "WRONG" to `wrong.txt`
git add . # Add the `wrong.txt` file
git commit -m "adding WRONG to wrong.txt" # Commit with the message "Adding WRONG to wrong.txt"

echo More >> first.txt # Add the text "More" to `first.txt`
git add . # Add the `first.txt` file
git commit -m "adding More to first.txt" # Commit with the message "Adding More to first.txt"

echo Even More >> first.txt # Add the text "Even More" to `first.txt`
git add . # Add the `first.txt` file
git commit -m "adding Even More to First.txt" # Commit with the message "Adding More to first.txt"

# OH NO! We want to undo the commit with the text "WRONG" - let's revert! Since this commit was 2 from where we are not we can use git revert HEAD~2 (or we can use git log and find the SHA of that commit)

git revert HEAD~2 # this will put us in a text editor where we can modify the commit message. If you are in vim you can press Shift + Z + Z to save and close.

ls # wrong.txt is not there any more!
git log --oneline # note that the commit history hasn't been altered, we've just added a new commit reflecting the removal of the `wrong.txt`
```

Este es el ejemplo en donde quiere revertir algo que hizo hace 2 commits atras. Entonces usa git revert HEAD~2.

Lo que hace eso es eliminar ese commit, y te abre un editor en donde podes cambiar el mensaje que usaste para hacerlo. Ahi se podria decir que lo eliminaste porque no era necesario. Pero auque sea queda el informe de que lo hiciste.

Recorda que **HEAD** hace referencia a la current branch. Cuando se pone, es porque se quiere generalizar en cuanto a la branch en que estes parado.

Mas info para revert:

- https://git-scm.com/docs/git-revert



##### Por ultimo

No te quedes solo con esto. Ante cualquier duda consulta en google antes de hacer algo de lo que no estes seguro.

Para mi, es imposible entender en un principio las cosas al 100. Por eso hay que conformarse con entender mas o menos como funcionan las cosas, e ir perfeccionandolas con el tiempo de experiencia. 

La idea de esto fue tener un pantallazo de lo que es Git, y como usarlo mas o menos sin dudar. Pero obviamente la documentacion de Git debe ser gigante, y es muy dificil entender todo. 

Cualquier cosa que se te cruze por la cabeza en el momento de hacer algo nuevo en git, hay que preguntarle a google.

