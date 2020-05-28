## GitHub

Sobre GitHub y al igual que Git, es buena idea leerse el tutorial desde la pagina, porque probablemente hayan muchas cosas que no vamos a ver aca que son importantes.

#### GitHub Introduction

GitHub es un repositorio de almacenamiento remoto de Git que funciona en la web. Es una herramienta que permite la colaboracion entre un equipo de desarrolladores en un mismo proyecto, y deja que todo el progreso se guarde en el almacenamiento remoto de GitHub. 

Mientras que Git es un sistema de control de versiones,  GitHub es una plataforma online de hosting y para compartir codigo, archivos de texto y otros arichivos mas complejos.

GitHub no solo que es un servidor remoto, y es una muy buena herramienta para utilizar como almacenamiento, en caso de que nuestra computadora local falle. Si no que tambien es una excelente forma de poder trabajar en conjunto en un mismo proyecto de forma puclica o privada. Varios proyectos de reconocimiento mundial estan alojados en GitHub, ya que es el almacenamiento de repositorios online mas conocido y usado a dia de hoy. 

Vamos a aprender como hacer para mover archivos desde nuestro repositorio local al remoto en GitHub con el comando *push*, y tambien a recuperarlo desde el repositorio remoto a nuestra maquina usando el comando *pull*. Tambien otros conceptos especificos de GitHub como *forking* y *pull requests*.

Algunos de los proyectos mas conocidos incluyen a Angular, React, Ruby on Rails, Twitter Bootstrap, NodeJs, JQuery, Homebrew y una infinidad mas.

##### Getting started

Si no tenemos una cuenta en GitHub, hay que crearla y asegurarse de que sea la misma con la que se configuro Git, para ahorrarse problemas.



#### Working with Remotes

##### Creating a remote repository

Un repositorio contiene todos los archivos de un proyecto, incluido la revision del historial.

Para crear un nuevo repositorio en GitHub, hay que poner en crear repositorio o ir al path */new*. 

Te va a pedir un nombre de repositorio. Nosotros le vamos a poner *first_repo*

Hay algunas opciones aca. Una de ellas es la descripcion del repositorio. La otra es la opcion para elegir si queres que sea un repositorio publico o privado. Y luego un casillero indicando si queres inicializar el repositorio con un archivo README. Nosotros nos vamos a saltear todos.

Una vez que ponemos en crear repositorio, GitHub nos va a dar algunas instrucciones.

Hay varias formas de mover un repositorio desde nuestro local a el remoto. Aca en las instrucciones GitHub te varias. Te da la opcion de crear un nuevo repositorio en la command line y luego subirlo, o solo hacerle un pushing, en caso de ya tenerlo hecho.

Nosotros no tenemos nada, por lo tanto vamos a seguir las primeras instrucciones:

```bash
echo "# first_repo" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/tomasstyalrek/first_repo.git
git push -u origin master
```

Veamos cada uno de estos comandos por separado:

- `echo "# first_repo" >> README.md` - lo que hace es mandar algo a un archivo markdown que creamos. Es algo muy simple para el ejemplo. Aca escribimos dentro " # first_repo", que vendria a ser un first repo en h1.

- `git init` - como ya sabemos, esto lo que hace es inicializar un repositorio de git dentro del directorio en donde estemos.

- `git add README.md` - añadimos o trackeamos el file para poder hacerle el commit.

- `git commit-m "first commit"`  - le hacemos el commit.

- `git remote add origin https://github.com/tomasstylarek/first_repo.git` - lo que hace esto es darle a saber a Git que nuestro repositorio remoto tiene ese URL, y lo que haces con este comando es decirle que setee a "origin" como un alias para tu repositorio. Uno tranquilamente podria hacer `git push https://github.com/tomasstylarek/first_repo.git master`, pero es muy largo tener que copiar siempre el URL. Entonces, mas facilmente, se elige un alias y listo. Asi se deja todo listo para enviar desde tu rama *master* al repositorio local

  Por lo tanto, volviendo atras, *git remote add* es la forma de contarle a nuestro repositorio local sobre nuestro repositorio remoto, y dejarlo seteado con un nickname para futuros envios o recuperaciones de datos. El alias *origin* se usa por defecto o convension.

  Para ver todos los repositorios remotos, usamos *git remote -v*. Y si necesitamos eliminar un repositorio remoto, usamos *git remote rm NAME_OR_REMOTE*. 

