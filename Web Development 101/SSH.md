## Secure Shell (SSH)

SSH es el nombre de un protocolo y del programa que usa ese protocolo, que tiene la funcion de acceder de forma remota a un servidor por medio de un canal seguro, en donde la informacion esta cifrada. 

Ofrece varias funcionalidades de transferencia de datos. Ademas, puede copiar datos de forma segura, gestionar claves encriptadas para no escribir contraseñas y pasar datos por un tunel seguro. 

Lo que hace es trabajar de forma similar a como lo hace Telnet (que es un protocolo que nos deja acceder a una computadora de forma remota y controlarla). Pero lo que hace SSH es usar un sistema de cifrado en el que la informacion que viaja no es legible, evitando que terceron puedan leer el usuario y contraseña de conexion durante toda la sesion. Aunque si hay posibilidades de interceptar la informacion con un ataque llamado REPLAY. 

Pero la conclusion, que es es un protocolo para acceso de forma remota a otra computadora. Como si yo accediera desde aca a otra compu en cualquier parte del mundo. Se suele usar mas para acceder a servidores remotos supongo, para gestionar tu aplicacion web. Lo que hace es protejer tu usuario y contraseña enviando datos ilegibles.