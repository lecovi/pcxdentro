[^ Índice](README.md) | [Siguiente >](apendice1.md)

----

1-114
------------------------------------------------------------------------------------------------------------------
1.14|#PARA ENTENDER LOS 
    |#PENTIUMr I, II, III, 4, XEONr 
    |#Y LOS PROCESADORES RISC

###¿Qué es el "modelo de Von Neumann", y en qué medida los
###procesadores actuales lo cumplen?
 -----------------------------------------------------------------------------------------------------------------
	si bien con importante mejoras en la velocidad de procesamiento, _la mayoría de los procesadores actuales
	procesan en base al esquema de la figura_ 1.7, denominado "__modelo de Von Neumann"__[^nota1], que supone:

	~~~
	+ Existe una sola UCP, que procesa en secuencia una instrucción tran otra.
	  Ejecuta una sola intrucción por vez mediante una serie de paso

	+ Las instrucciones a ejecutar y los datos a procesar, codificados en binario, deben almacenarse en una 
	  rapida memoria interna (memoria principal) antes de realizar el procesamiento de los mismos.

	+ Existen instrucciones de "salto", (figura 1.35) que ordenen a la UC discontinuar o no (según se
	  alcance o no un resultado interno) la secuencia de intrucciones que viene ejecutando, para 
	  pasar a ejecutar otra secuencia, cuya primer intrucción se debe poder localizar. 
	~~~

	En la figura 1.27 se endicaban cinco pasos o etapas básicas para ejecutar una instrucción.
	Una de las primeras mejoras en velocidad para el modelo, fue ejecutar el paso 5 mientras se espera el
	dato a operar (paso 3), quedando asi 4 subprocesas típicos por lo que pasa la ejecución de cada intruc
	ción: los cuales progresan con cada pulso reloj, según se ha visto (figura 1.30, que se repite en la 1.84).

					INSERTAR FIGURA 1.84
	
	La figura 1.85 (izquierda) es similar a la 1.84, salvo la dirección (diagonal) en que avanza el proceso, 
	para poder comparar el procesamiento según el modelo original de Von Neumann con otro más eficaz. 
	La ejecución de una instrucción progresa de un renglón al siguiente con cada pulso reloj, por lo
	cual los pulsos se han dibujado en sentido vertical. 
	Primero se termina de ejecutar totalmente una intrucción (__I1__), y luego la siguiente (__I2__), insumiendo 
	ejecución de ambas intrucciones 8 pulsos reloj.

###¿Qué mejora en la velocidad presentan los procesadores actuales con "pipe line"?
-----------------------------------------------------------------------------------------------------------------------
	Hoy día, para aumentar la velocidad de procesamiento se ha mejorado el modelo original, dando 
	lugar a otro que podemos denominar modelo de Von Neumann con "solapamiento de procesos", o
	con "__pipe line__" o "__segmentado__" -como quiera llamarse- que se pasa a exponer conceptualmente.
	Intel en 1978 ya adoptó el "pipe line"°° en el procesador 8086.

	-------------------------------------
	[^nota1]  > En el presente tambén se denomina "escalar o "secuencial", generalizable a cualquier computador que opera en forma secuencial
	> sobre los datos. 
	[^nota2]  > Tracucible "como un tubo"), término originado en el proceso de fabricación en serie de autos, adoptado por Ford en 1919.														1-115
---------------------------------------------------------------------------------------------------------------------
	Esta mejora sustancial en la cantidad de intrucciones que se procesan por segundo se basa en las líneas de
	producción en serie de las fábricas dde autos.. En ellas se divide el proceso de fabricación en una serie de
	subprocesos que se pueden realizar en forma independiente. En una cadena de este tipo, cuando se termina
	un subproceso de fabricación de una unidad (como ser el de pintura), la misma es desplazada al lugar donde
	se realiza siguienta subproceso de la cadena, a la par que otra unidad -también en proceso de fabricación- 
	ocupa el lugar de la primera, para ser sometida al mismo subproceso realizado sobra la unidad anterior.
	De esta forma _se realizan simultáneamente todos los subprocesos_ independientes que requiere el  
	armado de un auto, *pero aplicados a distintos autos* en curso de fabricación. Cuando se termina de 
	producir un automóvil, los que fueron entrando a la cadena estarán parcialmente contruidos.
	Para plantear didácticamente la mejora habida apelaremos a un proceso conocido: el lavado de autos.
	Un lavadero simple tiene una persona a cargo de todas las estapas del lavado. Entra un auto por
	vez, y después de un tiempo, en el cual se sucedieron dichas etapas, el auto sale limpio. Luego 
	entra el auto siguiente a lavar, y así de seguido.
	Esto es semejante al procesamiento de cada instrucción en el modelo original de Von Neumann
	(figura 1.85 izquierda), siendo que la siguiente instrucción recién se peude comenzar a ejecutar 
	luego de transcurrido el número de pulsos que requiere la ejecución de la anterior. 

	En un lavadero semiautomático en el cual el proceso se hace en 4 etapas de 5 minutos (entrada y pago
	del ticket --> cepillado automático --> limpieza de ruedas e interior --> limpieza de vidrios y secado final[^nota1])
	se pueden ir procesando 4 autos simultáneamente. Cada auto tardaría 20 minutos en salir, pero puede
 	salir __un__ auto terminado cada 5 minutos. Esto es, aumenta la cantidad de autos lavados por hora, lo cual
	redunda en un menor precio de lavado, pero _cada cliente debe esperar_ las 4 etapas (20 minutos).

	Si al modelo de Von Neumann se le agrega "piperlining", la UCP mantiene su esquema básico, pero se le 
	debe agregar circuitería adicional, del mismo modo que un lavadero automático requiere más personal, 
	marquinaria y espacio interno para espera, en comparación con un lavadero manual unipersonal.
	Así, se necesita un buffer para almacenar por orden de llegada los códigos de varias instrucciones (como
	ser __4__ ó 5) pedidas a la memoria (o al caché), y los otros buffers intermedios entre etapas. Estos sirven para que 
	no se pierda el código de una instrucción en curso de ejecución, o datos y resultados relacionados con ella.[^nota2]

	La figura 1.85 (derecha) ilustra cómo un "pipe line" permite procesar simultáneamente diversas etapas 
	de distintas instrucciones, completándose en cada etapa una parte de la ejecución de cada instrucción.
	Se ha supuesto a los fines comparativos que el "pipe line" se realiza con las 4 etapas y tiempos 
	(dados por pulsos reloj, designados __t1__, __t2__,. ...) de la figura 1.84 ó 1.30, y que todas las intrucciones 
	requieren para su ejecución 4 pulsos). Entonces la UC ordenará:
	
	En __t1__, la primera de estas instrucciones que corresponde ejecutar (__I1__), pasa del butter al registro RI.
	En __t2__ el código de __Isub1__ es decodificado, y al registro RI pasa a contener el código de __I2__.
	En __t3__ se trae[^nota3] el dato a operar para __Isub1__, se decodifica __I2__, y a RI llega desde el buffer el código de __I3__. 
	En __t4__ termina de ejecutarse __I1__, se trae el dato a operar para __I2__, se decodifica __I3__ y llega RI el código de __L4__

	Así de seguido se llevan a cabo en paralelo los procesos indicados en diagonal en la figura citada, cada uno
	independiente del otro. De esta forma, al cabo de 8 pulsos se habrán terminado de ejecutar 4 instrucciones, o
	sea, 4 veces más que con el modelo sin "pipe line" que aparece a la izquierda de la misma figura.
	En general, si se tiene un "pipe line" de __n__ etapas, teóricamente[^nota4] se puede procesar hasta __n__ veces más
	instrucciones por segundo que sin "pipe line", suponiendo que todas las intrucciones requieran __n__ etapas.
	Esto implica también una situación ideal, con todas las instrucciones de igual complejidad, ejecutándose
	en 4 pulsos reloj. Así, _con cada pulso entra una instrucción al "pipe line", y se termina de ejecutar otra_.
	Resulta, que si bien _no se reduce el tiempo de ejecución de una instruccion_ (cada una requiere __4__ pulsos reloj), 
	en cada pulso __reloj__ se está ejecutando una etapa de 4 instrucciones distintas, lo cual permite ejecutar varias
	veces más rapido (4 en este caso) las instrucciones de un programa que en un modelo sin "pipe line".

	-------------------------------------
	[^nota]  > Suponiendo que esta última etapa sea la que dura 5 minutos y otras mucho menos, ella determina el ritmo de lavado.
	[^nota]  > Del mismo modo, en el lavadero citado puede requerirse un lugar entre dos subprocesos, donde un automóvil que sale de un sub-proceso
	> permanezca en él demorado, antes de pasar al siguiente, so pena de llevarse por delante el auto que aún está en este subproceso.
	[^nota]  > Desde la memoria caché, si está en ella (sino habrá que pedirlo a la memoria principal) o desde un registro de la UCP.
	[^nota]  > Un "pipe line" sin circuitos para "predicción de saltos condicionados" puede cortarse, si por ejemplo __I1__ es una instrucción de salto
	> condicionado (figura 1.35), que obligue que la siguiente que corresponda ejecutar no sea __I2__; o si tiene lugar de interrupción por
	> hardware. O demorarse un pulso reloj por que el dato a operar no está el caché y hay que pedirlo a memoria. Asimismo, la circuitería
	> extra para el "pipe line" hace que cada instrucción se ejecute con pulsos de mayor duración en relación con un modelo sin "pipe line"1-116
