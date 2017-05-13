# 1.3 Hardware del computador

**¿Qué es el hardware?**

 **Hardware** son los medios físicos (equipamiento material) que permiten llevar a cabo un proceso de datos, conforme lo ordenan las instrucciones de un cierto programa, previamente memorizado en un computador. 


En inglés duro; es hard, y hardware: significa ferretería.

El hardware de un computador es la totalidad física, conformada por todos los componentes de su equipamiento: circuitos electrónicos (hoy microcircuitos contenidos en chips cuadrados con patas para conexión), plaquetas que los soportan, cables o caminos conductores (buses) que los interconectan, mecanismos, discos, motores, gabinetes, tornillos, pantallas, teclas, etc.

Con estos elementos se construyen los distintos bloques funcionales del hardware: procesador, memoria, periféricos, interfaces, etc.

En la figura 1.5 se indican  elementos constituyentes  del hardware correspondientes a la plaqueta principal de una PC, conocida como **motherboard** cuyos bloques principales se irán tratando.

 Salvo detalles de la motherboard y otros menores, los **conceptos y definiciones que siguen son válidos para el funcionamiento de**  **cualquier**  **computador**. Como se indica en el prefacio, **todos los computadores con un solo procesador funcionan básicamente de la misma forma que una PC actual**. Cualquier procesador actual (Pentium, Motorola, Risc, etc) o anterior, funciona sobre la base del llamado  **modelo de Von Neumann** planteado en 1946, cuyos enunciados se dan en la sección 1.14.

**¿Cuáles son los bloques constituyentes básicos del hardware de un computador y qué funciones cumplen?**

En lo que sigue, si bien se parte de la fig. 1.2 es esencial tener presente lo dicho en relación con la fig,1.3   

La comprensión de las funciones que cumple cada una de las partes que conforman el proceso de datos de la figura 1.2, permite entender cómo funciona en esencia cualquier computador,  dado que cada trabajo que realiza un computador siempre es un proceso de datos, que tiene la particularidad  de ser automático.

En un proceso automático (figura 1.6) también están presentes los cuatro subprocesos constituyentes:

**Entrada - Memorización - Procesamiento - Salida** que llevan a cabo los bloques a definir (periférico de entrada  - memoria  principal - unidad de  procesamiento - periférico de  salida), siendo que en un computador existen diversas posibilidades para la entrada o salida de datos. Las flechas indican movimientos semejantes en ambas figuras.

Los bloques se comunican eléctricamente entre sí a través de caminos formados por un conjunto de cables o líneas conductoras que constituyen un  **bus**. **Un mapa de buses actual está en la fig 1.80**.

A los fines didácticos de mantener los cuatro bloques citados en el orden dibujado en las figuras 1.2 y 1.3, aparecen repetidos dispositivos que pueden actuar tanto para la entrada como para la salida de datos (las unidades de disquete y disco, y el módem). El bloque **I** se refiere a una **Interfaz** intermediaria, necesaria para conectar su periférico, la cual contiene los registros **ports** ( **Ver sección 1.10** ).

En líneas muy generales, en las figuras 1.6 y 1.7 se supone lo que sigue. Un disco de la unidad de disco rígido provee un  programa, cuyas instrucciones pasarán a través de buses hacia la memoria. Los datos llegarán también a través de buses a la memoria, provenientes del teclado.

Luego, dichas instrucciones son ejecutadas, una por vez. A tal fin primero cada una por un bus llega a un  registro de  instrucción (Rl) de la Unidad Central de Procesamiento (Procesador), donde permanece mientras se ejecuta, para  que la Unidad de Control interprete qué operación ordena ella.

A continuación, a través del mismo bus, el dato a operar por dicha instrucción llega desde memoria a un registro acumulador AX del procesador, antes de ser operado (conforme a la operación ordenada) en la Unidad Aritmética, a fin de obtener un resultado. Este puede sustituir en el registro AX al dato ya operado, y luego pasar a memoria -nuevamente a través del bus citado si una instrucción así lo ordena.