- `git push -u origin master` - ahora si mandamos nuestros archivos que les hicimos commit, a nuestro repositorio remoto, usando nuestro alias del repositorio. La flag *-u* nos permite poder usar solo *git push* en vez de tener que poner todo devuelta. En caso de que tengamos que mandar muchas cosas al repositorio.

Hay algo que aparece que es *origin/master*. Esta es nuestra master branch en nuestro repositorio remoto. Mientras que origin es nuestro repositorio remoto y master el local.

Ahora, el tema con todo esto, es que cada vez que vamos a subir algo al repositorio local, nos va a pedir que le demos un mail y una contraseña. Esto se vuelve realmente algo cansador si tenemos que mandar muchas cosas.

Pero lo que se puede hacer es que GitHub reconozca a tu computadora como tuya y te deje hacer los push y pull con libertad. Para esto vamos a crear una **SSH key**.



#### SSH Keys

##### Using SSH over HTTPS

GitHub lo que hace es pedir autenticacion del usuario antes de hacer cualquier cambio en el repositorio remoto. Esto tiene sentido ya que si no fuera asi, cualquiera podria hacer lo que quiera. Pero al mismo tiempo se vuelve tedioso en poco tiempo, tener que copiar tantas veces lo mismo. 

Lo que se puede hacer es crear una key local de SSH, que es un protocolo que ya vimos, para envio de informacion encriptada, y pasarsela a GitHub. De esta manera nos ahorramos la autenticacion esa.

##### Creating a SSH Key

1. Open up Terminal.
2. Anywhere in Terminal paste the following `ssh-keygen -t rsa -b 4096 -C "PUT YOUR EMAIL HERE"` and replace "PUT YOUR EMAIL HERE" with the email you used to sign up with GitHub.
3. Once you are prompted with `Enter a file in which to save the key (/Users/you/.ssh/id_rsa): [Press enter]` press enter.
4. You will then be prompted to enter a passphrase. **Just press enter here**
5. You will then be prompted to enter a passphrase again. **Just press enter here as well**
6. Paste the following in terminal: `eval "$(ssh-agent -s)"`. If you do not see a `pid` number, start from the first step again.
7. Paste the following in terminal: `ssh-add ~/.ssh/id_rsa`. if you see an error message, start from the first step again.
8. Paste the following in terminal `pbcopy < ~/.ssh/id_rsa.pub`.
9. Head over to your GitHub account (make sure you sign in).
10. In the top right corner of any page, click your profile photo, then click Settings.
11. In the user settings sidebar, click SSH and GPG keys.
12. Click New SSH key or Add SSH key.
13. In the "Title" field, add a descriptive label for the new key. For example, if you're using a personal Mac, you might call this key "Personal MacBook Air".
14. Paste your key into the "Key" field. (you can just right click and click paste or use a keyboard shortcut. The previous command `pbcopy` did the copying for you).
15. Click Add SSH key.
16. If prompted, confirm your GitHub password.
17. Anywhere in Terminal, type `ssh -T git@github.com` and if you see "Successfully authenticated" (ignore the rest of the message) you are good to go! If you do not see that, start from the beginning again.



#### GitHub Workflow

Ya vimos como hacer un **push request**, es decir, pasar un repositorio local a nuestro repositorio remoto. Ahora vamos a seguir con el flujo de trabajo en GitHub.

##### Fork

Discutamos un concepto especifico de GitHub: forking 

Cuando trabajamos con otros en GitHub, a veces no va a ser posible hacer un push al repositorio cuando quieras. Imaginate que no cualquiera te dejaria hacerlo, porque seria un desastre capas, mas que nada en los repositorios de proyectos muy grandes. Entonces lo que tenemos que hacer es una copia del repositorio del otro, y asegurarnos que este bajo nuestro nombre de usuario, asi podemos hacerle un push de codigo a el.

