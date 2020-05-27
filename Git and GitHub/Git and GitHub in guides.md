### Git and GitHub guides

Ultra necesario en algun futuro, leer el libro Pro Git que esta en la pagina de Git. Es una guia entera del uso de Git. Es necesario para un futuro porque todas las empresas te piden laburar con git, es una realidad.

Algo que estaba pensando para empezar a tenerla mas clara con el uso de Git y GitHub es empezar a subir todos estos tutoriales que me estoy haciendo ahi. Total se subirian en formato .md, y ya se guardarian ahi todos juntos en el repositorio remoto, tendria espacio de sobra y no hay chance de que se rompa nada. Ademas, voy teniendola mas clara de como se hacen pull y push requests. Es decir, como funciona GitHub.

-----

#### Git Guide

##### Crear un nuevo repositorio 

Crea un nuevo directorio, abrilo y pones:

- git init

para crear un nuevo repositorio de Git.

##### Checkout a repository

Se puede crear una working copy a un repositorio local con el comando

- git clone /path/to/repository

y usando un servidor remoto, tu comando es

- git clone username@host: /path/to/repository

##### Workflow

Tu repositorio local consiste de tres arboles mantenidos por git. El primero es el *working directory*, en donde se encuentran los archivos. El segundo es el *Index* que actua como el staging area, el area antes de que se haga el commit. Y por ultimo el *HEAD*, que muestra el ultimo commit que se hizo.

Con *git add* lo mandas a la staging area, y con *git commit* queda en el head.

##### add y commit

Podes añadir al Index con el comando

- git add <filename>

o si queres mandar todo

- git add .

Para hacer un commit, es decir, terminar de mandarlo al area HEAD, usas

- git commit -m "commit message"

Ahora el archivo se mando al HEAD, pero no esta todavia en el repositorio remoto.

##### Pushing changes