---------------------------------------------------------------------------------------------------------------


	INSERTAR FIGURA 1.85

###¿Qué es el multiprocesamiento o procesamiento en paralelo?
---------------------------------------------------------------------------------------------------------------
	Los requerimientos actuales de velocidad de procesamiento hicieron necesario el desarrollo de 
	máquinas designadas "__no Von Neumann__", en el sentido de que existen __varios procesadores__ operando 
	juntos, __en paralelo__. Así se puden ejecutar ejecutar, en forma independiente, varias instrucciones de un
	mismo programa, o varios programas independientes, u operar con diversos datos a un mismo tiempo.
	Esto se conoce como "__multiprocesamiento__", contrapuesto al "uniprocesamiento" de Von Neumann.
	De existir varios lavaderos que trabajen "en paralelo" sería factible que varios autos salgan
	terminados simultáneamente y que además se ayuden mutuamente. En las arquitecturas "no Von
	Neumann", varias UCP pueden terminar de ejecutar juntas varias instrucciones por pulso reloj.

	~~~
	No debe confudirse _multiprocesamiento_ con "__multiprogramacion__" ("_multitasking_", también traduci-
	ble como "_multitarea_"), consistente en la ejecución alternada por un UCP de varios programas que
	están en memoria principal. Dada la velocidad de procesamiento, _puede parecerle al usuario como 
	simultánea la ejecución de dos o más programas cuya ejecución en realidad se alterna muy rápidamente_.
	~~~


###¿Cómo funciona básicamente un micropocesador 486?
----------------------------------------------------------------------------------------------------------------
	A continuación describiremos los principales bloques que están en el interior de un procesador 486 (figura
	1.86), y las funciones que cumplen. Luego se concretará de que modo los mismos parcipan, paso a paso,
	en la ejecución de la conocida secuencia de instrucciones __I1, I2, I3, I4__ desarrollada en las figuras 1.23 a 1.26.
	Este procesamiento, que fue realizado en dichas figuras conforme al modelo "original" de Von Neumannm 
	fue acelerado ya en procesadores de Intel anteriores al 486, como se desarrolló en una respuesta anterior.
	En la figura 1.86 aparecen los siguientes sub-bloques y bloques:

	+ Los registros de direcciones (RDI) y de datos (RDA), pertenecientes a la "_Unidad de Interconexión con
	  el Bus_" (__BIU__ en inglés), encargada de la comunicación con el exterior a través de las 32 líneas de datos y
	  32 líneas de direcciones del bus, conectadas a las correspondientes patas del procesador ("local bus"). En
	  Relación con éste, los registros RDI y RDA cumplen las mismas funciones que en la figura 1.23, siendo 
	  que ahora intrucciones y datos leídos en memoria pasan al caché interno de 8 KB del procesador 
														1-117
-------------------------------------------------------------------------------------------------------------
	. La _Unidad de caché_ de 8 KB guarda las instrucciones y datos que seguramente serán requeridos próx-
	  mamente. Por una parte, a través de un bus de 128 líneas,se pueden leer del caché 128/8 = 16 bytes que
	  pasan a un buffer de la Unidad de pre-carga de instrucciones. Corresponden en promedio a unas 5
	  instrucciones a ejecutar, que así llegan juntas para entrar al "pipe line".Por otra, el caché puede ser leído
	  para que se envíen 32 biys de datos a la UAL, o un registro de la UCP ó 64 bits de datos a la Unidad de 
	  Punto Flotante(FPU en inglés). En una escritura van hacia el caché 32 ó 64 bits, respectivamente 

	. La _Unidad de Pre-Carga_ proporciona las direcciones de las próximas instrucciones a ejecturar, y
	  guarda las mismas en orden en dos buffers de 16 bytes, para que luego cada una sea decodificada

	. La _Unidad de Decodificación_ realiza dos decodificaciones de cada instrucción, según se verá.

	. La _Unidad de Control_ (UC) mediante líneas que salen de ella(dibujadas en figuras 1.87 a 1.89), activa las
	  operaciones que con cada pulso reloj deben realizar los distintos bloques de la UCP (U. de pre-carga,
	 U.Decodificadora, UAL UPF y UC), Conforme lo establecen microcódigoa de la ROM de Control.

	. La _Unidad de segmentación, paginación y protección de memoria_, conocida como "Unidad de 
	  manejo de memoria" (__MMU__ en inglés) se encarga de proporcionar las direcciones físicas de
	  memoria que utiliza un programa Para tal fin esta unidad convierte la referencia a la dirección del
	  dato -que viene con la instrucción- en la correspondiente dirección física. Puesto que la memoria
	  de una PC se divide en segmentos, y éstos -de ser necesario- pueden subdividirse en páginas
	  (por ejemplo si se usa el sistema operativo Unix). Esta unidad se encarga de ello, así como de la 
	  protección contra escrituras no permitidas en zonas reservadas de memoria. Conviene aclarar que 
	  el nombre de esta unidad no tiene mucho que ver con la traducción castellana de "pipe line" como
	  "segmentación", razón por la cual se prefirió usar dicha palabra inglesa.

					INSERTAR FIGURA 1.86
	
	Todas estas unidades participan en el "pipe line" de instrucciones, que en el 486 consta de 5 etapas, 
	que progresan con cada pulso reloj, al compás de sus millones de ciclos por segundo:1-118
