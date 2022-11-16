# HARDWARE: CPU, RAM, PLACA BASE Y ALMACENAMIENTO  

## ***Arquitectura Von Neuman***
Tres elementos principales:

1. CPU
2. Memoria RAM
3. Buses de interconexión  

Todo lo demás son "periféricos" o elementos secundarios. El problema de esta arquitectura es que el cuello de botella es el bus del sistema. La arquitectura Harvard separa bus de instrucciones de datos. En la actualidad, se usa la arquitectura Von Neuman (con pequeñas modificaciones) para los sistemas informáticos de propósito general (computadoras, etc.) y la Harvard para los específicos (procesadores de señal digital, microcontroladores, etc.)



## ***Microprocesador o CPU (Central Process Unit)***  

- **Función:** el "cerebro" del sistema informático, es el elemento que realiza los cálculos, ejecuta las instrucciones, etc.
- **Partes principales:**
    - ALU (Unidad Aritmético-Lógica): Realiza las operaciones y cálculos  
    - UC (Unidad de Control): Decodifica las instrucciones y las ejecuta
    - Registros: es la "memoria interna" del procesador, donde se almacenan los datos, se guardan los resultados, se indican las direcciones de memoria, el contador de instrucciones, etc.
 
- **Principales parámetros a tener en cuenta:**
    - Velocidad o frecuencia de reloj: medido en Hz (a día de hoy lo normal es estar entre 2-3 Ghz)
    - Número de cores
    - Como hemos visto, las CPUs son bastante complejas y en su rendimiento depende de muchos factores. Por eso, estos parámetros sólo nos dan un idea muy básica de lo bien o mal que se puede comportar una CPU. Para poder comparar y obtener valores fiables, es necesario realizar tests de rendimiento o benchmarks, que pueden consultarse en la web.
 
- **Otros parámetros a tener en cuenta:**
    - **Tamaño de las cachés internas y uso dedicado por core o compartido para cada nivel:** L1, L2 y L3 (en algunos procesadores hay también L4, aunque no es muy común, y se suele usar como apoyo para las GPUs integradas): 
        - L1: La más pequeña y más rápida (y más cara), con tiempos de acceso comparables a los de la CPU, es la más cercana al core. Cada core cuenta con su propia L1 dedicada que suele tener 64KB-128KB, separadas en caché de datos y caché de instrucciones (por ej: 32KB para datos + 32 KB para instrucciones).
        - L2: Un poco más grande que la L1 (sobre 256-512KB de media por core), pero también un más lenta. Puede estar dedicada para cada core, o bien compartida para todos los cores, según la gama del procesador (en caso de compartida, el tamaño sería aprox. 256KB x nº de cores).
        - L3: La más grande, pero también la más lenta. Es compartida para todos los cores, y su tamaño total depende del número de cores, siendo lo normal que tenga unos pocos MB por core.
    - Todos estos niveles de caché son "transparantes" al usuario, es decir, no son gestionados por el usuario, sino por el sistema que es quien decide qué datos se colocan en cada nivel. Existen otros sistemas de caché especiales que sí permiten que el usuario las gestiones y dedica qué datos se colocan en ellas, como la scratchpad memory, aunque no son muy comunes.
    - **IPC (Instrucciones por segundo).** También se puede expresar como CPI (Ciclos Por Instrucción) o IPS (Instrucciones Por Segundo)
    - **Litografía**, que indica a qué tamaño se construyen los chips (14-10nm para Intel, 7nm para AMD, etc)
    - **Arquitectura de instrucciones:** CISC (Complex Instruction Set Computing) para procesadores AMD e Intel; o RISC (Reduced Instruction Set Computer) para procesadores ARM y marcas como Qualcomm, Samsung, M1 de Apple, etc.
    - **Arquitectura de bits:** 32 o 64 bits
    - Uso de tecnología de **HyperThreading** de Intel o SMT (Simultaneous MultiThreading) de AMD: Permite que un sólo core físico pueda ejecutar dos hilos de ejecución (threads), emulando de esta forma 2 cores lógicos. Para ello duplica parte del core (los elementos "baratos", como los registros, parte de la UC, etc) para permitir que cuando un hilo se detenga por alguna razón (espera recibir datos, etc.), el otro hilo se pueda ejecutar rápidamente, de forma que el core esté siempre trabajando. Aunque no es posible ejecutar los dos hilos a la vez, sí que se obtiene una mejora sustancial por el rápido paso de una ejecución a otra, pudiéndose lograr mejoras del rendimiento entorno al 30% (esto depende mucho del tipo de aplicaciones que se ejecuten, para computación intensiva o supercomputación puede incluso ser contraproducente usar estas técnicas, y se suelen deshabilitar).
    - **Técnica de colocación de chip en placa:** ZIF (Zero Insertion Force)
    - **Tipo de Socket**, principalmente PGA (Pin Grid Array) para AMD (AM4, etc.) o LGA (Land Grid Array) para Intel (LGA1200, LGA1700, etc.) y modelos más recientes de AMD (AM5). También existe un BGA (Ball Grid Array), pero no se suele usar en procesasdores modernos.  
    - **Overcloking**



