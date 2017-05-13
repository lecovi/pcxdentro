# El Software, los datos y su codificación

### *¿Qué es el software o "logical"?*
---

Además de la velocidad y confiabilidad, no cabe duda que la versatilidad es otra de las características relevantes de las computadoras. A partir de su uso inicial como calculadoras automáticas, poco a poco han ido invadiendo distintas áreas de aplicación: científica, industrial, administración pública, apoyo profesional, entretenimientos, modelación, enseñanza, etc. (en el Apéndice se hace una reseña de estas aplicaciones). 
Esta versatilidad es también observable en muchas herramientas que usamos, incluidas las primeras: nuestras manos. Pensemos también en los múltiples usos que puede tener un simple cuchillo, según la forma de tomarlo, moverlo, porción de filo usada, etc. En el conjunto cuerpo humano-cuchillo, el cambio de plan de uso se *realiza fácil y rápidamente* en nuestro cerebro, sin modificación física visible. 
Otra actividad o proceso cotidiano, útil para comprender los conceptos de hardware y software, es la elaboración de comida. En ella distinguimos: 

1. **Una parte fija, estable y tangible**, constituida por una persona, la cocina y sus utensilios, que serán los medios físicos ("hardware") con que se cuenta para llevar a cabo la elaboración. 

2. **La receta o procedimiento**, que depende del plato deseado. Ella instruye ordenadamente cómo usar los medios físicos en cada paso de la elaboración de los ingredientes. Es el plan lógico ("software").

Nos encontramos con un tipo de proceso versátil, con múltiples resultados (platos distintos), llevado a cabo mediante un mismo equipamiento físico, y un sinnúmero de planes lógicos de elaboración posibles. Éstos son fáciles de cambiar en nuestra mente. Están pensados en función de los medios disponibles, y están limitados a los mismos. Por ejemplo las recetas de una cocina a gas no sirven para un asador al aire libre. Asimismo, *con el equipamiento físico solo no se puede hacer nada, si falta el plan lógico correspondiente.*

Un computador no sabe cómo procesar datos. Se le debe indicar mediante instrucciones: dónde están los datos a procesar, qué procesamiento realizar con ellos, y hacia que medio irán los resultados obtenidos.|
:-|

Hacia 1946 en la Universidad de Pennsylvania funcionaba el prototipo de computador ENIAC descripto en el apéndice A3 de esta unidad. El mismo, una vez programado realizaba velozmente una serie de cálculos que se necesitaba efectuar en forma repetida, en cada oportunidad con datos distintos. Si hacía falta realizar otros cálculos distintos había que *reprogramarla cambiando el cableado de un panel*, lo cual podía insumir horas. El matemático de esa universidad, John von Neumann, para solucionar esto planteó la necesidad de almacenar en una sola memoria interna electrónica de rápido acceso (la memoria principal), por un lado el programa a ejecutar, y por otro los datos a procesar. Este es uno de los postulados del llamado **"modelo de Von Neumanan"** (Ver apéndice A3 citado). 
De esta forma, de poderse cambiar rápidamente en dicha memoria el programa a ejecutar, se podrían realizar nuevos cálculos, sin necesidad de modificar el conexionado de circuitos de la máquina, con la pérdida de tiempo que ello implica.
Un programa (software) almacenado en la memoria principal de un computador, si bien está registrado en ella, no forma parte material de los circuitos que la constituyen (hardware) 
Estar registrado significa que esos circuitos quedarán en determinados estados eléctricos en su interior, que representarán al programa citado, que en la figura 1.9 hemos asimilado a posiciones de llaves "si-no" Estos estados pueden hacerse equivaler a una determinada configuración espacial de "unos" y "ceros" en la memoria, que se mantendrá mientras no se ordene memorizar otro programa en reemplazo del existente. De ser así resultará otra configuración interna de estados eléctricos, que corresponderán a los "unos" y "ceros" del nuevo programa. 

> Entonces, cuando se cambia el software no hay cambio material de componente alguno del computador: el hardware permanece invariable. Solo se modifica el estado eléctrico del material semiconductor que compone los circuitos de la memoria.