-------------------------------------------------------------------------------------------------------------------
	1. __Pre-carga__ ("pre-fetch") consiste en la llegada de los códigos de las próximas instrucciones que entrarán
	   al "pipe line" a dos buffers(de 16 bytes cada uno) de la Unidad de Pre-carga, ,para formar una "cola".
	   En la figura 1.86 se ha supuesto que a uno de estos buffers han llegado desde el caché 5 instrucciones
	   (promedio de instrucciones que entran en los 16 bytes de este buffer) en forma simultánea. Los códigos
	   de ellas son los mismos que hemos usado en la figura 1.15 para __I1, I2, I3, I4,__ que en hexa son A10050,
	   30600500, B0600650, y A31050, respectivamente. La instrucción __I5__, aparece con un código XXXX. De no 
	   haber estado estas intrucciones en el caché, primero se hubiera pedido __I1__ a la memoria principal[nota1], y 
	   llegaría una copia de su código al buffer de pre-carga para que entre al "pipe line", y otra copia del mis
	   mo al chaché. Inmediatamente legarán luego al caché desde memoria, uno tras otro, los códigos de __I2, 
	   I3, I4__[^nota2], que pasarán a la cola del buffer. De esta forma, sólo se pierde tiempo en obtener del exterior a __I1__
	
	2. __Primera Decodificación:__ a la Unidad de Decodificación llegan los primeros 3 bytes de cada 
	   instrucción, para separar -entre todos los bytes que forman su código de máquina- su código
	   de operación, del número que hace referencia a la dirección del dato (Los códigos de operación
	   pueden tener de 1 a 3 bytes). Así, en la figura 1.86, al primer decodificador llegan los bytes
	   A10050H, que en este caso son todos los bytes de la instrucción __I1__, identificándose __A1__ como el
	   código de operación, y __0050__ como la referencia a la dirección del operando, número que pasará
	   a la Unidad de segmentación y paginación, que formará la dirección del dato a operar, de modo
	   que pueda ser leído del caché (si está en éste).

	3. __Segunda Decodificación:__ en la figura 1.87, el código de operación __A1__ identificado en el paso
	   anterior es ahora decodificado. Esto permite determinar la secuencia de microcódigo contenida en la 
	   ROM de Control. Merced a esta secuencia la UC generará las señales de control, que enviará por las 
	   líneas (insinuadas con flechas) que salen de ella, para que cada unidad que controla, ejecute una
	   parte de la instrucción con cada pulsos reloj (como en la figuras 1.31 y 1.32), Si la instrucción es
	   simple se ejecuta en un solo pulso. Al mismo tiempo que __I1__ pasa por esta etapa del "pipe line", tres
	   bytes (030600H) del código de __I2__ (03060050H) entran a la etapa de primera codificación, siendo que 
	   0050 -dirección traspuesta del dato- pasará a la U.de segmentación, para leer luego el dato del caché.

	4. __Ejecución:__ en la figura 1.88 el dato que debe transferirse al registro AX -como ordena __I1__- hay que
	   leerlo en la dirección (500H) que la U. de Segmentación dejó en el registro RDI, la cual permite leer el
	   dato a operar en el caché. Suponiendo que el dato está en la U de caché, el mismo llegará al registro
	   RDA[^nota3]. Paralelamente con la acción recién descripta para __I1__, el código 0306 de __I2__ pasa a la segunda
	   decodificación, a la par que los bytes 2B0606 del código 2B060650 de __I3__ van a la primera decodificación.

	5. __Almacenamiento de resultados:__ a esta etapa final del "pipe line" llega __I1__, completándose su 
	   ejecución, para lo cual el dato (1020H) pasará al registro AX (paso incluido en la figura 1.88).
	   Al mismo tiempo se tiene que: __I2__ entra en la etapa de ejecución obteniéndose del caché el dato
	   1020H, que pasa al RDA. Este dato se suma en la UAL con el contenido (1020H) de AX (figura
	   1.88), conforme ordena el código de dicha instrucción.
	   El código 2B06 de la instrucción __I3__ entra a la segunda decodificación, y los bytes A31050, o sea
	   todos los que conforman el código A31050 de __Isub4__ son sometidos a la primer decodificación.
	
	En la figura 1.89 se ha incluido cómo progresa el "pipe line" con otro pulso reloj, a fin de terminar 
	de ejecutar __I2__, que pasa a la quinta etapa. En ésta, el resultado de la UAL (2040H) debe guardarse
	en AX, así como los "flags" SZVC que ella también genera, resultantes de la operación, en el regis-
	tro de estado (no dibujado). Paralelamente, __I3, I4__ e __I5__, pasan por las etapas 4, 3 y 2 del "pipe line".







	----------------------------------
	[^nota3]  > Si como es corriente, existe un segundo nivel de caché exterior (por ejemplo de 256 __KB__), se buscaría __Isub1__ primero en este caché
	> rápido, y de no encontrarse en el mismo, se obtendría __I1__ de memoria principal.
	[^nota3]  > Cuando no hay un contenido en un caché, su controlador solicita a la memoria el mismo y los que están en las direcciones siguientes
	[^nota3]  > Por razones didácticas se ha buscado continuidad con el modelo de Von Neumann (figuras 1.23 a 1.26), aunque la ejecución de __I1__
	> pueda realizarse en un paso menos en el 486. Esta simplicación puede traer alguna inconsistencias en el paso 5.   1-131
	Las *µops-R generadas por instrucciones complejas son aportadas por la ROM* vinculada al TC (fig.194),por
	ser las mismas infrecuentes de aparecer en un programa.
	También debe suponerse que cuando se direcciona al __TC__ para localizar en una línea del mismo una próxima
	secuencia de 3 µops-R a ejecutar, éstas deben aparecer en las salidas del __TC__. Dichas µops-R (de igual 
	longitud) irán a la etapa de Renombramiento de Registros ( __RR__ ) de donde pasan según el orden originario a
	la "Cola de µops-R", junto con la dirección de la instrucción que los originó. Lo mismo ocurre con las µops-R
	generadas por la ROM. Esta cola oficia de buffer intermediario entre los subsistemas que operan en orden y desorden.
	Para la "HT" este buffer se comparte mitad para cada "thread", pudiéndose identificar en esta cola las µops-R
	de cada "thread". Si para la "HT" se debe acceder simultáneamente al __TC__ para obtener líneas con µops-R de 
	ambos "threads", durante un ciclo pedirá una línea cada uno de ellos, y en el siguiente una línea del otro.
	Mientras uno de ellos esta detenido se podrá acceder durante ciclos sucesivos al __TC__ para obtener líneas 
	del otro.Por lo tanto el __TC__ es un recurso compartido en "HT", puediendo un "thread" tener más líneas que otro.
	También es compartida la ROM de µops-R. Cuando el caché L2 llega una instrucción compleja, el __TC__ le envía a la ROM
	el número que genera la __UPD__ el cual es como la dirección de la ROM donde está la primera de una secuencia de
	µops-R, en que se traduce una instrucción compleja que llegó a la __UPD__. Para "HT" el hardware permite identificar
	a que "thread" corresponde dicha sencuencia.
	Si al direccionar el __TC__ *hay un fallo* ("miss") se debe acceder a la jerarquía de memorias (en primer lugar al caché
	L2) para obtener dos líneas de instrucciones (64 bytes), las cuales serán traducidas por la __UPD__ (de a una por
	vez) y enviadas como µops-R a la __UT__ y también a la "Cola de µops-R".
	>Obsérvese que en esta arquitectura sólo se pierde tiempo en las traducciones cuando hay un fallo en el __TC__ 

Antes de ir a la __UPD__ los 64 bytes citados  provenientes del caché L2, temporariamente se guardan en el Buffer L2
	( __BL2__ ) hasta que puedan ser decodificadas las instrucciones. Para "HT" existen dos __BL2__, uno para cada "thread".
	También existen dos __CRS__ y dos buffers para instrucciones de retorno (de subrutina, por ejemplo).
	>En definitiva el __TC__ mayormente provee las µops-R que se van ejecutar próximamente, y cada vez que en el __TC__
	hay un fallo, la __UPD__ traducirá en µops-R las instrucciones __BL2__ ( *a razón de una por vez* ) que irán al __TC__
	y también a la cola de µops-R, salvo que aparezca alguna instrucción compleja. Esto es como en una UCP con caché: si
	hay fallo, las instrucciones a ejecutar van al caché y la UCP (en este caso dicha cola).
	
Si en "HT" hace falta decodificar instrucciones de los dos "threads", se sacan alternadamente secuencias de cada __BL2__
	
En Proceso de ejecución de µops-R se inicia con una asignación ("allocation") en la etapa __RR__ que renombra los
	registro de 80x86 indicados en la µops-R, que están en la "Cola de µops-R" en otros registros "alias". Para tal fin
	existen 128 registros para enteros y 128 para punto flotante, más buffers para reordenamiento y para operaciones
	load/store., que para "HT" son particionados en mitades, una para cada "thread", siempre identificables por el 
	hardware del procesador, como en todos los casos.
	En "HT" en la "Cola de µops-R" Hay µops-R de los dos "threads",y con cada pulso reloj se alterna la asignación de 
	recursos de la __RR__ . Si en un "thread" usa todos los recursos que tiene reservados, la asignación sigue para el otro.	
	Junto con la asignación se realiza el renombramiento de registros. Para ello existen dos "Tabalas de Registros Alias",	
	que indican para cada nueva µops-R que se va a ejecutar de cada "thread" en que registro "alias" estarán sus operandos
	(que pueden ser resultados de µops-R ejecutadas antes),y en que registro "alias" irá el resultado.
	Las secuencias de µops-R con sus registros nombrados pasan a dos colas": una para provenientes de instrucciones 
	load/store (que deben acceder a memoria), y otra para las que se tradujeron de las instrucciones que no ordenan acceder 
	a memoria. Estas dos colas también pueden ser particionadas con la mitad de entradas para cada "thread". De estas colas
	salen µops-R hacia la __UPRE__ , en forma alternada -una por "thread" y con cada pulso reloj.
	
En la __UPRE__ existen 5 "Lógicas planificadoras" (__LP__) que determinan cúando µops-R se puede ejecutar. Cada __LP__
	tiene su propia cola de 8 a 12 µops-R que debe seleccionar para enviar a las __UE__. *Las __LP__ no distiguen entre µops-R
	de dos "threads"*. Las µops-R se seleccionan en función de la dependencia de datos y disponibilidad de __UE__. Para evitar
	problemas está limitado el número de entradas en uso que puede tener en cada cola un "thread".	
	
