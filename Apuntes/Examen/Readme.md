# APUNTES PARA EXAMEN PRÁCTICO:

## ***Parte de linux:*** 
Debemos saber alguno básicos como que: "/" Es la raíz o directorio principal, "." es nuestra posición actual, ".." es la posición o directorio anterior, "man" o "help" nos da una ayuda sobre el comando que queramos, "*" indica cualquier cosa
- ```cd / ; .. ; documentos/textos``` : Con cd nos vamos a mover entre directorios. 
- ```ls -l ; -la; -ls```: Es el comando list, muestra una lista de contenido del directorio que indiquemos. 
- ```mkdir + rmdir```: Para crear y eliminar directorios. Podemos crear de forma acumulada. Con rmdir borramos el directorio y su contenido. 
- ```mv documento carpeta```: Movemos el archivo a donde queramos. En el comando indicaremos en primer lugar el origen o archivo y en segundo lugar el destino
- ```rm documento.txt```: Sirve para eliminar archivos. Si usamos rm -r borramos un directorio más su contenido
- ```cat documento.txt```: Sirve para mostrar el contenido de un archivo. 
- ```touch```: Para crear un fichero.
- ```cp archviooriginal copia```: Sirve para copiar archivos y directorios. De nuevo indicamos primero el origen y luego su destino. De nuevo, si usamos el -R copiará el directorio con su contenido
- ```df + du```: DF muestra el espacio en disco (disponible, usado y total), DU muestra cuanto espacio ocupa un archivo o un grupo de ellos.
- ```find ```: Sirve para encontrar un archivo o directorio. Dentro del comando tenemos -type (para buscar por tipo de fichero), -name (por nombre), -atime (días) -amin(minutos), -size (por tamaño), -empty (lo que esté vacío)...
- ```grep```: Para buscar dentro de un fichero. Podemos usar ^a(que empiece por a), a$ (que termine por a), ^t.*s$ (que empiece por t, que tenga cualquier caracter(.) las veces que sea ( * ) y que acabe por s), si indicamos grep -i nos buscará de forma insensitive (sin importar minúscula, mayúscula), [ abc ] búsqueda algo que contenga a, b o c.
- ```wc```: Nos hace un conteo de línes, caracteres... Si indicamos -l al final solo nos saca las lineas. Es interesante para contar ocurrencias. 
- ```sort | uniq```: Ordena alfabeticamente y nos elimina lo repetido. 