Han ocurrido cambios energéticos localizados; la materia sigue constante. En el caso de las llaves "si-no" citadas, en cada una se habrá estirado o encogido un resorte por la acción de nuestra mano pero no hay cambios materiales.

Por esta manera fácil y veloz de cambiar de programa en el interior de un computador, éste resulta una herramienta tan versátil para efectuar cualquier proceso de datos. Cambiando el programa se modificará el comportamiento de la máquina.|
:-|

Una computadora para aplicaciones comerciales puede convertirse en una de tipo científico utilizando un programa adecuado. Se modifica el procedimiento sin cambiar de equipo.
En todos los casos descriptos nos encontramos con el aprovechamiento *múltiple* de un mismo equipamiento físico (**hardware**), como si cada procedimiento programado que se ordena realiza (**software**) generara un dispositivo físico *a la medida* del proceso que ordena ese plan.

> Conforme con lo anterior, resulta que el hardware proveé funciones procesadoras, que son activadas por cada una de las instrucciones de un programa ejecutado según ellas.

Cada marca y modelo de computador *tiene un repertorio definido de códigos de instrucciones que puede ejecutar*, acorde a las posibilidades funcionales de su hardware.
No acepta instrucciones que no pertenezcan al mismo. Una misma instrucción, como ser sumar, tiene distinto código en dos procesadores distintos.

Software de un computador es cualquier programa[^1] que puede ser almacenado total o parcialmente en su memoria principal, para ser ejecutado por el procesador de dicho computador.|
:-|

Su nombre hace referencia al hecho de que los programas son materia dúctil, "blanda" ("soft" en inglés). Esto es, *los programas son fáciles de modificar, y de cambiar unos por otros en la memoria principal* de un computador, para que éste, siendo hardware fijo, sea una herramienta de múltiples usos. Dicha facilidad se debe a que *los programas no forman, físicamente, parte del hardware, sino que ésta les sirve de soporte material.* Únicamente se modifica el estado eléctrico de los circuitos de la memori, principal, mediante señales eléctricas ºtransparentes" al operador o al proceso. El software también puede registrarse en cintas, discos magnéticos u otros medios.

La *esencia* del software *son los algoritmos[^2] que el expresa, representa.* Ellos son *expresados* mediante programas usando determinados lenguajes. Cada programa que puede ejecutarse en un computador -al ser almacenado en memoria, y luego ejecutado- permite llevar a cabo un cierto proceso de datos. Debido a esta relación del software con algoritmos, es que a veces se lo denomina **"logical"**.

> Un computador con todos sus circuitos electrónicos energizados, pero sin ningún programa en memoria principal, no puede procesar datos. *No sabe qué hacer.* Es sólo "puro hardware". Cada instruccíón que es ejecutada por la UC da lugar a una secuencia predeterminada de movimiento de datos, y operaciones en la UAL, que se desarrollan con los pulsos reloj. O sea *que cada código de instrucción determina implícitamente qué partes del hardware se activarán y en qué orden,* según se verá. 
> Por lo tanto, puede afirmarse que "el software controla al hardware". En ese sentido cuando de una secuencia de instrucciones se salta a otra distinta, correspondiente a una subrutina o a otro programa, se habla de "transferencia de control", vale decir que el control se ha transferido a la nueva secuencia en ejecución.

En el apéndice A.2 se encontrará una clasificación del software, donde se incluyen la función de un sistema operativo y de programas utilitarios, así como el software constituido por los denominados "virus".

---
[^1]: Sean del sistema operativo, del usuario (procesadores de texto, base de dato, traductores de lenguajes, de juegos), de diagnóstico, etc.

[^2]: Un *algoritmo* es un procedimiento que asegura, mediante un número finito de pasos, una salida requerida, a partir de una entrada dada, independientemente del tiempo en que se realiza. Las conocidas reglas aprendidas en la escuela primaria para realizar manualmente las cuatro operaciones aritméticas, son algoritmos.

### *¿Qué es el firmware?*
---

