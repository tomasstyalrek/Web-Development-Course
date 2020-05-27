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
