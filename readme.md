11
git reset --hard HEAD~1
Con ~1 deshacemos el último commit, además incluimos en el comando –-hard para dejar vacío el staging area y dejar el working copy como estaba antes del commit eliminado.

También podríamos haberlo realizado de la siguiente manera:
git reset HEAD~1
y a continuación git restore git-nuestro.md (o incluso git restore *)

12
He utilizado los siguientes comandos:
git reflog 
Para saber todo lo que ha ocurrido en mi repositorio. Gracias a este comando, he conseguido localizar el commit deshecho anteriormente y, a continuación, he copiado su número identificativo corto(3184349).
git reset 3184349
De esta forma el puntero head de la rama styled se sitúa nuevamente en este commit. 
git restore git-nuestro.md  
Y finalmente, modificamos el working copy para conseguir que nuestro archivo vuelva a estar como se encontraba en el commit que habíamos deshecho.

13
git merge master
No causó conflicto, ya que el archivo git-nuestro.md, no se ha editado en la misma línea, en dos ramas diferentes.

19
En este caso concreto sí que hay un conflicto, debido a que tanto en la rama styled, como en la rama htmlify, estamos intentado modificar en las mismas líneas el archivo git-nuestro.md. Es decir, en una rama tiene un contenido y en la otra rama tiene otro.

21
No hay conflicto, aunque el contenido del archivo git-nuestro.md en master, ahora es idéntico que en la rama styled.

25
git log --graph --pretty=oneline

También podría haber creado un alias para no tener que escribir el comando anterior, cada vez que quiera mostrar el gráfico. 
Yo en mi caso he llamado al alias grafico.

git config alias.grafico “log --graph --pretty=oneline”

git grafico

El alias creado anteriormente únicamente se ha creado para nuestro repositorio. Si quisiéramos que se ejecute para todos nuestros repositorios de git, tendríamos que incluir al comando –-global.

git config –-global alias.grafico “log --graph --pretty=oneline”


26
Sí que podría ser fast-foward, ya que las ramas master y title, forman una lista.


27
git reset HEAD~1

28
git restore git-nuestro.md

29 
git branch -d title
Pero me ha avisado de que title estaba mergeado. Por esta razón he tenido que utilizar el comando 
git branch -D title

30
git checkout 8743b51 
Salta el mensaje You are in 'detached HEAD' state.
git branch title

32
git reset abcc37e
git restore git-nuestro.md

33
git reset 4f93cae
git restore git-nuestro.md  



