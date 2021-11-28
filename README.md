# PR1_Git
Práctica de Git para el curso de KeepCoding




** - ¿Qué comando utilizaste en el paso 11? ¿Por qué? **

Utilizo el comando "get reset --hard HEAD~1".

Utilizando este comando me puedo posicionar (gracias al “reset”) sobre el commit justo anterior (con el HEAD~1). Y añadiendo el “--hard” se consigue dejar el working copy exactamente igual que el working copy del commit en el que me estoy posicionando. De este modo, se deshace el último commit perdiendo los cambios que he realizado en el working copy.




** - ¿Qué comando o comandos utilizaste en el paso 12? ¿Por qué? **

Para poder rehacer el último commit, el que se acaba de deshacer (es decir, volver al mismo sitio que estábamos), es necesario en primer lugar obtener el identificador de dicho commit al que queremos acceder (ya que desde el commit que me encuentro, con el “git log”, no tengo acceso al commit que quiero acceder) utilizando la sentencia "git reflog" y analizando cada uno de los saltos de commit del repositorio para conseguir su identificador.

Una vez encontrado el identificador del commit al que quiero acceder, utilizado el comando reset: "git reset <id_commit>"

De este modo, ya estoy posicionado sobre el commit, pero aún no está todo el trabajo hecho, ya que al no utilizar la opción “--hard”, mi working copy es el mismo que el del commit desde el que vengo y no que el del commit en el que me encuentro ahora.

Por lo tanto, haciendo "git status", el sistema indica que el archivo git-nuestro.md es diferente. Por lo tanto, para restaurarlo y dejarlo todo como estaba se utiliza el siguiente comando: "git restore git-nuestro.md"

Una vez ejecutado, ya nos encontramos sobre el commit que queríamos y con el working copy igual que el repositorio. Por lo tanto, ya estaría rehecho el último commit que se acaba de deshacer.




** - El merge del paso 13, ¿Causó algún conflicto? ¿Por qué? **

No se produce un conflicto como tal, ya que en la consola no aparece la palabra "CONFLICT" al ejecutar el merge. Sin embargo, el merge no se produce puesto que aparece un mensaje que indica "Already up to date".

Esto se produce porque se está intentando fusionar desde la rama hijo hacia la rama padre. Y la rama hijo ya tiene acceso y "puede ver" todos los commit de la rama padre, por lo que no tiene sentido hacer ese merge. Sí habría tenido sentido que fuera al revés, es decir, que la rama "master" absorbiera a la rama "styled", porque la rama "master" no tiene acceso a todos los commit que sí que tiene "styled".




** - El merge del paso 19, ¿Causó algún conflicto? ¿Por qué? **

Sí, causa un conflicto por el contenido de los documentos de ambos commit. A la hora de hacer el merge, compara el contenido de ambos documentos y ve que en las mismas líneas el contenido es diferente y, por ese motivo, no hace el merge. Si el contenido que es diferente estuviera en líneas no iguales (o es el mismo en las mismas líneas), sí que haría el merge, pero al encontrarse en la/s misma/s línea/s, indica el conflicto para que seamos nosotros mismos quien lo resolvamos.

Esto también se produce porque es un no-fast-forward. En caso contrario, en caso de que fuera un merge fast-forward, no habría conflicto.

Se resuelve el conflicto quedándonos con el contenido del documento de la rama "styled".




** - El merge del paso 21, ¿Causó algún conflicto? ¿Por qué? **

En este caso, a diferencia del caso anterior, no causa ningún conflicto porque es un merge fast-forward (y en este tipo de merge no se producen conflictos).




** - ¿Qué comando o comandos utilizaste en el paso 25? **

Para pintar el gráfico del repositorio utilizo el siguiente comando: "git log --graph --decorate --pretty=oneline"




** - El merge del paso 26, ¿Podría ser fast forward? ¿Por qué? **

Sí, el merge del paso 26 podría ser fast-forward puesto que al hacer el merge, la rama master no se deja por el camino (es decir, no se pierde) ningún commit.

Además, el commit de la rama master es el padre del commit de la rama "title", por lo que tiene "acceso directo" a dicho commit.




** - ¿Qué comando o comandos utilizaste en el paso 27? **

Para deshacer el merge sin perder los cambios del working copy utilizo el comando reset: "git reset HEAD~1". De este modo, volvemos al commit anterior con el working copy tal cual se tenía en el commit del merge.




** - ¿Qué comando o comandos utilizaste en el paso 28? **

El comando restore: "git restore git-nuestro.md". Con este comando se restaura el estado del working copy sobre el que se encuentra la rama posicionada.




** - ¿Qué comando o comandos utilizaste en el paso 29? **

El comando branch: "git branch -D title".

Con el comando "git branch -d title" (es decir, con la "-d" en minúscula) no permite hacer el borrado de la rama, puesto que no está mergeada con ninguna otra rama y no se podría tener acceso. Entonces, por este motivo, si queremos borrarlo hay que utilizar "-D" (en mayúscula).




** - ¿Qué comando o comandos utilizaste en el paso 30? **

Ahora es necesario descubrir mediante el comando “reflog” cuál es el identificador del commit que se originó del merge anterior.

Una vez se sabe, se utiliza el comando reset con la opción “agresiva” (es decir, utilizar la opción "--hard"): "git reset --hard <id_commit>".

De este modo, se restaura la misma situación (es decir, el mismo working copy) que cuando se realizó el merge.




** - ¿Qué comando o comandos usaste en el paso 32? **

Utilizo en este caso el comando "checkout" para mover el puntero "HEAD" al commit solicitado: "git checkout <id_commit">.

Para poder obtener el identificador del commit sobre el que me quiero posicionar, con el comando "git reflog", puedo ver todo el rastro de commit por los que ha ido pasando y obtener dicho identificador (en este caso, el inicial).




** - ¿Qué comando o comandos usaste en el punto 33? **

Utilizo en este caso el comando "checkout" para mover el puntero "HEAD" al commit solicitado: "git checkout <id_commit">.

Para poder obtener el identificador del commit sobre el que me quiero posicionar, con el comando "git reflog", puedo ver todo el rastro de commit por los que ha ido pasando y obtener dicho identificador (en este caso, el del título al poema).