Un computador encendido sin ningún programa en memoria principal (MP) no puede hacer nada. Los programas que residen en la porción RAM de MP *desaparecen cuando se apaga un equipo.*

> Por ello cada vez que se enciende, hay que traer del disco a memoria una copia del sistema operativo (SO). Esta acción se conoce como *"arranque"* o *"boot"* o **"buteo"¨** (ver detalle en la sección 1.15).

Todavía en la década del 70, luego del en encendido había que escribir en MP un pequeño programa en forma manual, mediante llaves "si-no" dispuestas en el panel frontal del computador. Al ser ejecutado este programa traía a MP, del disco o cinta, programas constituyentes del SO. 
En el presente, al encender un computador el arranque es automático, sin intervención manual, merced a que está almacenado en la porción ROM de MP un primer programa, que permite traer a MP los programas del SO archivados en un disco. 
También están en esta ROM programas de diagnóstico (que verifican el correcto funcionamiento y configuración del hardware antes de traer el SO), y programas que son invocados cada vez que se necesita realizar una entrada/ salida, constituyentes del BIOS (Basic Input Output System). 
Se trata, pues, de software que está *permanentemente fijo* en el hardware, o sea que una vez que un programa o varios se han escrito en la porción ROM de MP, permanecen siempre almacenados en MP. Así, estos programas se conservan inalterados aunque se corte la energía del equipo, por ser la ROM "no volátil", listos para ser usados toda vez que sea necesario si el equipo está encendido.
No necesitan ser traídos de un disco para ser re-escritos en MP. Recordemos que una ROM es también una memoria "random" como una RAM, con tiempo de acceso de 3 a 5 veces mayor que ésta. Además de programas, una ROM se usa para conservar en forma permanente tablas de datos y constantes.

En forma extensiva, se denomina firmware al software (programas) almacenado permanentemente en el hardware constituido por una memoria ROM soportada por circuitos electrónicos.|
:-|

Decimos en forma extensiva, por que la palabra "firmware" se acuñó en relación con la ROM que existe en la UC de los procesadores "CISC"[^3], como los 80x86 de Intel. Según se verá (sección 1.7), en esta ROM están guardadas las combinaciones binarias ("micro-códigos") que le indican a la UC la secuencia de acciones necesarias para ejecutar cada instrucción. Ellas constituyen la "inteligencia" de un procesador. Un programa contenido en un disco CD ROM no es firmware, pues no es una ROM circuital. 

### *¿Qué es un microprocesador dedicado?*
---

El microprocesador (80x86, Pentium, Power PC, 88000, etc.) que caracteriza un computador, es su procesador "central". La memoria de la cual lee las instrucciones a procesar, es *predominantemente RAM*, si bien tiene una pequeña porción ROM para el arranque y el BIOS. Esto es así por que en un computador para uso general debe poderse cambiar el software residente en memoria principal, según las necesidades del usuario (programas para procesar texto, para planillas de cálculo, para base de datos, para juegos, etc.).

Un sistema de computación también presenta **"procesadores dedicados"** y **microcontroladores** ( éstos en el chip también contienen memoria principal y registros "ports". *Son como una computadora en un solo chip*). Dada la complejidad de los periféricos actuales, su electrónica requiere de un microprocesador para controlar las operaciones que realiza, siendo que su costo en general es mucho menor que el del procesador central citado Encontramos procesadores dedicados en el teclado, en una impresora láser, en la plaqueta de un módem, en la electrónica de una unidad de disco rígido, entre otros.
Puesto que *un procesador dedicado se caracteriza por ejecutar siempre los mismos programas*[^4], éstos se encuentran residentes en algún tipo de memoria ROM (firmware) que oficiará de memoria principal del procesador dedicado. No debe confundirse con la memoria principal del procesador central. En general, para este último, los procesadores dedicados y los programas de los mismos le son "transparentes".
Se comprende que un procesador dedicado necesita que sólo una pequeña porción de su memoria principal sea RAM. Esta puede no necesitarse si los datos que procesa y los resultados que obtiene entran en los registros del procesador dedicado, en cuyo caso la memoria principal del mismo sería totalmente ROM.

---

