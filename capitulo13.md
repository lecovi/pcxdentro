[^ Índice](README.md) | [Siguiente >](capitulo14.md)

----

# 1.13 DETALLES DE LOS BUSES #
## ¿Qué características tienen los buses compartidos? ##

Un **bus** es un camino eléctrico constituido por líneas conductoras, que permiten intercambiar información binaria entre dos o más dispositivos. Si es compartido (fig. 1.79.b) por más de dos, éstos pueden comunicarse entre sí a través del bus a razón de dos por vez, siendo que en un instante dado uno solo puede transmitir. Cualquier señal que éste trasmite puede ser recibida por cualquier otro dispositivo del bus, pero sólo responderá el que fue seleccionado.| 
:-|

En general se trata de que un bus permita económicamente que se conecten a él dispositivos de distinto tipo con tal que cumplan con especificaciones mecánico-eléctricas y de señalización temporal.
El hecho de compartir líneas implica una gran economía de cableado y espacio, en relación con los mismos dispositivos conectados de a dos, "punto a punto", con un bus independiente *dedicado* entre cada par.

![imagen 1.79.a.b](1.79.a.b.jpg)

Un bus compartido tiene la limitación que dispositivos conectados al mismo deben esperar para recibir o transmitir datos, pues ello se realiza *sólo* entre dos dispositivos a la vez; y que se necesita circuitería adicional de *control del bus*, que asegure esto último, para evitar interferencias.
Lo dicho puede equipararse a teléfonos internos que comparten una misma línea. Antes de comunicarse uno con otro debe constatarse que el indicador luminoso de que 2 están hablando no esté encendido.
En un bus compartido se necesita un *protocolo de arbitraje* que especifique la secuencia de pasos (señales) que deben ocurrir para que un dispositivo pueda comunicarse con otro. Con los teléfonos sería: ver si el LED está apagado, sino esperar; levantar el tubo; digitar el número de otro interno, etcétera.  
Así se determina, *controlador del bus* mediante, cual es el próximo dispositivo *("master")* que se va a iniciar una transferencia con otro del bus. El *"master"* selecciona el dispositivo *"slave"* o *"target"* con el cual realizará la transferencia de datos en un sentido u otro.  
En un bus *serie* la información se transmite bit a bit por un solo conductor (dos en el USB), mientras que en un bus *paralelo* esto se realiza mediante un cierto número de conductores para transmitir simultáneamente *n* bits. Para más detalles eléctricos es conveniente ver la sección 1.10.  
Cada dispositivo se identifica y selecciona por un número que es su *dirección* (el número de interno en los teléfonos). Entre dos dispositivos comunicados se establece un *enlace* o camino entre ellos.

### Estructura de un bus paralelo: ###
En un bus paralelo la selección se realiza mediante *líneas de dirección*, y la transmisión de datos usando *líneas de datos*, cuyo número (8, 16, 32, 64,128) se define el *ancho* del bus.
La fig. 1.79.c ilustra estas líneas en un bus ISA que interconecta una UCP 8088, su memoria SLOT para tarjetas de interfaces para periféricos.


![imagen 1.79.c](1.79.c.jpg)

