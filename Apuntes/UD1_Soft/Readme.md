# SOFTWARE APUNTES: 

## *Licencias:*  
Las licencias son un contrato entre el autor y el usuario en el que se definen los derechos y deberes de ambas partes. Podemos distinguir las licencias en:  
- ***Software propietario o Copyright:*** La licencia más restrictiva y conocida. Es un conjunto de normas donde todos los derechos son del propietario de la obra (no se puede utiizar ni modificar sin autorización). Si la obra no tiene ningún aviso legal, se considera que tiene Copyright. Algunos tipos de licencia son:
    - Licencias OEM: Cuya venta queda supeditada a formar parte de un equipo nuevo
    - Licencia por volumen: Normalmente para grandes empresas, se define cuantos equipos pueden usar la misma clave...
    - Freeware: Software gratuito que normalmente pide registro. 
    - Shareware (Demo): Normalmente tiene límites de tiempo/funcionalidades o alguna otra restricción si no se paga la licencia  
    - Freemium (Version por tiempo): Tiene una parte gratis durante um cierto nº de tiempo tras el que luego no se podrá usar o tendrá funcionalidades reducidas. 

- ***Software libre:*** Para que un software se considere como tal debe cumplir 4 características/libertades: 
    - 1. Uso ilimitado (lo usa cualquiera)  
    - 2. Se pueda estudiar el código y adaptarlo a las necesidades personales (ver código)  
    - 3. Código mejorable (se puede mejorar y hacer públicos los cambios)
    - 4. Código distribuible  

    Si un programa no incluye todas las características se consideraría como software semilibre. Software libre no quiere decir que sea en todos los casos gratis, puesto que se puede distribuir comercialmente    

    Un ejemplo muy importante de Software Libre es GNU/Linux que es un diseño de una especie de Unix pero siendo software libre. Además, debemos saber que dentro del software libre tenemos varias licencias como: 
    - *Licencias GNU GPL (Licencia pública general de GNU):* Conservan los derechos de autor y permiten la redistribución y modificación bajo términos de la propia GLP. Esto hace que si se usan licencias GLP, se debe devolver un resultado final GLP para no patentar código ajeno.
    - *Licencias LGPL:* Se trata de una especie de GPL pero en versión reducida, de forma que no obliga a que el resultado final sea software libre. Solo recoge copia, distribución y modificación.
    - *Copyleft:* Garantizan el derecho de utilizar, modificar y redistribuir una obra y sus derevados siempre que se mantengan esas condiciones de utilización y difusión. Las obras pueden ir desde un programa informático gasta obras de arte, ciencia...  

    Por último, y bajo unas condiciones que ahora definiremos surgen 6 tipos de licencias CC (Creative Commons):  
    - *Attribution (BY):* La obra puede ser explotada pero es obligatorio reconocer al autor.
    - *Non commercial (NC):* El material puede ser distribuido, copiado o exhibido siempre que su uso no sea comercial.  
    - *No derivate works (ND):* La obra se puede copiar, distribuir o exhibir pero sin alterar la obra original. Por ejemplo, cogerse una parte de una fotografía.  
    - *Share alike (SA):* Se puede realizar trabajos derivados pero deben tener la misma licencia para ser distribuidos.  
    ![](img/Captura%20de%20pantalla_2022-11-03_16-27-26.png)  

- ***Dominio público:*** No está protegido por nada y no requiere de licencia, ya que sus derechos de explotación son para toda la humanidad. Esto ocurre cuando el autor lo dona a la humanidad o si los derechos han expirado (70 años tras muerte del autor).

- ***Secreto profesional:*** 
    - Información o cosas privadas de la empresa que no se puede compartir con nadie. En caso de hacerlo se estaría cometiendo un delito penal. 


## *Sistemas de archivos:*

- Ficheros y directorios: Desde el punto de vista de un sistema de ficheros, un archivo no es sino una colección de byes con un formato determinado, que se organizan en el disco duro en sectores o bloques. Es el sistema de ficheros el encargado de dar sentido a esta colección de bytes.  
Un directorio se puede definir como un fichero con un formato especial a grandes rasgos. 

- Sistema de ficheros:  
    - FAT: Es un sistema muy simple y antiguo que con nuevas versiones perdura en los S.O de hoy en día, porque sigue siendo usado sobre todo en dispositivos extraibles. Funciona de modo que, si el fichero que buscamos empieza en el cúster 5, buscaremos la entrada 5 en la FAT para conocer el siguiente cúster. Cuando lleguemos al final de la FAT se pone una marca especial. Esta tabla se mantendrá en la RAM para que las lecturas de ficheros no sean lentas. Existen variantes: FAT12, 16, 32...
    - NTFS: Es el sistema de ficheros que forma parte de la rama NT de Windows. Tiene muchas mejoras sobre FAT, como el uso del journaling, listas de control de acceso, soporte de metadatos, soporte integrado apra compresión... La madre de lo formateado en NTFS es la Master File Table (MFT), que es una especie de índice que se asocia a los ficheros. 
    - HFS+ y APFS: Es el sistema de archivos por defecto de OS X, y en cierto modo similar al de NTFS. Se trata de un árbol B+ que contiene entradas para todos los ficheros y directorios que esté en ese volumen. 
    - ext: Son los sistemas de ficheros de Linux