[^3]: Siglas de Complex Instruction Set Computer, o sea computador con instrucciones complejas en su repertorio de instrucciones. 

[^4]: Por lo cual, dada su sencillez, en general no requiere de un sistema operativo. 


### *¿Cómo se prepara el proceso de datos en el computador antes definido, cómo se le ordena a éste qué debe hacer?*
---

En cualquier proceso de datos con computador, es indispensable escribir en memoria los datos las instrucciones del programa, antes de comenzar a ejecutar éstas. El programa Debug permite realizar fácilmente esto por medio del teclado[^5] como se describe en la próxima pregunta. 

Es esencial releer paso a paso la explicación , relacionada con las figuras 1.2 y 1.3, pues sirve de base para comprender cómo funciona un computador, y para experimentarlo en una PC, así como para los temas que siguen. Al final del Apéndice A1 se da un ejercicio integrador basado en el ejemplo aquí desarrollado.|
:-|

El proceso de datos a codificar, que será luego llevado a cabo en una PC es semejante al proceso manual que ilustra la figura 1.2. Dicho proceso estaba descrito por la secuencia de instrucciones I1 a I5. Por simplicidad didáctica codificaremos y ejecutaremos las 4 primeras, o sea que efectuaremos **R = P + P - Q** Supondremos que los datos son **P** = 1020H y **Q** = 2040H[^6]. 

##### *1. Codificación de los datos:*

Primero escribiremos en memoria estos datos de dos bytes que en binario serían: son 0001 0000 001O 0000 1020H y 0010 0000 O100 0000 = 2040H, conforme a las equivalencias dadas por la tabla de la figura 1.4, detallado en el Apéndice 1. Dado que cada celda de memoria guarda un byte, **P** y **Q** deben ocupar dos celdas sucesivas cada uno[^7]. Se han asignado *arbitrariamente* las direcciones *5000H* y *5001H*[^8] a **P**, y *5006H* y *5007H*[^9] a **Q** (en la fig 1.15 se supone escritas **P** y **Q**). Nótese que primero en la dirección más baja (*5000H* para **P** y *5006H* para **Q**) se escribe en la UCP de Intel™ la mitad derecha de cada número (20 y 40 respectivamente). __O sea **XXYY** se escribe **YYXX**.__ Al resultado **R** de hacer **P + P - Q** le asignaremos direcciones *5010* y *5011*, asumiendo que ocupará 2 bytes. 
Las direcciones también están escritas en hexa, aunque *dentro de un computador sólo pueden existir unos y ceros.*

La dirección de un dato puede ser elegida arbitrariamente, siempre que dicha dirección sea la que forme parte de instrucción que va a operar dicho dato, puesto que una instrucción debe indicar cómo localizar el dato a operar.|
:-|

##### *2. Codificación de las instrucciones en código de máquina:*

Habiendo establecido que el dato 1020H ocupará las direcciones *5000H* y *5001H*, y que el dato 2040H estará en binario en *5006H* y *5007H*, ahora se pueden codificar y escribir las instrucciones, puesto que como veremos, *para codificarlas se requiere __primero conocer las direcciones elegidas__ donde se han guardado los datos.*

La combinación binaria que codifica una instrucción constituye su "código de instrucción" o "código de máquina"[^10], en el sentido que es el código que "entiende" la máquina, o sea los circuitos de la UC. **Cada procesador tiene sus propios códigos de máquina que puede ejecutar.|
:-|

El código de máquina comprende necesariamente el **código de la operación** (cod-op) ordenada (transferir, sumar, restar, comparar, dividir, saltar a otra instrucción... ). Si el dato a operar está en memoria, __al cod-op le sigue una dirección__[^11] que indica dónde éste se encuentra (o dónde memorizar un resultado que está en un registro de UCP, si se ordena una escritura). __No confundir el valor de un dato con el valor de su dirección.__

---

