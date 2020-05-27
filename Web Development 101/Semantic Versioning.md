## Semantic Versioning 2.0.0

El semantic versioning, o versionado de software, es el procedo de asignacion de un nombre, codigo o numero unico, a un software oara indicar su nivel de desarrollo.

Lo vamos a ver por encima, simplemente para saber que existe y que los numeros no se ponen al azar. Si no que hay una regulacion.

##### Sumario

La regla para el **versionado del software** es la siguiente:

Dado un numero de version de software de la forma MAJOR.MINOR.PATCH, se incremeta:

1. MAJOR version cuando uno hace un cambio incompatible en la API del software.
2. MINOR version cuando uno añade funcionalidades por detras, de una manera compatible.
3. PATCH version cuando haces fixing de bugs que sean compatibles.
4. Adicionales es para pre-released y built metadata, que se usa como extension de lo ya visto.

Es decir, dado un software, su version tiene un porque y debe cambiarse acorde a esto. Cuando uno actualiza su software, de manera que cambie completamente la API del mismo, y no haya forma de que sean compatibles las versiones, se cambia el numero principal. Luego, para funcionalidades del software todavia compatibles con la misma version, se cambia el segundo. Para debugeos, el tercero.

