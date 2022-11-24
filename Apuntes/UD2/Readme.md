# ADMINISTRACIÓN LOCAL DE SISTEMAS  

## Sistema operativo:
Es el software que se situa entre las aplicaciones y el hardware para controlar el uso que las aplicaciones hacen del mismo. Para ello aparece el kernel, que es el núcleo del sistema operativo. Este arranca a la vez que el ordenador y se mantiene en memoria realizando funciones básicas. Las distribuciones de linux nacen de la modificiación de las aplicaciones asociadas al kernel. Al ser software libre, podemos hacer estas modificaciones.

## ***Comandos gestión de linux:***  
El uso de los comandos es importante para la gestión de los servidores, los cuales no tienen interfaz gráfica y necesitamos de los comandos para gestionarlo. Es decir, es de acceso remoto.  

Además, los comandos nos permiten automatizar las cosas que requiramos. Por ejemplo, para la creación de usuarios si necesitamos crear 700 usuarios será mucho mejor vía comandos que acceder 700 veces desde la interfaz gráfica.  

Una de las diferencias entre Linux y Windows es que es case sensitive, es decir que linux distingue entre mayúsculas y minúsculas. En linux, si el comando va bien no se muestra nada, si hay un error se va a mostrar

Las operaciones básicas son las CRUD: Crear, leer (read), actualizar (update) y borrar (delete)  

Dentro de Linux debemos saber cosas como: / todo el disco, ~ mi usuario, . donde estoy situado...

**Comandos básicos:**

- ```mkdir``` Crear carpeta/directorio 
- ```man mkdir``` // ```mkdir --help``` El comando man nos da la ayuda de cada comando. Podemos ir acumulando la creación de directorios, pero para ello el primer debe estar siempre el primero creado. Para solucionar eso, ponemos -p antes de los directorios y así funcionaría.
- ```ls``` Vemos el contenido de directorios (directorios que hay). Si estamos dentro de un directorio, nos mostrará su contenido
- ```ls -l || -a``` De nuevo muestra el contenido de directorios pero listado. Si le ponemos ls -la, la a de "all" nos muestra todo, archivos que no se muestran como puede ser la configuración. Todo lo que tenga un . delante, es algo oculto. 
- ```cd ... ``` Con el comando cd entramos al directorio que queramos, podemos poner las primeras letras y darle al tab para autocompletar. Si nos aparece una / antes del directorio, es que estamos dentro de la HOME.
- ```pwd``` Nos indica exactamente la ruta en la que estamos, incluyendo también la home
- ```clear``` Limpia la terminal si tiene mucha información
- ```history``` Te muestra la lista de comandos a ejecutar
- ```mv nombremal/ nombrebien``` Nos permite cambiar el nombre de un directorio si lo hemos escrito mal. También funciona para mover directorios de un lado a otro. En caso de querer cambiar el nombre de un fichero no pondremos la barra
- ```rmdir loquesea ``` Borra el directorio que queramos  
- ```-v``` Si lo colocamos al final, nos muestra que se ha hecho  
- ```cd ..``` Poniendo el punto, vamos yendo hacia directorios desde ```ls -la```
- ```touch``` Se utiliza para crear ficheros  
- ```rm``` Se utiliza para borrar ficheros   
- ```cp directorio/archivo destino``` Copia los ficheros, en primer lugar va el origen y lo último que coloquemos es el destino. Si después del directorio usamos *, copiará todo lo que tenga dentro. Además, si hacemos cp origen destino/nuevonombreorigen, copiamos un archivo cambiandole su nombre 