Si por ejemplo se quiere enviar dicho resultado al exterior para ser visto en pantalla, ó para ser guardado en el disco rígido o en un disquete, ello se consigue mediante la ejecución de instrucciones que así lo ordenen.

En la figura 1.6 se ha reemplazado al idóneo de la figura 1.2 encargado de obtener de la memoria en el orden establecido cada instrucción y ejecutarla por un  circuito denominado  **Unidad de Control**,**(UC)**, capaz de realizar sus mismas acciones básicas, pero millones de veces más veloz. Dichas acciones formaban parte de una secuencia siempre repetitiva:

•  obtener de la memoria la próxirila instrucción que corresponde ejecutar,

•  localizar los datos a operar (en la memoria principal, o en un registro como AX u otro, según se ordene)

•  ordenarle al circuito de la Unidad Aritmética  que realice con dichos datos la operación indicada,

•  guardar el resultado en un registro acumulador o en memoria principal

Por lo tanto:

 La UC tiene a su cargo el secuenciamiento de las acciones necesarias que deben realizar los circuitos involucrados en la ejecución de cada instrucción, según el código de la misma; y también tiene a su cuidado el orden de ejecución de las instrucciones de un programa, conforme como éste fue establecido 


La calculadora de la figura 1.2 se ha dividido en dos porciones: una que contiene los circuitos de cálculo, que denominaremos **Unidad Aritmética Lógica** ( **UAL** o ALU en inglés), y otra constituida por el **registro acumulador** designado **AX** , para datos y resultados (que en la calculadora es su registro visualizable). La UC  ordenará  mediante señales eléctricas transmitidas  por  cables, las operaciones (suma, resta, multiplicación, etc.) que debe realizar la UAL. Esta forma de control electrónico directo reemplaza a las lentas teclas de una  calculadora de la figura 1.2. Asimismo, el hecho de tener un registro separado, permite a la UC entrar al mismo datos a operar en forma electrónica directa, mediante cables que  llegan a él, sin que  tampoco se requiere teclas para ello.

 La **UAL** sirve para realizar las operaciones aritméticas o lógicas que le ordena la UC, siendo auxiliada por registros acumuladores para guardar transitoriamente resultados datos y resultados. 


Mientras que la UC es la encargada de ordenar operaciones de lectura-escritura de registros y de memoria, así como de las operaciones que debe realizar la UAL, ésta es pasiva: no puede emitir orden alguna.

Por lo tanto, la UAL **no** ejecuta instrucciones. O sea, no puede ordenar las operaciones correspondientes a los pasos que requiere la ejecución una instrucción. Sólo realiza uno de ellos: la operación aritmética o lógica que la instrucción ordena, cuando así lo requiere la UC. Mediante una operación de la UAL, a partir de uno o dos números (materia prima) se puede obtener un número (resultado) que antes no existía.

Conforme al  proceso de  la  figura 1.2, no debe perderse nunca de vista  que el  conjunto UAL Acumulador forman de hecho una calculadora con funciones semejantes a una de bolsillo, siendo la UC la encargada de manejarla, según la operación ordenada.

La palabra &quot;Lógica&quot; de las siglas UAL puede llevar a equívocos, en el sentido de suponer inteligencia. Como se ejemplifica en 1.8, las operaciones &quot;lógicas&quot; de la UAL son las operaciones AND, OR, negación, etc.

Se denomina **Unidad Central de Proceso** ( **UCP** o **CPU** en inglés) al conjunto formado por:•  la Unidad de Control•  la Unidad Aritmético-Lógica•  los registros (como el AX, RI y otros) usados durante la ejecución de cada instrucción. 

La UCP es el bloque donde se lleva a cabo la ejecución de las instrucciones. Hacia ella se dirigen las instrucciones que serán ejecutadas (una vez que la UC decodifique su código), y los datos para ser operados por la UAL a la par que de la misma salen resultados generados por la UAL.