>Puesto que para cada µops-R se efectúa en una __UE__ la operación que ordena con los datos apropiados y se deja el
	resultado en el destino indicado por ella: y dado que dichos datos están fisicamente en registros que están definidos
	desde la etapa __RR__, al igual que el destino del resultado, y que para "HT" dichos recursos están separados para cada 
	"thread", no hay problemas en encontrar los resultados que usarán las µops-R que se ejecutarán luego.
	Asimismo las µops-R se pueden identificar, pues tienen asociado (incluso en la __UT__) un número que es la dirección
	en memoria de la instrucción originaria de la cual fueron traducidas.
	
Si bien cada ciclo reloj de las __LP__ pueden hacer que las __UE__ efectúen las operaciones de hasta 6 µops-R, como el 
	máximo de µops-R que genera la __UT__ es 3, *queda limitado a este número la cantidad de µops-R ejecutables por ciclo*.
	
	
	
Figura 1.94

Existe 4 **UE**, siendo que las dos que contienen una **UAL** operan al doble de la frecuencia del procesador, o sea
que en medio ciclo completa una operacion, siendo por ello posibles hasta 6 operaciones por ciclo. Ellas son:
**UE0** dedicaca a µops-R "store", y **UE1** para µops-R "load", a razón de una µop-R por ciclo.
**UE2**: en la primer mitad de un ciclo puede operar enteros en una **UAL**, o una instrucción de transferencia en
punto flotatnte; y en la segunda mitad de un ciclo puede operar nuevamente enteros en la **UAL** de dicha **UE**.

Para µops-R load/store existe un Bufer Conversor compartido en "HT" por los dos "threads", que es una memoria
totalmente asociada (definida al tratar cachés), que convierte direcciones a direcciones fisicas de memoria.
Después de haberse realizado la operación ordenada por cada µop-R en la **UE** correspondiente, las µops-R
pasan a un buffer de reordenamiento, que hace de intermediario entre la **UPRE** y la **UR**. este buffer se parte en
mitades si hay dos "threads".

La **UR** retira las µops-R en orden en forma alternada para cuando "thread".
Luego que las µops-R ejecutadas se retiran, los resultados pasan desde registros hacia el caaché de datos **L1**.
Este es un caché asociativo de 4 vias con líneas de 64 bytes, que siempre escribe "write-through" en el caché
asociativo **L2** de 8 vías con líneas de 64 bytes, con 128 bytes por línea. Este Xeon tiene un caché similar al *L3*
Los cachés **L2** y **L3** operan con direcciones físicas y el **L1** con virtuales, pero con tags físicos.

De la descripción anterior reslta, que dos "threads" que se están ejecutando en paralelo comparten (en principio
por partes iguales) la mayoría de los recursos físicos de un único procesador, ya sea por partición de los mismos o 
por alternancia (en un ciclo reloj uno y en el siguiente el otro) y no se trata simplemente que se ejecuta un "thread" 
y cuando éste se detiene por algún motivo se pasa a ejecutar el otro.           
1-133
# REPRESENTACIÓN DE NÚMEROS BINARIOS NATURALES Y OPERACIONES CON ELLOS

A1.1|  ##SISTEMAS NÚMERICOS POSICIONALES
	
####¿Qué es un sistema numérico posicional?
La necesidad de representar conjuntos de objetos ah llevado a las distintas culturas a adoptar diversas formas de 
	simbolizar su valor numérico.
Una manera primera de representar el número de elementos que constituyen un cierto conjunto, es establecer una 
	correspondencia con un número igual de símbolos.
	Esto lo hacemos cuando contamos con los dedos,o si para representar, como ser, los días de la semana,
	dibujamos igual números o trazos:           | | | | | | |
	Tal sistema de representación sería *"unario"*, pues se usa un solo tipo de símbolo. Su desventaja es que no permite
	simbolizar cómoda y rápidamente conjuntos de muchos elementos.
	
Cuando fue necesario designar la existencia de muchos elementos, se trató siempre de *utilizar menos cantidad de simbolos*	
	,para lo cual se establecieron *implícitas* ente los mismos.
	Los romanos utilizaron un sistema de signos de valor creciente: __I__,__V__,__X__,__L__,__C__,__D__,__M__, etc,
	que se agrupan de derecha a izquierda, sumándose o restándose entre sí, según sugieran o no el orden creciente.
	
__CXVII__ = cien + diez + cinco + uno + uno
						__MCMV__  = mil + (mil - cien) + cinco

Esta codificación requería nuevos símbolos cuando seagotaban los de mayor valor, a la par que los cálculos por su
	complejidad convenía realizarlos con ábacos.
	Fueron los pueblos orientales y americanos (mayas) los que desarrollaron los sistemas *posicionales*, basados en un conjunto
	limitado y constante de símbolos, entre los cuales se encontraba el "cero", para indicar la ausencia de elementos. Miles 
	de años antes, el ábaco, construido en la tierra  o con madera fue el antecesor natural de estos sistemas, siendo que la ausencia
	de objetose en una posición o varilla implicaba de hecho el cero.
	
>En estos sistemas, __cada símbolo__, además del número que elementos de un tipo que representa considerado aisladamente,
	__tiene un significado o peso distinto, según la posición que ocupa en el grupo__ de caracteres del que forma parte.

De esta manera es posible representar sistemáticamente *cualquier* número, empleado en forma combinada un conjunto *limitado* de
	caracteres simbólicos.
	Los caracteres se denominan *"dígitos"*, y constituyen piezas de información digital (sección 1.10)
	
>Relacionado con los diez dedos, el __sistema posicional decimal__ , también denominado de *"base o raíz diez"* por utilizar
	diez símbolos (que forma la sucesión monótona creciente __0,1,2,3,4,5,6,7,8,9__) permite representar cualquier número de elementos
	combinando dichos símbolos.

Este sistema servirá para comprender conceptualmente en qué consiste y cuál es la estructura de cualquier sistema numérico posicional.134

Si bien en la práctica apreciamos mecánica e intuitivamente, sin pensar, la magnitud de un número decimal con solo
visualizarlo, en realidad la cantidad de elemntos que un número simboliza se determina sumando los productos
que se obtienen de multiplicar el valor de las unidades que representa cada dígito por el ***peso*** (valor) de la
posición que ocupa (unidades, decenas, etc).

9323 = 9x1000 + 3x100 + 2x10 + 3x1   siendo: 10 = 1 x 10[^nota1]; 100 = 10 x 10 = 10[^nota2; 1000 = 100 x 10 = 10[^nota3]

>Resulta que __el peso de cada posición es el de la anterior multiplicada por la base__ (diez, o sea el número de símbolos de
sistema), *resultando así los pesos potencias crecientes de la base*. Esto es común a todos los sistemas posicionales. En caso
de necesitarse representar números más grandes se usan siempre los mismos diez símbolos,y sólo es necesario agregar nuevas posicionse 
a la izquierda.
Un sistema numérico es una forma de fraccionar una totalidad de porciones, cuyos tamaños, a partir del valor uno, se van escalonando
-a medida que se requieren nuevos tamaños- de forma tal que cada tamaño que se necesite es el anterior multiplicado por la cantidad de 
símbolos de la base.
El número máximo de porciones de cada tamañoo lo determina el símbolo de mayor valor de la base en cuestión.

Cuadno leemos 109 personas (109 = 1x100 + 0x10 + 9x1) en relación a la totalidad de dichas personas, las mismas de hecho han sido 
divididas en forma *virtual*, de modo de conformar de manera única:
- un solo grupo de 100, (pueden existir hasta 9 grupos posibles de 100),
- con las restantes (109-100=9) no se puede formar ningún grupo de 10, y sí 9 grupos de personas.
También puede pensarse en relación a un número 109,que en una balanza (figura A1.1) se debe pesar un objeto 
*de peso supuestamente desconocido*, pero que a los fines didácticos de simular su pesada debemos partir de que dicho peso es conocido
(109 grs)

	INSERTAR FIGURA A1.1

Los juegos de pesas a utilizar en base diez serán subconjuntos de 9 pesas de múltiplos de diez:
- 9 pesas de 1 gramo.
- 9 pesas de 10 gramos.
- 9 pesas de 100 gramos.
- 9 pesas de 1000 gramos... y así de seguido; o sea que podemos tener más subconjuntos de 9 pesas que sean múltiplos de diez 
(teóricamente infinitos), según sea la magnitud del peso de los objetos que se quiere pesar.

Para pesar dicho objeto se usaría primero una pesa de 100grs. (la de mayor peso posible para empezar a equilibrar, siendo que con
dos pesas de ese tipo se extendería los 109 grs. a pesar: 100 + 100 = 200 > 109).
Luego si se prueba con una pesa de 10grs, también se exederá el peso a ponderar: 100 + 10 = 110 > 109).
Finalmente agregando 9 pesas de 1gr, se equilibra la balanza. En definitiva se usaron: __1__ pesa de 100grs, __0__ pesas de 10grs
 y __9__ pesas de 1gr con lo cual el número 109 indica el peso del objeto en base diez. O sea: 1 0 9 = 1x100 + 0x10 + 1x9