Las líneas de dirección y datos se indican como caminos grisados. Se supone que el 8088 envía una dirección (que llega a todos los dispositivos) para seleccionar una celda de memoria con orden de lectura (línea de control L/E=1). Sólo responde la memoria enviando un byte por las líneas de datos. Es factible que un mismo conjunto de líneas primero se use para direccionar y luego para transmitir.  
Las *líneas de control* transmiten señales SI/NO para: peticiones (por ejemplo la línea IRQ solicita interrupción), órdenes (por ejemplo línea L/E para leer/escribir), avisos, confirmaciones y tipo de información enviada. Así controlan el acceso y la ocupación de las líneas de dirección y datos, y de hecho *indican cuando son válidos los valores* presentes en esas líneas.  
Si el bus es *sincrónico* (como el ISA o el PCI) una de las líneas de control designada "clock" o Mhez recibe pulsos regularmente espaciados en el tiempo, generados por un oscilador, los cuales marcan los instantes en que se pueden activar o desactivar líneas de control, o enviar direcciones o datos.  
En un bus *asincrónico* a partir de la activación de una línea por un "master" en un instante no regido por un clock, se sucede en respuesta la activación de otra línea por el "slave", a la cual puede seguir la activación de otra, etc.
Así la activación de una línea depende de la activación de otra, pero no del clock: cada nuevo evento sólo es respuesta del evento anterior al mismo. Este bus (como el SCSI) es más complejo de implementar, pues los dispositivos deben ser auto-temporizados.  
Una *transacción* en un bus presenta dos fases: envío de una dirección seguida del envío de datos.   
La velocidad de transmisión (Mbytes/seg) *"ancho de banda"* de un bus está limitada por su longitud y por el número de dispositivos conectados al mismo. Su causa es la inercia en la velocidad de cambio de las señales eléctricas digitales debido en esencia al tiempo de carga/descarga de capacitadores parásitos distribuidos a lo largo de las líneas de un bus, cuyo efecto aumenta con cada dispositivo conectado. Por tal motivo el bus local vinculado al procesador es de corta longitud frente a buses de E/S como el ISA, el SCSI o el USB, que por lentos permiten longitudes mayores y más dispositivos conectados.
### Jerarquía de buses ###
Muchos computadores se hicieron con un único bus, como ilustran las figs 1.79.c, 1.67 y 1.72 para ser convertidos por los dispositivos arriba indicados y los controladores de ADM. Pero a medida que crece el número de dispositivos conectados aumenta la puja de los mismos por usar el bus, produciéndose "cuellos de botella". Si bien puede mejorarse la velocidad de transferencia (como ser con más líneas para datos, realizando transferencias de datos mediante grandes bloques de bytes sucesivos, arbitrajes rápidos y utilización de buffers) para disminuir el tiempo de ocupación por dispositivo, dicha velocidad se ve limitada entre cosas por la capacidad parásita que agrega cada dispositivo. Ello no se condice con las cada vez mayores exigencias de velocidad de dispositivos para gráficos y videos.  
A los efectos de descongestionar el tráfico que tiene lugar si se usa un solo bus, hoy día los computadores presentan una *jerarquía de buses* de distinta velocidad y longitud, que por un lado minimiza la competencia por el acceso a memoria. Por otro permite conectar muchos periféricos reduciendo conflictos y tenerlos fuera del gabinete. Así (fig.1.80) el bus que une el caché L2 (sección 1.12) con la UCP concentra todo el tráfico, que cuan el mismo no existía iba de memoria principal a la UCP por el bus que los une. Este ahora queda más despejado para transferir por ADM (sección 1.10) datos entre periféricos y memoria.
Así mismo, las interfaces de los periféricos no se conectan al bus del sistema PCI, sino a otros **buses de E/S** como el ISA, USB, SCSI, de modo que al PCI solo están conectados los adaptadores inteligentes o puentes ISA/PCI, USB/PCI, SCSI/PCI que aíslan al PCI de un *número grande* de periféricos de *velocidad dispar*, conectados a dichos buses. Esto permite conectarlos con buses de mayor longitud (SCSI, USB) fuera del gabinete, sin ocupar el número limitado conectores ("slots") existentes. También dichos adaptadores evitan conflictos en relación con la configuración de IRQ y ports de las interfaces (sección 1.11 y 1.10).  
El nivel más alto de la jerarquía está constituido por el "local bus" que sale de la UCP, de muy alta velocidad y corta longitud, con *muy pocos y veloces* dispositivos conectados a él. Como estos operan con velocidades altas y no muy dispares, es recomendable que el bus sea sincrónico, por ejemplo para transferir entre memoria y el cache L2 (que en un Pentium actual están conectados por un bus interno dedicado). Mediante un chip "puente" este bus se comunica con el bus PCI, al cual están conectados los buses de E/S citados, a los que se conectan los restantes componentes del computador (fig.1.80).  
El bus PCI (fig.1.80), está ubicado en una jerarquía intermedia entre los buses ultrarrápidos que salen de la UCP y los buses de E/S. Por el pasan datos desde o hacia la UCP, la memoria, y dispositivos periféricos.  
Debe mencionarse que el denominado port acelerado para gráficos **(AGP)**, que funciona a los Mhz de la UCP, está pensado como intermediario para las transferencias entre memoria y la tarjeta de video, de modo que se efectúen a máxima velocidad (528 Mbytes/seg para 2X, y 1GByte/seg para 4X, siendo la velocidad máxima del PCI cercana a los 100 Mbytes/seg), a través del chip que contiene al puente PCI.

## ¿Cómo funciona el bus PCI? ##

El bus **PCI** (*Peripheral Component intenconnect*) creado por Intel, por su independencia del 
procesador y subsistema de memoria usados, por su versatilidad de conexionado con otros buses
para periféricos existentes (ISA,SCSI,USB, etc.), por sus 64 líneas para datos, y por su característica
"plug'n play" (**PnP**), se ha constituido en un estándard para los fabricantes de motherboards.  
Buses como el VESA local bus para transferencias rápidas en aplicaciones gráficas, por estar directamente
conectando al bus local de la UCP dependía del mismo. En cambio el PCI es independiente, es estándard.  
Es un bus sincrónico de 66(ó 33) MHz: su línea "reloj" durante los 15nseg que dura cada uno de los 66 millones 
de pulsos (ciclos) que ocurren por segundo, permanece durante 7,5nseg en 0 volts y entre los 7,5nseg en 3,33
volts, marcando instantes en que se pu7eden enviar datos, direcciones, o comandos(fig.1.80.b).
Si se trabaja con 64 líneas de un PCI, se pueden enviar juntos 8 bytes en cada ciclo, por lo que
teóricamente se podría enviar 8 bytess 66 millones de veces por segundo, o sea 66x8=528 Mbytes/seg,
que no es suficiente para usar el PCI como un bus para leer o escribir datos en memoria.  
En promedio un bus PCI opera a 100 Mbytes/seg., pues entre otras cosas parte de los ciclos se usan
para preparar las transferencias, sin que haya transmisión efectiva de datos.  
Para comparar, el bus ISA es de 8,33 MHz y tiene 16 líneas, lo que en teoría de 8,33x2 = 16,66
Mbytes/seg.; y el EISA de 8,33 MHz y 32 líneas alcanzaría los 8,33x4 = 33,32Mbytes/seg.  
Dado que antes de transferir se requiere en cada lectura a través del PCI ocupar 2 ciclos preparatorios, en 
realidad debe estimarse una velocidad promedio de transferencia de dataos bastante menos que la calculada,
la cual aumenta a 266 Mbytes/seg cuando se transfieren en ráfaga ("burst") muchos bytes consecutivos.
![imagen 1.80](1.80.jpg)  
A diferencia de otros buses, en el PCI un "burst" no tiene longitud fija: continúa hasta que uno de los 2
dispositivos intervinientes indique fin de transferencia, o si otro de alta prioridad debe usar el bus.  
El bus PCI se comunica mediante el **puente PCI** o controlador PCI (fig. 1.80) con el bus local que va a la
UCP, y con el bus memoria que va a ésta. 
En el chip que contiene al puente PCI también se encuentra el **árbitro del bus PCI**, y el controlador de
memoria, que transforma las órdenes hacia la memoria DRAM en una secuencia de señales para ella (Sección 1.4).  
Dicho puente, conforme a su nombre, *permite la comunicación entre dos de los tres buses citados por vez*.
Además contiene buffers inteligente, para el re-envío de datos que temporalmente guarda según
distintas necesidades. Así permiten que la UCP y el puente trabajen en paralelo de manera que se 
intercambien datos entre dos dispositivos del PCI mientras la UCP direcciona memoria. También detecta
si se realizan sucesivas L/E que no sean en ráfagas a posiciones consecutivas de memoria (por ej. a la
memoria de vídeo), cuyo caso junta en un buffer los datos llegados al puente en forma aislada, y 
los reenvía en ráfaga a máxima velocidad de transferencia, compatible con las necesidades de la UCP.
Al encenderse el equipo, el puente PCI puede configurar automáticamente ports e IRQ correspondientes
a distintos periféricos, para lo cual rastrea dispositivos conectados al bus PCI, y luego asigna una
única dirección dase para sus ports, y un determinado nivel*n* de IRQn para interrumpir.