Como se verá, además del registro acumulador definido, en la UCP existen otros registros necesarios para la ejecución de las instrucciones, que se irán definiendo.

 La UCP de una microcomputadora -como lo es una PC- está contenida en el chip **microprocesador** central (por ejemplo, el 80286/386/486, Pentium, 68000, Alfa, Power PC, etc.). 


Los términos UCP, microprocesador y procesador suelen ser sinónimos.

Al igual que el depósito fabril de la figura  1.3, la memoria principal o central o interna almacena materia prima (datos), instrucciones, y los resultados del proceso realizado en circuitos electrónicos. O sea:

 La **memoria principal** ( **MP** ) almacena instrucciones de programas, que próximamente serán ejecutadas en la UCP, y los datos que ellas ordenan procesar (operar); así como resultados intermedios y finales de operaciones sobre datos recientemente llevadas a cabo en la UCP. 


Vale decir, los datos que se procesan  y el programa que se ejecuta para ese proceso deben estar en MP. Cada programa comparte la MP con sus datos,  pero las instrucciones están en una zona y los datos en otra.

Esta információn queda almacenada temporariamente mientras se opera con ella, pudiendo ser luego reemplazada por otras instrucciones a ejecutar, y datos que éstas procesan. También existen programas que residen en MP en forma permanente, como los del sistema operativo, que facilitan el uso de un computador, cuya ejecución se alterna con la de programas de los usuarios.

Las instrucciones y datos a procesar que pasan a la UCP llegan a la MP desde el exterior del computador (figura 1.6); y los resultados que llegan a MP provenientes de la UCP deben luego pasar al exterior:

En una **operación de entrada** , la MP es el destino de instrucciones y datos provenientes del exterior (que ingresan a través de unidades de discos o disquetes, teclado, mouse, módem, u otros).

Asimismo, en una **operación de salida** , la MP es el origen de resultados que deben salir al exteríor (a través del monitor, impresora, unidades de discos o disquetes, módem, u otros).

Típicamente los programas llegan a MP para ser ejecutados provenientes de archivos en discos o disquetes. los datos a procesar pueden llegar a MP provenientes del exterior desde cualquier periférico.

 Los dispositivos que se encargan de entrar desde el exterior datos o instrucciones hacia el computador, o dar salida de resultados del computador al exterior, se denominan **periféricos** o **unidades de entrada/salida**. 

Para tal fin su función principal es **convertir** datos externos en internos en las operaciones de entrada, o a la inversa en las operaciones de salida. Un periférico oficia de frontera entre el exterior y el interior de un computador para la conversión de señales. Del mismo modo (figura 1.1), nuestros ojos, oídos, piel, etc., sensan señales externas y las transforman en señales eléctricas que van hacia nuestro cerebro o médula. Nuestras  cuerdas vocales y cavidades asociadas permiten un proceso opuesto para la comunicación con el exterior.

Hay que diferenciar el periférico de lo que es su exterior. Así, para los periféricos unidades de discos (o disquetes), el exterior  está constituido por el disco para la impresora el exterior es el papel, para el módem es la línea telefónica, etc.

Usualmente, en  un  sistema  de  computación personal existe un  conjnnto  de  periféricos (teclado,mouse, y otros) construidos sólo para entrar del exterior datos o instrucciones, que se escriben en MP. Periféricos como el monitor con pantalla y la impresora sólo pueden dar salida a datos o resultados. En cambio, las unidades  de discos o disquetes y el módem son periféricos que operan ya sea para entrada  o salida,  pudiendo llevar  a cabo una de estas operaciones por vez. Por tal motivo, en el esquema de la figura 1.6 aparecen  repetidos en la entrada y salida, aunque en realidad se trata siempre de la misma unidad actuando de una forma u otra, como ya se expresó.

La denominación periféricos proviene de su posición, vinculada al mundo exterior en relación con la **porción central** o **interna** , constituida por el microprocesador (UCP) y la memoria principal.