- Journaling: Es una especie de diario / checklist para que, en caso de interrumpción de proceso, se pueda borrar y rehacer o continuar en el momento en el que se interrumpió el proceso. Es decir, si mientras formateamos un disco se nos fuera la luz, gracias al journaling no se nos quedaría un sistema de archivos incoherente, ya que este se encarga de "volver atrás" para volver a hacerlo coherente. 

## *Acerca de los discos:*  

Se puede tener un disco exclusivo para un S.O o pueden hacerse particiones para diferenciarlos. Si surge un problema en el que las particiones se muestran como un único disco. (Spanned). Esto es la forma de discos RAID (Grupo de discos de redundancia independientes). De esta forma, si se pierde una de las particiones no se pierde la totalidad de los datos. Existen:  

## ***RAIDS:***

***Raid 0 (Stripe):*** En esta forma, un fichero se divide en dos (al igual que el disco) y uno va a cada partición del disco. De esta forma va a tardar menos en leerse y guardarse. Es decir, la principal ventaja es que se acelera el proceso n veces según los discos/particiones que tenemos. Además, en el tamaño se va a mostrar el total de todos. Si tengo 3 discos de 1TB, se va a mostrar que tengo 3TB. La desventaja es que desde que pierda uno de los n discos, pierdo todo el sistema / todo lo almacenado. Nos da un muy alto rendimiento pero con una baja seguridad/fiabilidad.   

***Raid 1 (Mirror):*** Un RAID 1 crea una copia exacta de un conjunto de datos. Es ideal cuando queremos tener mucha seguridad, pero desaprovechando capacidad. Si perdiéramos un disco, no importaría ya que tenemos otro con la información exactamente igual. En este tipo de RAID, la velocidad de lectura se reduce ya que la búsqueda se hace en dos discos a la vez, pero el rendimiento de escritura no se ve afectado, puesto que el conjunto se comporta como 1 único disco.  En este, la capacidad siempre va a ser del 50% de los discos. 

***Raid 2***: Permiten recuperar información perdida bit a bit  

***Raid 3 (Paridad):*** Aquí utilizamos el byte para la recuperación de la información perdida. Se completa para tener una paridad en los 0 / 1, buscando la rapidez para hacer los procesos.  

***Raid 4:*** Igual que Raid 3 pero leemos un bloque completo y no byte a byte.  

***Raid 5:*** El disco de redundancia es un disco normal que va almacenando lo que hacia este disco en Raid 4. De esta forma se distribuye la paridad entre todos los discos para que ningune se desgaste en exceso o por encima del resto. En este, la velocidad de escritura se ve afectada ya que se necesita hacer la paridad. Siempre se va a desperdiciar el tamaño de 1 disco.  

***Raid 6:***  En sistemas críticos se utiliza esta opción. En esta se usa 2 discos de redundacia para estar cubierto ante un problema.  

## *Sistema de arranque:*

Boostarp, que viene de hacer algo por si mismo, define la forma en la que el PC se enciende por sí mismo solo con darle a un botón. La BIOS (Sistema básico de entrada y salida)es un chip físico que funciona a 16 bits y con 1mb máximo de memoria. Antiguamente, la BIOS era ROM, estaba definida por el fabricante y no se podía modificar. La BIOS va a hacer:  

1. ***POST:*** Power on self test, comprueba que todo está en orden para arrancar el ordenador (Tiene CPU, RAM...). Si algo falta, cada placa lo mostrará de forma difente (Pitido, luces, parpadeo)  
2. ***Gestor de arranque:*** En la BIOS decido donde quiero arrancar el ordenador, por ejemplo si lo quisiera hacer desde un pendrive o de qué disco hacerlo.
3. ***Cargador del sistema:*** Una vez que la BIOS le pasa al cargador del sistema la información, se carga el sistema operativo que se haya indicado o que haya guardado la BIOS. 
4. ***MBR:*** Existe una parte reservada del disco que guardaba la información necesaria en la que la BIOS va a buscar. Esa reserva era de 512b. El Master Boot Record por tanto es un esquema de particionado de dispositivos de almacenamiento, denominado sector 0, donde toda la información que la BIOS necesita está guardada.  

## *Virtualización:*

La virtualización (v12n, esta es una forma de abreviar palabras largas para no cometer errores al nombrarlas) permite