Al bus PCI (fig. 1.80) están conectados al **puente ISA** (el cual también conecta al PCI la electrónica
IDE del rígido) y los adaptadores inteligentes para los uses USB, SCSi, otro PCI, así como para
conexión a red. Pueden conectarse ap PCI a través de zócalos de expansión interfaces de periféricos, 
los cuales por su velocidad no pueden conectarse al ISA. Se trata, pues, de un bus intermediario
entre el bus local y otros buses. También puede existir en la motherboard conectados al PCI apartadores 
de vídeo para manejar monitores. El bus PCI también puede dar apoyo en multiprocesamiento,
siento que a un bus PCI puede conectarse otro PCI (PCI a PCI) mediante otro puente.

De los dispositivos conectados al PCI incluidas las interfaces, sólo 2 por vez pueden comunicarse a 
través del mismo: el *iniciador* o bus master (**M**) -al cual un árbitro le otorgó el control del bus entre
varios dispositivos que pujaron por dicho control para ser **M**- y el *target* (destinatario) o slave (**S**).  
El  arbitraje si bien se realiza sincronizado por el reloj el bus, *no requiere la utilización de ciclos extras*,
dado que tiene la ventaja de que se efectúa paralelamente al uso del bus por otro **M**. Para tal fin, cada 
posivle **M** (incluso la UCP) se comunica con el árbitro mediante dos líneas dedicadas (fig 1.80.a).