Por las razones que se exponen en la sección 1.10, un periférico no se conecta directamente a la porción central, sino por intermedio de una interfaz circuital (indicada con la letra **I** en la figura 1.6), que en una PC en general está contenida en una plaqueta que se inserta en un zócalo apropiado (figuras 1.60 a 1.65).

Debe consignarse que la UC **no** gobierna directamente a los periféricos mediante líneas que llegan a ellos, sino que la UCP ejecuta un subprograma preparado para cada periférico, merced al cual desde la UCP llega a la interfaz del periférico cada comando que ordena a la electrónica de éste qué debe hácer

Los periféricos como el teclado, el monitor, la impresora, el graficador (plotter) y cualquier otro que permita la comunicación directa mediante símbolos usados por los hombres, se denominan terminales. Las unidades de disco (magnético u óptico), de disquete, de cinta son periféricos conocidos como **unidades de almacenamiento masivo** ,también denominadas **memorias auxiliares** o **externas** o **secundarias**.

Distintos circuitos de un computador se comunican entre sí mediante un conjunto de conductores (cables o líneas) que interconectan eléctricamente las patas  de los chips que contienen dichos circuitos.

Así, las líneas conductoras de electricidad que salen de las  patas del chip de un microprocesador para transmitir direcciones, instrucciones, datos y resultados, constituyen el denominado **bus local**.

| Un bus de un computador es una estructura de interconexión para la comunicación selectiva entre dos o más módulos de un computador, a fin de poder transmitir información entre dos módulos por vez. |
| --- |

En general, en un bus encontramos líneas para direcciones, datos, y señales  de  control (a veces denominadas bus de direcciones, bus de datos, y bus de control, respectivamente Ver figura 1.8).

Las **líneas de  dirección** , conducen de UCP a MP cada combinación de unos y ceros que indica dónde localizar instrucciones o datos en MP. Es unidireccional.

Las **líneas de datos** , en cada lectura de MP conducen de ésta hacia la UCP tanto datos a operar como instrucciones; y en una escritura conducen desde la UCP hacia MP datos resultantes. Son pues, líneas bidireccionales. Las líneas  de control, son unidireccionales individuales para que la UCP dé órdenes cómo leer o escribir MP y para que ella reciba señales como la que origina la MP para inicar lectura efectivizada-

Un bus presente en las PC es el bus **PCI** (Peripheral Component Interconnect) creado por Intel, al cual a través de zócalos (figura 1.5)se conectan plaquetas para conexión de periféricos, y de otros buses. Este bus también emplea las tres clases de líneas citadas. No está vinculado directamente al procesador central.

En la sección 1.13 se detalla este bus, el **USB** y el **SCSI** , y en la figura 1.80 se da un mapa de cómo se comunican entre sí (como sugieren las figs 1.6 y 1.7) a través de chips que hacen de &quot;puente&quot; entre distintos buses. **Las señales eléctricas digitales se transmi en por las líneas de un bus  como se indica en la fig 1.48**

Las figuras 1.7 y 1.6 son en esencia similares, salvo la ubicación relativa de la UCP (más acorde  a la figura1.3), y que  los periféricos de entrada o salida (según indica el sentido de las flechas) aparecen espacialmente en  un  mismo nivel  de proceso,  aunque  como se aclaró, por ejemplo una unidad de disco cuando actúa como periférico de entrada no puede  simultáneamente operar para salida, y viceversa.

En  ambas figuras se  han  respetado los  orígenes y destinos de los movimientos.

Otra  diferencia  menor,  pero importante, es que por la forma en que se comunican los buses de la figura 1.7, es factible que datos o instrucciones que entraron  por un periférico, en lugar de pasar directamente a memoria principal, primero pasen a un registro de la UCP, y de éste a memoria, resultando una triangulación.

Esto es lo que sucede en  una  PC cuando se entran datos desde el teclado, el mouse, o el disco rígido. Asimismo, en una operación de salida, un resultado en memoria puede pasar a un registro de la UCP, y desde éste ir a un  periférico. Así se realiza  una impresión  o un almacenamiento en el rígido en una PC.