[^5]: En la práctica esto sólo ocurre cuando se desarrollan o modifican programas, dado que el sistema operativo se encarga de manejar la escritura rápida en memoria principal de las instrucciones de los programas a ejecutar, que trae del disco. Así, cuando desde Windows llamamos a un procesador de texto, este programa en pocos instantes está en memoria, esperando qué módulo del mismo se va a ejecutar, de acuerdo con nuestros requerimientos. Los datos (letras, palabras) van entrando a memoria a través del teclado, a una velocidad que depende del usuario, siendo también ubicados en la zona de memoria que se les ha asignado mediante la ejecución de subrutinas.

[^6]: Sumar 1020 + 1020 resulta 2040 tanto en decimal como en hexa (H), pero como se indicó anteriormente, la cantidad de unidades que representan los sumandos y el resultado son distintas en ambos sistemas de numeración. Se han elegido ex profeso, por razones didácticas, los datos indicados, ara evitar resultados ue recién ueden inte retarse en conocimiento el Apéndice 1. Se ha revisto que el resultado sea cero.

[^7]: Cuando en un computador un dato o una instrucción no entra en una posición de memoria, se fragmenta en posiciones sucesivas, y se localiza por la dirección de la primera.

[^8]: Como se verá, el Debug permite escribir direcciones desde la 0100 H = 0000 0001 0000 0000 binario hasta la FFFF H = 1111 1111 1111 1111 binario = 65535d, por lo que se dispone cerca de ese número de celdas (bytes) libres para almacenamiento. 

[^9]: Las letras **P** y **Q** que en alto nivel se denominan **variables**, __**a nivel de máquina se corresponden con las direcciones de memoria**__ (5000H Y 5006H) elegidas para las mismas .. Los valores particulares 1020H y 2040H que en esta oportunidad tienense han asignado a dichas variables se corresponden con los contenidos a escribir en esas direcciones de memoria (o sea los mismos 1020H y 2040H).

[^10]: Los archivos que guardan instrucciones en código de máquina se denominan **"archivos de código"** o **"ejecutables"**.

[^11]: O un número relacionado con ella. Si el dato está en un registro de la UCP el código de operación determina de qué registro se trata.

En general una instrucción ordena una __operación__ (mediante su cod-op), y en relación con ésta permite __localizar__ uno dos __datos__ a operar (en este caso dando su dirección en memoria), e indica dónde guardar el resultado.|
:-|

El formato de las instrucciones usadas es: 
|CODIGO DE OPERACIÓN | DIRECCIÓN DEL DÁTO |
|---|---|

![Figura 1.15 - Memoria Principal DRAM](/figura-1-15.jpg "Figura 1.15 - Memoria Principal DRAM")

Teniendo presente el proceso de datos con calculadora de la figura 1.2, la instrucción **I^1** del mismo, adaptada para una PC, ordenarla la operación de 'transferir (mover) hacia el registro **AX** (de **2 bytes**) una copia de un número de 2 bytes localizable en la dirección de memoria que indican los dos últimos bytes de la instrucción" ( en este caso es 5000H). O sea escribir en **AX** una copia del número 1020H, que es el que se encuentra en dicha dirección[^12] en este ejemplo, lo cual implica que se destruirá el número que antes estaba en **AX**.

Esto puede simbolizarse así: AX &lt;--- M5000 y 5001|
:-|

Para un procesador de Intel o de AMD el cód-op que ordena la operación escrita entre comillas es **A1H** = 10100001. [^13]
El código de máquina de **I1** comprende su cod-op **A1**, seguido de la __dirección__ del dato a operar (en este caso fue elegida 5000H[^14]). Por lo tanto, el código de máquina completo que se escribirá en memoria (figura 1.15) es **A1**0050H = **1010 0001** *0000 0000 0101 0000* en binario, o sea que **I^1** consta de 24 bits= 3 bytes, por lo que ocupará tres posiciones consecutivas de memoria. Se ha elegido arbitrariamente para 11 (y también para la secuencia de instrucciones a ejecutar) que la primer dirección a partir de la cual se escriben los tres bytes que la fonnan sea *0200H*. O sea que 11 ocupa las direcciones *0200H* a *0202H*, con su código de máquina fraccionado en **Al**, 00 50 en esas direcciones.

