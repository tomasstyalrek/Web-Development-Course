## Terminal and UNIX commands

Debido a que ya tenemos en evernote un tutorial entero del uso del terminal que sacamos de Rithm School, no vamos a escribir todo, solo vamos a poner alguna que otra cosa teorica y poner una cheat sheet de todos los comandos. Porque realmente ya sabemos como funciona, y solo tenemos que saber lo que vamos a usar por ahora, que son los comandos mas faciles.

Vamos a aclarar la diferencia entre los diferentes tipos de nombres que se encuentran por ahi. Entre ellos pueden estar, UNIX, Linux, Terminal, Shell, Bash, Command line interface, y si surgen mas los vamos poniendo.

Una cosa es un **terminal** o **consola**, un dispositivo electronico o electromecanico, o sea es hardware no software, que esta hecho para que pueda interactuar con una computadora. Se suele confundir con lo que se llama emulador del terminal o emulador de consola, que vendria a ser su homonimo virtual.

Un **emulador del terminal o de consola** es un programa informatico, es decir software, que simularia el funcionamiento de un terminal de computadora. Realiza las mismas acciones, es decir, la comunicacion con la computadora en su parte mas basica. La GUI de la terminal se llama ventana de terminal.

Aca es cuando entra el concepto de **shell**. Una shell es un interprete de ordenes o de comandos, un programa informatico que provee una interfaz de usuario (GUI) para acceder a los servicios del sistema operativo. Es decir, no hay un solo tipo de shell, si no que depende del OS en donde se corra.

Dependiendo el tipo de interfaz que empleen, los *shells* pueden ser:

- De lineas de texto (**CLI, Command Line Interface**).
- Graficos (GUI, Graphical User Interface)
- De lenguaje natural (NUI, Natural User Interface)

De aca la que vamos a rescatar es la interfaz de linea de comandos. Una **CLI (Command Line Interface)** es un metodo, a diferencia de un shell que es el programa informatico que lo utiliza. Este metodo permite darle a los usuarios instrucciones a algun programa informatico por medio de una linea de texto.

Es decir, el CLI es un metodo, mientras que la shell y el emulador del terminal son solo programas que lo utilizan.

Los CLI pueden usarse tanto dando entradas de texto en forma de comandos, o como una forma mas automatizada (archivo batch), leyendo ordenes desde un script.

Los shells CLI mas comunes son Bash, Zsh, Simbolo de sistema o ahora llamado Power Shell. 

Power Shell es un shell como cualquier otro, pero como digimos depende del sistema operativo. Este shell es el perteneciente al sistema Windows de Microsoft.

**Bash** o **GNU Bash** es un lenguaje de comandos y el shell de los sistemas UNIX. Es hoy en dia la shell preterminada que utilizan todos los sistemas operativos Linux y MacOS. Ultimamente tambien la implementa Windows 10 habilitando algunas opciones.

Es decir, Bash no solo es el nombre del shell, si no que tambien es un lenguaje entero. Es un procesador de comandos, que se ejecuta en un programa o ventana de texto, en donde el usuario puede escribir comandos que respenten la sintaxis del lenguaje. Tambien ofrece la opcion de ejecutar acciones mediante un archivo script de shell. Ademas, ofrece varias herramientas como tuberias, variables, estructuras de control, etc. Es un lenguaje entero.

 En cuanto a **UNIX**, este es un sistema operativo. A el le pertenece el nombre de Bash shell. A partir de UNIX se hicieron mucha cantidad de sistemas operativos, como todas las distribuciones de linux y MacOS. 

Lo que se llama Linux en realidad es **GNU/Linux**, un sistema operativo de tipo UNIX, multiplataforma, multiusuario y multitarea. Es un proyecto llevado a cabo por la combinacion de otros, que son GNU y Free Software Fundation. Linux es el ejemplo maximo del software libre, ya que puede ser utilizado, modificado y redistribuido por cualquier persona, siempre y cuando se aftenga a la licencia GLP (Licencia Publica General de GNU) y otras mas.