En cambio, la unidad de disquete envía o recibe información directamente a memoria, sin triangulación. Estas  alternativas  de triangulación para entradas y salidas no se han dibujado, para no complicar la figura. En la 39 mother de una PC existen chips que integran distintas funciones, constituyendo el chipset

**¿Cómo puede resumirse el funcionamiento básico de un computador?**

|
- Los datos y las instrucciones del programa que los procesará, deben llegar a MP desde periféricos. Cada instrucción está codificada mediante una combinación de unos y ceros, que constituye su código.
- La UC localiza en MP la instrucción que debe ser ejecutada (como se explica en la siguiente pregunta), para que su código llegue a la UCP, donde la UC determinará qué ordena ese código.
- Dicho código permite: localizar los datos que operará la UAL, la operación que debe realizar la UAL, dónde guardar el resultado, y dónde localizar la próxima instrucción en MP.
- Se vuelve al paso 1.
 |
| --- |

Si una instrucción ordena una transferencia de un dato desde la UCP hasta la plaqueta donde está conectado un periférico, tendrá lugar una operación de salida, encargándose el periférico de llevar los datos al exterior (representado por la pantalla del monitor, un disco, etc.). Igualmente existen instrucciones para llevar un dato que entró desde un cierto periférico hasta la UCP, mientras se desarrolla una operación de entrada.

| Se debe tener siempre presente que las instrucciones son interpretadas (decodificadas) por la UC; luego de lo cual la UC ordena encaminar los datos hacia la UAL, y la operación que ésta debe realizar con los datos. 

**¿Qué registros de la UCP falta definir para realizar las primeras prácticas con el programa Debug a fin de operar en el interior de un computador?**

En la figura 1.2 el idóneo ; recuerda, en una zona de su cerebro, cuál instrucción ejecutó, para luego leer la instrucción siguiente en la planilla. Esta sirve para escribir qué ordena realizar cada instrucción.

Si por razones de velocidad el idóneo ; sólo pudiera leer una sola vez cada instrucción de la planilla -como ocurre con la UC- debería registrar en su mente o en algún papel dicha información.

Para tal fin, como antes se trató, el código de cada instrucción leído en memoria principal (MP) queda registrado en el registro de instrucción (RI), para  que la UC determine qué ordena el mismo y llevar una cuenta para poder ubicar en MP la instrucción a ejecutar.

Para localizar en MP la siguiente instrucción que sigue en orden de ejecución, en la UCP existe registro muy  necesario para la UC, conocido como **contador de programa **(CP) o **registro de próxima instrucción**, que en el modelo de PC que operaremos con el Debug será el denominado registro puntero de instrucción ( **IP** - Instruction Pointer). El IP indica un número, el cual permite localizar en una zona de memoria dónde está la instrucción a ejecutar. 

 Además de los registros AX, RI e IP, definiremos un cuarto registro denominado registro de estado (RE), que contiene un conjunto de bits llamados indicadores (flags), los cuales pueden cambiar de valor luego de cada operación que hace la UAL. Los flags  se usan en instrucciones de salto, esenciales para el proceso automático de datos, pues permiten repetir muchas veces un mismo subprograma, o saltar de un subprograma a otro que ordena acciones diferentes. 

También una calculadora común muestra, junto con el resultado de una operación, otras indicaciones de interés,  que  pueden asimilarse a dichos  flags. Así, un  signo menos  que  aparezca  en  el visor adelante del resultado de una  resta, nos indica que el minuendo es menor que el sustraendo. La no aparición de este indicador de signo, implica que el minuendo es mayor. Asimismo, si el resultado de una resta es cero, significa que ambos números son iguales. Otro indicador es el de resultado excedido.

Igualmente, la UAL luego de cada operación aritmética  o lógica que realiza, genera & 39 de estado del resultado:  si fue positivo o negativo, si fue cero o no, si como número entero sobrepasó o no el máximo representable. Cada uno de estos si o no ; es un bit que se guarda en el registro de estado citado, actualizado por la UAL.