## ***Memoria principal (RAM)***
Elemento indispensable, puesto que la CPU sólo puede acceder a los datos e instrucciones a través de la RAM. Técninamente se llaman SDRAM (Synchronous Dynamic Random-Access Memory), pero es más conocida simplemente por RAM. Es una memoria volátil (tiene que estar siempre alimentada. Si falla la alimentación, por ejemplo al apagar el equipo), su contenido se borra.

- **Características principales:**

    - **Capacidad (tamaño en GB)**, generalmente 8-16GiB para los equipos actuales
    - **Velocidades y tasas de transferencia:** Se miden en GT/s (GigaTransferencia por segundo) y las frecuencias medidas en MHz (para diferenciaras de la CPU que se miden en GHz). Ver la tabla de velocidades según versión de DDR (DDR4 o DDR5)
    - **Tecnología de acceso:** Las primeras memorias eran SDR (Single Data Rate DDR). En la actualidad ya no se usan las SDR, sino las memorias DDR (Double Data Rate). La generación DDR indica las capacidades máximas y velocidades de la memoria, su voltaje, pines, etc. Ahora mismo estamos en el paso de las DDR4 a las DDR5 (no son compatibles entre sí, tienen pines, voltajes, velocidades, etc., diferentes).
    - **Tipo de conector:** aunque ha habido muchos conectores ya obsoletos (DIP, SIPP, RIMM, SIMM, etc.), en la actualidad se usa el conector denominado DIMM (Dual In-line Memory Module) para equipos de sobremesa. Para portátiles es común el conductor SODIMM (Small Outline DIMM, más pequeño), mientras que los servidores suelen tener FB-DIMM (Fully-Buffered DIMM).
    - **Método de inserción en la placa:** LIF (Low Insertion Force). Se retiran las pestañas del conector, y presionando suavemente el módulo hasta que las pestañas encajen.
    - **Dual Channel:** mejora el rendimiento al permitir el acceso de forma simultánea a dos módulos de memoria (también es posible Quad Channel con acceso a 4 módulos de memoria diferentes a la vez). Para poder aplicar estas técnicas, la placa debe soportar esta tecnología y debemos tener módulos de memoria suficiente colocados en los zócalos correctos. DDR5 incluirá por primera Dual Channel en un único módulo usando 2 canales de 32 bits.
    - **ECC (Error Correcting Code):** permite detectar errores, usado principalmente en servidores, mientras que las memorias de equipos sobremesa son NON-ECC (no detectan errores). Las memorias DDR5 ya soportan ECC de forma nativa.
    - **XPM:** Perfiles de memoria RAM (para overcloking "más seguro").  

## ***Placa base (MotherBoard)***
Siguiendo con el paralelismo de compara un sistema informático con un "humano", la placa base sería el "cuerpo" que contiene los principales "órganos" del sistema, aportando las comunicaciones y la alimentación, mediante los buses de comunicación.

**Los elementos principales de una placa base son:**