Para practicar el forking, lo vamos a hacer con el repositorio que creo rithmschool para nosotros, que se llama *learn_forking*.

Lo que vamos a hacer es ir arriba a la derecha y clickear en **Fork**.

Hacer fork es simplemente un concepto de GitHub y no esta relacionado a Git. Lo unico que hace es permitirnos crear una copia del repositorio que querramos y guardarlo en nuestra cuenta, para poder hacer lo que queramos con el.

##### Clone

Una vez que le hicimos un fork al repositorio, ahora tenemos que agarrarolo y descargar el codigo en nuestro repositorio local para poder trabajar con el. Y ahora, en vez de hacer un directorio y hacer todo el proceso con *git init*, en cambio podemos usar el comando **git clone**, que acepta un link al repositorio remoto y descarga todo dentro del directorio (y setea todo por nosotros).

Lo que hacemos es ir a nuestro repositorio en GitHub que ya forkeamos, e ir al boton que dice "clone or download". Ahi nos dice si queremos clonar con HTTPS o SSH. Nosotros vamos a elegir SSH, ya que tenemos la key creada ahi, y de otra manera nos pediria credenciales. Entonces, copiamos el link que nos pasa GitHub.

Ahora solo quedaria ir al terminal, y directamente en el home pones:

- **git clone PASTE_URL_HERE**

En donde el PASTE_URL_HERE es el URL que te tiro GitHub. 

Lo que hace esto es crearnos una carpeta llamada de la misma forma que el repositorio. Segun donde estemos parados en el terminal la crea ahi. Y lo que hace es dejar todo listo, con git ya puesto y todo.

Ahora ya tenes el repositorio de forma local, y podes trabajar de forma normal como siempre. Haces add, commit y con *git push origin master* vas actualizando el repositorio remoto.

##### Pull Request

Suponete ahora que estas colaborando con alguien, una organizacion o cuenta de cualquier persona. Para hacerlo primero tuviste que haberle hecho un fork al repositorio remoto ese, y luego clonarlo en tu compu local. 

Ahora suponete que queres hacer un cambio en ese repositorio, queres unir lo que estas haciendo en el repositorio original. El tema es que no lo podes hacer asi nomas, porque no tenes los permisos para hacerlo ya que no sos el propietario de la cuenta. Lo que se puede hacer es solicitar un **pull request** y alguien que posee el permiso lo va a aceptar para que se una lo que hiciste con el original, o bien lo va a rechazar.

Para hacer esto, hay que clickear en el boton que dice "New pull request" y despues en "Create pull request". Despues de eso deberias poder ir a repositorio original y ver tu pull request o "PR". 

Notar que GitHub sabe que la copia que hiciste en tu cuenta del repositorio (el fork) le pertenece a otra cuenta. Por esto es que directamente toma al pull request como para modificar el original.

NOTA: Ahi lo que hice fue añadir un nuevo archivo, prueba.md, que lo cree y lo puse en la carpeta. De ahi le hice add y commit, y luego le mande git push para que lo tire al repositorio que forkeamos. Entonces ahi te aparece en el repositorio. En caso de querer mandarlo al orginal, pones en hacer un pull request.

##### Retrieving Code from GitHub + Setting Upstream

Ahora, que pasa si alguien mas hace un pull request y eso es agregado al repositorio original? Como llevamos todo lo que se puso nuevo a nuestra computadora? Tenemos que hacer el fork y el clone devuelta? Bueno, no, porque vamos a usar un flujo de trabajo diferente y mas simple.

1. Asegurate primero de que este hecho el commit de forma local.
2. Hace un pull al ultimo codigo que tenes desde GitHub. (desde uno nuevo que llamamos *upstream*)
3. Ajusta errores de union si los hay.
4. Hace un push back del codigo a nuestro repositorio origin.