> Es importante notar que *00 50* o sea *5000* __es la dirección__ del dato, que forma parte del código de la instrucción, sin la cual cuando se ejecuta **I**^1 no habría manera de encontrar __el dato que es 20 10__, o sea 1020.

La instrucción **I^2** ordena "sumar al número contenido en el registro **AX**, una copia del número de 2 bytes localizable en la dirección de memoria queindican los dos últimos bytes de la instrucción" (que en este caso vuelve a ser *5000H*, por haberse sumado **P + P**).

En símbolos: AX &lt;--- AX + M5000 y 5001|
:-|

O sea sumarle al número que existía en **AX** una copia del número 1020H (que es el que está en dicha dirección), y el resultado escribirl0 en lugar del número que existía en **AX**. La operación escrita entre comillas la ordena el cod-op 0306H, al cual debe seguirle la dirección del dato (5000H), por lo que el código de máquina de **I^2** será 0306 0050H (0050 corresponde a 5000 con las mitades traspuestas) que en binario es: **0000 0011 0000 0110** *0000 0000 0101 0000*. Estos 32 bits = 4 bytes obligatoriamente deben ser escritos a continuación del código de **I^1**, o sea que ocupará las posiciones *0203H* a *0206H* (figura 1.15).

**I**^3 ordena "restar al número contenido en **AX** una copia del número de 2 bytes localizable en la dirección de memoria que indican los 2 últimos bytes de la instrucción"[^15] (*5006H* en este caso, donde está el dato 2040 H).

---

[^12]: En gran medida es equivalente a pulsar **MR** en una calculadora de bolsillo, si previamente se ha memorizado 1020, con lo cual este número aparecerá en el visor, sin importar lo que el visor tenga antes. Dado que, como dijimos, los circuitos de cálculo y el registro acumulador de la UCP se comportan en gran medida como una calculadora, **es importante ir notando que las instrucciones** (códigos) **de máquina más simples** -que son también las mas usadas- **ordenan operaciones del tipo de las que realiza una calculadora.**

[^13]: Los códigos que usaremos para las instrucciones son los reales que "entiende" cualquier microprocesador de Intel™, del 80286 al Pentium, o sus "clones" de AMD. Pueden hallarse usando el Debug, como se indicará, al tratar Assembler en la Unidad 3. En relación a los códigos, si en lugar del registro AX se hubiera usado el BX para la misma orden, el código hubiera sido 8B 1 E H

[^14]: Si bien el dato a operar está en las direcciones .5000H y 5001H, basta con dar la primera, dado que el código de operación (AlH) cuando se ejecute la instrucción ordenará a la UCP pedir lo que está en 5000H y 50001H. El Debug simula un 286, por lo que en este ejemplo estamos operando con números del tamaño de un word. Cambiando el código de la instrucción puede ordenarse leer sólo la dirección 5000.

[^15]: Como si en una calculadora que hemos memorizado el número 2040 pulsáramos sucesivamente las teclas **- MR =** .

__No confundir el dato (2040) con su dirección (5006) indicada en la instrucción__ en estas instrucciones.
Su código_de máquina será: 2B06 *0650* H, que también ocupará 4 bytes (direcciones *0207* H a *020A* H[^16] ).

En símbolos la operación que ordena I^3, puede escribirse: AX &lt;--- AX - M5006 y 5007.|
:-|

Por último, **I^4** ordena "transferir hacia las 2 posiciones de memoria cuya primer dirección indican los dos últimos bytes de la instrucción (en este caso *5010*) una copia del número que está en el registro *AX*"[^17]. El código de operación A3 ordena la operación entre comillas, seguido de la dirección que en este caso es 501O, o sea que el código de máquina será A31050.

En símbolos la operación que ordena I^3 puede escribirse: M5010 y 5011 &lt;--- AX|
:-|

En la figura 1.15 en las celdas de R no aparece  ningún  valor,  puesto  que  el  resultado  (0000) queda memoria luego de ejecutar las cuatro instrucciones, como se ejemplifica usando  el  Debug en  la  sección empieza en la página siguiente. También en ella se verá el procedimiento por el cual se escriben en memoria en las direcciones elegidas, los  valores  de  los  datos  a procesar,  y las instrucciones (*en la práctica programas del sistema operativo se encargan de ello*).