![imagen 1.80.a](1.80.ajpg)  
Una señal de requerimiento (REQ#) sale de cada posible **M** hacia el árbitro,(GNT#) va en sentido opuesto.
Se busca beneficiar a las transferencias largas (modo ráfaga),aunque el árbitro puede obligar al **M** a
ceder el bus en el próximo ciclo si existen prioridad. Dicho **M** puede ganar el bus para una nueva transferencia 
si no llegaron otros requerimientos al árbitro.  
Puede establecerse que el primer **M** en solicitar es el primero en ganar el bus, o una cesíon cíclica, o 
prioridad (por ej. el que opera en modo ráfaga tenga prioridad sobre otro en modo simple).
Un bus PCI presenta 64 (ó 32) líneas A/D (adress/data) que en un ciclo pueden usarse para
direccionar un dispositivo PCI, y en el siguiente(s) para transferir datos ahorrando espacio.

Las órdenes (tipo de transacción) se dan por códigos de 4 bits en 4 líneas designadas C/BE
(Comando/Byte Enable). El código del comando se envía por estas 4 líneas en el mismo ciclo en
que una dirección se pone en las líneas A/D. En los ciclos en que por las líneas A/D se envían
datos, por las 4 líneas citadas mediante otra combinación binaria se indica cuáles de los 8 bytes que
van por las 64 líneas A/D deben seleccionarse.  
Suponiendo que un **M** gana el control del bus, y que el mismo se efectiviza más tarde en el ciclo 1 
(fig. 1.80.b), dicho **M** activa (hasta el inicio de la última fase de la transacción) la línea Frame de 
transacción en curso, y envía una dirección del inicio (de memoria o de un port) a través de las líneas 
A/D, a la par que ordena una transacción mediante un código en las 4 líneas C/BE#. Dicha dirección
llegará a todos los dispositivos del bus. El **S** que reconoce como una de sus direcciones esa dirección, 
la guardará junto con la orden. Ejemplos de las 16 transacciones que ordena un comando son: 
- *lectura/escritura de un por* (E/S),
- *lectura/escritura de la memoria*,
- *secuencia intA*: envío de la dirección del vector interrupción a la UCP (Unidad 3 de esta obra),
- *lectura/escritura de configuración*: cada dispositivo dispone de 256 bytes para configurarlo en la
   inicialización del sistema ("espacio de la configuración") que otros dispositivos pueden leer activando
   la línea IDSEL Dicho espacio puede ser leído por un Sistema Operativo para determinar
   qué dispositivos están conectados, y así brindar el servicio "plug ´n play" (conectar y operar).

Si es una transacción de *escritura*, en el ciclo 2 (fig.1.80.b), el **S** que en el ciclo 1 guardó la dirección enviada activará la línea Devsel (Dispositivo seleccionado),con los cual el **M** que direccionó se entera que **S** recibió la dirección, y **S** también activará Trdy (target preparado para recibir).
Las líneas se activan en 0 volts. El **M** también activará la línea Irdy (Iniciador operando) y enviará por las 64 (o 32) líneas A/D el dato a escribir, a la par que codificará en las 4 líneas C/BE cuáles de los 8 (ó 4) bytes que envía por A/D deben ser considerados.


![Figura 1.80.b](/figura-1-80.b.jpg "Figura 1.80.b")

Al comenzar el ciclo 3 (flanco creciente del pulso correspondiente) el buffer del **S** (suponiendo que sea el puente PCI u otro chip) habrá tomado los datos de las líneas A/D sin esperar que se escriban en el destino final (como ser la memoria principal) de modo de no demorar la transferencia de los datos que **M** puede enviar en el ciclo 3.Para ello durante este ciclo **M** mantiene activadas a Frame e Irdy, a la par que por A/D envía los nuevos datos a escribir y por C/BE indica los bytes que deben ser considerados. El **S** también seguirá con Devsel y Trdy activadas, indicando que están preparados para tomar nuevos datos por A/D. De existir algún problema (buffers llenos en **M** o en **S**) se desactivarán las líneas Irdy ó Trdy. Entonces hasta que ambas no vuelvan a estar activas no se transmitirán datos durante uno o varios ciclos ("wait states").  
El **M** se desentiende de la manera cómo el **S** o los bloques vinculados al mismo (como el controlador de memoria) van incrementando la dirección de escritura a partir de la dirección de inicio.
En el ciclo siguiente al que **M** terminó de enviar todos los datos desactiva Frame e Irdy indicando que deja el bus libre para el **M** que ganó el control del bus, con lo cual el **S** desactiva Devsel y Trdy.
Las líneas de control citadas, son compartidas por todos los dispositivos del bus.  
Si la transacción es una *lectura* el ciclo 1 será igual (salvo la información que se envía por las líneas A/D),pero recién en el ciclo 3 ocurrirá lo que sucedió en el ciclo 2 de la escritura, dado que **S** no puede enviar datos hacia **M** por las líneas A/D (aunque **M** active Irdy),siendo que **S** está diseñado para que al inicio de una lectura deba perderse un pulso para invertir el sentido en que transmiten estas líneas. Por lo tanto la velocidad en una lectura resulta menor que en una escritura.

## **¿Cómo funciona la conexión Interfaz-Bus SCSI para periféricos?**

El **SCSI**(siglas de Small Computers System Interface)no es un bus como el bus local, el PCI, el ISA u otros que consisten en un conjunto de líneas conductoras de corta longitud, fijos en una placa .Se trata de un bus exterior al gabinete de un computador,*uno de cuyos extremos se conecta al bus PCI* mediante un adaptador-controlador SCSI.A éste se pueden encadenar por conexionado "daisy channel" (fig.1.81) hasta 7 periféricos, prolongándose con cada periférico agregado la longitud del bus (máxima 6 mts.).Cada conjunto de cables que conecta un dispositivo con el siguiente es un tramo del bus SCSI que se conecta con el tramo anterior. La salida del último dispositivo debe terminar en resistencias o en un circuito según la longitud y el tipo de SCSI.  
Este bus surgió en los 80 para conectar periféricos en Macintosh sin usar zócalos. Es apto para conectar con buena performance unidades de CD, discos duros, cintas, scanners, RAID, y multimedia.  
El original SCSI-1 supone 8 líneas para datos y velocidad de transmisión dentro del bus de hasta 3 Mbytes/seg. En los 90 apareció la SCSI-2 para 16 ó 32 líneas, y con hasta 20 ó 40 Mbytes/seg.

![Figura 1.81](/figura-1-81.jpg "Figura 1.81")


Normalmente el  bus SCSI funciona en forma totalmente asincrónica, pudiendo hacerlo sincrónicamente durante la fase de transferencia de datos. Esto debe acordarse entre los dos dispositivos que se han comunicado. Se considera al adaptador SCSI a PCI como una unidad SCSI, por lo que quedan disponibles sólo 7 unidades para conectarse al bus SCSI. Cada unidad tiene una dirección (**ID**) entre 0 y 7 configurable mediante jumpers.  
Es factible conectar a un bus SCSI por ejemplo 4 adaptadores SCSI, los cuales pueden conectarse a 4 computadoras, que así comparten dicho bus y pueden intercambiar información entre sí.
Si bien lo común es que la información se transfiera entre memoria principal y algún periférico vinculado al bus SCSI (a través del bus PCI y del adaptador SCSI), *el bus SCSI permite intercambiar información entre las unidades conectadas al mismo.* 
Así pueden comunicarse un disco rígido con una unidad de cinta, sin pasar por la memoria principal y *sin la intervención de la UCP* ejecutando programas.

Cualquier unidad SCSI puede tomar el control del bus SCSI actuando como iniciador (**M**) y enviar por el bus la dirección de la unidad "target" (**S**) con la que quiere comunicarse (para enviarle comandos y transferir datos. La línea de control BSY del bus indica si éste está ocupado, siendo que sólo se pueden enviar datos dos dispositivos por vez. Las direcciones, comandos y datos viajan por las mismas 8 líneas en distintos momentos.  
El bus SCSI permite por ejemplo que si el adaptador SCSI/PCI (**M**) le envía a la unidad SCSI de disco rígido (**S**) la orden de acceder a un sector para leerlo,
mientras el cabezal se posiciona **S** libera el bus, a fin de que mientras dura el tiempo de acceso al sector, el bus pueda ser usado por otras unidades. Cuando la unidad de disco puede transmitir la información pedida, pide seleccionar el adaptador y se la envía. El bus SCSI presenta 9 líneas de control:

BSY (Busy): indica bus ocupado.

SEL (Select): usada por un **M** para seleccionar un destinatario **S**, o para que éste seleccione al que fue su **M** para reconectarse a él en una fase de reselección (en cuyo caso además debe activarse la línea I/O).

I/O (Input/Output): indica en que sentido se transfiere los datos.

C/D (Control/Data): para indicar si por las 8 líneas de datos pasan códigos de control (órdenes, status, o mensaje) o datos.

REQ (Request): el **S** seleccionado solicita que se transfieran datos de **S** hacia **M** o en sentido contrario.

ACK (Acknowledge): el **M** acepta que datos sean enviados de **S** a **M** o en sentido contrario.

MSG (Message): generado por un **S** para indicar que la información que se transmite es un mensaje.

ATN (Attention): cuando un **M** tiene un mensaje para su **S**.

RESET: resetea todos los dispositivos del bus, que pasa a la fase de bus libre.

La actividad del bus se da en una secuencia de hasta 8 fases, dado que al arbitraje puede seguir una fase de selección o reselección. Luego se pueden repetir *n* veces las últimas **4** fases agrupables en una:

1. *Bus libre*: cuando no hay ningún dispositivo usando el bus. Se detecta si BSY y SEL no están activas.
2. *Arbitraje descentralizado*: si uno o más de los 8 dispositivos quieren ganar el control del bus y ser **M**, activan BSY y colocan en las 8 líneas de datos su ID (cada una activada sola es un ID distinto). Cada uno lee estas líneas para ver si hay un ID más alto; de ser así deja de activar BSY. El ganador activa SEL.
3. *Selección*: el **M** selecciona su **S** activando 2 de las líneas de datos: la de su ID y la del ID de **S**. El **S** debe activar BSY al detectar su ID (pasado un lapso el bus es libre), indicando que la operación puede hacerse. 
4. *Reselección* (opcional): Permite que un **S** lento libera el bus (ejemplo anterior del acceso a la
unidad de disco), y cuando termina la parte lenta de la operación ordenada se vuelve a 
conectar con su iniciador **M**.
5. *Ordenes*: El **M** transmite al **S** por las líneas de datos una o varias *ordenes encadenadas.
Mediante REQ seguido de ACK se van transmitiendo byte a byte las ordenes a ejecutar.
6. *Transferencia*: Desde una unidad a otra según sea, activándose REQ seguido de ACK con cada
byte transmitido por las líneas de datos. Las líneas S/D y BSY deben estar activas.
7. *De estado*: Para que el **S** solicite al **M** enviar información acerca del desarrollo de la transferencia.
8. *Mensaje* : Para que **S** solicite enviar a **M** uno o más mensajes, como ser de desconexión o de 
orden cumplida, con lo cual se vuelve a la fase de bus libre.

### ¿Cómo funciona el universal serie Bus (USB)?

El número de zócalos en el bus ISA o PCI para insertar tarjetas interfaces de periféricos que se
quiere agregar es limitado. Si bien con la tecnología PnP se evita configurar mediante muchas llaves o
puentes el valor de *n* de un IRQn, se requiere igualmente para tal fin abrir el gabinete.  
Por otra parte, el ISA o el PCI por ser buses de transmisión paralelo necesitan protección por las posibles 
interferencias entre sus líneas, tienen grandes limitaciones en su longitud, ocupan mucho lugar en 
la "mother" y requieren conectores grandes y relativamente costosos. Ello se justifica para el envío de 
datos desde o hacia el procesador y la memoria, cuando son necesarias altas velocidades de transmisión
Pero en la PC para el envío de datos desde periféricos no muy rápidos o lentos hacia sus ports o en 
sentido inverso, técnicamente no se justifica el uso de dicos buses, El ISA ya obsoleto, subsiste en
razón del gran número de usuarios que no tienen periféricos y tarjetas adquiridos para ese bus.  
En cambio, un bus serial usa sólo 2 líneas para enviar datos, direcciones y control, y otras 2 con +5
y 0 volts para los periféricos. Así resulta pequeño, económico y apto para computadores pequeños. 
Asimismo, a medida que surgen nuevos dispositivos multimedia hacen falta más ports por cada 
uno de ellos, y hay que resolver conflictos resultantes de compartir líneas IRQ. Como se verá un
bus serie permite compartir mejor y disminuir el número de puertos y líneas IRQ requeridas.

Para conectar periféricos de baja velocidad (teclado, mouse, scanner, joysticks, parlantes, cámaras,
teléfonos digitales, etc.) y de velocidad media (modems, unidades de CD, impresoras) en los años
90 las principales empresas de hardware y software acordaron crear un bus estándar denomidado 
**USB** (Universal Serial Bus) que los fabricantes de motherboards incluyeron desde entonces en
ellas, y que entre otras cosas permite:
- Conectar dispositivos mientras el equipo está funcionando, sin usar puenteadores (jumps) ni
microllaves para configurarlos, sin reconfigurar el sistema, y sin tener que abrir el gabinete.
- Instalar hasta 127 dispositivos en un solo equipo, mediante cables de 4 conductores, con
conectores que evitan errores de conexionado.
- Facilitar la conexión de dispositivos que operen en tiempo real (teléfono, audio).

A diferencia del SCSI, el USB no permite transferir directamente datos entre periféricos conectados a él.
Cuando se conecta un nuevo dispositivo al USB con el computador funcionando, el adaptador USB/
PCI (figs. 1.80 y 1.82.a) detecta el evento y se produce interrupción que llama al sistema operativo. 
La subrutina llamada lee en el dispositivo insertado sus características, tipo de dispositivo y la velocidad 
de transmisión que utiliza. Si es compatible con el bus USB le asigna una dirección entre 1 y 127, 
y ordena escribir ésta en los registros de configuración del dispositivo, Los dispositivos sin configurar
tienen escrito por defecto dirección cero para poderlos direccionar la primera vez que se conectan.

Se distinguen dos tipos de software ejecutados por la UCP: el "Client Software" correspondiente a un
dispositivo, y el USB System Software, que es software de un sistema operativo que soporta al USB.
Para el USB existente dos clases de dispositivos: las *funciones* (periféricos), y los *hubs* (concentradores).

El bus "raíz" del USB inserto en la "mother" está conectado en uno de sus extremos (figs. 1.80 y
1.82.a) al **Controlador-Adaptador** USB/ PCI (**CAUSB**) *inteligente*, vinculado al bus PCI y que forma 
parte de un chip de la "mother". Este adaptador, que tiene software asociado, permite regular
velocidades de transferencia hasta de 1.5 Mbytes/seg. para dispositivos lentos, hasta 12 Mbytes/seg 
para veloces, y hasta 60 Mbytes para más veloces.  
Este bus "raíz" en su otro extremo tiene por lo menos un conector USB para enchufar un dispositivo de
E/S, o un cable de expansión, o un hub USB, conforme a una topología de conexionado tipo árbol
irregular, con su raíz tronco en la "mother". usando hubs se conectan hasta 127 dispositivos.

![Figura 1.82.a](/figura-1-82a.jpg "Figura 1.82.a")

Un **hub** por un lado se conecta al bus "raíz" o a otro hub, y por otro lado
presenta varios conectores hembra, para concentrar el conexionado de 
cables USB que se dirigen hacia él como centro de una conexión "estrella"
(al igual que los rayos de una rueda que van hacia su soporte central),
siendo que en el otro extremo de cada uno de esos cables hay un
dispositivo, u otro hub. Así se logra ampliar el número de dispositivos
que se pueden conectar al USB, los cuales funcionan paralelamente y en
forma independiente.

El USB *no tiene líneas para direcciones o control*. Como en una red, por las
dos líneas de información se transmiten uno tras otro bits de control, de 
direcciones y de datos, formando **paquetes** de bits. Se usan de dos líneas
para rechazar el ruido. Cada bit viaja codificado en NRZI (fig 1.82.b).
El **CAUSB** decide, auxiliado por el software, cuál dispositivo puede
enviar o recibir datos a través del conexionado. Para ello envía, cuando
el bus no es utilizado, un paquete de bits que llega a todos los
dispositivos, en forma directa o a través de hubs que lo re-envían, para
que el dispositivo elegido detecte que debe enviar o recibir datos. O sea
que el **CAUSB inicia todas las transferencias**, para lo cual accede a la 
lista de transacciones preparadas para un software, y **las traduce en paquetes** que envía por el bus.

Los hubs complementan este proceso, dado que cada uno tiene incorporada inteligencia para:
- Detectar, en sus conectores (ports[^capitulo113Nota1]), la conexión/desconexión de dispositivos y configurarlos.
- Controlar transferencias de datos y órdenes vinculadas a los dispositivos conectados a él. 
- Proporcionar tensión de alimentación a dispositivos vinculados al mismo.
- En el caso de un Hub USB 2.0, intercambiar información a alta velocidad con el adaptador
USB/PCI o con otro hub, según las normas USB 2.0 que permiten transferir a mayores velocidades.

Se requiere que los dispositivos puedan disponer de un USB Peripheral Controller, y que con los hubs
contengan un USB Hub Controller, que contienen las siguiente funciones circuitales:
- *Transceivers*: para conformar la información binaria que viaja por el conexionado.
- *Serial Interface Engine* (SIE) convierte en serie la información y la transcodifica la información binaria
nativa del dispositivo en codificación NRZI que viaja por el bus (y viceversa), a la par que se 
encarga de concretar protocolos, detectar errores, y de secuenciar los paquetes de información.
- *Buffers* tipo FIFO, para recibir y enviar datos, cuya transmisión puede ser masiva o isócrona.
- *Functiones de monitoreo* del estado del controlador y los buffers.
Tanto en memoria principal como en los dispositivos se requieren buffers para transacciones pendientes.

Los movimientos de datos que ocurren a través del USB (u otros buses) se originan en el software,
cuando desde un programa se necesita transferir datos de memoria a un dispositivo periférico o en 
sentido contrario. Para tal fin se debe pasar a ejecutar un "client software" (**CSW**) que "ve" a cada
dispositivo conectado al USB como una entidad lógica identificable por un número, denominada
"*función*". Los sistemas operativos contienen software para manejar el USB: el USB "System
Software" (**SSW**) para el cual una "función" es un "USB logical device". El CSW se comunica con el 
SSW -vía su USB Driver interface (**USBD**)- para mover datos entre memoria y una "función",
generando una solicitud denominada I/O request packet (**IRP**).  
Una vez que dicho movimiento se ha realizado, el CSW recibe una notificación del software driver
asociado al CAUSB, a fin de que pueda acceder por ejemplo a los datos transferidos a memoria.
Este driver convierte cada IRP en transacciones que debe concretar el **CAUSB** mediante paquetes, y 
lleva una lista de transacciones a realizar así como de su estado de progreso (dada por el **CAUSB**).  
En el USB cada *transferencia* de datos entre memoria principal y un dispositivo (pasando por el 
**CAUSB**) consta de una o más *transacciones*. Cada transacción puede realizarse dentro de lapso de 
una unidad de tiempo de 1 mseg denominada *frame*, mediante el envío de uno o varios paquetes.

[^capitulo113Nota1]: Acá el sentido que se da a "port" no es de un registro (como en la interfaz de un periférico). Si no el de un punto de conexionado.


Se dan 4 tipos de transferencias, solicitadas mediante el paquete “token” (indicación) correspondiente:

 -*Isócrona*: se transmite una secuencia de paquetes de tamaño fijo, a intervalos regulares que dependen de la aplicación en tiempo real que se trate4. Así se garantiza  velocidad de  transferencia constante, como se requiere en telecomunicaciones (por ejemplo, para video, micrófonos o telefonía digitalizados).
 
-*Masiva* (bulk): las transmisiones de los paquetes no son periódicas, pero se efectúan a altas velocidades, a fin de enviar rápidamente importantes cantidades de datos (caso de impresoras, scanners y transmisión de imágenes corrientes). Estas   transferencias pueden realizarse entre dos isócronas.

-*Interrupt data*: Dado que el USB no reconoce interrupciones, como la usada para manejar el evento de apretar / soltar una tecla de teclado, si se conecta este al USB se requiere que una subrutina del sistema operativo cada 50 mseg pregunte si sucedió tal evento a fin de que se transfiera el código de la(s) tecla(s).

-*De Control*: típicamente son transferencias entre el **CAUSB** y un dispositivo del bus, para leer en los registros de éste información necesaria para su configuración (setup).

Las características de un dispositivo que interesa determinar y registrar en su configuración automática son: identificación del fabricante, clase de dispositivo, y capacidad de manejo de potencia. Cuando se configura un dispositivo que se conecta al bus, el SSW debe determinar si es compatible con el USB, para lo cual examina el descriptor del dispositivo localizado en el mismo, a fin de determinar por ejemplo si su velocidad de transferencia es compatible con el bus. Luego debe verificar si el tiempo máximo para realizar una transacción no supera un milisegundo (frame).

El CSW se vincula con una función (dispositivo) considerándola compuesta de una hasta 16 subentidades lógicas, cada un denominada “*endpoint*”, identificables con un numero de 4 bits en los paquetes “token”. Este número se encuentra en el campo ENDP que sigue al de la dirección de 7 bits del dispositivo (ADDR). Ambos números (fig. 1xxx) son necesarios para identificar el “endpoint”, y se asignan en el momento en que el dispositivo se conecta al USB.  
Por ej. la unidad de disquete es de entrada/salida, puede ser vista por el CSW como dos endpoints del USB con los cuales se comunica a través de dos “*pipes*” (canal lógico): uno para entrada y otro para salida, dado que un endpoint solo puede enviar o bien recibir datos, o sea es unidireccional.  
Un endpoint presenta propiedades que definen el tipo de transferencia que puede hacer con el CSW, como ser:

-Frecuencia de acceso al bus y demoras máximas permitidas en el pasaje por el bus.

-Velocidad de transferencia requerida.

-Tamaño máximo de paquete que el endpoint puede recibir o transmitir.

-Tipo de transacción que realiza.

-Manejo de errores requerido.

Cualquier paquete que se envía (ver más abajo) debe comenzar con un campo SYNC de 8 bits para sincronismo seguido por otro, el PID (Packet Identification) de (bits, 4 de los cuales codifican entre otros: 

SOF (Start Of Frame): comienzo de envío de paquetes.

ACK (Acknowledge): acuse de datos recibidos sin errores por el **CAUSB** o un dispositivo. 

NACK (Not Acknowledge): señal de un dispositivo al **CAUSB** que no pudo recibir o transmitir datos.

IN: enviar datos desde el dispositivo.

OUT: enviar datos hacia el dispositivo.

SETUP: configurar dispositivo.

DATA0: bloque de datos en orden par.

DATA1: bloque de datos en orden impar.

STALL: enviado por un dispositivo, indicando que no puede recibir o transmitir datos.

La mayoría de los paquetes termina en un campo **CRC** (Cyclic Redundance Code) que sirve para detectar errores en la transmisión de un paquete, en cuyo caso se retransmite el paquete.
Las transferencias isócronas no admiten retransmisiones por errores en los datos recibidos, dado que no hay tiempo para que el receptor emita paquetes ACK o NACK, por lo que debe decidir luego que hacer. Existen paquetes de indicación (“token”), paquetes de datos, y paquetes de dialogo (“handshaking”).

El paquete SOF sirve *para marcar tiempos*. Es emitido cada mseg por el **CAUSB** hacia todos los dispositivos, incluyendo los hubs, como si fuera un reloj sincronizador. Luego del mismo pueden enviarse otros paquetes, dentro del mseg. Así definido, entre un paquete SOF y el siguiente. Al PID le sigue un campo de 11 bits para indicar número de frame, al cual le sigue un CRC (5 bits).
Dicho número interés en especial a dispositivos isócronos. Un SOF no exige paquete de respuesta; solo marca tiempos. Su formato es:
| SYNC (8) | SOF (8) | Nro,(11) | CRC (5) |
|----------|---------|----------|---------|
Los paquetes “token” cuyo PID es IN, OUT o SETUP intervienen en una transferencia de Control para enviar datos a un endpoint de un dispositivo recién conectado. El endpoint que recibe un paquete SETUP, luego puede recibir datos y responder con un ACK si fueron correctos. Su formato es:
| SYNC (8) |  PID (8)| ADDR (7) | ENDP (4) | CRC (5) |
|----------|---------|----------|----------|---------|
Los paquetes de datos (siguen a paquetes “token”) tienen DATA como PID, y a este campo le sigue otro con los bytes transmitidos (de 0 a 1023), y luego otro para CRC de 16 bits. La transmisión o puede ser isócrona, masiva o interrupt data. En cualquier de estas una transferencia supone un o más transacciones DATA. Para las transferencias tipo Interrupt Data las normas USB no establecen formatos específicos, siendo 64 y 8 bytes la máxima cantidad de datos a transmitir por paquete en full-speed, y en low speed, respectivamente. En el momento de la configuración del dispositivo el SSW determina dicho máximo, el cual es  mantenido.
| SYNC (8) |  DATA (8)|      (1 a 1023 bytes de datos)            | CRC |
|----------|----------|-------------------------------------------|-----|
Los paquetes de dialogo ACK y NACK se transmiten solo con el campo PID (además del SYNC):
| SYNC (8) |  ACK (8)| 	
|----------|----------|     
        

| SYNC (8) |  NACK (8)|
|----------|----------|
Según se describió antes, el USB tiene dos líneas en lugar de una para enviar cada bit de información. En cada instante se sensa la diferencia de tensión entre esas dos líneas (*tensión diferencial*) a fin de compensar los ruidos electromagnéticos que pudieran generarse. Cuando ocurre un ruido este afecta por igual a las dos líneas, o sea que ambas durante  cortos lapsos pueden subir o bajar igual valor de tensión en relación a masa, pero estas variaciones no modifican el valor de la diferencia neta de tensión entre los dos conductores.  
La información se envía en el código vinario **NRZI** (Not Return Zero Inverted), que tiene la ventaja de que el ritmo fijo con que se envían por el bus unos y ceros (frecuencia reloj, o “clock”) está inserto en la información, por lo el receptor no necesita una tercer línea para identificar cuando hay uno o cero.

![imagen 1.82.b](1.82.b.jpg)

En NRZI (fig. 1.82.b) los bits de la información binaria que se quiere codifican en NRZI se van generando igualmente espaciados en el tiempo (“bit time”), siendo que una sucesión de ceros hace que la señal NRZI vaya cambiando con cada cero, mientras que una sucesión de unos hace que la señal NRZI no cambie. Un cero debe insertarse luego de cada 6 unos consecutivos (“bit suffering”) para forzar una transacción de nivel. Este cero es reconocido y descartado por el receptor cuando pasa de NRZI al código binario originario.
### USB 2.0
La descripción desarrollada corresponde a los buses USB que cumplen con las normas USB revisión 1.1. La norma 2.0 define USB con velocidades de transferencia de hasta 60 Mbytes/seg con lo cual pueden conectarse dispositivos de video y de almacenamiento, entre otros. Se establecen 3 tipos de dispositivos:
-Low Speed (LS): hasta 10.000 Bytes/seg (teclado, mouse, joysticks, realidad virtual) 
-Full Speed (FS): de 50.000 Bytes/seg a 1 Mbyte/seg (audio, micrófonos)
-High Speed (HS): de 3 a 50 Mbytes/seg (video, almacenamiento)

USB 2.0 permite aprovechar dispositivos y hubs USB anteriores,pero para funcionar en 2.0 se requiere un **CAUSB** para 2.0 y hubs 2.0 , aménde cables de conexionado para operar en **HS**.  
Este genera un paquete SOF cada 125 useg (*un microfame* = 1 uframe)que llega a los hubs, y éstos por cada 8 de éstos generan un SOF cada mseg (125 seg x 8 =1 mseg) que llega a *todos* los dispositivos FS o LS.Para éstos todo sucede en esencia como si trabajaran con la norma 1.1, siendo cada hub una interfaz entre el adaptador y los dispositivos. Un dispositivo *HS* conectado a un hub USB 2.0 es como si estuviese conectado al **CAUSB** 2.0.  
Cuando el **CAUSB** 2.0 en uframe determinado quiere ordenar una transacción (fig. 1.82.c), como ser que un dispositvivo "X" low o full le envie (IN) datos al **CAUSB** 2.0; luego de enviarle éste *al hub* un oaquete SOF, le enviará dos: uno denominado *Start Split Transaction Token* (SSPLIT), indicado a continuación, al cual seguira un IN "token" como el anteriormente definido en USB 1.1.

| **PID**   |**Direcc.**   | **S/C**(1)   | **S**peed | **E** en Start | **ET**(2)|**CEC**|
|----------|--------------|--------------|-----------|----------------|----------|-------|
| de Splip (8)|hub 2.0 (7)|o start /1 complete | hub 1.1 (7) (si existe)|o full/1 low )1) |complementa a **S** en full speed (1)|End Point Tipe | (5)
                           
 El hub reenviará el "token IN al dispositivo "X", el cual durante los frames siguientes (de 1 mseg) enviará paquetes de datos al hub, que los guardará en su buffer, y le responderá con un paquete ACK al dispositivo "X" ("X" es un dispositivo full o low speed, pero no high speed).  
A todo esto el **CASB** 2.0 luego de haber enviado los paquetes SOF, SSPLIT e I en **un** uframe, en el siguiente puede iniciar otra transacción con otro dispositivo "Y", enviando SOF;SSPLIT y otro token, sin esperar a que el dispositivo "X" envíe los datossolicitados en el uframe anterior. Luego de varios uframes posteriores, el adaptador enviará al hub el *Complete Split Transaction Token** (CSPLIT) -token Split como el de SSPLIT pero con S/C=1 - seguido del mismo In token enviado anteriormente,para requerir que el hub le envié el resultado de la transacción completada con "X".  
El hub por las dos líneas de alta velocidad que lo unen con el adaptador, enviarña paquetes con losdatos enviados por el "X", que estaban en su buffer.  
![imagen 1.82.c](1.82.c.jpg)

----

[^ Índice](README.md) | [Siguiente >](capitulo14.md)