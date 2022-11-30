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

## *Gestor de arranque:*  

EL gestor de arranque es el programa encargado de tomar el control de la máquina justo después de conectarse y de haber terminado las verificaciones de software.  

- Registro de arranque maestro (MBR):  
Se llama MBR a un esquema de particionado de dispositivos de almacenamiento diseñado para permitir arrancar un sistema residente en el volumen. ESte esquema define un regitro de 512 bytes, que reside en el sector 0 del volumen. 

- Tabla de particiones guid (GPT):  
Es el particionado definido en el estándar UEFI. Utiliza números pseudoaleatorios para identificar las particiones. Cuando un dispositivo se particiones en GPT se escribe en el sector 0 un registro "MBR protector" cuyo propósito es mantener la compatibilidad con sistemas BIOS. La GPT empieza en el sector 1. GPT proporciona redundancia manteniendo una GPT secundaria al final del disco.  

- Gestor de arranque y cargadores del sistema:  
Gestor de arranque (boot manager) y cargador de sistema (boot loader). Un cargador de sistema es un programa sencillo diseñado para cargar en memoria un sistema operativo, mientras que un gestor de arranque es un programa que nos permite operaciones previas a la carga del sistema, permitiendo por ejemplo el arranque desde otros dispositivos.  

- BIOS:  
Basic Input/Ouput System es un firmware para arquitectura x86, está diseñado para ser el primer código que se cargue en memoria al encender el equipo y sus funciones son establecer una interfaz de acceso a los dispositivos del sistema junto a configurar e inicializar los mismos además de iniciar la carga del sistema operativo. Ha quedado obsoltea.  

La primera función de la BIOS es identificar, configurar, comprobar e inicializar los dispositivos del sistema(tarjetas de video, teclado, memoria...). Esta rutina se conoce como POST. Al abar, la BIOS "busca" un código de arranque y le cede el control.  

- Interfaz UEFI:  
Supera las limitaciones de BIOS. UEFI define una nueva interfaz entre los sistemas operativos y los firmware de los dispositivos de la máquina que sustituye a la BIOS. Se basa en tablas de datos que contienen información de la máquina y por otra parte en rutinas de acceso para los gestores de arranque y el sistema operativo. Estos servicios de arranque. Estos servicios proporcionan un panel de control en modo interfaz gráfica. Las ventajas de la UEFI es que nos permite gestionar el esquema GPT y sistema de archivos FAT. 




1. ***POST:*** Power on self test, comprueba que todo está en orden para arrancar el ordenador (Tiene CPU, RAM...). Si algo falta, cada placa lo mostrará de forma difente (Pitido, luces, parpadeo)  
2. ***Gestor de arranque:*** En la BIOS decido donde quiero arrancar el ordenador, por ejemplo si lo quisiera hacer desde un pendrive o de qué disco hacerlo.
3. ***Cargador del sistema:*** Una vez que la BIOS le pasa al cargador del sistema la información, se carga el sistema operativo que se haya indicado o que haya guardado la BIOS. 
4. ***MBR:*** Existe una parte reservada del disco que guardaba la información necesaria en la que la BIOS va a buscar. Esa reserva era de 512b. El Master Boot Record por tanto es un esquema de particionado de dispositivos de almacenamiento, denominado sector 0, donde toda la información que la BIOS necesita está guardada.  

## *Virtualización:*

La virtualización (v12n, esta es una forma de abreviar palabras largas para no cometer errores al nombrarlas) permite crear una versión virtual de algún recurso tecmológico. Hay un hipervisor que crea una capa de abstracción entre el hardware de la máquina física y el sistema operativo de la máquina virtual. Este hipervisor maneja, gestiona y arbitra los 4 recursos principales de un ordenador (CPU, Memoria, Periféricos y Conexiones de Red), de esa forma reparte los recursos entre las máquinas virtuales.