- **Factor forma:** ATX (más común), mini-ATX, micro-ATX, BTX, ITX, etc.  
- **Socket de CPU:** Es el zócalo o slot más grande de la placa, por lo que es muy fácil de reconocer. Según si los pines están en el chip o en la placa, tenemos varias alternativas: LGA (Land Grid Aray: los pines están en la placa, mientras que el chip tiene conectores planos), PGA (Pin Grid Array: los pines están en el chip y en la placa hay agujeros para conectarlos), BGA (Ball Grid Array: no hay pines, sino pequeñas bolas en el chip).
Ej. Intel: LGA1200, LGA1700
Ej AMD: AM4 (PGA), AM5 (LGA)
- **Slots de RAM:**  suelen ser de dos a cuatro slots alargados, uno al lado del otro. El conector actual es DIMM (equipos de escritorio). Algunas variantes del conector DIMM es el SODIMM (más pequeño, para portátiles). FB-DIMM (Full Buffered DIMM, especialmente en servidores), etc. Las placas suelen tener Dual Channel (o incluso Quad Channel), que permite el acceso simultáneo a dos (o cuatro) módulos de memoria.

- **Puente Norte (North Bridge):**  Es un chip relativamente grande que cuenta con disipador y que suele estar en medio (o cerca) de la CPU y la Memoria, por lo que es fácil de reconocer. Gestiona las comunicaciones "rápidas" de la placa: controlador de memoria (comunicación memoria – CPU), PCIe, Vídeo integrado, etc. Este es el motivo por el que se llama "Puente Norte", porque hace de "puente" entre la memoria y la CPU, y está situado al "Norte" (parte superior de la placa si ponemos la CPU arriba). Este componente está presente en placas un poco más antiguas, mientras que las más recientes ya no cuentan con el puente norte, sino que la CPU asume su funcionalidad, debido a la alta velocidad de las comunicaciones.
  
- **Puente Sur (South Bridge):** Es un chip también relativamente grande, pero menor que el puente norte y no suele estar disipado, aunque podría estarlo. Está situado al "sur" de la placa, en la parte baja (colocando la placa de forma que la CPU esté en el lado superior), cerca de las ranuras de expansión. Gestiona las comunicaciones "menos rápidas", tales como el controlador E/S: USB, SATA, IDE, Ethernet,..., comunicando a estos dispositivos con el Puente Norte, para que desde ahí puedan acceder a memoria. Este componente está presente en placas un poco más antiguas, mientras que en las más recientes estas funcionalidades, entre otras, las asume el PCH.
 
- **PCH (Platform Controller Hub):** en las placas más modernas, el puente sur ha sido sustituido por el PCH que, si bien no es exactamente lo mismo, realiza una funcionalidad similar, gestionando los dispositios "menos rápidos".

- **VRM (Voltage Regulator Module):** regulan el voltaje y convierten la potencia que viene de la fuente de alimentación para ofrecer aquellos valores que necesitan componentes como la CPU, memoria RAM, etc.
  
- **Técnicas de inserción de componentes:** ZIF (Zero Insertion Force): CPU / LIF (Low Insertion Force): Memorias, tarjetas de expansión, etc.
 
- **Buses:**
    - Bus de datos
    - Bus de direcciones (32bits → 4GB RAM, 64bits → 16EB)
    - Bus de control
    - Bus de sistema (el conjunto de buses de datos + direcciones + control)
    - Bus de expansión
    - (Bus de alimentación)
    
- **Conectores de almacenamiento:**
    1. SATA (I, II y III) para HDD y SSD (SATA)
    2. M.2 (U.2 para servidores) y PCIe para SSD (NVMe)
    3. Antiguos: IDE y Floppy  
- **Ranuras de expansión:**
    - PCIe: dispositivos "rápidos" (tarjetas de vídeo, tarjetas de red Gigabit Ethernet, etc.)
    - PCI: dispositivos "menos rápidos" (tarjetas de red, wifi, etc.)
    - Antiguos: AGP (antiguo para tarjetas gráficas), PCI-X
    - Mucho más antiguos: ISA, EISA, VLB: Vesa Local Bus...  

- **Conectores de alimentación:**
    - 20+4 (ATX): para alimentar la placa desde fuente
    - 4+4: EPS (12V) para CPU
    - 6+2: PCIe (cuando requiere potencia extra, > 75W)
    - Alimentación SATA
    - Ventiladores, etc.
    - Otros antiguos: Molex (4pines) para HDD y versión reducida para diskettera, etc.
  