La dirección (0200) de I^1 es *arbitraria*, dado que si cuando I^3 se va a ejecutar el registro IP tiene esa dirección será localizada por la UC encargada de ejecutarla. A partir de esa dirección, el cod-op de esa instrucción y de las siguientes indica lo que debe sumarse al IP para localizar la siguiente instrucción a ejecutar. El número a sumar al IP es la cantidad de celdas que ocupa cada instrucción. Es el sistema operativo, quién decide cual será la dirección de la primera instrucción de un programa, la cual llegará al IP merced al programa cargador.|
:-|

### *¿Qué sería "alto nivel" y "bajo nivel" en la codificación realizada?*
---

Cuando escribimos la ecuación **R = P + P - Q** estamos indicando una serie de operaciones aritméticas, cuyo resultado -que depende de los valores que les asignemos a **P** y **Q** les asignemos- debe asignarse a **R**.
Se trata de una forma bastante abstracta y compacta de codificar *varios* pasos a realizar, que el lenguaje matemático permite así formular. Dicha expresión que resume un proceso a realizar, en una PC hemos visto que requiere cuatro instrucciones (procesos a realizar) que hemos codificado en hexa A10050 03060050 2BO6O65O y A31O5O, códigos que en memoria principal se almacenan en binario.
Las dos formas de codificar que debe hacerse (**R = P + P - Q** y los códigos citados), ordenan realizar el *mismo* proceso. La expresión matemática lo hace en una forma más compacta y fácil de expresar para nosotros, mientras que los códigos de las instrucciones a ejecutar amen de resultar poco manejables para el hombre, están codificados en un lenguaje que sólo pueden entender los procesadores de Intel™ o AMD. Así mismo, el proceso a realizar ha sido descompuesto en 3 subprocesos (uno por instrucción) acorde a lo que es capaz de realizar y "entender" (decodificar) la máquina. La forma "matemática", abstracta, de codificar más familiar a nosotros, se dice de "**alto nivel**", y es la que se emplea para programar procesos en los lenguajes de alto nivel (Fortran, Pascal, Cobol,Basic, C, Java, etc.).
En cambio, la codificación binaria al nivel de códigos de instrucción que "entiende" una máquina determinada se denomina de "**bajo nivel**" o "**nivel de máquina**" o "**código de máquina**" o "lenguaje absoluto" de máquina".
Cuando antes codificamos la expresión matemática en cuatro instrucciones, de hecho hemos pasado de alto a bajo nivel. Esta *traducción* en las primeras computadoras era realizada por personas que codificaban en binario las instrucciones para el computador, mediante llaves existentes en un panel frontal.
Posteriormente este proceso fue realizado por programas denominados "**compiladores**" encargados de traducir las órdenes codificadas en un lenguaje de alto nivel que estaban en memoria principal, en códigos de instrucciones, que también quedaban en memoria. Para Java se usan traductores tipo "**intérpretes**".

Un programa en alto nivel que fue  traducido por ejemplo para un 80x86, no puede ser ejecutado por otro procesador y viceversa. Para cada procesador existe un compilador creado sólo para el mismo.|
:-|

Como se verá, cuando una instrucción se ejecuta, para que se lleve a cabo el subproceso que ella ordena, la UC lo lleva a cabo mediante una serie de movimientos o subprocesos menores, más simples, que los circuitos de la UCP y memoria pueden realizar.

---

[^16]: En hexa al 0209 le sigue el 020A, y no el 021 O como sería en decimal,. Esto es acorde con que en la tabla de la figura 1.4, al 9 le sigue A. Esto se trata en detalle en el Apéndice A1.

[^17]: Esta instrucción en una calculadora es equivalente a pulsar **M+** (suponiendo que **MC** fue pulsada previamente). Así en ésta para efectuar **A + B** y memorizar, primero hay que llevar **A** al visor y luego sumarle **B**, y tercero memorizar con **M+** el resultado (pudiendo ser necesario pulsar antes **CM**).