Por lo general se suelen referir a GNU/Linux solo como Linux, pero asi se le llama al kernel o nucleo. El kernel es uno de los tantas formas que puede tomar este sistema operativo, y depende de su estructura y funcionamiento. 

El sistema operativo Linux tiene diferentes tipos de distribuciones, todas hechas y desarrolladas bajo la misma licencia, y cada una con un proposito general. Muhcas dedicadas a usuarios normales, programadores, y otra a servidores. Se dice que la gran mayoria de servidores grandes, supercomputadoras, y sistemas embebidos usan Linux como su sistema operativo. Esto es por su gran capasidad de estabilidad en estas areas.

Por ultimo, **GNU** es otro sistema operativo de tipo Unix,  mientras que Free Software Fundation es una organizacion. Estos son los dos fundadores de linux. GNU actua de la misma manera de lo que seria linux, o sea, es propietario del nombre de todas las distribuciones que hay. Tiene licencias de software libre a su nombre.

##### Cheat sheet de los comandos de bash

CORE COMMANDS

| cd             | Home directory                                               |
| -------------- | ------------------------------------------------------------ |
| cd [folder]    | Change directory                                             |
| cd ~           | Home directory, e.g. ‘cd ~/folder/’                          |
| cd /           | Root of drive                                                |
| ls             | Short listing                                                |
| ls -l          | Long listing                                                 |
| ls -a          | Listing incl. hidden files                                   |
| ls -lh         | Long listing with Human readable file sizes                  |
| ls -R          | Entire content of folder recursively                         |
| sudo [command] | Run command with the security privileges of the superuser (Super User DO) |
| open [file]    | Opens a file                                                 |
| open .         | Opens the directory                                          |
| top            | Displays active processes. Press q to quit                   |
| nano [file]    | Opens the Terminal it’s editor                               |
| pico [file]    | Opens the Terminal it’s editor                               |
| q              | Exit                                                         |
| clear          | Clear screen                                                 |

COMMAND HISTORY

| history n | Shows the stuff typed – add a number to limit the last n items |
| --------- | ------------------------------------------------------------ |
| ctrl-r    | Interactively search through previously typed commands       |
| ![value]  | Execute the last command typed that starts with ‘value’      |
| !!        | Execute the last command typed                               |

FILE MANAGEMENT

| touch [file]             | Create new file                      |
| ------------------------ | ------------------------------------ |
| pwd                      | Full path to working directory       |
| ..                       | Parent/enclosing directory, e.g.     |
| ls -l ..                 | Long listing of parent directory     |
| cd ../../                | Move 2 levels up                     |
| .                        | Current folder                       |
| cat                      | Concatenate to screen                |
| rm [file]                | Remove a file, e.g. rm [file] [file] |
| rm -i [file]             | Remove with confirmation             |
| rm -r [dir]              | Remove a directory and contents      |
| rm -f [file]             | Force removal without confirmation   |
| rm -i [file]             | Will display prompt before           |
| cp [file] [newfile]      | Copy file to file                    |
| cp [file] [dir]          | Copy file to directory               |
| mv [file] [new filename] | Move/Rename, e.g. mv -v [file] [dir] |

DIRECTORY MANAGEMENT

| mkdir [dir]          | Create new directory                                    |
| -------------------- | ------------------------------------------------------- |
| mkdir -p [dir]/[dir] | Create nested directories                               |
| rmdir [dir]          | Remove directory ( only operates on empty directories ) |
| rm -R [dir]          | Remove directory and contents                           |

PIPES - para combinar multiples comandos y generar output

| more      | Output content delivered in screensize chunks             |
| --------- | --------------------------------------------------------- |
| > [file]  | Push output to file, keep in mind it will get overwritten |
| >> [file] | Append output to existing file                            |
| <         | Tell command to read content from a file                  |

HELP

| [command] -h     | Offers help                               |
| ---------------- | ----------------------------------------- |
| [command] —help  | Offers help                               |
| [command] help   | Offers help                               |
| reset            | Resets the terminal display               |
| man [command]    | Show the help for ‘command’               |
| whatis [command] | Gives a one-line description of ‘command’ |