Es importante observar qeu tanto con las personas como con la balanza, se empieza siempre respectivamente por los grupos o pesas mas
grandes (de valor ...1000, 100.....) que se puedan formar  o emplear. De este modo se aseguran qeu la representación simbólica es única.


##¿Cuáles son las características de los sistemas numéricos posicionales?

Podemos sistemizar como sigue las características del sistema decimal, que también, como se tratará, *son comunes a todos los sistemas 
numéricos  posicionales*, cualquiera sea su base (definida por el número de símbolos empleados para formar números)

> -Consta de un número finito de símbolos individuales que constituyen la  *"base o raíz"* del sistema (diez en sistema decimal, dos en 
el binario, etc).
- Cada símbolo aislado representa un número específico de *unidades*.
- Existe un símbolo (*cero*) para indicar la ausencia de elementos a representar.
- Los símbolos pueden ordenarse en forma monótona creciente.
- Formando parte de un número compuesto por varios símbolos, *un mismo símbolo tiene un significado o "peso"  distinto según su posición
relativa en el conjunto*.
-La posición extrema derecha corresponde a  unidad (peso uno): a partir de ella, cada posición tiene el peso de la que está a su derecha 
multiplicada por la base, resultando siempre que *el peso de cada posición es una potencia de lab ase. Esta en todas las bases se simboliza*
__10__ ("uno cero").135

A1.2 # SISTEMAS NUMERICOS OCTAL BINARIO Y HEXADECIMAL

## ¿Qué símbolos se emplean en otras bases numéricas y cómo se representan números en ellas?

A los fines de que resulte fácil simbolozar en otros sistemas numéricos, los símbolos 0 y 1 existen en todos los sistemas con 
igual significado que en el decimal.
Si otros sistemas usan algunos o todos los símbolos decimales restantes del 2 al 9, se ha acordado que su significado es el mismo
que en decimal. Así 7 representa siete unidades, ya sea en decimal, octal o hexadecimal.

El __sistema hexadecimal__ tendrá __dieciséis__ símbolos distintos que constituyen la base.
Del 0 al 9 coinciden en significado con los correspondientes decimales; para los seis restantes se crearon los simbolos de la
__A__ hasta la __F__, como aparecen en la figura A1.1 en correspondencia a sus equivalentes decimales y con los números de otros sistemas

INSERTAR FIGURA A1.2

###Sistemas en base ocho u octal

En base ocho los símbolos van de 0 al 7 (fig A1.2), con los cuales se puede formar cualquier número.
Con los mismos supuestos que planteamos para la pesada realizada en relacion con la fig A1.1, pesaremos (fig A1.3) el mismo objeto cuyo
peso en octal supondremos desconocido, siendo que en base diez pesa 109 grs.Veamos cúales son las pesas en base ocho. Si en base diez cada
pesa en relación con la del tamaño anterior era diez veces más pesadas, en octal lo será __ocho veces__. Juntando ocho pesas de un valor 
se construye una pesa del tamaño siguiente. Si para fines didácticos simbolizamos en base diez el peso de cada tipo de pesa octal, por lo
que se tendrpia la serie de valores: __1__ gr; 1gr x 8d = ___8__d grs x 8 d = __64__d grs; 64d grs x 8d = __512__d grs., etc...
El símbolo "d" indica que se trata de base diez. El símbolo para representar 1 es el mismo en ambas bases.
*De cada uno de dichos tamaños existen un total de 7 pesas octales* (en base diez eran 9), siendo 7 el símbolo octal de mayor valor:
- 7 pesas de 1gr.
- 7 pesas de ocho veces mayor que la de 1gr (8d grs)
- 7 pesas dieciséis veces mayor que la de 1gr (16d gramos) y ocho veces mayor al tamaño anterior.
- 7 pesas sesenta y cuatro veces mayores que la de 1gr (64d grs) y ocho veecs mayor que el tamaño anterior.
y asi de seguido, o sea que podemos tener más subconjuntos de 7 pesas que sean múltiplos de ocho (teóricamente infinitos), según
sea la magnitud del peso de los objetos que se quiere pesar.

INSERTAR FIGURA A1.3

Volvemos a pesar el objeto que en base diez pesaba 109grs.Cuando se pesa un objeto en general se desconoce su peso, el cual hay que determinar
Para ello se requiere ir probando poniendo y sacando pesas (octales en este caso), hasta que con las pesasdas adecuadas a la balanza alcance 
el equilibrio. La selección de las pesas adecuadas la simualremos haciendo cálculos simples en base diez, como se hizo en relación con la 
figura A1.1.
Suponiendo (fig A1.3) que se empeiza adecuadamente a equilibrar la balanza con __una__ pesa setenta y cuatro veces mayor que la de 1gr
en el platillo derecho. Pensando en base diez se habría equilibrado 64d grs, por lo que faltará quilibrar 109 - 64 = 45d grs.
Si se coloca otra pesa del mismo tamaño que el anterior se tendría: 64d + 64d = 128d > 109d, y el peso del platinillo derecho superaría 
al del izquierdo, por lo qeu no puede colocarse más que una pesa de dicho tamaño.ï»¿m.ginzburg
-F pesas de 1gr
-F pesas diecisÃ©is veces mayor que la de 1gr. (16d grs)
-F pesas docientoscincuenta y seis veces mayor que la de 1gr. (256d grs) y dieciseis veces el tamaÃ±o anterior 
-F pesas mil veinticuatro veces mayor que la de 1gr. (1024d grs) y diecisÃ©is veces el  tamaÃ±o anterior.
y asi de seguido, o sea que podemos tener mas subconjuntos de F pesas que sean mÃºltiplos de diecisÃ©is
(teÃ³ricamente infinitos), segÃºn sea la magnitud del peso de los objetos que se quiere pesar.

figura A1.7
Otra vez pesaremos el objeto que en base diez pesa 109 grs. la selecciÃ³n de pas pesas adecuadas la simula-
remos haciendo cÃ¡lculos simples en base diez, como se hizo en relacion con las figuras A1.1 y A1.3.
suponiendo (fig A1.7) que se empieza adecuadamente a equilibrar la balanza con las pesas diecisÃ©is veces mas 
pesadas que 1 gr., se podrÃ¡n colocar hasta 6 pesas de ese peso, con lo cual, calculando en base diez, 
habremos equilibrado 6x16=96d grs., faltando equilibrar 109-96=13dgrs. El equilibrio de los platillos se logra
agragando 13d=Dh pesas del tamaÃ±o menor siguiente, que es de 1gr. por consiguiente,
el peso del objeto en hexa es *6D*. O sea: 109d=155 base(0)=1101101b=6Dh

asimismo, si pensamos en el conjunto de personas que en base diez fue dividido conforme indican los simbolos 109, 
dicha totalidad en base dieciseis fue dividida (pensando el tamaÃ±o de los grupos en base diez), en 6 grupos
de 16, y 13 grupos de una persona, siendo que pueden existir hasta F=15 grupos de cada tipo.

**Â¿Como se sombolizan los pesos en hexadecimal sin necesidad de estimarlos en bases diez?**
AL igual que cualquier otro sistema, el hexadecimales no surge del sistma decimal, sino que es independiente como
asi lo sufiere la posibilidad de pesar el objeto en cuestion usando pesas hexadecimales, pudiendose simbolizar en 
hexa el valor de las pesas o pesos de este sistema simplemente (fig a 1.8) si ponemos en el plato izquierdo de la 
balanza un peso de dieciseis veces mayot que 1gr.(16 grs. en base diez) para equilibrarlo hace falta una sola presa 
dieciseis veces mayor que 1 gr, y ninguna (cero) pesa de 1gr., osea que esta pesa o pseo en hexa se simboliza 10
(lease uno-cero y no "diez").
conforme con esto, en el fig. A1,2 luego del simbolo mayor F sigue el **10** (1^16 0h^1 = 16d), asi como en base diez
despues del 9 sigue el 10, en octal despues del 7 sigue el 10, y en binario despues del 1 sigue el 10.
Del mismo modo si en el plato izquierdo se colocaria un peso docientos cincuenta y seis veces mayor que 1gr
se equilibra con una sola de peso de ese tamaÃ±o y ninguna de los tamaÃ±os menores, por lo que en hexa este peso 
se simboliza 100h (lease uno-cero, y no "cien").
por lo tanto, tambien en hexa las pesas se simbolizan 1, 10, 100, 1000...(estos mismos simbolos representan los
valores de las pesas que se usan en base diez, aunque en hexa representan 1, 16, 256, y 4096, respectivamente).
osea 100% en hexa:  


