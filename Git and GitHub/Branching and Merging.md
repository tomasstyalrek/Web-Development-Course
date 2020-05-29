## Branching and Merging

#### Checkout and Reset

En este capitulo vamos a aprender algunos comandos para revertir acciones en git. Hay casos en que uno hace adds o commits, y accidentalmente mandas algo que no querias mandar. Esto sirve para esos casos.

##### checkout

En caso de querer eliminar archivos que estan en el working directory, antes de que se manden al area de staging, podemos usar el comando:

- `git checkout NAME_OF_FILE`

Hay que tener cuidado, porque una vez ejecutado el comando, no hay vuelta atras.

Osea, en realidad lo que hace esto es darte la posibilidad de deshacer cambios a un archivo que no este en la staging area ni hecho el commit.

O sea, supongamos que creamos un directorio y ejecutamos git init. Luego creamos un archivo de texto, first-txt, que esta vacio. Le hacemos git add y git commit. Ahora supongamos que le ponemos dentro algo. Por lo tanto, si git nota que hay un cambio en el archivo, ahora si ejecutas git status te va a tirara que hay un archivo que esta listo para trackear.

Si ahora decidis que no queres guardar los cambios del archivo, no es necesario eliminarlo. Asi perderias el archivo entero y solo quedaria el que esta en el commit. Para esto lo que haces es usar `git checkout -- first.txt`. Y ahora el archivo va a volver a estar vacio, es decir, al estado que tiene el ultimo commit en el historial del archivo que ve git.



##### clean

Si estas lidiando con un archivo que no esta untracked o unmerged, y todavia no se le hizo el commit ni nada, no se puede usar checkout. Tenes que usar el comando `git clean -df`.



##### git rm --cached

Que pasa si accidentalmente mandamos un archivo al staging area, y lo queremos devuelta en el working directory? Para esto podemos usar el comando `git rm --cached NAME_FILE`. 

Si lo que queres es eliminar todo del working directory y el staging area, pones `git reset --hard HEAD`. Esto no tiene vuelta atras.



##### Undoing commits with reset

En caso de haberle hecho un commit a uno o mas archivos que no queriamos hacerselo, podems usar el comando `git reset`. Lo que hace es devolver todo al working directory.

Hay tres flags que se le pueden pasar a esto:

- `git reset --soft COMMIT_SHA` - mueve los archivos con commit al staging area.
- `git reset --mixed COMMIT_SHA` - por default. Mueve los committed files al working directory.
- `git reset --hard COMMIT_SHA` - saca el commit entero.

Ese SHA que esta ahi, es el identificador del commit. Es la unica forma de poder traer devuelta ese archivo, poniendo su id.

Su id lo podes saber poniendo git log --oneline. Esto te va a mostrar los mensajes de los commits y sus id. 

Cuando copias un id y lo pones en el git reset, te toma los commits que vienen despues de ese.

##### Sumario: 

Si tenemos uno o mas archivos en el working directory, con git clean .df los eliminamos a todos, como si pusieras directamente un rm file. 

Si tenemos un archivo que lo añadimos al staging area con git add, podemos devolverlo al working directory con git rm --cached. 

Es mas, git mismo nos da una sugerencia al añadir el archivo a la staging area. Si ponemos git status, nos dice que hay un archivo por hacerle commit, y que para hacerle unstage tenemos que usar git rm --cached.

Si queres borrar todo del working y del staging area, pones git reset --hard.

Para chequear el historial de commits en una linea, pones git log --oneline. Ahi te muestra los id de cada uno.

Estando los archivos ya con el commit hecho, poner git reset y te los tira al working.



#### Branching

Por ahora todos los ejemplos y explicaciones que se hicieros estaban diseñados para trabajar en una sola *branch*. Esto es porque estamos nosotros solos, y estamos haciendo pruebas. Pero en el caso de trabajar con un equipo, seria bueno tener una forma de probar cosas nuevas, sin necesidad de romper nada del codigo ni molestar a nadie.

Por lo general cuando uno trabaja con software, no posee solo una rama. Uno tiene varias, ya que al ser un proyecto mas grande uno necesita mayor organizacion. Por lo general hay branches para bux fixes, new features, deployment, etc. Por eso es necesario entender como se crean nuevas branches, se borran y se unen.

Antes de crear una nueva rama, primero pongamos en el terminal *git branch*. Esto nos muestra todas nuestras branches actuales. Nos deberia mostrar una sola, que es la *master*. Esta es la rama principal para todo repositorio local.

Para crear una nueva *branch* usamos:

- `git checkout -b NAME_OF_BRANCH`.

Para movernos a esa branch creada, usamos:

- `git checkout NAME_OF_BRANCH`

Para eliminar una branch, primero nos aseguramos que no estemos en ella y ejecutamos: 

- `git branch -D NAME_OF_BRANCH`