- ```cp -vi``` Nos pregunta si queremos sobrescribir archivos uno a uno  
- ```cp -r``` Copia directamente todo el directorio donde indiquemos  
- ```rm -r``` Para borrar un directorio con ficheros dentro. Si le ponemos una f después, forzamos el borrado sin preguntar. 
- ```cd test ;touch test2 ``` Se ejecutan los comandos independientemente de si funciona el primero de ellos o no.
- ```echo``` Nos devuelve lo que pongamos en pantalla, normlamente un mensaje
- ```cd test || mkdir test ``` Las dos barras es una especie de OR. Si se cumple la primera, no hace la segunda. Y si la primera no se cumple, se hace
- ```cd test && touch Hola ``` Si usamos el && como separador, hacemos que se haga el primer comando y después el segundo, si A falla no se va a ejecutar el siguiente
- ```cat``` Permite acceder al contenido de un fichero
- ```more or less + fichero``` Si es demasiado contenido, permite mostrarlo a cachos o de forma continua
- ```dev null``` Es una especie de papelera, todo lo copiado o que se mueva allí irá a la "basura"
- ```grep a ejemplo``` Busca la letra A en el fichero que le indicamos
- ```grep -v run salida.txt``` En este caso muestra todo lo que NO tenga run 
- ```grep -v run salida.txt | grep snap``` Aquí, muestra todo lo que NO tenga run pero SI tiene snap
- ```grep -i``` Para case sensitive
- ```|``` Usamos las barras para concadenar comandos, es decir hacemos una cosa, a la salida le aplicamos otra cosa y así sucesivamente
- ```grep ^t ejemplo.txt``` Lo que hace el sombrerito de delante es mostrar lo que empueza por T en el fichero indicado  
- ```grep ^t x$ ejemplo.txt``` La $ detras indica que termine por lo indicado
- ```ls -l /``` Con este comando veremos enlaces, de ahí viene el lm. Es decir, para ver contenido dentro de --> podemos ir directamente al origen. Sirve para, por ejemplo, poner un fichero en dos lugares y modificarlos y que esas modificaciones cambien en ambos lugares
- ```ln -s``` Creamos un enlace para entrar con facilidad a ciertos ficheros o directorios
- ```find``` Nos permite encontrar ficheros, directorios y cualquier cosa que queramos
- ```Comodín *``` Cualquier número de letras
- ```Comodín ? ``` Busca nombre de dos letras donde la primera es la que indiquemos. Los comodines son solo para ficheros
- ```find / -name "*.txt" ``` Este comando busca cualquier archivo txt en todo el disco duro
- ```wc``` Es para contar cuánto hay de algo. Nos devuelve 3 números, líneas, caracteres 
- ```find / -type d/f/l ``` Nos busca ficheros, directorios y enlaces
- ``` ```
- ```find / -atime +30 ``` Los ficheros que han sido accedidos en x tiempo. Con time es días. Con min, minutos. Además podemos pedir atime(acceso) mtime(modificado) y ctime(cambios). 
- ```find / -name / -iname ``` Busca por nombre y además, si añadimos la i es insesnsitive
- ```find / -size ``` Por tamaño 
- ```find / -empty ``` Busca todo lo vacío
- ``` find /tmp -type... -exec rm {} \;``` Con esto indicamos que borre todo lo encontrado en lo que hayamos puesto
- ```head ...``` Muestra las primeras 10 lineas
- ```tail -n 5 ...``` Muestra las últimas 5 lineas
- ```head -n -1``` Si ponemos un -1, nos quitará la primera linea
- ```cut -d "," -f 1``` Corta por columnas por ejemplo una base de datos
- ```grep ^Will$``` Que empiece por WIll y el $ indica que no tenga nada más
- ```[abc]``` Para buscar una a, una b o una c
- ```grep ^...,...``` Si ponemos los puntos indica caracteres
- ```grep ^S.*n$``` Si indicamos esto decimos: Que empiece por S, el . indica cualquier caracter, el * las veces que sea y el n$ que termine en eso
- ```sort | uniq - c ``` AL indicar el -c nos cuenta los repetidos, el sort ordena todo. Luego si hacemos uniq -n nos sale esa cuenta
- ```tr "%" "&"``` EL tr nos permite cambiar caraeteres por otro que indiquemos
- ```tr -d ``` Con el -d borramos lo que indiquemos y que esté repetida
- ```date -d ``` Buscamos la fecha que querramos

## ***Comando gestión Windows:***
Windows es INsensitive, es decir que no distingue entre mayúscula y minúscula. Otras diferencias es que la barra separadora de directorios es la barra invertida \
**Comandos básicos:**
- ```mkdir o md``` El uso de MD es para acortar, misma función
- ```rmdir o rd```
- ```cd o chdir```
- ```dir``` Para ver los directorios
- ```move``` Para mover cosas como ficheros o directorios
- ```ren o rename``` Para renombrar cosas
- ```cls``` Para limpiar la pantalla, clear screen
- ```help comando o comando|?``` Al final de algo para ayuda de comando
- ```Echo > fichero``` Para crear un fichero
- ```cd (vacío)``` Nos dice la ruta en la que estamos trabajando
- ```copy``` Comando para copiar cosas 
- ```xcopy /s``` Para copiar directorios (subdirectorios) pero que tengan contenido
- ```xcopy /e``` Para copiar directorios aunque estén vacíos
- ```del o erase``` Para borrar ficheros
- ``` ```
- ``` ```

