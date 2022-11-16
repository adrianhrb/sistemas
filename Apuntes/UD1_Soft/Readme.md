# SOFTWARE APUNTES: 

## *Licencias:*  
Las licencias son un contrato con la empresa y el uso sobre qué se puede hacer y qué no con el programa/S.O o cualquier cosa que tenga una licencia. Podemos dividir las licencias en:  
- ***Secreto profesional:*** 
    - Información o cosas privadas de la empresa que no se puede compartir con nadie. En caso de hacerlo se estaría cometiendo un delito penal. 
- ***Licencias propietarias:*** Licencias por las que hay que pagar una parte y que tiene las restricciones que la empresa o el autor decida. Dentro de ellas tenemos:
    - Freeware: Se da gratis pero con limitaciones  
    - Shareware: Normalmente tiene límites de tiempo/funcionalidades o alguna otra restricción si no se paga la licencia  
    - Freemium: Tiene una parte gratis y una parte de pago  
- ***Software libre:*** Para que un software se considere como tal debe cumplir 4 características: 
    - 1. Uso ilimitado (lo usa cualquiera)  
    - 2. Se pueda estudiar el código (ver)  
    - 3. Código mejorable  
    - 4. Código distribuible

    Un ejemplo muy importante de Software es GNU/Linux que es un diseño de una especie de Unix pero siendo software libre. Además, debemos saber que dentro del software libre tenemos varias licencias como: 
        - *Licencias GNU GLP:* Permiten la redistribución y modificación bajo términos de la propia GLP. Esto hace que si se usan licencias GLP, se debe devolver un resultado final GLP para no patentar código ajeno.
        - *Licencias LGPL:* Ofrece grandes ventajas, pero algunas veces ofrece algunas restricciones. En estas, y a diferencia de las GPL, el resultado no tiene por qué ser libre. Pero, cualquier cosa fuera de copia, distribución o modificación no está cubierta por esta licencia.  
        - *Otras:* Hay otro tipo de licencias como las Copyleft, que garantizan el derecho de utilizar, modificar y redistribuir una obra y sus derevados siempre que se mantengan esas condiciones de utilización y difusión. Las obras pueden ir desde un programa informático gasta obras de arte, ciencia...  

    Por último, y bajo unas condiciones que ahora definiremos surgen 6 tipos de licencias CC:  
        - *Attribution:* La obra puede ser explotada pero es obligatorio reconocer al autor.
        - *Non commercial:* El material puede ser distribuido, copiado o exhibido siempre que su uso no sea comercial.  
        - *No derivate works:* La obra se puede copiar, distribuir o exhibir pero sin alterar la obra original. Por ejemplo, cogerse una parte de una fotografía.  
        - *Share alike:* Se puede realizar trabajos derivados pero deben tener la misma licencia para ser distribuidos.  
        ![](img/Captura%20de%20pantalla_2022-11-03_16-27-26.png)  

- ***Dominio público:*** No está protegido por nada y no requiere de licencia, ya que sus derechos de explotación son para toda la humanidad. Esto ocurre cuando el autor lo dona a la humanidad o si los derechos han expirado (70 años tras muerte del autor).


## *Sistemas de ficheros:*  

Windows: NTFS, FAT32, EXFAT
GNU/LINUX: ext4
Mac: HFS+ (Antiguo), APFS (nuevo)

Cifrado: Permite encriptar nuestros datos. Los simples no, pero los más modernos si soportan cifrado. Para saberlo, lo miramos en la wikipedia. FAT32 por ejemplo no soporta cifrado.  

Compresión ficheros: Si permiten o no comprimir ficheros.  

Cuotas: Divisiones de los ficheros para diferentes usos  

Uso preferente: Sistemas preferentes que compatibilizan los sistemas de ficheros  

Journaling: Es una especie de diario / checklist para que, en caso de interrumpción de proceso, se pueda borrar y rehacer o continuar en el momento en el que se interrumpió el proceso.  

## *Acerca de los discos:*  

Se puede tener un disco exclusivo para un S.O o pueden hacerse particiones para diferenciarlos. Si surge un problema en el que las particiones se muestran como un único disco. (Spanned). Esto es la forma de discos RAID (Grupo de discos de redundancia independientes). De esta forma, si se pierde una de las particiones no se pierde la totalidad de los datos. Existen:  

***Raid 0 (Stripe):*** En esta forma, un fichero se divide en dos (al igual que el disco) y uno va a cada partición del disco. De esta forma va a tardar menos en leerse y guardarse. Es decir, la principal ventaja es que se acelera el proceso n veces según los discos/particiones que tenemos. Además, en el tamaño se va a mostrar el total de todos. Si tengo 3 discos de 1TB, se va a mostrar que tengo 3TB. La desventaja es que desde que pierda uno de los n discos, pierdo todo el sistema / todo lo almacenado.  

***Raid 1 (Mirror):*** La escritura se mantiene. La lectura, se acelera porque se puede buscar en n discos. Aquí, tenemos un espacio de 100% // n discos y además, podemos perder n-1 discos. Aunque el rendimiento se reduzca la información queda mucho más protegida que en el anterior.  

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