Para ver todas las branches que tenemos, hasta las creadas de forma remota en GitHub, usamos `git branch -a`. Esa flag -a es para esto ultimo.

Cuando uno trabaja con varias ramas, la que esta parado tiene un *. Lo que permite tener varias ramas es el hecho de poder trabajar de forma independiente, y organizar mejor el proyecto.



#### Merging

Usualmente, uno si quiere probar algo nuevo en su codigo, o hacer algo en particular, lo que hace es abrir una nueva rama para poder trabajar ahi. Cuando ya terminamos de hacer esa modificacion, tenemos que poner nuestro codigo devuelta en la rama master. Tradicionalmente, la rama master se reserva para produccion de codigo y bug fixing inmediato. Para poder hacer esto de poner el codigo devuelta en la rama principal, tenemos que hacer un *merge*.

Supongamos que creamos un repositorio local. Por lo tanto, ya tenemos nuestra rama principal master. Creamos algunos archivos, los añadimos y les hacemos commit. Los dejamos ahi.

Luego agarramos y creamos otra branch, y dentro hacemos lo mismo, creamos archivos, los añadimos al staging area y commit.

Una cosa a notar es que ninguna branch se entera en ningun momento de la existencia de los archivos en la otra. Las dos son independientes.

Entonces, cuando estamos listos con la branch secundaria que creamos, nos vamos a la master. (Recorda que siempre las acciones como borrar o hacer merge no se hacen desde la branch que queres hacerselo). Entonces queremos unir todo lo que hicimos en la otra branch, en la master. Para esto usamos el comando:

- `git merge second_branch`

Entonces nos copia todo lo de la otra en la master. Muy simple. Luego si queremos borrar la second, usamos `git beanch -D second`. Lo hacemos desde master.

Ahora si ponemos git log, nos muestra el historial de los archivos y que ahora esta todo en master.





#### Visual Diff Tools

##### Seeing commits and changes

Una ves que uno hace un commit, uno puede ver el mensaje, el autor y alguna info adicional usando el comando *git log*. Ademas, cuando se pone esto se puede ver el SHA, que es el identificador del commit.

Cuando un proyecto va creciendo y se van haciendo commits, el git log va creciendo en su historial. Hay veces que uno quiere comparar dos codigos en dos diferentes tiempos del historial. Para esto se puede usar el comando *git diff*.

Para hacer esto, uno puede usar el SHA del codigo que quiere comparar. Usas git diff, y comparas el codigo actual con el del SHA que pones.

Entre los usos mas comunes estan:

- `git diff` - Ver cambios en el working tree todavia no staged para el proximo commit.
- `git diff --cached` - ver cambios entre la staging area y tu ultimo commit.
- `git diff ANOTHER_BRANCH` - compara con el ultimo codigo en otra branch.

Con el uso de esta herramienta se le puede ir agarrando la mano. Es muy util, porque te deja ver lo ultimo que agregaste al archivo. Te lo imprime en el terminal. Para salir tenes que apretar q.



#### Merging and Merge Conflicts

Cuando queremos unir el contenido de una branch con otra, usamos el comando git merge. Dependiendo en la historia de nuestros commits, hay dos formas en las que funciona este merge. Una es fast forward y la otra es recursive. 

La que paso en los anteriores casos es la fast forward. Esto seria porque git puede determinar bien de que forma ocurrieron los commits. 

Pero cuando diferentes commits pasan en distintos tiempos en dos branches, git usa una forma recursiva, que no nos interesa mucho saber como funciona. 

El tema importante es que tambien pueden haber conflictos en un merge. Esto ocurre cuando git no puede procesar bien lo que hiciste. Suele pasar por error nuestro. Esto se llama *merge conflict*.

Por ejemplo, vamos a generar uno:

```bash
mkdir merge_conflicts
cd merge_conflicts
git init
echo first > first.txt
git add .
git commit -m "first commit"

git checkout -b new_branch
echo second > second.txt
git add .
git commit -m "adding second.txt"

git checkout master
echo something_else > second.txt
git add .
git commit -m "adding second.txt on the master branch"

git merge new_branch
```

El output es:

```bash
Auto-merging second.txt
CONFLICT (add/add): Merge conflict in second.txt
Recorded preimage for 'second.txt'
Automatic merge failed; fix conflicts and then commit the result.
```

Osea, lo que esta pasando es esto. Crea un directorio, lo inicializa, todo normal. En la rama master, crea un archivo y le hace commit. Luego crea otra rama, dentro de ella un archivo y tambien le hace commit. 

El tema es que despues vuelve a la master, y quiere hacer una modificacion al archivo second.txt, pero como no existe ahi lo crea, todo bien. Hace el commit y todo. Pero cuando quiere hacer el merge, tira conflicto.

Lo que esta pasando es que git no sabe que archivo second usar. Porque hay uno en la master, y otro en la otra.

Por lo tanto, para que este conflicto se solucione, lo tenemos que hacer manualmente.