.                        6^10  D^1 h^jh  =6x10+Dx1jh

esta cuenta (que indica 6 pesas de 100,mas D pesas de 1) realizada en hexadecimal daria, obviamente, 6Dh.

con los pesos de 6Dh en base diez es: 6^16 D^1 h=[6x16+13x1]d=109d;
esto es, pesos de 6Dh en base de diez se usaron una pesa de 64 mas 5 de 8, mas 5 
de 1, suma que da 109d.

Figura A1.8
como ya se dijo, al valorar los pesos de una base en diez en esencia se esta pasando dicha base a base diez.

**ejercicio:**
con la balanza con peso hexadecimales pesar un objeto que en base diez pesa 112d.        Respuesta:70h
idem otro que pesa 100d                                                                  Respuesta 64h

##**Â¿cono se halla facilmente el siguiente de cada numero en base ?**
Elcuenta vueltas que indica los kms. recorridos por un auto consta de ruedas con los simbolos del 0 al 9.
Cada rueda al cambiar de 9 a 0 obliga a la que esta a su izquierda a avanzar una posicion. La rueda de las unidades
progresa una unidad merced a una accion exterior para que las otras puedan cambiar, si asi debe ocurrir.
suponiendo que el numero que esta en frente al vidor es 4588, si la rueda de las unidades avanza un simbolo, oasara de 8 a 9sin
adectar la rueda de las decenas, por lo que el numero siguiente es 4589. Cuando las unidades vuelvan a aumentar uno, ahora 
pasaran de 9 a 0, lo que hara que las decenas tambien progresen uno. De 8 a 9, sin afectar la centenas. Por lo tanto.el
numero que sigue sera 44590. Con las mismas consideraciones si las unidades siguen aumentando uno. Sucesivamente se
tendra: 4591,4592....4599. Luego de Ã©ste  las unidades pasan de 9 a 0, lo que hace que las decenas  tambien pasen de 9 a 0,
lo cual a su vez obliga que las centenas cambien de 5 a 6. asi se forma 4600, y asi seguido   ï»¿*cuentas vueltas hexadecimal y binario* nos permintiran hallar facilmente el numero que sigue a otro dado.
en hexadecimal cada rueda tiene desiseis simbolos (0,1,2,3,4,5,6,7,8,9,a,b,c,d,e,f), y cuando cambia de f a 9 hace cambiar la
rueda qye esta a su izquierda salco que hay 16 simbolos en cada rueda en vez de diez, todo es igual al cuenta vueltas anterioro.
asumiendo que el cuenta vuelta hexadecimal indica 3899. si la rueda de las unidades avanza un simbolo pasara de 9 a A, sin
hacer cambio en la rueda la  que esta a su izquierda, por lo que el numero hexadecimal siguiente es 389A. Luego cada vez que las 
unidades aumentan en uno, sucesivamente se iran formando 389B, 289C, 289E, 389F. con el siguiente cambio de la
rueda de las unidades, esta pasara de F a 0, con lo siguiente avance en uno de la rueda delas unidades esta pasara de F a
0, forzando que la rueda que esta a su izquierda rambien cambie de f a 0, lo que a su vez tambien hace que su rueda vecina izquierda
pase de f a 0, lo que a su vez hara que la rueda que esta a su izquierda cambe de 3 a 4, en  fefinitiva 3FFF se paso a 4000.

Podemos imaginar un **cuenta vueltas binario** constituido por ruedas que solo tienen dos simbolos **0** y **1**, cada uno ocupando una
mitad de cada rueda. cuando una rueda pasa de 1 a 0 obliga a la que esta a su izquierda que gire media vuelta para que pase a 1
si estaba en 0, o que pase a 0 si estaba en 1.
suponiendo que este cuenta vueltas indique 1010, si la rueda extrema derecha de las unidades avanza uno pasara de 0 a 1, sin afectar
a la rueda que esta a su izquierda, por lo que el numero binario que sigue sera 1011. cuando la rueda de las unidades vuelva a
cambiar, esta vez de 1 a 0, hara que la rueda vecina izquierda que estaba en 1 pase a 0, esto a su vez obliga a que la rueda vecina 
izquierda que estaba en 0 cambie a uno, lo cual no afectara a la rueda vecina izquierda de la misma. entonces 1011 sigue 1100, etc,
en la figura 1.4 puede verificarse con este metodo la generacion de la sucesion de binarios del 0000 a 1111.

##**Â¿Cuantos bits se necesita por cada digito decimal a representar?**
El numero decimal 109 de 3 digitos, resultan aproximadamente 7/2=2,5 bits por cada digito decimal.
512d=1000000000b o sea 10bits para representar 3 digitos decimales :10/3=3,3 bits por cada digito decimal.
con 2 bits se forma 4=2^2 combinaciones binarios (00 11 10 11). con 3 bits se forman 8=2^ combinando binarios (000 001
010 011 100 101 110 111). en la figura 1.4 de la seccion 1.2 aparecen las 16=2^4 combinaciones binarios que se forman con 4 bits.
O sea, que el exponente de dos indica la cantidad de bits que se necesita en uno, el numero de combinaciones se duplica.

es importante recordar siempre que 2^10=1024, numero cercano a 1000 = 10^3 (1K)
EL exponente diez de dos indica que con 10 bits puede formarse 1024 numeros o combinaciones binarias distintas
(de 0000000000 a 1111111111b=1023d), numero cercano a 1000d que es el numero o combinaciones
que en base diez pue en el platillo derecho den formarse con 3 digitos decimales (de 000 a 999), siendo 3 el
exponente de diez.

por lo tanto, un numero aproximadamente igual de combinaciones distintas se forma con 10  bits en binario, y con 3
digitos decimal. osea unos 10 bits por cada 3 digitos decimales, lo que da 10/3 =3,33 bits por cada digito decimal.
ejercicio: cuantos bits se necesita para fotmar 10^6(1mega)numeros distintos.     respuesta 6x3,3 3=19,98 - 20bits
otra forma de hacerlo: dado que 2^10 , se tiene 10^3x10^3 ~ 2^10x2^10=2^20   Eo exponente indica que hacen falta 20bits

#**1.3 CONVERSION ENTRE BASES**
##**Conversion de una base cualquiera a base diez** 
se trata de una metodologia que de hevho hemos realizado anteriormente cuando evaluamos en base diez
los valores de las pesas con las cuales formamos numeros en otras bases. Asi, hemos realizado

64  8  1
1   5  5=[1x64 + 5x8 + 5x1]d=109d


64 32 16 8 4 2 1 d
1   1  0 1 1 0 1 b=[1x64 + 1x32 + 0x16 + 1x8+ 1x4 + 0x2 + 1x1]d=109d

16 1
6  Dh=[6x16 + 13x1]d =109d 












**regla:**
1. escribir sobre cada posicion su peso en decimal
2. sumar los prductos del peso decimal de cada posicion por el simbolo que aparece en ella (en hexa se debe
pasar los simbolos A, B, D, E, F a base diez). El resultado de essta suma sera el numero decimal buscado.

ejercicio: convertir a decimal el numero binario 10000   respuesta 16d
           convertir a decmial los numeros hexadecimales 109 y 100A
           convertir a decmial el numero octal 137

##**conversion de base diez a otra bese cualquiera por el "metodo pesas"**
como mse puso de relieve anteriormente, el hecho pesar con pesas de otras bases objetos cuyo peso es
conocido en base diez (figuras A1.3, A1.5, A1.7)permite determinar en octal, binario etc. Los simbolos
que representan en estas bases el peso de dichos objetos.
O sea que el metodo de simular que se pasa un bojeto, cuyo peso se conoce en base, diez con pesas de una
cierta base cuya magnitud se estima en base diez permite convertir un numero en base diez a otra cualquiera.