- **Conectores de la carcasa:**
    - Botón de encendido (POWER)
    - Reset
    - USB (2.x y 3.x)
    - Audio (minijack)
    - LEDs (encendido, controlador de discos, etc.)
    - Speaker / Buzz
    - (regulador velocidad ventilador carcasa
- Otros:
    - (Ventiladores)
    - Speaker / Buzz (integrado en placa)
    - BIOS y pila BIOS
    - Switch y jumpers (antiguo)  

## ***Almacenamiento:***
Importante: NO confundir memoria (memoria principal o RAM) con almacenamiento (memoria secundaria o auxiliar).

La necesidad del almacenamiento o memoria secundaria viene dada por conservar los datos de formar permanente cuando el equipo esté apagado y desconectado de corriente (recordemos que la RAM es una memoria volátil que sólo almacena datos cuando está alimentada).

Como "almacenar" electricidad es muy complejo, se han probado diferentes métodos (tarjetas perforadas, medios ópticos como CD y DVD, etc), siendo el más ampliamente utilizado durante muchos años los medios magnéticos, con los disquetes flexibles (Floppy) y discos duros (HDD: Hard Disk Drive) como elementos principales (también cintas magnéticas para copias de seguridad, etc.).

El gran problema de los discos duros magnéticos es, sobre todo, la existencia de partes móviles que los hacen muy lentos con altas latencias (comparativamente hablando, son millones de veces más lentos que la CPU y miles de veces más lentos que las memorias RAM).

En la actualidad, con la irrupción de las unidades SSD (Solid State Drive) que suelen usar puertas NAND, han reducido drásticamente la latencia y aumentado considerablemente la velocidad de transferencia, comparado  

- **Discos duros (HDD)**
    - Tamaños: 3.5", 2.5" (para portátiles)
    - Capacidades: 1-16TiB
    - Tecnología: magnética con partes móviles (disco que gira)
    - Velocidades de rotación (rpm: rotaciones por minuto): 5400 rpm, 7200 rpm, 10000 rpm, 15000 rpm
    - Protocolo de conexión y conectores: IDE (conector paralelo muy antiguo, ya abandonado) y SATA (conector serie, versiones I, II y III)
    - Latencia: 4-15 ms
    - Para servidores encontramos los discos SAS (Serial Attached SCSI), con una mecánica superior a los SATA y materiales mucho más robustos y mayor durabilidad, y una electrónica y controladores mejorados que permiten, por ejemplo, detección de errores. Estos discos usan un conector SAS (aunque físicamente es compatible con SATA, el conector SAS es diferente).
    Una alternativa intermedia entre SAS y discos SATA, son los NL-SAS (NearLine-SAS), que son mecánicamente similares a los SATA, pero con una electrónica mejorada, más parecida a los SAS.  

- **Unidades de estado sólido (SSD)**
    - Tamaños: (3.5"), 2.5", (1.8")
    - Capacidades: 256MiB - 2TiB (hay de tamaños mayores, aún un con precio elevado)
    - Tecnología: electrónica (memorias Flash a partir de puertas NAND) sin partes móviles. Más rápidos y con una latencia muy inferior que los HDD.
    - Latencia: 70-250 µs
    - Protocolo de conexión y conectores: Los SSD más económicos usan el protocolo SATA v3 (conector SATA), que tiene un límite de transferencia de 6 Gbps (sobre 560 MB/s). Los SSD de gama más alta utilizan el protocolo NVMe (Non-Volatile Memory Express) sobre conectores M.2 y PCIe, con unas tasas de transferencia mucho más altas (hasta 5 o más veces superiores).
    - Para servidores se suele usar el conector U.2 por sus ventajas (mejor refrigeración y, sobre todo, permite conectar y desconectar unidades en caliente, sin apagar el equipo).  

- **Mejorar HDD con SSD**
Existen diversas técnicas para mejorar el rendimiento de los discos duros rotacionales (HDD) con técnicas SSD. Una de ellas es poner una pequeña caché SSD dentro del disco duro rotacional, dando lugar a los discos duros híbridos (SSHD). La otra es colocar una pequeña memoria SSD directamente en placa que funciona como caché, como por ejemplo las memorias Intel Optane. Ambas técnicas están hoy en día en desuso, por la bajada de precios de las unidades SSD y aumento de su capacidad. 
