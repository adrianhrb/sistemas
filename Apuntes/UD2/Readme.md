# ADMINISTRACIÓN LOCAL DE SISTEMAS  

## ***Comandos gestión de linux:***  
El uso de los comandos es importante para la gestión de los servidores, los cuales no tienen interfaz gráfica y necesitamos de los comandos para gestionarlo. Es decir, es de acceso remoto.  

Además, los comandos nos permiten automatizar las cosas que requiramos. Por ejemplo, para la creación de usuarios si necesitamos crear 700 usuarios será mucho mejor vía comandos que acceder 700 veces desde la interfaz gráfica.  

Una de las diferencias entre Linux y Windows es que es case sensitive, es decir que linux distingue entre mayúsculas y minúsculas. En linux, si el comando va bien no se muestra nada, si hay un error se va a mostrar

Las operaciones básicas son las CRUD: Crear, leer (read), actualizar (update) y borrar (delete)

Comandos básicos:  

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