##**Regla para pasar un numero decimal a binario:**(no se requiere realizar dibujo alguno)
a. dado el numero a convertir, se parte de la pesa binaria que en base diez tiene un valor igual a dicho numero.o que
presenta el valor menor mas proximo al mismo; t apartir de este valor se escriben en base diez los sucesivos valores
decrecientes de las pesas binarias hasta el valor uno, siendo cada valor la mitad del anterior.
B. se coloca un uno debajo del primer balor determinado en el paso anterior. A este valor decimal se le sumara el valor
pesa que sigue a la ultima que se analizo el resultado alcanzado igual o es menor que el numero decimal a convertir,
se coloca un uno debajo del valor de esa pesa; y si ese resultado supera dicho numer se coloca un cero, para indicar
que esa pesa no se usa para balancear.
c. Los unos y cero asi determinado de izquierda a derecha son los bits del numero binario buscado

**Ejemplo**: convertir el numero 284d binario
a.=> 256 128 64 32 16 8 4 2 1 d 
b.=>   1   0  0  0  1 1 1 0 0 b    c.284 = 100011100d
en el paso a. se comenzo con la pesa del valor 256, que es la menor en relacion con 284. siendo que la de 512 lo supera.
el paso b. comienza escribiendo un uno debajo de 256. sumando el valor 128 que le sigue daira 256+128=384>284.
por lo que se coloc 0 debajo de 128. Lo mismo ocurre si intentamos sumar al 256 ya sea 64 o 32, por lo que tambien
escribimos un cero debajo del 64 y del 32, para indicar que no se han usado estas pesas. Con el paso 16. Con el peso 8
=272<284 (siendo que aun faltan equilibrar 284-272=12), por lo que escribimos un uno debajo del 16resulta 256+16 
resulta  272+8=280<284 por lo que tambien se escribe un uno debajo del 8. resultan equilibrar 284-280=4, lo cual se
consigue con la pesa de ese valor, escribiendose un uno debajo del 4. Dado que se ha equilibrado el 284 con las pesas
indicadas con un uno, no se usaran la pesas de 2 y 1,colocandose un cero debajo de cada uno de esos valores.
**Verificancion: siempre** es factible determinar si el resultado de una conversion esta bien, realizando el pasaje inverso a
base diez del numero binario hallado, segun la regla antes indicada:

256 128 64 32 16 8 4 2 1 d
1     0  0  0  1 1 1 0 0 b=(1x256+1x16+1x8+1x4)d=284d se verifica que la conversion fue bien hecha

**ejercicio**  convertir 100d a binario     respuesta:1100100b
con el presente metodo formar los numero binarios del 0 al 15, y verificar su concordancia concordancia con la fig 1.4.
 ##**Metodo para pasar de base diez a hexadecimal:**
a. Dado el numero a convertir, se parte de la pesa hexadecimal que en base diez tiene un valo igual a dicho numero, o que 
presenta el valor menor mas proximo al mismo; y a partir de  este valor se escriben en base diez los sucesivos valores
decreciente de las pesas hexadecimales a traves de siguiente ejemplo representativo.
b. Repitiendo la metodologia de las pesas desarrollada en relacion con la figura A1.7,sistematizaremos la forma 
de hallar os digitos hecadecimales atraves del siguiente ejemplo representativo.

**EJEMPLO:** convertir el numero 2574d a hexadecimales
a=> 256 16 1d
b.   A   0 Eh

