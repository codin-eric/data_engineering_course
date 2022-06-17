# Dia 0
## Bases de git y github
Git es un programa creado para hacer seguimiento y versionado de archivos, usualmente utilizado para trabajar y colaborar entre programadores durante el desarrollo de software.
Git fue originalmente creado por Linus Torvalds en el 2005 para el desarrollo del kernel de linux. Hoy en dia git es la herramienta numero uno utilizada en todas las empresas de desarrollo de software

### Git workflow
git divide su workflow de la siguiente manera.
Primero devemos crear un repositorio haciendo `git init` al crear esto se creara una carpeta .git en nuestro root del proyecto. En esta carpeta git tiene todo lo necesario para funcionar.
Todos los archivos y carpetas dentro de este root pasaran a estar en lo que se conoce como `untracked` lo que significa que se encuentran dentro de la carpeta de nuestro proyecto pero no forman parte de el.
Al hacer `git add [file name]` pasamos el archivo o carpeta o lista de archivos de `untracked` a `tracked` lo que significa que estamos siguiendo ese archivo o carpeta y lo pasaremos a versionar. Esta estapa se conoce como staging area.
Si hacemos `git status` veremos que todos los archivos trackeados aparecen en verde y los no trackeados aparecen en rojo.

nota: `git add ` permite wild cards como `"."  "*" "*." "*.py"`

Ahora que tenemos nuestros cambios en el estado de staging tenemos que commitearlos, de esta forma crearemos una nueva version de nuestro proyecto.
Para esto devemos hacer `git commit` si usamos el flag `-m` podemos escribir un pequeno comentario con los cambios `git commit -m'cambios'` al correr esto generaremos un nuevo commit que marca una nueva version en nuestro proyecto.
Para poder ver nuestro historial de commit podemos hacer `git log` Al usar este comando podremos ver la lista de commits en nuestro proyecto.

### Github
Github es una pagina que en sus bases permite crear un repositorio de git en internet. Esto nos permite compartir de forma rapida y simple nuestro repo con el mundo a traves de una simple pagina web. Tambien da una interfaz web para poder hacer review del codigo y hace la colaboracion mucho mas fluida.
Github es la pagina web por excelencia para compartir codigo abierto.

#### de git a github
Crear un repo en Github es super trivial y la pagina te guia para que esto sea super simple pero hay un concepto que tal vez se te escape cuando usas github.
Como dije antes github es un repo en internet, ahora, nuestro repo que creamos enterirormente esta en nuestro local. Para poder "sincronizar" nuestros repos debemos primero agregar el repo remoto (remote)
Si seguis la guia de github en un momento te dira que debes correr un comando parecido a `git remote add origin git@github.com:User/UserRepo.git`
Si nos detenemos a mirar un momento este comando lo que esta haciendo es agregar un repo remoto con el nombre origin y le indiga la url de github.

#### Trabajando con remote
Cuando creamos un repositorio remoto aparecen un par de comandos basicos.
```
git clone git@github.com:User/UserRepo.git
```
Este comando clona un repositorio remoto en tu local creando una carpeta con todo lo necesario para empezar a trabajar.
```
git push origin master
```
Este comando como su nombre lo indica empuja nuestro local hacia origin. Este comando se usa para mandar nuestros cambios al repositorio remoto
```
git pull origin master
```
Contrario al comando anterior este trae los cambios del repositorio remoto a nuestro local.

### Branch Workflow
El concepto de "ramas" es la razon por la cual git es tan poderoso.
```
-main---------------------------------------------------
             \                  -f2---         /
              \               /        \      /
               -develop-----------------------
                           \               /
                            -f1-----------
```
Como podes observar en el hermoso grafico tenemos una rama principal antiguamente llamada `master` o maestro aunque hoy en dia se esta eligiendo cambiar el nombre por `main` o principal. Luego tenemos una ramificacion a una rama llamada `develop` luego tenemos 2 ramas `f1` y `f2` que luego vuelven a `develop` y por ultimo todo se suma a `main`
Casi como si supiera, este grafico representa lo que se suele hacer cuando se trabaja en un proyecto donde, main es la branch que tiene nuestro codigo de produccion, develop es la branch donde se hacen todas las pruebas, generalmente, en un ambiente parecido a produccion pero limitado y las branches f1, f2 son branches que se usan para desarrollar features.
En empresas mas grandes se suele tener una branch de `staging` entre main y develop que es una copia exacta de produccion pero se usa para hacer pruebas de QA.

### Agile Workflow with Git
WIP

## Cheat sheet
- git init: Crea un repositorio
- git add archivo: Nos permite agregar archivos al staged
- git add .:Agrega todos los cambios a staged
- git commit -m "":Pasa archivos del staged al repositorio 
- git rm archivo: Elimina archivo de git
- git rm --cached archivo:Elimina archivo del staged
- git diff commitA commitB: nos permite ver cambios entre 2 commit
- git reset commit --hard: nos permite volver a un punto del repositorio donde todos los commit y progresos que hemos hecho se borran
- git checkout commit archivo: Nos permite volver a ver una version de un archivo especifico para ver el contenido de este, el archivo estará guardado en staged por ende si se hace un commit luego del checkout, esté se mandara al repositorio
- git checkout master: Nos devuleve la ultima version del repositorio
- git reset head: saca todos los archivos de staged pero no los elimina ni devuelve en el tiempo
- git merge rama:traemos el ultimo head de la rama que especificamos a la rama actual
- git commit -am "": Nos permite hacer un add y commit al mismo tiempo(Solo funciona con archivos a los cuales hemos usado el add anteriormente)
- git branch rama: Crea una nueva rama
- git checkout rama: Nos cambiamos de rama
- git config --list: Muestra configuracion
- git config globlal user.xxx: Cambia la configuración
- git remote add origin direccion: Agregamos un repositorio en linea a nuestro repositorio local
- git pull origin master: Hacemos pull de la rama master remota a nuestra rama master
- git pull origin master --allow-unralated-histories: Si el comando anterior no nos deja hacer pull, utilizamos este para forzar a que fusiones
- git push origin master: decimos que al origen[Rama remota] se le agreguen los cambios de nuestra rama local
ssh-keygen -t rsa -b 4096 -C "mata649@hotmail.com": genera una llave publica con el algoritmo rsa de complejidad 4096, asignada al correo "mata649@hotmail.com"
eval $(ssh-agent -s): Evaluamos si el servidor ssh esta corriendo
ssh-add rutaLLavePrivada: Se agrega la llave privada al sistema
- git remote -v: verificamos las url a las cuales hacemos push y pull
- git remote set-url origin git@github.com:mata649/hyperblog.git: cambios tanto la url para push y pull con la nueva asignada a ssh
- git log --all --graph --decorate --oneline: Se muestra toda la linea de tiempo de nuestro proyecto de una manera grafica
- git tag -a v0.1 -m "Resultado de las primeras clases del curso" 1998ebe: Agregamos un tag
- git push origin --tags: Enviamos tags a github
- git remote add upstream url: Se agrega una nueva rama para poder hacer pull de esta(Por lo general esto lo haremos cuando trabajemos con proyectos Open Source y requiramos constatemente hacer pull de la rama del proyecto original)