Ahora, que es este nuevo repositorio *upstream* del que hablan? Bueno, nosotros ya tenemos nuestro repositorio que se llama *origin*, que corresponde en este caso al repositorio que forkeamos. O sea, se le llama origin a todo repositorio remoto con el que estemos trabajando, y las cosas se envien directamente a el desde el local. Pero en el caso de que pase esto que decimos, que alguien haga un pull al original, y este cambie, nuestro repositorio origin, el forkeado, no se da cuenta y no se actualiza. Para obtener los nuevos cambios, tenemos que ir para atras al repositorio original.

Lo que se puede hacer es un pull para obtener los ultimos cambios. Pero para hacer esto necesitamos decirle a Git de que repositorio remoto vamos a hacer esto. Entonces vamos a crear un nuevo remoto que se llame **upstream**.

- *git remote add upstream git@github.com:rithmschool/learn_forking.git*

Lo que estas haciendo aca es crear un nuevo alias para el repositorio original que forkeamos. 

Entonces ahora que lo tenemos seteado, podemos ejecutar el comando **git pull upstream master**, y obtenemos el ultimo codigo del repositorio original. Y claro que siempre que hagamos un push con **git push origin master** te lo va a mandar al repositorio forkeado, no al original. Recorda que no podes hacer un push directamente al original, si no que primero va de tu repositorio local al forkeado, y del forqueado se hace un pull request. 

El **git pull** command es una combinacion de dos comandos en realidad, el **git fetch + git merge**. O sea, git fetch va buscar el nuevo codigo que se agrego al upstream (al original), y git merge lo une a tu repositorio local. 

Si te das cuenta, por ejemplo, que el repositorio remoto tiene nuevas branches, podes usar **git fetch** y luego para verlas usas **git branch -a**.



##### Conclusion: 

Veamos lo que aprendimos hasta ahora. 

Primero vimos como empezar a usar Git. Para crear un nuevo repositorio local con git, usamos git init. Para ver su estado, usamos git status. Para ver el historial, usamos git log. 

Una vez tengamos nuestro directorio inicializado como un repositorio master, podemos empezar a crear archivos e ir añadiendolos o trackeandolos, que es el paso anterior al commiting. Uno puede añadir con git add FILE. Una vez tenemos todo añadido, con git commit los ponemos el area HEAD. Esto significa que ya estan listos para enviar a nuestro repositorio remoto.

Por el lado del repositorio remoto, tenemos que crearlo en GitHub, y de el necesitamos su URL. Entonces lo que hacemos es ir a git, e indicarle cual es nuestro repositorio remoto. Para esto podemos crear un alias con git remote add origin URL. Le ponemos origin al alias por convension. 

Entonces ahora ya lo tenemos registrado al alias, y podemos empujar (push) los archivos que le hicimos commit al repositorio remoto con git push origin master. Si usamos la flag -u, en git push -u origin master, ya nos guarda el push, y en los siguientes solo es necesario hacer git push y lo manda siempre al origin.

Por otro lado, vimos que es un fork. Vendria a ser una copia de un repositorio que no es tuyo, en tu cuenta. Lo copia exactamente como si fuera tuyo ahora, pero guarda al original. De forma que ahora podes trabajar con este repositorio.

En caso de querer tenerlo de forma local, para poder mandar archivos a este repositorio forkeado, tenemos que clonarlo. Entonces vamos a este repositorio forkeado, y ponemos clone or download por SSH. Lo que hace es darnos un link, y con git clone LINK lo clonamos con carpeta y todo seteado al directorio que le decimos en nuestra maquina. Ahora tenemos el mismo repositorio pero de forma local.

Luego, si queremos subir cosas a este, ya lo tenemos como el directorio origin, por lo tanto solo hay que hacer push. 

Pero si queremos poner las cosas en el original, tenemos que, desde github, hacer un pull request y tiene que ser aceptado por el usuario del original.

En caso de que haya cambios en el original, podemos setear otro alias para el mismo. Por convension se le llama upstream. Asi se puede hacer un pull hacia tu repositorio local, sin tener que forkear y clonar devuelta. Asi usando el comando git pull upstream master te actualiza tu repositorio local con lo que esta en el original. Y ahi lo que podes hacer es actualizar el forkeado tuyo con todo lo que te pasaron, haciendo un push.