en el paso a, no se pudo usar ninguna pesa de valor 4096d, por lo que se comenzo con las de valor 256d que es la menor
en relacion con 2574d. para el paso b, si usamos 10d= a pesas de 256d habremos equilibrado 10x256=260<2574(de
haber puesto 11=b pesas de 256. faltan equilibrar 2574
-2560=14 si se probara equilibrar con pesos hexadecimales que valen 16, bi seria posible colocar ninguna 
(cero), pues si se pusiera una, se tendria 2560+16=2576 excediendose el numero 2574, por lo que debe escribirse 0 pag 142

debajo del 16. Los 14 que falta equilibrar se consiguen con 14d = Eh pesas de valor uno, debiéndose escribir **E** debajo del 1

En definitiva resulta 2574d = A0Eh.

**Verificación**:

**256**  **16**  **1**
     
..A.. 0...Eh =(10x256 + 0x16 + 14x1)d = 2574d         Se verifica que la conversión fue bien hecha.

**Ejercicio**:   convertir 45056d a hexadecimal >>>>>>>>>  Respuesta: B000h 

#Otros métodos para convertir de base 10 a otra base cualquiera

##*Método de las divisiones sucesivas por la base a la que se quiere pasar:*

**1.** Dividir por el valor decimal de la base el número decimal a convertir.

Idem el cociente asi obtenido.

Idem hasta obtener un cociente menor que divisor


**2.** Este último cociente y los restos de las divisiones efectuadas, constituyenª, en ese orden, el número buscado.


##Ejemplos                 
(la justificación de este método se da en la Unidad 4 de la presente obra)

**a.** Convertir a binario los números decimales 13 y 12 

      13 | 2__                            
          
        1   6 |2__ 
             
             0   3|2__
                 
                 1  1     =  1101(base 2) = 13(base 10)



      12| 2__
       
        0   6 |2__
             
             0   3|2__
                 
                 1  1     =  1100(base 2) = 12(base 10)



**b.** Convertir a hexadecimal el número decimal 16140



      16140 |16__
         
       0140   1008  |16__
                     
        12=C   48      63  |16__
                           
                0=0    15=F  3=3      = 3F0C(base 16)= 16140(base 10)


**EJERCICIO** : Usando el presente método pasar el número 109d a binario y hexadecimal


#*¿Cómo se pasa directamente de binario a hexa, y viceversa?*
Como se anticipó al tratar el sistema hexadecimal, éste se usa para pasar de una forma sencilla de binario a hexa y viceversa **usando en pantalla o en el papel la cuarta parte de los símbolos de los que se utilizan en binario**, siendo que en el interior de un computador sólo se puede representar el sistema binario.

###*Regla para pasar de binario a hexadecimal:*

1. A partir del bit extremo derecho del número binario, dividirlo en cuartetos, agregando ceros a la izquierda si se necesita.

2. Asignar a cada cuarteto los pesos 8-4-2-1 en forma escrita o mentalmente.

3. Sumar en base diez los pesos de cada cuarteto correspondientes a los bits de valor 1, o sea hallar su valor en base diez.

4. El número resultante de cada suma así efectuada en cada cuarteto según el paso anterior, será el digito hexadecimal correspondiente a ese cuarteto, siendo que si dicho número es del 0 al 9 será el mismo en hexa; y si el mismo es 10 el digito hexadecimal será A, si es 11 será B. si es 12 será C, si es 13 será D, si es 14 será E, si es 15 será F.


##Ejemplo: 

convertir a hexadecimal el número binario 110011100

Pasos 1. y 2.    ........   **8421** .... **8421**...... **8421**

   ................................0001.......1001........1100

............................... ----- .... ----- ... ------ =  19Ch

pasos 3. y 4. ............. **1**.......8+1=9.....8+4=12=C


**Ejercicio**: 

Convertir a hexa 1010000011110111   y    1100011101     ( respuesta: A0F7h y 31Dh)

Con un método semejante y formando tríos, pasar 1101101b a octal (Respuesta: 155o)

___
ª      En caso que los restos decimales superen el valor 9, (como puede ocurrir cuando se pasa de decimal a hexa) se debe convertir dichos restos al símbolo equivalente de la base en cuestión( por ejemplo 10=A; 11=B; etc.)



pag 143


**REGLA PARA PASAR DE HEXADECIMAL A BINARIO:**

1. Separarlos dígitos hexadecimales de modo de poder formar debajo de uno de ellos un cuarteto binario a determinar de pesos 8-4-2-1. Estos números pueden escribirse o ser imaginados mentalmente. 
2. Convertir cada dígito hexadecimal de 0 a F a decimal (serán iguales del 0 al 9), y éste número a su vez en un cuarteto de pesos 8-4-2-1 por el método de las pesas ya visto.
3. El conjunto de cuartetos así formados constituirán el número binario buscado.


**EJEMPLO:** Convertir a binario el número hexadecimal A07

paso 1   ..............A...............0................7h

 ............... ......**8421**...........**8421**..........**8421**d

paso 2 ...........1010..........0000...........0111b        ............O sea A07h = 101000000111b

.....................A=10=8+2................7=4+2+1

**Ejercicio:**  Convertir a binario 10h .........................................................Respuesta: 00010000b


#A1.4|| OPERACIONES ARITMÉTICAS CON NÚMEROS BINARIOS NATURALES


##*De qué forma la UAL suma dos números?*

>En cualquier base numérica pueden definirse las distintas clases de números (naturales, negativos, imaginarios, reales, etc.), y todas las operaciones que empleamos en base diez. Estas presentan las mismas propiedades conocidas en base diez, pueden aplicarse los mismos algoritmos que conocemos para realizarlas con números de varios dígitos.

>Comenzaremos con la suma de binarios

>Si bien pueden sumarse manualmente varios números binarios ordenados uno debajo del otro, interesa especialmente operar dos números binarios por vez, como lo hacen las unidades aritméticas de los microprocesadores y las calculadoras de bolsillo.

>Para sumar en binario se debe tener presente que en la sucesión de los números naturales: 0, 1, 10, 11, ....; si se suma cero a un numero debe resultar el mismo, y si se suma uno debe obtenerse el siguiente.

>Esto se verifica en las siguientes sumas elementales, que son las variantes que tienen lugar en la suma de dos números binarios:

0+0=0  

1+0=1   

0+1=1  

1+1=10 

10+1=11


Efectuar    110110100 + 11010110

...................................................................1 1 1 1....1

...................................................................1 1 0 1 1 0 1 0 0

................................................................+... 1 1 0 1 0 1 1 0


........................................................... -----------------------------


................................................................ 1 0 1 0 0 0 1 0 1 0

.....................................................................i h g f e d c b a


La suma se ha realizado, posición por posición, como se detalla:

**a.**.. 0 + 0 = 0

**b.**.. 0 + 1 = 1

**c.**.. 1 + 1 = 10 --------------> se escribe el 0 y "me llevo 1" de acarreo ("carry") a la posición siguiente   

**d.**.. 1 + 0 + 0 = 1 + 0 = 1

**e.**.. 1 + 1 = 10 --------------> (ídem c.)

**f.**.. 1 + 1 + 0 = 10 + 0 = 10 ----(ídem c.)

**g.**.. 1 + 0 +1  = 10 -------------(ídem c.)

**h.**.. 1 + 1 + 1 = 10 + 1 = 11 ----se escribe 1 y "me llevo 1" a la posición siguiente. 

**i.**.. 1 + 1 = 10

página 144

En la resta indicadaª, toda vez que se "pide 1" si la siguiente posición del minuendo vale 1,
éste pasará a ser 0, dado que (1-1=0) como indica el reglón superior.Si la siguiente es 0 pasará 
a ser 1(10-1=1), debiéndose nuevamente "pedir 1" a la subsiguiente, que también pasará a ser 1 si es 0, 
y así sucesivamente. Si hay ceros en el minuendo se transformarán en unos, hasta llegar a un 1 que pasará a ser 0.

El procedimiento de "pedir prestado" no se emplea en los circuitos de un computador, por la complejidad y lentitud que ocasionaría.
En su reemplazo se usa el método de **sumar al minuendo el complemento al módulo del sustraendo,** cuyos pasos se indica a continuación,
y cuya justificación se trata en detalle en el **Complemento para Enteros y Punto Flotante"** que está al final de esta Unidad.


##*¿De qué forma se realiza manualmente una resta de binarios?*

La tabla de restar binaria es sencilla:

0 - 0 = 0

1 - 0 = 1

1 - 1 = 0

0 - 1 = 1  -----> y se "pide 1" a la siguiente; o sea se hace 10 - 1 = 1


..............001 ..01..0

..........10~~1~~~~1~~~~0~~0~~1~~~~0~~010

-- ............11100101

.. -----------------

 ...........10010101101

##*¿Cómo efectúa la UAL una resta sin pedir prestado, mediante una suma?*

Realizaremos la misma resta anterior sin pedir prestado, mediante **una sola suma** que hace la UAL




..........10110010010

-- ......00011100101

.. -----------------

........111......1....1

..........10110010010

. + ....11100011010

.. -----------------

 .......1 **10010101101**
 
 (El primer 1 se descarta)

 (El resultado está en negrita recuadrado)
 
 **Regla**

 1. El minuendo se sumará sin modificación.

 2. Se invierten cada uno de los bits del sustraendo, y el número así formado es el segundo operando.

 3. Se escribe un uno para ser sumado en la posición de las unidades.

 4. Sumar los tres números indicados en 1, 2 y 3 , y descartar el 1 que está fuera del formato de los n bits que se restan.
 
 Los bits restantes a la derecha del bit descartado constituyen el resultado de la resta.
 
 ##*¿Cócomo se multiplican y dividen manualmente números binarios naturales?*
 
 La tabla de multiplicar es muy sencilla, al igual que la operatoria manual (que no se usa en cálculos automáticos): se repite el multiplicando desplazado a la izquierda, conforme a la posición que ocupen los unos del multiplicador. Luego se realiza la suma de los sumandos así ordenados.
 
 0x0=0

 0x1=0

 1x0=0

 1x1=1
 
 
..........11011

X ...........101

.. ----------

..........11011

.....11011

.. -----------

...1 0000111


 
     111011 | 110_____                           
    -110         1001
	 ____
     0010
    - 000
	 _____
       0101
	-    110
	     _____
		  101
		  
La división se ha realizado con el método de las diferencias sucesivas, siendo que cada sustraendo se obtiene: multiplicando por 1 al divisor si este último es menor o igual que el resto parcial en cuestión, o por 0 si el mismo es mayor que dicho resto.


Es imporatente señalar que cada vez que se multiplica o divide un número entero binario  **por la base 10b = 2d al igual que en base diez se agrega o se quita un cero**, respectivamente:


(1011x10)b = 10110b           ...........................................................(10x10)b = 100b

(10110 x 10 x 10 = 10110 x 100)b = 1011000b(1110 : 10)b = 111b

(101011000 0 : 1000)b = 1010110b




---------------
ª Es conveniente comparar las similitudes de la resta efectuada con restas en base diez, como : 880010010 - 5349809)D 




1-132
----------------------------------------------------------------------------------------
				
				INSERTAR FIGURA 1.94
	
	Existen 4 __UE__, siendo que las dos que contienen una UAL operan al doble de la frecuencia del procesador, o sea
	que en medio ciclo completan la operacíon, siendo por ello posibles hasta 6 operaciones por ciclo. Ellas son:
	__UE0__ dedicada a uops-R "store", y __UE__1 para uops-R "load", a razón de una uop-R por ciclo.
	__UE2__: en la primer mitad de un ciclo puede operar enteros en una UAL, o una instrucción de transferencia en 
	punto flotante; y en la segunda mitad de dicho ciclo puede operar otra vez enteros en la UAL de dicha __UE__.
	__UE3__: en la primer mitad de un ciclo puede operar enteros en una UAL, u operar (en el coprocesador) todas las
	operaciones aritméticas en un punto flotante, pero no las de transferencia, o cualquier operación SIMD, o llevar a cabo
	una uop-R de salto; y en la segunda mitad de un ciclo puede operar nuevamente enteros en la UAL de dicha __UE__.

	Para uops-R load/store existe un Buffer Conversor compartido en "HT" por los dos "threads", que es una memoria
	totalmente asociativa (definida al trata cachés), que convierte direcciones a direcciones físicas de memoria.
	Después de haberse realizado la operación ordenada por cada uop-R en la __UE__ correspondiente, las uops-R
	pasan a un buffer de reordenamiento, que hace de intermediario entre la __UPRE__ y la __UR__. Este buffer se parte en 
	mitades si hay dos "threads".
	La __UR__ retira las uops-R en orden en forma alternada para cada "thread".
	Luego que las uops-R ejecutadas se retiran, los resultados pasan desde registros hacia el caché de datos L1. 
	Este es un caché asociativo de 4 vías con líneas de 64 bytes, que siempre escribe "write-through" en el caché
	asociativo L2 de 8 vías con líneas de 64 bytes, con 128 bytes por línea. Este Xeon tiene un caché similar L3.
	Los cachés L2 y L3 operan con direcciones físicas y el L1 con virtuales , pero con tags físicos.

	~~~
	De la descripción anterior resulta, que dos "thread" que se están ejecutando en paralelo comparten (en principio
	por partes iguales) la mayoría de los recursos físicos de un único procesador, ya sea por partición de los mismos o
	por alternancia (en un ciclo reloj uno y en el siguiente el otro)'y no se trata simplemente que se ejecuta un "thread"
	y cuando éste se detiene por algún motivo se pasa a ejecutar el otro.
	~~~

----

[^ Índice](README.md) | [Siguiente >](apendice1.md)