# Dia 0
## Bases de git y github
git init: Crea un repositorio
git add archivo: Nos permite agregar archivos al staged
git add .:Agrega todos los cambios a staged
git commit -m "":Pasa archivos del staged al repositorio 
git rm archivo: Elimina archivo de git
git rm --cached archivo:Elimina archivo del staged
git diff commitA commitB: nos permite ver cambios entre 2 commit
git reset commit --hard: nos permite volver a un punto del repositorio donde todos los commit y progresos que hemos hecho se borran
git checkout commit archivo: Nos permite volver a ver una version de un archivo especifico para ver el contenido de este, el archivo estará guardado en staged por ende si se hace un commit luego del checkout, esté se mandara al repositorio
git checkout master: Nos devuleve la ultima version del repositorio
git reset head: saca todos los archivos de staged pero no los elimina ni devuelve en el tiempo
git merge rama:traemos el ultimo head de la rama que especificamos a la rama actual
git commit -am "": Nos permite hacer un add y commit al mismo tiempo(Solo funciona con archivos a los cuales hemos usado el add anteriormente)
git branch rama: Crea una nueva rama
git checkout rama: Nos cambiamos de rama
git config --list: Muestra configuracion
git config globlal user.xxx: Cambia la configuración
git remote add origin direccion: Agregamos un repositorio en linea a nuestro repositorio local
git pull origin master: Hacemos pull de la rama master remota a nuestra rama master
git pull origin master --allow-unralated-histories: Si el comando anterior no nos deja hacer pull, utilizamos este para forzar a que fusiones
git push origin master: decimos que al origen[Rama remota] se le agreguen los cambios de nuestra rama local
ssh-keygen -t rsa -b 4096 -C "mata649@hotmail.com": genera una llave publica con el algoritmo rsa de complejidad 4096, asignada al correo "mata649@hotmail.com"
eval $(ssh-agent -s): Evaluamos si el servidor ssh esta corriendo
ssh-add rutaLLavePrivada: Se agrega la llave privada al sistema
git remote -v: verificamos las url a las cuales hacemos push y pull
git remote set-url origin git@github.com:mata649/hyperblog.git: cambios tanto la url para push y pull con la nueva asignada a ssh
git log --all --graph --decorate --oneline: Se muestra toda la linea de tiempo de nuestro proyecto de una manera grafica
git tag -a v0.1 -m "Resultado de las primeras clases del curso" 1998ebe: Agregamos un tag
git push origin --tags: Enviamos tags a github
git remote add upstream url: Se agrega una nueva rama para poder hacer pull de esta(Por lo general esto lo haremos cuando trabajemos con proyectos Open Source y requiramos constatemente hacer pull de la rama del proyecto original)