### *Hipervisores:*  
Fueron creados a finales de los 60. Hay dos tipos de hipervisores:
- Tipo 1: Denominado nativo, es el software que se ejecuta directamente sobre el hardware.  
- Tipo 2: Denominado hosted, es el que se ejecuta sobre un sistema operativo, que actua como anfitrión.  

### *Máquina virtual:*  
Una máquina virtual es un software que simula un sistema de
computación y puede ejecutar programas como si fuese una computadora real. Una característica esencial de las máquinas virtuales es que los procesos que ejecutan
están limitados por los recursos y abstracciones proporcionados por ellas. Estos procesos no pueden escaparse de esta "computadora virtual".

### *Contenedores de software:*  
Son un entorno ligero y portable que permite ejecutar aplicaiones en cualquier otro equipo, independientemente de su sietma operativo, aplicaciones... Es similar a una máquina virtual, pero mucho más ligera (no necesita S.O) ya que solo cuenta con recuros mínimos para ser ejecutada en otras máquinas.  

### *XaaS: Servicios y computación en la nube*  
A la hora de lanzar una aplicación hay varias opciones. La primera de ellas es gestionar nuestro propio servidor web (es comoplejo y hardware costoso además de tener que configurar e instalar todo). 

La computación en la nube abre un abanico de alternativas si queremos externalizar los servidores web a otras empresas en forma de servicios. De esta forma, ponemos en manos de empresas especializadas el uso de sus recursos de software y hardware para usarlos como servidor web donde correrá nuestra aplicación. Tenemos las siguientes opciones:

- IaaS (Infraestructura como servicio): En esta modalidad obtenemos un servidor virtualizado como si hubiéramos adquirido una máquina física. Tenemos acceso a un servidor sin tener que preocuparnos de climatización, alimentación, almacenamiento, acceso a la red... pero nos debemos encargar de la instalación de un S.O, software que necesiten nuestras aplicaciones, gestor de base de datos...  

- PaaS (Plataforma como un servicio): Con esta opción, tenemos un servidor listo para instalar nuestra aplicación (gestión de software y hardware es hecha por terceros). Reducimos la flexibilidad a cambio de ahorrarnos trabajo en mantenimiento y gestión.  

- SaaS (Software como un Servicio): Esta es una alternativa de alto nivel, ya que recibimos un servidor en la nube con todo el software ya instalado y nuestro papel solo se va a centrar en la gestión y uso de ese software, sin preocuparnos de capas inferiores. Es decir, tenemos hasta la aplicación instalada y solo tenemos que darle uso a la misma. 

### *VPS (Servidor virtual Privado)*  

Un servidor virtual privado (VPS, del inglés virtual private server) es un método de
particionar un servidor físico en varios servidores virtuales (máquinas virtuales con tareas
de servidor) de tal forma que todo funcione como si se estuviese ejecutando en una única
máquina. Cada servidor virtual es capaz de funcionar bajo su propio sistema operativo y
además cada servidor puede ser reiniciado de forma independiente.
La práctica de particionar un único servidor físico para que funcione como varios
servidores virtuales ya comenzó con los mainframes y ha vuelto a resurgir con el 
desarrollo de la virtualización y las tecnologías para otras arquitecturas.
Al funcionar un VPS con su propia copia del sistema operativo, los clientes tienen nivel de
acceso root o de superusuario y por tanto, pueden instalar cualquier tipo de software que
pueda ser ejecutado bajo este sistema operativo. Algunos programas no ejecutan bien en
entornos virtuales, incluyendo firewalls, clientes antivirus e incluso otras herramientas
virtuales; algunos VPS proveen fuertes restricciones, pero generalmente son laxas
comparadas con las que existen en los servidores de almacenamiento compartido. Debido
a que varios clientes (virtuales) pueden trabajar sobre una sola máquina, un VPS
normalmente tiene ciertas limitaciones en cuanto al tiempo de procesamiento, RAM y
espacio en el disco