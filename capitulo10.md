[^ Índice](README.md) | [Siguiente >](capitulo11.md)

---

## **ENTRADAS Y SALIDAS: SEÑALES, PERIFERICOS, BUSES Y PORTS EN EL CAMINO QUE REALIZAN LOS DATOS.**  

Hasta el presente habíamos mencionado brevemente la función de los periféricos en la sección 1.3 (figura 1.6 y 1.7), y nos habiamos ocupado de la **porción central** – vale decir, el procesador y de la memoria principal – sin importarnos cómo datos e instrucciones llegan a memoria, ni como de ésta salen al exterior. Ahora en un primer acercamiento trataremos esta cuestión, siendo que en la Unidad 2 de esta obra referida a periféricos y E/S se la considera más en detalle.

**¿Cómo viajan los bits de un lugar a otro en un computador?**

Durante un proceso de datos, los bits de los números binarios que representan ya sea dando instrucciones, direcciones o resultados, pueden existir dentro de un computador de dos formas:

 - Almacenados (en registros o posiciones de memoria durante un tiempo que depende de la próxima utilización), o
 - Transmitiéndose por líneas conductoras a velocidades electrónicas (cercanas a la de la luz) de un lugar de almacenamiento (origen) a otro (destino), siendo que viaja hacia el lugar de destino una copia de los bits del lugar de origen.

Al tratar la memoria se planteó una analogía con llaves (figura 1.9), en el cual cada bit se guarda como uno o cero, según uno de dos estados posibles “si-no” de cada llave, en la memoria o en registros.   
En un computador esos dos estados son generados por medios circuitos electrónicos, por lo cual en una escritura se puede pasar muy rápidamente de un estado al otro para cambiar el valor del bit almacenado.

Con el fin de aproximarnos más a funcionamiento eléctrico de estos circuitos supondremos (figura 1.46) que a cada llave de cualquier celda de memoria o registro donde se guardan bits por un lado está conectada a 5 volts, proporcionados por una pila que simula la fuente de alimentación del equipo, y por otro lado está conectada a un "cable de salida".
![enter image description here](https://lh3.googleusercontent.com/-EzEoKDd1EFg/WThciftoXeI/AAAAAAAADO0/veQWLxAzkNYCWwSQxUh8egvfXWGmSCeBgCLcB/s0/figura+1.46+y+1.47.jpg "figura 1.46 y 1.47.jpg")

Cuando la llave está en “no” (**0** almacenado), por estar abierta no permite que los 5 volts de tensión – que le llegan por el cable que la une con la pila – pasean al “cable de salida” hay 0 volts implica que la llave está en “no”, o sea que existe almacenado un bit de valor cero.
Por el contrario, con la llave en “si” (**1** almacenado), por estar ella cerrada, unirá el cable que sale de la pila con el “cable de salida”, lo cual indica que la llave está en “si” (existe almacenado un bit que vale **1**)

Si la llave durante un tiempo está en “no”, durante otra está en “si” y luego otra vez está en “no” graficando a lo largo del tiempo el valor de la tensión eléctrica que se mediría (en volts) en el extremo del cable que sale de ella, resulta la figura 1.47. Este tipo de señales eléctricas, restringida a tomar dos valores o niveles (alto o bajo) se denomina **señales digitales binarias**  simplemente binarias.


Resulta así que el valor (o volts ó 5 volts) que aparece en el "cable de salida", es una señal eléctrica indicadora en el lugar de destino (en el extremo del cable), de la existencia de un cero o un uno almacenado.

Puede decirse que el bit de valor **0** ó **1** que sucesivamente memorizó la llave se manumitió a través del cable que sale a la llave hasta el lugar de destino, donde su valor (0 ó 1) es detectado merced al valor de la señal eléctrica binaria censada en el destino.
Esta señal eléctrica es pues "portadora" y transportadora de información binaria.
![enter image description here](https://lh3.googleusercontent.com/-oAez9C-xz6o/WThjaxgCS4I/AAAAAAAADPI/f5l1eHTHXSwhKeNfcN0n0vMoM35ibZtKACLcB/s0/figura+1.48+y+1.49.jpg "figura 1.48 y 1.49.jpg")
Si consideramos 8 llaves como las que imaginamos para una posición de memoria, suponiendo que cada una de ellas lleve un cable hasta un microprocesador, éste podrá censar si cada llave guarda un **0** ó **1** de la forma vista. Basta una sola pila conectada a todas las llaves, para detectar si cada una transmite o no -según esté cerrada o abierta- los 5 volts de la pila. Asimismo, deberá llegar al microprocesador el cable conectado al negativo común ("masa" o "tierra") respeto del cual se mide la tensión eléctrica del cable de salida de cada llave.
Así operan los conductores del bus que comunican la memoria del microprocesador.
En la figura 1.49 se supone que en una primer operación de lectura se leyó la combinación 01100001, en una segunda la 11100010, y después la 01011111. En correspondencia las líneas del bus a lo largo de ese tiempo tendrán los valores dibujados, resultando en cada línea una señal digital binaria.
Para un bus de 32 líneas de datos puede imaginarse un mecanismo similar de transición hacia la UCP, desde 32 llaves, cuando se leen 4 posiciones consecutivas de memoria.

Lo descripto para un movimiento de datos desde memoria al microprocesador vale también para otro en sentido inverso, por ejemplo, cuando en una escritura de memoria, una copia del registro de datos (RDA) debe ir hacia memoria. Hay que imaginar llaves que en RDA guardan una combinación de bits, con cables que salen de ellas hacia la memoria. El esquema sería el mismo que la figura 1.48, cambiando sólo los nombres del origen y destino. Estos cables del bus de datos, son los mismos que los anteriores, pero cambia el sentido de transmisión cuando se usan para enviar bits de la UCP a memoria.

También opera conforme al esquema de la figura 1.48 el bus de direcciones, que como se trató, tiene un solo sentido de envío: del microprocesador a memoria. En la sección 1.4 se planteó que -como en un control remoto de TV- en el registro de direcciones RDI se formaba (suponiendo con llaves "si-no") el número binario que era la dirección que se enviaba a memoria para acceder directamente a la posición a leer o escribir. Los cables que salen de estas llaves van hacia memoria, constituyendo el bus de direcciones.

##**¿Qué diferencia existe entre transmisión de bits en paralelo y en serio?**

En la figura 1.48, la existencia de 8 cables para transmitir bits de datos, implica que en el destino (microprocesador en este caso) se puede conocer simultáneamente el estado de las 8 llaves, a través del valor que indica el cable que sale de cada llave.

	Esta forma de enviar varios bits juntos[^1] de un lugar al otro por varios cables, se denominan **transmisión paralelo.**

En cualquier punto de un cable, la tensión eléctrica en un instante corresponde en volts al valor **0** ó **1** del bit que se está trasmitiendo. **No es posible que en un mismo cable de tramo esté a 5 volts, y a otro a 0 volts.**

	Lo anterior implica que por un cable se puede enviar un solo bit por vez.

Si se quiere enviar 8 bits a la vez, hacen falta 8 cables, pudiendo estar cada uno a 0 ó 5 volts.

La combinación 01100001 trasmitida por 8 cables, también puede enviarse por un solo cable.

	**La transmisión serie** o "serial" supone enviar por un solo cable, uno tras otro, los bits que se quiere trasmitir.

Cuando se transmite por 8 líneas una combinación de bits en paralelo, como la 01100001(figura 1.48),en el extremo de dichas líneas el valor **0** ó **1** del bit trasmitido se determina en cada cable individual, conforme al valor de tensión (0 ó 5 volts)existente. Asimismo, la posición relativa de las líneas -siempre fija- determina la ubicación de cada bit en el conjunto de los 8 trasmitidos.

En la trasmisión serie, para poder distinguir ceros o unos repetidos se quiere que los 5 ó 0 volts que representa cada bit, **duren un lapso de tiempo fijo estipulado**.
![enter image description here](https://lh3.googleusercontent.com/-aHWKXDx3k6A/WThqt4nEvxI/AAAAAAAADPc/dRFDwQ-BYHMBJkdsjesePnxchmOuZ7yXgCLcB/s0/figura+1.50.jpg "figura 1.50.jpg")

Por ejemplo si en un cable cada bit dura un milisegundo, para transmitir en sentido la combinación 01100001 (figura 1.50), en un extremo del mismo durante 1 milisegundo se deben detectar 5 volts (por el "uno" final) seguidos de 0 volts durante 4 milisegundos (por los cuatro "ceros) seguidos de 5 volts durante 2 milisegundos (dos "unos"), y por último 0 volts durante otro milisegundo (por el "cero" de la izquierda)[^2]
O sea, que la transmisión en serie requiere sincronizar ambos extremos de la línea. Llevaría 8 milésimas de segundo enviar los 8 bits (contra una milésima si se hace en paralelo con la misma duración de cada bit).

En lugar de la figura 1.50 completa, suele escribirse la secuencia 01000011, ó también directamente la forma de onda dibujada. Siempre debe tenerse presente que se trata de una representación en el tiempo y no en el espacio. O sea que 01000011 ó dicha onda **no simbolizan una trasmisión de 8 bits "cruzando" un cable al mismo tiempo** (como autos que pasan sobre un puente en caravana).
Como se subrayó, cuando por un cable se trasmiten en serie dichos bits, sólo puede enviarse un bit por vez por el cable. En la figura 1.51 se supone que de la secuencia 01100001 ya se ha enviado 01 y se está trasmitiendo un "cero". Es como tener un puente que puede ser cruzado de a un vehículo por vez.
Igualmente, para ocho cables  (figura 1.52), si se deben enviar sucesivamente las combinaciones 01100001, 11100010, y 01011111 antes citadas, sólo se podrá enviar una por vez, resultando en el tiempo en cada línea los valores indicados en la figura 1.49.

> Mientras que en la trasmisión en paralelo con n cables se puede enviar y recibir n bits simultáneamente, en la trasmisión serie enviar bits demanda n veces el tiempo asignado a la duración de cada bit.

[^1]:  En general en un bus de datos se envían 8, 16 ó 64 bits simultáneamente, según el word de memoria que maneja el procesador. EN cambio en un bus de direcciones, la cantidad total de bits depende de la capacidad de la memoria. En las memorias DRAM una dirección se envía en dos tandas.

[^2]: Puede Pensarse que en el otro extremo de la línea una llave puede permanecer abierta o cerrada un tiempo mínimo de milésima de segundo. Para generar los 4 ceros sucesivos debe permanecer abierta 4 milèsimas de segundo, etc.



> Por tal motivo, en el interior de un computador solo se transmiten bits en paralelo, a fin de poder enviar más millones de bytes por segundo (megabytes/seg)

![enter image description here](https://lh3.googleusercontent.com/-0-cSWas0za4/WThvHt7aZ4I/AAAAAAAADPs/9vGrlqlhysQ-SkJQb4U-tmt9rSh-dOFugCLcB/s0/figura+1.51+1.52+y+1.53+.jpg "figura 1.51 1.52 y 1.53 .jpg")

Ya al tratar el bus que une el microprocesador con la memoria (figura 1.8), se indicó que todos los bits de datos se enviaban simultáneamente, por líneas en paralelo.

Transmisión de bits en  serie tienen lugar, por ejemplo, a través de uno[^1] de los conductores del cable de conexionado del teclado o del mouse al computador.
El uso de un solo cable para trasmitir datos es económico para enviarlos a distancia.
La trasmisión paralela sólo puede darse entre lugares próximos, como los existentes dentro del gabinete de un computador, dado que la interferencia electromagnética, existente a altas frecuencias entre cables que están próximos en un recorrido común, aumenta con la distancia común recorrida. Es por ello que una impresora se conecta en paralelo si está próxima al computador, y en serie en caso de estar a aviarios metros del mismo.

#### **¿Qué es información digital, y qué significa computador "digital"?**


Cuando contamos con los dedos ("dígitos") establecemos una correspondencia entre dos conjuntos de elementos individualizables, discretos (separados): el que se quiere contar y el de los dedos.
Estos levantados dormán una figura que representa un cierto número de tales elementos.

![enter image description here](https://lh3.googleusercontent.com/-py6OdxK0pxY/WThxSZdcO4I/AAAAAAAADQA/0HRKho7O8AMDBabDqF2dDOq_LxR-pn3qACLcB/s0/Screenshot+from+2017-06-07+15%253A34%253A29.png "Screenshot from 2017-06-07 15:34:29.png")

Esta correspondencia es la que también se establece mediante el ábaco (figura 1.52), pero de modo más complejo. En éste, una pieza individual ("cuenta") -deslizable en un alambre o varilla fina de madera- tiene por ejemplo valor cien en la varilla de las centenas, indicando que se han contado cien elementos mediante las dos varillas que están a su derecha. Así un ábaco puede representar un conjunto muy grande de elementos mediante otro conjunto de elementos mucho menor, constituido por las piezas que están en sus alambres. En cada varilla las cuentas pueden estar en uno de diez estados distintos, según la cantidad de ellas que estén arriba y abajo en la misma.

Asimismo, según la posición que tenga una varilla, cada cuenta de la misma vale uno, diez, cien, etc.
De la combinación de los estados individuales de cada varilla resulta un estado del ábaco que representa el número de elementos contados.

El sistema numérico arábigo, posterior al ábaco, asignó un símbolo del 0 al 9 para representar cada una de los diez estados posibles de las cuentas de cada varilla.
En esencia, las piezas del ábaco (que simbolizan objetos contados) se reemplazaron por otros símbolos abstractos que cumplen la misma función, más fáciles de transportar y manipular en el papel, los cuales constituyen números.
Si una varilla tiene cinco cuentas en su parte inferior, y luego se apila otra de ellas, se pasa de un estado de las cuentas a otro distinto, sin posibilidad de estados intermedios con significado.
Del mismo modo, del número 2025 se "salta" al 2026, sin que exista un digito entre el 5 y el 6.

[^1]:  Dicho cable está acompañado por otros, para enviar señales de sincronismo, control y alimentación. Una vaina de plástico recubre el conjunto.


> Tanto en el ábaco como los números son representaciones simbólicas de la acción de contar unidades.
> 
> En uno y otro caso la información consta de símbolos separados entre sí, cada uno con un valor propio otro que depende de su posición en el conjunto (no es lo mismo un 2 en  las decenas que un 2 en las unidades de mil)
> 
> Esta forma de información se denomina **digital**, siendo que se ha conservado la palabra "dígitos" para indicar símbolos que combinados representan un conjunto de elementos contados, siendo que también an cada uno de ellos según su posición relativa se les ha atribuido un valor numérico (uno, diez, cien, mil... a las varillas del ábaco; uno a cualquier otro)
> 
> Es característica de la información digital y de los fenómenos digitales en general, que entre estados, posiciones, o valores definidos, no existen otro intermedios.
> 
> Digital se ha convertido en sinónimo de **número**. Estados físicos como de la posición de las cuentas de un ábaco, los engranajes de los medidores domiciliarios de gas, agua, etc, es posible codificarlos mediante símbolos numéricos.

Los relojes digitales indican cuantitativamente la hora mediante números, provenientes de la acción de contar eléctricamente la cantidad de pulsos (conjunto a contar) generados a intervalos regulados por un oscilador de cuarzo.

La información recién descripta es el tipo **digital decimal**. En relación con la señal eléctrica de la figura 1.46, restringida a tomar sólo dos valores, estados o niveles (alto o bajo) que habíamos definido como **digital binaria**, podemos corroborar que tal denominacion ajusta al concepto establecido de información digital. Los 8 cables de la figura 1.48 son, como las varillas del ábaco, piezas separadas de información, con la diferencia que en un instante dado cada uno puede estar en un nivel alto o bajo.

![enter image description here](https://lh3.googleusercontent.com/-bOjtZja9YKc/WThzTHpOwkI/AAAAAAAADQQ/jUPSB3jQCMk_YcRb4GPnx3tzna4kcbyjgCLcB/s0/figura+1.54.jpg "figura 1.54.jpg")
Es factible construir un ábaco binario equivalente (figura 1.54) Asignando símbolo binario **0** al nivel bajo y **1** al alto, los niveles en que se encuentran los cables constituyen la combinación de símbolos binarios 01100001 que pueden hacerse corresponder con un número del sistema binario de representación.
Lo mismo en una posición de memoria, el estado "si-no" de las 8 llaves con que simulamos circuitos electrónicos con dos estados eléctricos son asimilables a un número binario.

Cuando en un cable la tensión eléctrica cambia de un nivel al otro va pasando físicamente por una serie de valores intermedios, que no son detectados por los circuitos, diseñados para reconocer sólo dos niveles.
O sea que cualquier valor intermedio de tensión eléctrica no tiene significado para el sistema. Del mismo modo, en un ábaco no tiene significado una cuenta que se desliza de un extremo al otro de una varilla.

Los conductores del interior de las computadoras presentan uno de dos niveles o estados eléctricos posibles Grupos de 8, 16, 32, 64 cables -según sea-  un instante dado representan un número binario que codificara un dato, instrucción o resultado, mientras que otros representan números que sirven como dirección
Al mismo tiempo, cables individuales que están en **1** ó **0** son usados para controlar (dar órdenes) los circuitos del computador acerca de las operaciones a realizar
En el interior de un computador en esencia se guardan y se trasmiten números binarios.


> La denominación **computadoras digitales** indica el tipo de máquinas que operan con señales eléctricas digitales binarias, que siempre es posible representar números binarios.

Computador digital es sinónimo de computador, desde los primeros prototipos de la década del () hasta los actuales. En laboratorios de física o matemática pueden existir "**computadores analógicos**". En éstos la tensión eléctrica no está restringida a dos valores como en los digitales.

Los niveles alto/bajo, así como los símbolos **1** y **0**, pueden adjudicarse a los valores "verdadero, falso" de la lógica clásica, como lo hizo George Boole hacia 1850. Es por ello que también se llaman señales lógicas las señales digitales binarias tratadas, y en correspondencia circuitos lógicos o binarios los encargados de generarlas y censarlas.


####**¿Qué es la información analógica?**

Los relojes difitales y analógicos son exponentes de dos formas diferentes de obtener informacion.
Un reloj solar es un dispositivo analógico, muy ilustrativo de las características de la información llamada "analógica". Se basa en el movimiento de la sombra de un objeto iluminado por el sol, que sirve como símil o analogía del trnascurso continuo del tiempo. Algunas marcas circunstanciales en el recorrido o tamaño de la sombra, sirven para indicar determinados instantes de interés horario.
En su recorrido, la sombra pasa teóricamente por infinitos puntos, sin solución  de continuidad.
Cada uno de los puntos significa información, y entre dos posiciones, siempre será posible encontrar otras intermedias. En esencia se ha convertido el movimiento del sol en una indicacion en un cuadrante.
Las manecillas de un reloj analógico, que se mueven en forma continua, pasan tambíen por infinitas posiciones para estimación horaria. la existencia de números en tales relojes puede no ser necesaria. Sólo bastan unas pocas marcas de referencia en el cuadrante, como presenta muchos modelos, para estimar la hora.
Existe un sunnúmero de dispositivios mecánicos ideas para estimar o medir magnitudes físicas, los cuales presentan varaciones análogicas a éstas. La temperatura se mide por su efecto dilatador en una línea de mercurio de un termómetro. La altura del aceite en el motor de un auto se representa por la película oscura que deja en la varilla que está sumergida en el cárter. La velocidad de un vehículo se reprenta por la posición de la aguja en un cuadrante en función del número de vueltas por segundo que da una rueda.
El peso de un objeto, se representa en una balanza a resorte, por el estiramiento que sufre éste a causa de dicho peso. la longitud de una pieza de género puede medirse en relación con el número de vueltas que debe dar un cilindro donde se enrolla.

> En los ejemplos citados; se tiene una magnitud físicaa evaluar, medir (tiempo, altura, velocidad, peso, etc.), cuyo valor puede sifrir una sucesión de varaciones -en más o en menos- tan pequeñas como sea. Esto es, ella puede tomar un rango continuo de valores (teoricamente infinito, pues entre dos valores siempre hay otro intermedio.)
> Dicha magnitud se ha ***reemplazado*** por algún sistema que pueda representarla o sustituirla, por variar en general proporcionalmente, en igual medida.
> 
> Se ha construido en todos los casos un análogo, un sistema analógico, cuya salida brinda **informacion analógica**, esto es una indicacion (señal), que puede variar en forma semejante a la magnitud física de rango continuo de lores a medir, evaluar o trasmitir:

Esto en algunos casos se hace por razones práctico- constructivas como el caso de la observación directa del nivel de aceite, o de combustible de un vehículo. En el caso de un cuerpo sólido a pesar, no es factible fraccionarlo en porciones de 1Kg ó submúltiplos, so pena de destruirlo. Igualmente una tela no se puede cortar en trozos de un metro para medirla. asimismo, resulta mas sensillo evaluar variaciones de temperatura por sus defectos dilatadores, que en forma absoluta por el grado de agitación molecular.

Nos interesar en particular las señales eléctricas que se hacen variar en forma análogica (señales analógicas) a la variaciones que presentan ciertas magnitudes, como las tonalidades del gris o color de una imagen cuando es barrida por un escáner, o la presión de aire que actúa sobre el micrófono de un teléfono cuando hablamos por él.
En un escáner (ver unidad 2) mediante una fila de fotodiodos -uno al lado de otro- muy sensibles a las variaciones luminosas, se barre una imagen que se requiere almacenar en memoria. Una luz ilumina la zona que se está barriendo, y los fotodiodos sensan la luz reflejada por la pequeña superficie que está debajo de cada uno. Considerando un fotodiodo cualquiera, durante su recorrido sobre la imagen barrerá una tira vertical angosta de la misma (figurra 1.55), y detectará las distintas tonalidades que encuentre a su paso. Cuando pasa por zonas de color negro el diodo prácticamente no circulará corriente eléctrica, y pr zonas blancas dará lugar a una intensidad de corriente máxima. Entre estos extremos, las distintas tonalidades de gris reflejerán valores intermedios de luz, y en correspondecia por el diodo circulará una corriente proporcional al tono de gris sensado. Teóricamente existen infinitos tonos de grises, por lo cual la corriente que regula cada fotodiodo puede tomar infinitos valores entre los dos extremos para el negro y el blanco.
Suponiendo un escáner de mano que se mueve a velocidad constante, si en un segundo recorre X m, el diodo considerado al barrer la tira, indicada en grisado, dará lugar a una circulación de corriente, que en el transcurso del tiempo sufrirá las variaciones de intensidad indicadas.

![enter image description here](https://lh3.googleusercontent.com/-afMmz0Y7yF8/WThoxhUbiHI/AAAAAAAAAww/1igwE4EQYzw6AlEaWu3de7EJ6wYf3lpNACLcB/s0/figura+1.55.jpg "figura 1.55.jpg")
 Según se vio, en las señales digitales binarias sólo tienen significado (0 y 1) dos valores (0 y 5 volts), saltan abruptamente de un valor a otro. A diferencia, en las señales analógicas cualquier valor de tensión representa información acerca de los tonos d gris del área barrida por diodo en ese segundo.

> En general, una **señal eléctrica analógica** puede variar a lo largo del tiempo de una manera continuada, gradual, sin saltos bruscos, entre des valores extremos que determinan un rango, y en un instante dado puede tener un valor cualquiera con significado informativo dentro de dicho tango.

A fin de explicar el principio de generación de las señales eléctricas a analógicas que se transmiten por las líneas telefónicas como réplica de las señales que emiten nuestras cuerdas vocales, se  describirá una experiencia fácil de realizar o imaginar, que permite además tener una primera aproximación al concepto de madulación.
Sea una habitación cuya lampara eléctrica en lugar de estar simplemente gobernada por una llave  8 ("si-no", lo está mediante un potenciómetro regulador de intensidad luminosa. Si giramos éste había 
un lado y otro a un cierto ritmo, la intensidad luminosa fluctuará de igual forma. Esto sucede por  que la corriente eléctrica que pasa por la lámpara está variando de intensidad de manera análoga las variaciones a que sometemos en el regulador.
Cuando hablamos, de vibraciones de nuestras cuerdas vocales impulsan el aire que las rodea produciendo variaciones de presión semejantes (como lo hace en mucho mayor grado el cono de un  parlante al vibrar). Si dichas variaciones de presión del aire actúan sobre el micrófono de un  teléfono, producen vibraciones analógicas a las generadas por las cuerdas vocales sobre una pieza móvil del micrófono. Por formar parte el micrófono del circuito eléctrico telefónico, actúa de manera parecida al regulador luminoso citado: hace variar la corriente eléctrica que circula de 
modo análogo a las vibraciones de las cuerdas vocales.

1.Teóricamente, puesto que entre dos valores próximos es factible encontrar otro intermedio, una señal análoga podría tener 
infinitos valores en su rango.


Esta corriente llega por un cable hasta el receptor del otro aparato telefónico que esta en comunicación, merced a la conexión establecida en la centrar telefónica.
De esta forma, una señal eléctrica analógica sirve para transmitir variaciones de presión (también analógica) de un extremo a otro de una línea telefónica. Si estas señales llegan a un parlante o auricular, harán que este vibre al compás de sus variaciones, las cuales se convertirán en audibles, por lo que se llaman **señales de audio**. Otras señales analógicas como las de radiofrecuencia y TV no pueden ser escuchadas de esta forma, por ser de rápida variación.

La comunicación entre dos computadoras por vía telefónica supone las existencia en cada extremo de un dispositivo periférico modular/ demulador (**módem**). Cuando un computador transmite datos a otro, el módem del primero actúa como modulador. Esto es, el módem hace variar la corriente eléctrica que envía al otro extremo, como ocurre cuando se está hablando por teléfono; pero se transmite tonos de audio simples (como los que se escuchan al discar), cuyas variaciones 
representan unos y ceros (proceso de conversación digital a analógico denominado **modulación**). Es un parlante ubicado en la plaqueta del módem del computador que está recibiendo se pueden escuchar dichos tonos de audio enviados en esta "conversación" entre computadores.

**¿Qué implica una conversación analógica-digital (A/D) y en qué periféricos tienelugar?**

Como se trató, a los efectos de contar unidades o entes separables, individualizables , usábamos los números naturales 1,2,3....85,...205 que simbólicamente reemplazaron al ábaco para representar los objetos contados. La acción de medir magnitudes que varían dentro de un rango continuo de valores es diferente a la acción de contar. Una medición en general se realiza cuantificando mediante números la salida de un sistema analógico, o sea la señal analógica que varía de manera similar a la magnitud física a medir. 
Una forma de cuantificar es usar una escala graduada (que es recta en un termómetro, y circular en un reloj), dividida en unidades adecuadas, la cual presenta números en ciertos puntos calibrados. Divisiones 
menores entre los mismos permite apreciar temperaturas como 38,4°C. En esencia está representando la propiedad de dilatación de la materia mediante números fraccionarios, resultando una medida aproximada.

>  En general, cuando nos valemos de números para medir cuantitativamente una magnitud analógica, estamos efectuando una conversión analógica-digital (A/D).

Esta conversación no siempre es necesaria. Así cuando se aprecia el nivel de combustible o de aceite 
de un auto, no hace falta que la escala presente npumeros indicadores.

> Dado que en el interior de un computador sólo pueden existir señales digitales, y que señales provenientes del exterior son análogas, como las que se generan cuando un escáner barre una imagen, o las enviadas via módem por una línea, se requiere además que en dichos periféricos se lleve a cabo una conversación A/D. Igualmente será necesario convertir en señales eléctricas digitales el movimiento de la volita de un mouse, o las señales analógicas de audio que llegan a una plaqueta para multimedia.

 
En relación con la digitalización de estas últimas -semejantes a la que se hace antes de grabar música en CD de audio-trataremos una forma de conversación A/D empleada para este tipo de señales eléctricas de variación relativamente lenta. La figura 1.56 ilustra los conceptos centrales relacionadoscon esta forma de conversación A/D. En ella se supone que en los instantes t1, t2, t3...- se toma una muestra, o sea se mide el valor de una señal eléctrica analógica hipotética que varía ntre 0 y 5 volts[^1] . 
La medición realizada en t1 es de 0101= 5 volts, valor entero aproximado al valor real que es 5,4 volts1. 
Del mismo modo, en t2, t3... se han determinado los valores enteros **1001**(9 en vez de 8,8), **1001** "12 en vez de (11,6) ... etc. Si todos estos números binarios se guardan ordenados en memoria, la cirva continua (variable analógica) de la figura 1,56 quedará memorizada dentro de computados como el conjunto de puntos separados de la figura 1,57. Si se unen éstos, resulta una figura de forma parecida a la original. 
Se comprende, que si en lugar de tomar 16 niveles de valor 0000 a **1111**, se determinan 32 (de 00000 a 11111), existirá un menor error de cuantificación. En general, cuantos más bits se utilicen para representar cada medición, y cuanto menos separados estén los instantes t1, t2, t3 ...- o sea cuantos más muestras 

[^1] Se denomina "error de cuantificación" a la diferencia 5,4 - 5= 0,4


![enter image description here](https://lh3.googleusercontent.com/-EpVHOa6wdTs/WThxZC2WxnI/AAAAAAAAAxo/Z0fDzFjwnk8Ges7yCFRBLlfNw_3SiEMhgCLcB/s0/figura+1.56+y+1.57.jpg "figura 1.56 y 1.57.jpg")

se toman de la señal-mayor será la correspondencia entre la señal analógica y los números que representan puntos cuantificados de ella en memoria, requeriéndose mayor espacio en ésta para guardarlos. 
La conversión A/D que tiene lugar en un módem se llama "**demodulación**" no siendo un proceso cuantificación como el recién ejemplificado. Consiste en detectar en la señal eléctrica análoga que llega al módem receptor por la línea telefónica- los unos y ceros que fueron codificados por el módem transmisor (citado en la pregunta anterior), y generar en correspondencia los dos niveles de tensión de la señal binaria que puede manipular el computador. Por ejemplo, si dos módems intercomunicados intercambian información por modulación de frecuencia, al módem que está recibiendo una señal analógica que presenta dos frecuencias distintas (figura 1.70), y detectará una frecuencia como portado, representando, ceros y, la otra frecuencia, unos. 

En un mouse común la conversación A/D es en parte mecánica: el movimiento de la volita se convierte y descompone en movimientos análogos en dos direcciones perpendiculares que comunica a dos rueditas 
dentadas o ranuradas que pueden girar. (figura 1.60). Los dientes de cada ruedita al girar van dejando pasar o cortando un haz de luz que incide sobre ellos, generada por un dispositivo fotoemisor. En el giro de cada rueda dentada, cada paso-corte-paso de haz de luz es sensado por un fotodetector, que así genera un pulso eléctrico con cada diente de la rueda1. De esta forma, en el movimiento continuado de la bolita transmitido a las dos rueditas se convierte en dos series de señales digitales, que permiten determinar la dirección y velocidad de ese movimiento. Sea realizado así una conversión A/D.

**¿Qué implica una conversión digital-analógica (D/A) y qué periférios la levan a cabo?**

Mientras que una conversión A/D está relacionada con la entrada de datos desde el exterior hacia un com-
putador, una conversión D/A se requiere para ciertos tipos de salida desde éste hacia el mundo exerior. 
Merced a ella, una señal eléctrica digital que reresenta unos y ceros, se transforma en una señal analógica. Se trata de procesos inversos a los esquematizados en la figuras 1.60, 1.64 y 170. 
Así una conversión D/A se realiza en una plaqueta de vídeo (figura 1.67), para que el monitor hoy día analógico- pueda brindar una amplia graduación de colores, a fin de obtener una imagen más real. 
En un módem, la acción de convertir los unos y ceros provenientes del computador en variaciones de un señal eléctrica que se envía por línea telefónica, se denomina "**modulación**". 
También se requiere conversión D/A para ka información que recibe un periférico graficador ("plotter").

1. En la figura 1.60 la luz emitida por un fotoemisor pasa entre dos dientes de una rueda, la cual activa al fotolector correspondiente;
mientras que la luz qque emite el otro es interceptada por un diente, por el que el fotodetecor ligado al mismo recibirá luz.



**¿Qué hardware encontramos para la entrada/salida de datos, desde los periféricos hasta la porción central de un computador?**

Según dijimos, la designación "perifericos" proviene de la ubicación de estos dispositivos en la periferia de un computador, en relación a la **porción central** constituida por la CPU y la memoria principal. También se denomina unidades de entrada o salida según se su función.

> Anteriormente habíamos establecido que la función primera de los
> periféricos es **convertir** señales que representan datos externos en las
> operaciones de entrada, o a la inversa en operaciones de salida.

Esto es, un periférico oficia de "frontera" entre el exterior y el interior de un computador para la conversión de señales. Del mismo modo, nuestros ojos, oídos, piel, etc. , sensan señales externas y las transforman en señales eléctricas que van hacia nuestro cerebro o médula; y por ejemplo, nuestras cuerdas vocales y las cavidades asociadas realizan un proceso opuesto para comunicarnos con el exterior. 
En una PC existen que están fuera del gabinete de computador "teclado, impresora, mouse, etc.) 
y otros que están dentro del mismo (unidades del disco-flexibles, rígidos, DC ROM- o n módem interno).
Siempre indisolublemente ligado al periférico existe un medio que representa el mundo exterior el papel 
en la impresora, las teclas, la pantalla en el monitor, la superficie dodne se desplaza la bolita del mouse, la imagen que recorre el escáner, el disco fijo o inserto en la unidad correspondiente, etc.

> En una **operación de entrada de los datos** que llegan del exterior a
> un periférico tienen como destino  la memoria principal, mientras que
> una **operación de salida** el movimiento es el contrario.


Si se observa en una Pc el encadenamiento de subsistemas conectados desde un periférico hasta la 
"motherboard", que contiene la porción central, en general podemos distinguir las siguientes 
etapas de hardware "figura 1.60 a 1.65), cuyas funciones luego se detallan:
1. En el periférico encontramos circuitos que constituyen a lo que denominamos "**electrónica del periférico**"1.
2. Un cable conteniendo varios conductores une eléctronicamente el el periférico en cuestión con un conector correspondiente a una plaqueta **interfaz**2, insertable en el "motherboard"3. Para tal fin, 
dicho cable en sus extremos presenta conectores apropiados.
3. La **plaqueta interfaz**4 porta un nivel intermedio de electrónica- entre la electrónica de un periférico 
citada y la proción central- que llamaremos "**electrónica intermediária**"(que para el teclado está en la "motherboard"). Circuitos con memoria de ésta constituyen **registros** denominados **ports** ("puertos"). 
4. A un bus E/S de la plaqueta principal ("motherboard") están conectados varios zócalos donde se insertan plaquetas iterfaces, a razón de una por zócalo. De este modo bus oficia de "camino" común, para permitir que varios dispositivos se puedan conectar a circuitos de la parte central. Como se verá, en la "motherboard" de una PC puede haber distintos tipos de 
buses de E/S que cumplen esta función, pero con distinta velocidad de transferencia de datos5. 

1. Eligamos esta denominacióngenérica, evitar nombres como "controlador/a" de periférico, dado que también se desiga con 
este último nombre a plaquetas que se insertan en la plaqueta principal, a las cuales se conecta el cable del periférico correspondiente. 
Así, en una Pc se habla de "controladora IDE o SCSI "se produncua "scasi") para denominar los circuitos que están junto a la cada que  
contiene el disco rígido o a la del CD. Pero también por ejemplo se llama "controladora", a la plaqueta (o tarjeta, como se diga) de 
video a la que se conecta el monitor, y a los circuitos integrados de la "motherboard" que constituyen la denominada "controladora" del 
teclado, siendo hoy común encontrar también en la "motherboard" controladoras de disco y disqueteras. Vale decir, que la palabra 
controlador/a designa la electrónica que gobiernalas acciones de un periférico como el disco rígido, así como la que sirve como 
intermediaria para el pasaje de datos entre periférico y la parte central"
2.**Interfaz** es una palabra que en computación designa en general a un hardware intermediario, ubicado entre dos subsistemas 
independientes, que sirve para comunicarlos y adaptarlos eléctricamente. Así puede decirse que en un ériférico es una interfaz entre el 
exterior y en interior de un computador, o que un bus o un cable es una interfaz entre los dispositivos que conecta, atc. En las Pc 
cuando se habla de interfaz("interface" en ingles), se asume que se trata de una plaqueta adaptadora, insertable en la plaqueta 
principal, cuyos circuitos por un lado están conectados a la electrónica de un ériférico (a través de un cable)y por otro a la porción 
central (a través de un  bus). Dichos circuitos contienen registros de almacenamiento transitorio(ports), donde programas dejan ordenes para 
el periférico, y para retener entre este último, y la porción central. Otros circuitos sirven para generar señales de interrupción. 
3. El teclado se conecta directamente a la "motherboard", siendo que los circuitos de su interfaz("controladoda") están en dicha plaqueta.
4. Esta plaqueta también se llama controladora, o plaqueta controladora, por lo que vale lo dicho en el pie de la página anterior.
5. El primero en aparecer fue el bus ISA "Industry Stanbard Architecture) desarrollado por IBM para las XT, también llamo bus 
del sistema o bus de expansión. Este bus hoy existe- por razones de compatibilidad con plaquetas y periféricos corrientes- en las 



  **¿De qué forma intervienen las cuatro etapas de hardware citadas en operaciones de E/S, desde o hacia distintos periféricos?**


Ejemplificaremos para periféricos corrientes1, la función que desempeñan los cuatro subsistemas descriptos en una, operación de entrada, desde que un periférico en cuestión detecta datos, hasta que llegan a memoria 
principal; y en una operación de salida, en el movimiento inverso de datos2.

> Si bien en el presente casi todos os periféricos tienen el circuito de
> su interfaz y ports integrados en el chip o chips que constituyen el
> chipset que acompaña al procesador en la motherboard  (figura 1.5), se
> ha preferido mantener el esquema anterior con la interfaz visible en
> la tarjeta enchufable en el bus correspondiente,a los efectos de que
> se vea más claramente el camino que sigue a la información. Esto es,
> "independientemente" de que una intefaz esté en una tarjeta o en el
> chipster," lo que interesa es su función", que será siempre la  misma,
> "sin que interese dónde se entuentre fisicamente". Vale decir, que
> ningún periférico puede conectarse directamente a un bus (sea ISA,
> PCI, ect.), sino que por intermedio de una intefaz, la cual también
> presente  registros ports para que en uno de ellos el perifperico
> reciba órdenes, y que por otro envie o reciba datos.

Empezando con el **mouse** (figura 1.60), en el mismo tiene lugar a la conversión A/D antes descripta, como comienzo de cada operación de entrada. Los pulsos generados. que representan los componentes de movimiento de a bolita según dos ejes perpendiculares- son enviados en serie por la electrónica del mouse, a través de u conductor contenido en el cable de salida. Este cable se conecta a la plaqueta "multifunción" donde está la interfaz "port serie"4, elegida para el mouse(electrónica intermediaria)
Un circuit de ésta es un **registro port de datos**, siendo como todoo registro, hardware dedicado al almacenamiento temporario de datos que llegan desde la electrónica del mouse.
Del port, dichos datos salen en paralelo, byte por byte, a través de las líneas de datos de un bus de E/S, y así llegan al registro AX de la UCP "microprocesador). Por último, del registro AX pasan a memoria, donde un 
programa hace que el cursor del mouse aparezca en pantalla.

En el caso de la **impresora**(figura 1.61) la operación de salida tiene lugar cuando pasan de memoria principal al registro AX datos a imprimir, a razón de un byte por vez. Estos bits de datos desde AX, y a travéz de bus ISA, llegan silmultaneamente a un registro port de datos5 de la interfaz, que los guarda temporalmente. Este port forma parte de la circuitería de la interfaz"por paralelo" también ubicada en la paqueta "multifunción" (nivel
electrónico intermediario). De este port, cada byte a imprimir pasa en paralelo- a través del conector y cable que lo vincula con la impresora- a la memoria de almacenamiento temporario de este periférico, que forma parte de su electrónica6. Esta también se encarga de convertir la información binaria a imprimir, contenida en su memoria, 
en señales gráficas en tinta negra o color sobre un soporte de papel, que oficia de mundo exterior.

La electrónica del periférico **teclado** está contenida en la pastilla con u microprocesador dedicado(figura 1.62). 
El mismo, entre otras funciones, detecta qué tecla se pulsó. Luego envia en serie, hacia el registro port del teclado, el código binario de dichactecla por una línea, la cual forma parte del cable que se enchufa a un conector de la 
"motherboard". Por ser un periférico muy estándar, el teclado no se conecta a una plaqueta insertable en la "motherboard". La electrónica intermediaria(interfaz con port) del teclado, conocida como controladora de teclado;está en la plaqueta principal. Del port citado, los 8 bits del código de la tecla siguen en paralelo por el bus ISA, 
hasta el registro AX, de donde van a memoria principal.

1. Cuyo funcionamiento se describe en la Unidad 2
2. Datos se emplea acá en un sentido general, que puede incluir instrucciones y resultados, según el caso.
3. Esta plaqueta contiene varias interfaces: para disco rigido, CD ROM, disquete, port paralelo(para impresora), y una interfaz port serie 
4. Designado COM1 o COM 42 en una PC. Registro "port" es sinónimo de "port"-
5. No debe confundirse un port, que es un circuito con memoria que oficia de registro, con el conector de la parte trasera de un 
gabinete, que simplemente sirve para conectar un cable por el cual pueden llegar o salir datos desde o hacia dicho port. 
6. Esta electrónoca de hoy día es tan compleja que incluye un microprocesador dedicado a la impresora, con un programa en ROM que 
maneja el funcionamiento de la misma. En las impresoras láser dicho microprocesador puede ser uno veloz de tipo RISC. 


![enter image description here](https://lh3.googleusercontent.com/-1TYA_s-E8P8/WTh8b0FjhZI/AAAAAAAAAyI/ufD7_1eCgKs4VfeRWrx12Wn1QGTTvwkagCLcB/s0/Figura+1.60.png "Figura 1.60.png")

![enter image description here](https://lh3.googleusercontent.com/-eZnARRR532Y/WTh3uk3QvoI/AAAAAAAAAAU/2AQ7HhyGSFM1LGj8aes014gqs4zu6jmdQCLcB/s0/Figura+1.61.png "Figura 1.61.png")

![enter image description here](https://lh3.googleusercontent.com/-IsCUFBY4ZSA/WTh38FOmuGI/AAAAAAAAAAc/5f8xmdErYgg9pHMza0wNWOYgcYGIuq2wQCLcB/s0/Figura+1.62.png "Figura 1.62.png")


Un periférico incluido en el gabinete de una PC, como la **unidad de disco** (duro, flexible,CD ROM), presenta una electrónica[^1], que una operación de entrada (hacia memoria) sensa los bits 
grabados en serie en un sector de una pista de un disco, uno a uno, mediante el cabezal (figura 1.63). Luego de memorizar transitoriamente en un registro estos bits del sector leído, la electrónica
del periférico los envía en paralelo, por tandas, a través de un cable plano. Este cable se conecta mediante un conector con "agujas" a la plaqueta multifunción, donde existen interfaces para varios
periféricos. De ésta, los datos leídos siguen camino -por las líneas de datos del bus al cual ella está conectada -hacia la porción central con destino a la memoria principal.[^2]
Una operación de entrada implica un movimiento de datos inverso al descripto.
En la plaqueta multifunción están los ports que forman parte de la interfaz de la disquetera, mientras que  un disco rígido o en un CD tipo IDE, dichos ports están en la electrónica del periférico.

Actualmente (figura 1.5) están la "mother" de una PC, la electrónica y conectores que antes estaban en la plaqueta dibujada en la figura 1.63, con interfaces para unidades de disco (duro y CD), disqueteras (3 1/2 y 5 1/4),
y las interfaces "port serie" y "port paralelo", típicamente usadas para el mouse y la impresora.

El periférico **módem** interno[^3] junto con su interfaz "port serie" están en una plaqueta insertable (figura 1.64), a la cual se conecta una línea telefónica.
En una operación de entrada, la señal analógica modulada llega por dicha línea al circuito demodulador
-que forma parte de la electrónica del periférico módem- que la convierte en una serie de pulsos (conversión A/D). Estos entran a la electrónica intermediaria, o sea, a la interfaz del módem, en donde son
convertidos en 8 bits en paralelo (conversión serie a paralelo) y pasados a un port de datos. Desde éste se transferirán a través de un bus al registro AX de la UCP, y luego por otro bus llegarán a memoria.
De manera inversa, en una operación de salida (figura 1.70), otro port de la interfaz recibe desde SX por el bus, un byte en paralelo, para que sea convertido en bits en serie, los cuales son modulados y transmitidos
por la línea telefónica. De este modo, a través de ports de su interfaz, el módem[^4] puede enviar o recibir datos -hacia o desde memoria- usándose el registro AX como escala intermedia en la transferencia de datos entre
ports y memoria principal. En la figura 1.70 se traa con mayor detalle el módem y su interfaz "port serie".

Por las particularidades que se verán en relación con aspectos comunes de los periféricos tratados, dejamos en último término el periférico **monitor** (figura 1.65). Por empezar, la denominada "plaqueta de video"[^5] -que se enchufa a la "motherboard" - además de portar la electrónica intermediaria,
contiene una pequeña porción de la memoria principal, denominada **VRAM** (Vídeo RAM[^4]), donde se almacena la información a visualizar. Esta llega a la VRAM merced a la ejecución de un programa por el microprocesador, y es convertida en señales analógicas por la electrónica
intermedia. Por tres conductores del cable que une la plaqueta de vídeo con el monitor, estas señales[^7] (y las de sincronismo) llegan a la electrónica del monitor, que se encarga de convertirlas en una imagen visible en pantalla (soporte que conforma el mundo exterior, detallado en la unidad 2.
Obsérvese que de la VRAM, y luego de una conversión D/A, la información a visualizar llega directamente a la electrónica del monitor, sin que nadie entre ésta y la memoria principal, ningún resgistro port intermediario para datos, como sucedía en relación con los periféricos citados.

[^1]: En un disco duro o un CD, esta electrónica, que forma parte de la unidad de disco se conoce como "**controladora**" inteligente, que hace que un sistema operativos pueda "ver" un disco conforme al sistema de archivos que maneja. Hoy día las más usadas se conocen con las siglas de **IDE** Y **SCSI**
Comprende un microprocesador dedicado, registros y una memoria buffer para almacenar.

[^2]: En el caso de datos provenientes del disquete, ellos no pasan por el registro **AX** (como el caso del teclado), si no, que un subsistema electrónico se encarga de llevarlos directamente a la memoria, sin intervención de la UCP, acción conocida como accso directo a memoria ADM. Actualmente, en una
PC resulta más veloz que la interfaz de un disco rígido envíe los datos al registro AX, y de este van a memoria, dado que los buses utilizados para hacer ADM no son suficientemente rápidos en relación con la velocidad del procesador.

[^3]: Existen módems externos, que se conectan a una plaqueta con interfaz "port serie"

[^4]: Esta interfaz es del tipo "port serie". La plaqueta de un módem en el presente contiene un microprocesador dedicado.

[^5]: Conocida también como "controladora de vídeo"

[^6]: Esta RAM, a la par que es escrita por el microprocesador (UCP) puede ser leída por la electrónica intermediaria.

[^7]: Que gobiernan los tres cañones electrónicos que forman cada punto de estos colores. A diferencia de otros cables que conectan un periférico con su electrónica intermediaria, por este cable se transmiten señales análogicas.

![enter image description here](https://lh3.googleusercontent.com/-Ok85BsyJbLE/WTh43tkEpCI/AAAAAAAAAAw/0Rp5S8dtlko2V_JS4AQMs3GOMvDbADcpgCLcB/s0/Figura+1.63.png "Figura 1.63.png")

![enter image description here](https://lh3.googleusercontent.com/-Za0B_0_7deM/WTh5PmL695I/AAAAAAAAAA8/GvJkVckS0fojJNODGnnlvuWIwuN_kfqeACLcB/s0/Figura+1.64.png "Figura 1.64.png")

![enter image description here](https://lh3.googleusercontent.com/-6dYzDoUK--g/WTh5eu1zIrI/AAAAAAAAABE/cbQ5LqnjmDo4urGgjdRwbXXP5VwsC8CfgCLcB/s0/Figura+1.65.png "Figura 1.65.png")

**¿Qué es un Port ?**
-----------------

En descripciones anteriores hemos usado la denominación "registro port" y "port" a secas como sinónimos[^1].

> Cuando se habla de port se asume que se trata de un **registro**
> temporario, que está en la electrónica intermediaria contenida en una
> plaqueta interfaz[^2], o en chips de la "motherboard", dedicado a
> guardar datos en tránsito entre periférico y la porción central en una
> operación de entrada o salida, según sea.

Por su posición intermedia en relación con un bus de E/S y la electrónica de un periférico, un port sólo opera con información digital, ya sea cuando recibe (en una escritura del mismo)o transmite (cuando es leído).

Obsérvese que la palabra "registro" es bastante genérica. Hace mención a un circuito capaz de guardar, memorizar, un número reducido de bits (8,16 ó 32) durante un lapso de tiempo requerido.
Existen registros en la UCP, en la electrónica intermediaria, en periféricos; y también a las posiciones de memoria se las puede llamar registros.
O sea puede decirse que una memoria consta de registros. Por ejemplo, es correcto afirmar que los registros de la UCP conforman una pequeña memoria RAM, o que una memoria de un megabyte son 1.048.576 de registros de un byte. Si bien un registro posee memoria, esta última palabra se usa para detonar un lugar de almacenamiento de muchos bytes, compuesto en correspondencia por muchos registros.

Para evitar aclarar "registro de la UCP","registro port","registro de memoria",etc, es costumbre que:

* "registro" a secas se refiera a un registro de la UCP;
* "port" designa un registro que está en la electrónica intermedia (interfaz).
*  no se denomine registro a una posición de memoria.

**¿Por qué operan como "buffers" ciertas zonas de memoria, los ports de una interfaz, la memoria caché y otras memorias?**
------------------------------------------------------------------------

Una Traducción de la palabra "**buffer**" es amortiguador, dispositivo capaz de absorber rápidamente energía proveniente de un brusco desnivel recorrido por la rueda, para luego expulsarla lentamente, de modo de  no producir saltos bruscos en el chásis. Lo anterior supone una retención temporaria de la energía absorbida.

>  Como se ejemplificará, en general, un **buffer** adapta dos
> velocidades distintas, permitiendo independencia entre un transmisor y
> un   receptor, con el fin de que ambos puedan estar simultáneamente
> ocupados, sin que el más rápido pierda tiempo esperando al otro.

Un lavarropas automático cuando se desagota, envía rápidamente agua hacia una pileta (buffer), que retiene temporariamente toda el agua enviada, de modo que la rejilla pueda tomarla a un ritmo apropiado para no desbordar. Esto permite que mientras el agua pasa a la rejilla, el lavarropas realice otra operación, sin que tenga que enviar el agua lentamente, para adecuarse a la velocidad con que toma la rejilla.
O sea que se independiza a una velocidad de otra.
En el ejemplo anterior el transmisor es rápido y el receptor lento. Una situación opuesta ocurre cuando una canilla envia poca agua por segundo, y colocamos un balde para que se vaya llenando. Mientras esto tiene lugar podemos realizar otra tarea, conforme a nuestro ritmo de trabajo, sin estar inactivos esperando.
Una vez que el balde se llenó podemos usar el agua contenida, arrojando de una sola vez 10 ó 20 litros en un segundo. El balde es un buffer entre la canilla y la persona.
Igualmente un buzón acomoda, independiza, el ritmo de envío de cartas de las personas, con la velocidad del servicio del vehículo recolector, que recoge de una sola vez la bolsa con cartas a una determinada hora.
En computación, se empezó a usar la denominación **memoria buffer** para zonas de la memoria principal donde se guardan datos en tránsito, desde o hacia periféricos. Por ejemplo, permanecen en una de estas zonas de datos que van llegando a una cierta velocidad provenientes de un disco, para ser procesados luego, a gran velocidad, mediante la ejecución de algún programa por la UCP.
Mientras los datos van arribando a memoria, la UCP puede dedicarse a ejecutar otro programa.

---
[^1]:En algunas publicaciones se llama port al conector al cual se enchufa el periférico.

[^2]:El port del teclado está en la controladora del mismo, situada en la motherboard.

Otra zona de la memoria está destinada a datos a imprimir, que un programa deja rápidamente en ella, para que sean enviados a una impresora a una velocidad en promedio menor. El teclado también tiene reservada en memoria una zona buffer para los códigos de teclas pulsadas.
En general, cada periférico puede tener en memoria principal su zona buffer.

También puede designarse buffer a un registro o registros que almacenen temporariamente información en tránsito, con el fin de apdaptar, independizar, velocidades.
Con este sentido, son buffers los registros que forman parte de cada electrónica intermedia, ubicada entre su periférico y la porción central, como se estableció. O sea que los ports son buffers.

> Desde la primer generación de computadoras los periféricos **no** se
> conectan directamente a memoria principal, para entrar o sacar datos
> de ella[^not1], sino que reciben o envían datos desde o hacia memoria a
> través de registros ports intermediarios, que almacenan
> transitoriamente los mismo.

Dada la gran diferencia de velocidades de operación y transmisión de datos, entre la parte central de un computador (totalmente electrónico) y sus periféricos (con partes con movimientos mecánicos o accionados por personas, como el teclado), se impone necesariamente la existencia de buffers (ports) entre ambos, para poder almacenar la información en curso, durante el tiempo necesario.
Por ejemplo, en una PC se usa el bus común ISA[^2] para entrar datos desde el teclado o enviarlos hacia una impresora. Por ese bus es factible transmitir como máximo 1 MByte/seg. = 1 byte/microsegundo, o sea también una letra cada microsegundo. Si se piensa los pocos caracteres (bytes) por segundo que se pueden tipear desde un teclado, o que una impresora con cabezal móvil puede imprimir 200 a 300 caracteres por segundo, se comprende la diferencia abismal de velocidades que puede llegar a existir entre el mundo interior electrónico de un computador y el mundo exterior.

Otra situación se da en el caso de periféricos que en muy breves lapsos pueden transmitir datos a velocidades cercanas a las que tienen lugar en la porción central.
Suponiendo una memoria principal DRAM con 70 nanoseg. de tiempo de acceso, sería factible realizar lecturas o escrituras sucesivas, a razón de una cada 100 nanoseg. = 0,0000001 seg.[^3]
O sea que en dicha DRAM teóricamente sería posible realizar un máximo de 10 millones de lecturas o escrituras por segundo. Si en cada una se leen o escriben 2 bytes, en un segundo se podrían leer o escribir  20 millones de bytes desde o hacia memoria principal. Esto es, desde o hacia esa DRAM podrían transmitirse hasta cerca[^4] de 20 MBytes/seg = 20 Bytes/microseg [^5]. en un sentido u otro, según se lea o escriba.
Cuando en una lectura de un disco rígido la cabeza pasa sobre un sector de una pista, puede enviar hacia la electrónica de ese periférico una copia de los bits almacenados a una velocidad de transferencia de por ejemplo 5 Bytes/microseg. Si se usa bus local para enviarlos hacia la porción central, la velocidad de transferencia por dicho bus puede ser hoy de por lo menos 3,5 MBytes/seg = 3,5 Bytes/microseg.
Estas velocidades se acercan a los 20 Bytes/microseg. recién calculados, con que se pueden leer o escribir datos en forma continua en memoria. Por razones de disponibilidad de ésta, los datos que llegan desde la electrónica del disco deben aguardar unos breves instantes antes de pasarlos a memoria. Entonces, temporariamente hay que retener datos, hasta que la memoria pueda recibirlos.
Esto podría asemejarse a la situación en que un jugador de fútbol recibe la pelota que otro le pasa, y debe retenerla un instante, hasta que un tercero pueda recibirla. 

> En una plaqueta interfaz, además del port para datos en tránsito,
> existen otros registros para retener transitoriamente las órdenes
> (**comandos**) que provienen de la ejecución de programas (de la ROM
> BIOS). Estos programas ordenan las operaciones que debe realizar el
> periférico conectado a dicha plaqueta, o sea relacionadas con el
> **control** del mismo. Por tal motivo se conocen como "**ports de control**".

.
Así, a la interfaz (controladora) de una unidad de disquetes debe indicársele, como ser: que active el motor, el cilindro, pista y sector a acceder, y si debe leer o escribir. Los códigos de estos comandos llegan velozmente desde el registro AX de la UCP, merced a la ejecución de instrucciones (tipo OUT) de programas de la ROM BIOS[^6]. Estos comandos permanecen en los registros destinados a ellas en la interfaz, denominados **ports de control**, hasta que la electrónica del periférico los lleve a cabo.
A su vez, la electrónica del periférico informa del **estado** ("status") del mismo (si está listo o ocupado) o si hay algún problema (en un impresora:falta de papel, fuera de línea, etc) en un registro de port de la interfaz, que es leído por dichos programas antes de transferir datos, conocido como "**status register**".

---
[^not1]:El monitor, por ser un dispositivo totalmente electrónico, es el único periférico que no tiene port de datos como buffer adaptador de velocidades. Los datos a visualizar de la zona de memoria principal reservada para video ose convierten en señales para el monitor.

[^2]:Industrial Standard Architecture, o bus del sistema.

[^3]:En una memoria DRAM se debe esperar entre una lectura o escritura y la siguiente, por lo cual se ha estimado una cada 100 nseg en lugar de una cada 7nseg.

[^4]:Recordar que se define 1 MB como 1024x1024 bytes y no 1.000.000 de bytes.

[^5]:Puesto que un segundo es un tiempo muy largo en un computador, y que la memoria tiene unos pocos megabytes de capacidad, conviene pensar la anterior es su equivalente 20 Bytes/microsegundo. Del mismo modo, no da mucha idea decir que podemos arrojar 600 litros de agua en un minuto, en vez de su equivalente real de 10 litros por segundo, suponiendo baldes llenos de esta capacidad.

[^6]:Es importante recalcar al respecto que **la UCP no da órdenes a los periféricos. De la ejecución que la UCP realiza de programas para E/S (entrada o salidas) llegan a estos ports reservados para órdenes, las operaciones que debe realizar el periférico correspondiente. La UCP no comanda ni controla por hardwarre a los periféricos. La UCP ejecuta los programas que ordenan dichas operaciones mediante comandos que llegan a registros ports destinados a ellas, ubicados en cada interfaz**.

Otro buffer "inteligente" que está presente en las PC actuales, es la **memoria** "**caché**" (a tratar) interpuesta entre la memoria principal y la UCP (figura 1.77) El caché recibe memoria principal DRAM, a una cierta velocidad, las instrucciones que serán ejecutadas próximamente por la UCP, los datos que serán procesados por ellas. Como ser, al triple o más velocidad, la UCP puede tomar del caché dichas instrucciones y datos, dado que se trata de una memoria SRAM (Static RAM), de acceso más rápido que la DRAM de memoria principal. A ésta pasarán más lentamente desde el caché los resultados que la UCP escribió velozmente en el mismo.

También en la electrónica de periféricos, como las unidades de discos, la impresora, y el teclado, existen memorias buffers, para guardar temporariamente información, en tránsito hacia o desde el medio exterior.

**¿Qué son las direcciones de los ports de una interfaz, y cómo se vincula ésta con la porción central a través del bus al cual se conecta?**
------------------------------------------------------------------------

> Como se discutió, una plaqueta interfaz cumple funciones de
> intermediación, no solo respecto a los datos en tránsito que retiene
> brevemente, sino también en relación con las órdenes hacia un
> periférico, y con la indicación del estado de operatividad de éste.

Los registros **ports para datos y ports para control**[^1] de una plaqueta interfaz ("electrónica intermedia") constituyen una parte esencial de la misma, y están vinculados directamente con la electrónica del periférico conectado a ella.
El número de estos registros en general no llega a diez, y está en relación con la cantidad de comandos a enviar a la electrónica del periférico, y a la cantidad de información que envía ésta hacia registros ports de la interfaz que indican el "status" del periférico (**port de status**)
Al tratar luego los ports serie y paralelo se dan detalles de estos registros, presentes en todas las interfaces o "controladoras", como quiera llamarse.

> Cada interfaz (figura 1.66, que es un detalle de la figura 1.7) puede
> verse en parte como una pequeña memoria Ram, cuyos registros ports se
> pueden leer o escribir del mismo modo que si fueran posiciones de
> memoria, para lo cual cada port tiene asignado en una interfaz un
> número fijo, que es su dirección.

Un cable de lectura o escritura (L/E = 1/0) que llega de la UCP, ordena la lectura o escritura de un port.
En la figura 1.66 aparecen las direcciones 0278, 0279, 027A de los ports de una interfaz "port paralelo".

Al igual que la memoria, una interfaz está ligada a la UCP (microprocesador) a través de un bus (figura 1.7 y 1.66), con líneas para direcciones, datos y control. Entre estas últimas se tiene las líneas **L/E** e **IRQ**.
Por ejemplo, la interfaz "controladora" de las unidades de disquete ("drives"[^2]) de 3 1/2" y 5 1/4" , por un lado se comunica con el bus ISA en cuyos zócalos se inserta (figura 1.63) y por otro -a través de un cable plano- con la electrónica del perfiférico, que controla el movimiento del motor, cabezal lectura/escritura del disquete, y otras acciones.

---
[^1]:La denominación "controladora" para algunas de estas plaquetas, tiene relación con las órdenes de funcionamiento y operación que llega a estos registros generadas durante la ejecución de programas, mayormente residentes en la RAM BIOS.

[^2]:No confundir con "driver", que es un programa para manejar determinado periférico.


> Otra función esencial de una plaqueta interfaz, es generar por una
> línea la señal que se envía a la UCP para solicitarle interrupción del
> programa en curso de ejecución (**IRQ** -**interrupt request**- en las
> PC). Por ejemplo, cuando en el periférico ligado a una de estas
> plaquetas se concretó algo: en el teclado se apretó una tecla, una
> impresora está lista para recibir más datos, una unidad de disquetes
> terminó de leer o escribir, etc.

En las figuras 1.62 y 1.63 se muestra la línea IRQ saliendo de la electrónica de una interfaz, para luego continuarse primero en la correspondiente línea de control de mismo nombre del bus ISA, y luego en la línea que llega hasta un chip, al cual llegan todas las líneas IRQ de las distintas interfaces. Este chip oficia de "árbitro de interrupciones", para el caso que ocurra dos o más simultáneamente, y su línea de salida va a la entrada INT del microprocesador, a fin de solicitar interrupción transitoria del programa en ejecución.

**¿Cómo se escribe o lee desde un microprocesador 80x86 un registro port mediante las instrucciones IN y OUT?**
------------------------------------------------------------------------

Según se vio (figura 1.15), el código de máquina A10050 de la instrucción **I**, antes usada, comprede el código de operación A1, siendo que 0050 permite determinar la dirección de memoria (5000) donde está el dato que debe ir al registro AX de la UCP. O sea, que para una dirección XXXX cualquiera, el código de máquina genérico será A1XXXX, siendo A1 el código que ordena la operación a realizar.
Para evitar tratar con códigos numéricos, esta orden A1, de mover un dato de memoria AX se abrevia **MOV** en lenguaje assembler, que codifica abreviadamente la operación que ordena ese tipo de instrucción.
del mismo modo, en forma general, el código de operación de sumar (adicionar) es **ADD**, restar es **SUB** (sustraer), saltar es **JUMP**, etc.

En las **operaciones de entrada** de las figuras 1.60, 1.62 y 1.64, datos son enviados por la electrónica de un periférico hacia el port de datos de la interfaz, a la cual el mismo está conectado. Luego el dato pasa del port al registro AX, a través del bus ISA, y del bus del procesador. Este movimiento se realiza cuando la UCP ejecuta lo así ordenado por el código de una instrucción abreviada **IN** (de "input") en assembler, que forma parte de una subrutina, por ejemplo una de la ROM BIOS.
Una vez que un dato llegó al registro AX, la operación de entrada se completa mediante la ejecución de otra instrucción de movimiento, como **I** analizada, que ordena escribir en memoria dicho dato que está en AX.
De esta forma se completa la operación de entrada, que comenzó cuando el periférico envió el dato al port.

Las **operaciones de salida** de las figuras 1.61 y 1.65 empiezan con un movimiento desde memoria hacia AX, que se realiza merced a la ejecución de una instrucción de movimiento, como **I** tratada.
Luego el dato va desde AX hacia el port de datos de la interfaz a la que se conecta el periférico. Para que este movimiento tenga lugar, debe ejecutarse el código de una instrucción de abreviatura **OUT** (de "OUTPUT")
Luego que el dato llegó al registro port, la electrónica del periférico lo tomará (leerá) del mismo.
 

>  Por lo tanto, la ejecución de instrucciones del tipo **IN** sirve
> para trasnferir datos desde un registro port hacia el registro AX, o
> sea   para leer el contenido un port y las del tipo **OUT** para
> movimientos en sentido contrario, vale decir para escribir un registro
> port
> 
>  Antes que tenga lugar una operación de entrada o salida, se le deben
> enviar comandos a la electrónica del periférico involucrado, a fin  
> de indicarle qué debe hacer[^1]. Para ello estos comandos deben llegar
> hasta los registros ports (para comandos) de la interfaz a la cual  el
> periférico se conecta.

Esto se logra, como en una operación de salida, pasando primero el comando desde memoria al registro AX -ejecutando una intruccion tipo **I**- seguida de una instrucción tipo **OUT**, para que el comando pase de AX a un port de comandos. Esto se ejemplifica en la figura 1.67
Para ejecutar una instrucción **IN** (lectura de un port de dirección XXXX indicada en la instrucción y envío del contenido del port al registro AX), la UC ordena las siguientes acciones básicas (figura 1.68):

* Llevar al valor **1** el cable L/E de la UC que llega a todas las interfaces.
* Enviar por las Líneas de datos la dirección XXXX (0279 H en la figura 1.68).
* Destinar al registro AX el dato contenido en el registro port, enviado por las líneas de datos del bus.

---
[^1]:Asi, para las unidades de discos o disquetes se debe indicar el número de cilindro, pista y sector: y si se lee o escribe el sector.


Se trata, pues, de una operación muy semejante a la de lectura de una posición de memoria (figura 1.11)

La ejecución de una instrucción **OUT** (escritura de un registro port de dirección XXXX indicada en la instrucción, con una copia del contenido del registro AX), supone las siguientes acciones ordenadas por la UC.

* Por las líneas de direcciones del bus enviar la dirección XXXX. (0278H en la figura 1.66).
* Enviar al port, por las líneas de datos, una copia del contenido del registro AX.
* Poner en **0** el calbe de control L/E que llega a la interfaz donde está el port, para ordenar escritura.

Esta instrucción ordena un movimiento desde AX al port, o sea opuesto al ordenado por **IN**.

![enter image description here](https://lh3.googleusercontent.com/-EEYZMgdqAGY/WT7UZVPh2iI/AAAAAAAAAFo/l3J8PFz96iM99w8_aSy4v8QgU9u4ANaJgCLcB/s0/imag1.png "imag1.png")

 

> Óbservese que la "jurisdicciión" de la UC llega hasta los registros
> ports, siendo que hasta ellos llega la línea de control L/E que sale  
> de la UC, pudiéndose así leer el contenido de un port (o cambiarlo en
> una escritura). A los periféricos no llega ninguna línea de control 
> de la UC.  La UC **no** tiene comunicación directa mediante línea
> alguna con ningún periférico.
> 
> 
> 
> Esto es, la UC no ordena qué debe hacer un periférico mediante líneas
> que salen de ella. Esto realiza al ejecutar la UC instrucciones   como
> la **OUT**[^1] citada, que envía una combinación binaria (comando)
> hacia un port de la interfaz del periférico, para ordenar qué debe    
> efectuar la electrónica del periférico[^2].

---
[^1]:En una PC las instrucciones tipo OUT ó IN en general forman parte de subrutinas escritas en la ROM BIOS.

[^2]:**Del mismo modo que cada instrucción (software) que llega al registro de instrucción ordena qué debe hacer la UCP, cada comando que llega a un port de control (generado mediante la ejecución de software) ordena qué debe hacer un periférico determinado**.


 A través de los ports la UC se comunica con los periféricos para enviarles comandos y datos.
 Hasta los ports puede llegar directamente la UC en relación con los periféricos. Cada port es seleccionado por la UC mediante la     dirección que lo indentifica, la cual es enviada por las líneas de direcciones del bus ligado al port.

>  Los registros ports de todas las interfaces constituyen una suerte de
> "**frontera**", hasta la cual la UC puede enviar comandos y datos a   
> velocidades electrónica, sólo limitada por las características del
> bus.

Igualmente a tal velocidad puede tomar datos de un port. A su vez, dada la función buffer antes descripta de un port de datos (o de comandos), la electrónica del periférico lee un dato (o un comando) a la velocidad con que opera el mismo, en general varios órdenes de magnitud menor, por depender de sistemas mecánicos que gobierna (salvo el monitor que es totalmente electrónico)[^1].

**¿Qué se denomina "port serie" y "port paralelo"?**
----------------------------------------------------

Como se verá, una y otra denominación en realidad se refieren a un tipo de interfaz, a la que pueden conectarse distintos tipos de periféricos[^2], constituida por varios registros ports direccionables.
La primer distinción básica , que hace a su denominación, es que el "**port serie**" recibe (o transmite), bit por bit, por un solo cable los datos que transmite ( o recibe) la electrónica del periférico conectado al mismo[^3].
En cambio en un "**port paralelo**", esta transmisión de datos entre ambos subsistemas tiene lugar a través de 8 cables al mismo tiempo (figura 1.67), o sea puede realizarse más rápido.
En lo referente a su comunicación con el bus al cual se vincula - o sea donde se conecta la plaqueta que lo contiene- tanto el "port serie" como el "paralelo" se conectan en paralelo al mismo, típicamente a través de 8 líneas de datos, según el tipo de bus. Esto debe ser así, pues en cualquier caso, la porción central envía o recibe rápidamente información (datos o comandos según sea) hacia o desde un registro port.

Como se anticipó, los denominados "port serie" y "port paralelo" en realidad son interfaces conformadas por varios registros ports direccionables de la forma **vista**. En el "port serie" los datos se transmiten por un cable, bit a bit, al registro port de datos, pero los comandos para el periférico correspondiente llegan en paralelo desde la porción central, según verá.
Por la relativa reducida velocidad de transmisión con que operan, el mouse y el módem son los periféricos que típicamente se conectan a un "port serie" distinto cada uno. Periféricos más rápidos como la impresora, reciben datos de a 8 bits desde un "port paralelo". También es común conectar a éste una unidad de cinta magnética para copias de resguardo, o puede conectarse una computadora tipo notebook para enviar directamente archivos a otra, estando ambas próximas.
Asimismo, dado que por razones de ruidos electromagnéticos inducidos, cables en paralelo sólo pueden transportar señales hasta unos 4 mts, si se quiere conectar directamente una impresora a un computador a mayor distancia (hasta unos 20 mts), se debe usar un "port serie", a costa de una menor velocidad de transmisión de datos hacia ella.

La interfaz "port serie" es mucho más compleja que la "port paralelo" (puede contener hasta 10 registros port direccionables), por tener que manejar el protocolo RS232C, como se verá al tratar esta interfaz.

---
[^1]:En este sentido la denominación "port", traducible como "puerto", permite realizar el siguiente paralelo conceptual. Un puerto de un país está en la frontera entre la tierra y el mar, y se comunica con el resto del país a través de carreteras (buses en un computador).
Por ellas las mercaderías pueden transportarse hasta el puerto en vehículos a decenas de km/h. Luego las mismas se almacenan temporariamente en el puerto, y se transportan en embarcaciones viajando a velocidad mucho menor. Igualmente vale la analogía para el movimiento desde el mar hacia el territorio, con escala en el puerto.

[^2]:El "port" paralelo se conoce también como interfaz "**Centronics**", marca de impresoras que lo popularizó; y al "port" serie puede aparecer como port **RS232C**, siglas de las normas que especificaron por primera vez una interfaz serie. Sería correcto llamarlos **interfaz serie e interfaz paralelo**, respectivamente.

[^3]:Así se transmiten por ejemplo los 8 bits de un carácter codificado en ASCII, con bits adicionales de comienzo y final. Un "port serie" es asincrónico en el sentido que el primero de esos bits puede llegar en cualquier instante, dado que el mismo no necesita estar en sincronismo con ninguna otra señal que vaya por otro cable extra, como ocurre con cada bit que envía en serie el teclado a su port. Para poder identificarlos, tanto el primer bit como los diez o doce que se usan para transmitir un carácter deben ser de igual duración de tiempo.

¿Cual es la estructura interna de una interfaz "port paralelo", y qué protocolo cumple una impresora conectada a ella?
------------------------------------------------------------------------

Este tipo de interfaz (figura 1.66) consta de tres registros ports: para datos, "status"  y control (por ejemplo de respectivas
direcciones 0278, 027a en una PC).[^1]
Estos tres ports, por un lado, se pueden comunicar con el registro AX, a través de solamente 8 líneas de datos del bus, para ser leídos o escritos mediante la instrucción **IN** o **out**, respectivamente, según sea. Por otro lado(figura 1.66), estos ports están conectados
-conector de por medio- a conductores del cable que une la electrónica de la impresora con la plaqueta (típicamente la "multiplicación", donde
existe una interfaz "port paralelo". En el presente el conector y esta interfaz están en la "motherboard" (figura 1.5).

En lo que sigue, se detalla en el funcionamiento típico de la interfaz "port paralelo": conectada a una impresora. Las instrucciones indicadas, así como el código del comando enviado a la interfaz forman parte de una subrutina de la ROM BIOS de memoria principal.
En las figuras sólo aparece el movimiento de datos.

1. Desde la zona buffer de impresión de memoria principal de la impresora llega al registro AX un byte a imprimir, merced a la ejecución de una instrucción que ordena este movimiento (**1a**), como la **I**, antes vista. La ejecución de la instrucción siguiente -tipo **OUT**-
ordena escribir dicho byte en la port de datos de dirección 0278 (movimientos **1b** de la figura 1.66). Este port guarda temporariamente el byte a imprimir (sigue en figura 1.67)[^2]
![enter image description here](https://lh3.googleusercontent.com/-SqO4BOrvqQg/WThnmeH1GKI/AAAAAAAAOfA/lAo7GEZnhCkp9h0O4zATue8_jFEoquMBwCLcB/s0/figura+1.67.jpg "figura 1.67.jpg")

[^1]:En una PC puede existir hasta 4 de estas interfaces designadas con el nombre lógico LPTx, siglas de Line Printer.

[^2]: Si se quiere entrar datos desde otro computador usando esta interfaz, se debe usar el port de status para entrar los datos.


----------


2. A continuación (como ser una millonésima de segundo después), se ejecuta nuevamente una instrucción de movimiento tipo **i**, que ordena pasar al registro AX el byte de comando 01111111 **(2a)**. Este byte -merced a la ejecución de otra **OUT**- viaja por las líneas de datos del bus,
y se escribe **(2b)** en el port de control de dirección 027A. El primer bit de este byte ligado a la línea STROBE llega **(2c)** con el valor **0**.[^1]

3. Al detectar la electrónica de la impresora que STROBE=0, toma del port de datos los 8 bits llegados en el paso 1. Estos viajan por los 8 conductores (3) del cable de conexionado, transmitiéndose así (en otra millonésima de segundo) hacia un buffer, que forma  parte de dicha
electrónica.

4. Inmediatamente **(4a)**, la impresora envía la plaqueta con la interfaz: un 0 por la línea ACK(nowledge), reconociendo que recibió el byte enviado en el paso 1, y un 0 por la línea BUSY, para indicar que está ocupada. Estas dos líneas llegan a los correspondientes bits del port
de "status", por lo que ambos ceros quedan escritos en el mismo **(4b)**, resultando la combinación 00111111.[^2]
![enter image description here](https://lh3.googleusercontent.com/-Lz8SKXBZD0U/WTh2SHFwNOI/AAAAAAAAOfY/gInlzoDEE6IGiKqwXlMQcZIViyDxin57ACLcB/s0/fugura+1.68.jpg "fugura 1.68.jpg")

[^1]: Además de STROBE pueden enviarse al port de control de otros bits de comando, como: un bit de AUTO FEED, que ordena cambiar de renglón luego de recibir la orden CR (carry return): el bit de SeLeCT IN que ordena poner fuera de línea ("offline") la impresora: el bit de INIT ordena
reinicializar la impresora (por ejemplo en modo texto).

[^2]: Otros bits de estado de la impresora, que la electrónica de ésta envía al port de status son: PE(paper error) indica falta de papel: ERROR: indica que no se puede imprimir por otro problema distinto de PE: SeLeCT indica al procesador con 1 si la impresora está en línea (on-line) o no (off)
según el estado de la llave correspondiente ubicada en el gabinete de la impresora.


----------


5. Por la rapidez con que el microprocesador ejecuta instrucciones, se debe controlar de no enviar otro byte al port de datos (mediante el paso **1**), antes que la impresora haya tomado el anterior (paso 3 finalizado). A tal efecto, la subrutina del BIOS contiene instrucciones para leer repetidamente
el port de "status" de dirección 0279 (ejecutándose **IN**). Los 8 bits de este port (figura 1.68) llegarán por el bus de datos al registro AX (**5**), para determinar si cambiaron del valor 00111111 ( indicador que llegó el byte enviado en el paso 1, pero que aú no se puede enviar a otro) al valor 11111111.
Esto último implica que la impresora puso en **1** el bit BUSY del port de "status", por que puede guardar otro byte a imprimir en su buffer)

6. La determinación anterior (situación no dibujada) permite conocer cuándo la impresora puso en 1 el bit BUSY del port de "status" (que pasará a contener 11111111), lo cual implica que está lista para guardar otro en su buffer, por lo que se le puede enviar un nuevo byte a imprimir, mediante el paso **1**.

Esta secuencia preestablecida de señales a enviar y recibir ("handshaking") entre la subrutina y la impresora, constituye el "protocolo" para impresión por el "port paralelo".
     
     En general un protocolo es un sistema de reglas y procedimientos que gobierna la comunicación entre dos o más dispositivos.

Puede estimarse en 10 microsegundos el tiempo que insume el protocolo, entre el envío de un byte a imprimir y el siguiente. 
Esto implica la posibilidad de enviar por un "port paralelo" unos 100.000 bytes/seg, cifra que en la práctica es mucho menor cuando opera una impresora.

El "port paralelo" presenta -como toda interfaz- una línea de solicitud de interrupción (**IRQ**), que forma parte de las líneas de control del bus. Ella se activa cuando se puede enviar otro byte al port de datos. En una PC el envío de cada byte a imprimir no se hace por interrupción, sino por por "polling":
instrucciones de la subrutina del BIOS leen repetidamente el valor del bit BUSY, hasta detectar que cambio de valor. Entonces se envía otro byte al port.


----------


¿Cúal es la estructura interna de una interfaz "port serie", y como está preparada para conectar un módem usando el protocolo RS232C?
------------------------------------------------------------------------

Por la **interfaz serial denominada** **"port serie"** o **de comunicación** (COM 1,2 3 o 4 en una PC) pueden entrar bits en serie desde el exterior y transmitirse en paralelo (8 bits juntos) hacia la porción central; o bien desde ésta salir hacia ella 8 bits en paralelo y transmitirse hacia el exterior en serie.
Esta interfaz está preparada para cumplir con las normas **RS232C** en o referente a conectores, señales eléctricas, protocolos de transmisión y verificación de errores. Por lo tanto, ella puede ser interfaz de un módem es el periférico que utiliza mayoría de las líneas de señal que indica el protocolo RS232C,
otros dispositivos pueden ser conectados a la interfaz "port serie". Así, puede conectarse el mouse (que sólo envía datos en serie), o puede conectarse una impresora que está en una habitación distante del computador. También pueden conectarse dos computadoras a través de esta interfa.
En lo que sigue, supondremos conectado a la interfaz de un módem. Si éste es interno, estará en una misma plaqueta junto con su interfaz (figura 1.64). En este caso de un módem externo, el mismo se puede conectar a cualquier interfaz "port serie" disponible, a través del conector correspondiente (figura 1.71).

El funcionamiento y control de la interfaz "port serie" se basa (figura 1.69, del mismo tipo que las figuras 1.66 a 1.68) en un chip denominado "Universal Asynchronous Receiver-Transmiter" (**UART**). Este chip presenta una línea de entrada de datos RD (para recibir en serie del módem), y otra línea salida de datos TD
(para transmitir en serie hacia el módem), y contiene hasta 10 registros port direccionables. Cuando a una interfaz "port serie" se conecta un periférico de entrada, como el mouse, sólo se usa la línea RD, dado que únicamente se realizan operaciones de entrada.
La línea RD entra a un registro que convierte a paralelo el byte de datos que entraron en serie, y los pasa al port de datos recibidos (que puede comprender un buffer de 16 bytes -para conectar módems rápidos-)

Este port puede ser leído como cualquier port (según se ilustra en la figura 1.68), de a un byte por vez, mediante la ejecución de una instrucción como **IN**, la cual ordena que una copia del contenido del port pase al registro AX, a través de las líneas de datos del bus.

En una operación de salida, mediante la ejecución de **OUT**, (como en la figura 1.66) un byte contenido en AX pasa por las líneas de datos del bus al port de datos a transmitir[^1] (que puede constar de un buffer de 16 bytes); y de éste pasa en paralelo a otro registro (no dibujado).
Este es el encargado de convertir el byte de paralelo a serie, para que salgan, bit a bit, por la línea TD.

Debe tenerse presente, que conforme a las normas RS232C, además del grupo de bits de datos que se transmiten en serie (típicamente 7 u 8)[^2] deben existir bits adicionales de control, antes y después de los mismos como lustra la figura 1.70, con la presencia o no un bit de paridad.[^3]
Luego siguen uno o dos bits de "stop" de valor 1, que indican fin del grupo.
La UART se encarga de agregar los bits citados en una transmición, y de quitarlos antes que lleguen a memoria, en una recepción (entrada). Asimismo, la UART transmite los bits a la velocidad establecida por un programa.
La línea TD o la RD permanecen en el nivel alto hasta que tenga lugar una transmición de datos. Esto se detecta en una recepción, por que en correspondencia con el bit de comiendo (siempre de valor 0), la línea pasa al nivel bajo durante un tiempo igual al de duración de cada bit.
Esta forma de conformar los datos, pensada para poder distinguir un bit del siguiente (como se planteó en la figura 1.50), vale tanto para los datos recibidos, como para los transmitidos por una interfaz "port serie". O sea, que por ejemplo, cada byte de datos que envía el mouse a su
"port serie" debe cumplir con este protocolo, conocido como de "comienzo-final". La UART verifica este protocolo de transmisión y tambien el de detección de errores por paridad. 

Además de los dos ports para datos citados, la UART contiene 8 registros ports de un byte, direccionables, para comandos, protoolo y "status", que también se pueden escribir o leer. Ellos son:

Cuatro registros ports direccionables para comandos que se escriben (ejecutando la instrucción OUT) antes de que se transmitan datos entre dos módems intercomunicados.
Dentro de estos cuatro, existen dos ports designados de "bauds rates", para fijar (indirectamente, mediante un número de 2 bytes, Hi y Low) la velocidad ( en bauds) con que se recibirán y transmitirán los bits.

El registro port para control de línea permite fijar por programa (figura 1.70):
- La cantidad de bits en serie (5, 6, 7 u 8) que se recibirán o transmitirán por vez.
- Si al final de los bits en serie recibidos o transmitidos, habrá 1, 1/2 o 2 bits de final ("stop")
- Si se detectará o no si hubo un bit errado en la transmisión , usando un bit extra de paridad.
- Si cada grupo de bits transmitidos o recibidos con paridad tendrá un numero par o inpar de unos.

El port de habilitar interrupciones permite activar la línea de solicitud de interrupción (IRQ) en función:
    . del estado (lleno o vacio) de los ports de datos
    . del cambio del valor de cualquier bit de los ports para protocolo y "status"

Dos regitros ports direccionables de la UART se usan para llevar a cabo el protocolo RS232C:
 . El registro de control del módem (escrito mediante OUT) genera hacia este las señales RTS y DTR
 . Un registro de estado del módem (leído mediante IN) guarda el valor de las líneas DSR, CTS, RI, y RLSD que provienen del mismo.

Estas señales se relaionan con el protocolo que debe suceder antes de que el computador envíe datos al módem. Antes de enviar un byte al módem, debe darse la siguente secuencia de señales
(figura 1.69 y 1.70):

1. Merced a la ejecución de **OUT**, se direcciona (O3FC) el port de control de modem, para escribir 00000010. El "uno" de 00000010 activa la línea DTR, que avisa al módem que se le enviará un byte.


----------
[^1]:  Designado Transmitter Holding Register

[^2]: Por ejemplo, los bits de un carácter codificado en ASCII (Código tratado en el Apéndice A.1)

[^3]: Como en la memoria (sección 1.4 -donde a diferencia se transmiten bytes en paralelo- la paridad sirve para detectar si un bit está errado. Por ejemplo, si se envían 7 bits de datos.
Si este número es impar, el octavo bit vale 1: y si es par, vale 0 (suponiendo que la paridad total de unos deba ser siempre par). Cuando esos 8 bits se reciben, debe cumplirse que tengan una paridad
par de unos. Caso contrario se asume que algún bit está errado, pudiéndose solicitar retransmisión de esos 8 bits.


----------


2- El módem responde que está conectado, activando la línea DSR[^1], con lo cual se escribe un "uno" en el port de estado del módem, formándose la combinación 00100000. Merced a la ejecución de **IN** se direcciona
(O3FE) y lee este port, y una copia de esta combinación llegará al registro AX ( no dibujado).
3- Cuando 001000000 llega a AX, el programa detecta que el módem está activo, y ahora se escribe 00000011 al port de control del módem, mediante la ejecución de **OUT**. El último "uno" de 00000011 activará la línea RTS
que llega al módem, para preguntarle si está listo ("ready") para recibir.
4- Si el módem está listo, activa la línea CTS, con lo cual se escribe otro "uno" en el port de estado del módem, formándose la combinación 00110000 pues DRS debe seguir activada. Merced a la ejecución de **IN** se direcciona (O3FC)
y lee este port, y una copia de esta combinación llegará al registro AX.
5- Luego que AX recibió 00110000, el programa detecta que se puede enviar un byte, pasándose a ejecutar una instrucción **OUT**, que direcciona( 03F8)[^2], y escribe (**5a**) el registro de transmisión de datos con valor supuesto 11100110. Entonces 
la UART calcula que el valor del noveno bit (de paridad) que se le debe agregar es 1, si se ha establecido por programa que las combinaciones a enviar deben tener un número par de unos; y la UART también inserta los bits de comienzo y final,
conforme a la figura 1.70. Después de agregar estos bits, la UART realiza una conversion de paralelo a serie, y transmite uno a uno los bits hacia el módem[^3], por la salida TD (**5b**).

Mientras CTS siga activa pueden enviarse más bytes, que pasan rápido al buffer del módem (no dibujado).
Cuando éste se llena, el módem desactiva CTS. Para volver a enviar otro byte hay que repetir los pasos 4 y 5. De este modo , se adapta la rápida velocidad de envío del computador a la de operación del módem.

Los pasos 1 a 5 se refieren al protocolo RS232C entre el módem y el procesador. Una vez que un byte entró al módem se guarda en un buffer de éste, para que sus circuitos de modulación realicen (6) una conversión se señales digitales a analógicas. 
Por simplicidad se ha supuesto que se modula en frecuencia. A medida que se obtiene cada valor de la señal modulada, el mismo se envía por la línea telefónica (7).

Para entrar datos desde el módem u otro periférico no se requiere este protocolo: mietras DTR esté activa se le puede enviar datos a la interfaz "port serie", pues cada byte que entra puede ser tomado rapidamente (mediante IN) del port de datos recibidos.

![enter image description here](https://lh3.googleusercontent.com/-Q4So1Z5cges/WTh9a-EsPSI/AAAAAAAAOfs/30tptU3yuFgGQ0PYOimIrsAz1w32Yo9bACLcB/s0/figura+1.69.jpg "figura 1.69.jpg")
[^1]: DTR y DSR deben permanecer activas durante toda la comunicación

[^2]:  Aunque hay ports de igual dirección, mediante el estado de otro bit, el hardware determina cúal es el port direccionado.

[^3]: De los bits de datos primero sale el menos significativo (LSB -Less Significant Bit), que en un númer es el dígito extermo dereho,
y en úlltimo lugar sale el mas significativo (MSB -Most Significant Bit), o sea el dígito extremo izquierdo.


----------


![enter image description here](https://lh3.googleusercontent.com/-d4yWA_1yp24/WTh9o_4PbzI/AAAAAAAAOf0/ulxpOskIvXgy4p3HUabUH7exlV_irHl0wCLcB/s0/figura+1.70.jpg "figura 1.70.jpg")



Mediante a línea RI(ng) el módem avisa que el teléfono suena, para que desde el computador se maneje el protocolo que hace que el módem atienda el llamado.
Si se activa la línea RLSD o C (detectora de portadora), significa que el módem detectó la onda portadora de señal de otro módem que se quiere comunicar, el cual
puede ser atendido o no.

El port de "status" de la UART permite conocer, al ser leídos los valores de sus bits individuales, si:
- En el registro port de datos recibidos hay un byte para entrar
- Un nuevo byte entró al port de datos recibidos antes que el anterior fuera entrao
- El byte que entró al port de datos recibidos tiene un bit errado (error de paridad)
- Hubo error en la forma en que llegaron desde el exterior los bits en serie
- En el port de datos a transmitir el byte aún no fue transferido
- El registro de desplazamiento que pasa de paralelo a serie contiene datos a transferir
- Una línea para protoolo que llega desde el periférico (módem) está siempre fija en un valor

Por último, luego que la plaqueta interfaz serie solicita interrupción (mediante su línea **IRQ**), otro registro port identificador de interrupciones -al ser leído por la subrutina
que atiende estas interrupciones- permite determinar la causa de la misma, pues como se vio, puede haber varias posibles.

Hasta acá se ha supuesto una interfaz "port serie" ubica en una plaqueta -que contiene solo a ella o varias interfaces ( plaqueta multifunción)- con un conector (figura 1.60) para el
conexionado de un mouse (como aparece en dicha figura), un módem externo, o cualquier dispositivo que cumpla con las normas RS232C.
Este conector no existe en el caso de una plaqueta que contenga esta interfaz junto con un módem interno, en cuyo caso debe existir un conector para el conexionado de la línea telefónica (figura  1.64)

## **¿Cuáles son las características de otras interfaces, como la de disquete, la de unidad de disco rígido y la de vídeo?**

Estas interfaces están diseñas para ser conectadas a ellas exclusivamente los periféricos indicados.Por la complejidad de los periféricos que controlan, presentan un gran número de ports direccionables. Unos reciben comandos para dichos periféricos, y otros al ser léidos indican el estado de los mismos, de la forma vista para las interfaces "paralelo" y "serie", cuando se ejecutan las correspondientes subrutinas del BIOS.
Para disquetes, disco rígido y CD ROM, los comandos son del tipo: posicionar el cabezal, leer o escribir un sector, y otros de detalle, que serán tomados por la electrónica que controla las cabezas y los movimientos mecánicos. A su vez ésta informa mediante códigos en los ports de "status" si hubo algún error: somo ser falló el posicionamiento del cabezal, el sector no se encontró, error de lectura, etc.
La plaqueta interfaz "controladora" de vídeo es una de las más complejas. Como se estableció, contiene una parte de la memoria principal (**VRAM**) donde la UCP escribe datos codificados en  binario que luego se verán como texto o gráfico en la pantalla. Esto implica que no presenta ports intermediarios para datos. Contiene varios ports direccionables, mediante los cuales se puede tener acceso a decenas de registros identificables por un número. En ellos surutinas del BIOS para vídeo escriben una serie de comandos que permiten establecer la resolución, gama de grises o colores, manejo del cursor o otros atributos que tendrá la imagen que se verá en la pantalla. También es factible en muchos casos leer su estado.

Otra característica de esdtas interfaces, es que para las PC existen versionas de plaquetas para ser conectadas a distintos tipos de buses. Así, se tiene plaqetas multifunción y de vídeo para ser conectadas al bus tradicional ISA, con 16 líneas para datos; otras para ser conectadas al bus local VESA, de 32 líneas para datos (procesadores 386 ó 486) y otras para la conexión al bus local PCI. También estas alternativas se dan en una "motherboard" con un PEntium, siendo que su bus local es de 64 líneas de datos. Con estos buses de 32 y 64 líneas no sólo es posible enviar el doble o cuádruple de datos en paralelo que con el bus ISA, sino que también la velocidad de trasnmisión usando bus local puede ser varias veces mayor que la del bus ISA.

## **¿En qué se diferencia una E/S por acceso indirecto a memoria (AIM), de una E/S por acceso directo a memoria (ADM)?**

Como se trató racién, las operaciones de E/S de datos se hacen a través de interfaces con registros ports para datos.

> El pasaje de datos del registro de port de datos de una interfaz hasta memoria principal, o en sentido contrario consituye la **fase de trasnferencia** de una operacion de entrada o salida (E/S)

La figura 1.72 ilustra la fase de trasnferencia de dos operaciones de entrada, realizadas de distintas formas, para el caso del teclado y de la unidad de disquete. Se plantea en cada caso una manera diferente de trasnferir datos, desde el port de datos correspondiente hacia memoria principal.
Si bien a los fines comparativos ambas fases se han dibujado juntas, en el tiempo primero debe suceder una y luego la otra.

Para la entrada de datos del tablado (al igual que para el mouse y el módem) la fase de transferencia será:

> **Port de datos => registro AX => memoria principal.**

Esta "tringulación" se realiza mediante la jecucion de intrucciones del BIOS.
Desde el port de datos pasan al registro AX del procesador -a través del bus de E/S-, mediante la ejecución de una intrucción tipo **IN**; y desde AX llegan a la zona buffer de memoria reservada para ellos -a través del bus que une memoria con el procesador- mediante una intrucción de movimiento, como L4, la vista Esta formada la llameremos E/S con **Acceso Indirecto a Memoria (AIM)**, indicadas en figuras 1.60, 1.62 y 1.64.

Cuando en una operación de entrada se leen los 512 bytes de un sector de un disquete (figura 1.63), la fase de transferencia se realiza por **Acceso Directo a Memoria** (**ADM** ó DMA en inglés):

> **Port de datos => memoria principal.**

Para realizar ADM se requiere una circuitería complementaria a una interfaz, que pueda leeor o escribir datos en memoria principal como lo hace el microprocesador, dado que éste no internviene en el ADM, puseto que para llevar a cabo el mismo no se ejecutan instrucciones, como ocurre en el AIM citado.
En una PC esta electrónica se denomina **"Controlador de ADM"** (figura 1.72).

Básicamente, la lectura de un sector de un diquete, en general supone las siguietes acciones principales, ordenadas por intrucciones de subrutinas que están en la ROM BIOS. En la figura 1.72 aparece el movimento por ADM deund ato desde el port de datos hacia memoria. La escritura de comandos o direcciones en ports de la interfaz de disquete o del Controlador de ADM, es similar a las figuras 1.67 a 1.70.

1.  Mediante la ejecución de una instrucción tipo **OUT**, se ordena, mediante un comando a un port de control (comandos) de la interfaz de la disquetera, que su motor se ponga en marcha.
Luego la subrutuna espera un tiempo fijo, hasta que el motor alcance su velocidad de firo estipulada.
2.  A continuación, dicha subrutina direcciona y escribe, también mediante instrucciones **OUT**, registros de control de la interfaz, idicando número de iniodad de disquete seleccionada (A ó B), y número de pista al que se quiere acceder.
3.  Mientras el cabezal de lectura(escritura se posiciona sobre la pista indicada, una subrtina del BIOS direcciona y escribe -con intrucciones **OUT**- los registros port del Controlador de ADM. En el registro de "cueta" se indica la cantidad de bytes a escribir en memoria (FFH = 255p); y en el registro de dirección, la dirección (supuesta 4033H) de la zona de memoria a partir de la cual se deben escribir sucesivamente los 256 bytes. Estos datos llegan por las líneas de datos del bus conectado al Controlador.
4.  Ports de control de la interfaz de la disquetera (se muestra uno solo) son direccionados, y se escriben en ellos comandos -mediante instrucciones **OUT**- que indican entre otros: la cara, número de senctor.
5.  Cuando la cabeza está sobre el sector a leer, se activa la línea de requerimiento de DMA (DREQ) que va de la interfaz al Controladro de ADM, para que éste comience la fase de trasnferencia, a la par que los bits del sector leídos en serie por la cabeza lectora pasan a un buffer en la electrónica de la disquetera.
6.  El controlador de ADM toma el control de bus (ISA en una PC), ordena escritura por la línea de L/E que llega a memoria, y su registro de dirección envía por las lineas de dirección (igual que la UCP) su contenido (4033), que es la dirección donde el primer byte será escrito en memoria.
Activando la línea DACK que llega a la interfaz, le dice a ésta que coloque en las líneas de datos del bys el byte (o dos byte) que llegó en paralelo a su port de datos (a través del cable plano -digura 1.63- que une el buffer de la electrónica de la disquetera con la plaqueta interfaz), De esta forma, dicho byte (26), es escrito en memoria en la primer dirección y resta uno al registro de cuenta.
7.  Luego de la circuitería incrementa uno el registro de dirección y resta uno al registro de cuenta.
8.Mientras el registro de cuenta no llegue a cero (indicacipon que se escribieron 256 bytes) se vuelve al paso 6., y hasta que no se escribió el bloque de 256 bytes, la UCP no puede leer o escribir la memoria.
9.  Cuando el registro de cuenta llega a cero, el COntrolador activa la línea End of Process (EOP) que llega a la interfaz, para que ésta a su vez active su línea IRQ de solicitud de interrupción, para que la UCP ejecute una subrutina que verefique que la trasnferencia ordenada por ADM fue echa correctamente.
10. Se ordena en un port de control la interfaz, que se detenga el motor(si no se debe acceder a otro sector).

![enter image description here](https://lh3.googleusercontent.com/-zxjhBozFHas/WT7nf-__YVI/AAAAAAAADUs/vqFRRK2_MzAmmErJZcF6r3NQ4F1zpGtvQCLcB/s0/figura+1.72.jpg "figura 1.72.jpg")

Se han tratado las dos formas de realizar la fase de trasnferencia en una operación de entrada. De manera análoga, en una operacion de salida existen dos formas de trasnferir datos de memoria a un port:

POR AIM:

> **memoria principal => registro AX => port de datos**

Esto es, en una operación de salida, los datos que están en una zona buffer de memoria pasan -a través del bus de memoria- al registro AX del microprocesador (mediante una instrucción tipo I1), desde AX llegan al port direccionado (mediante una instrucción tipo OUT). Luego los datos siguen hacie el periférico.
La figura 1.61 ilustra estos movimientos.
POR ADM:

> **memoria principal => port de datos**

De lo anterior resulta que el AIM es un proceso controlado por el software, dado que es ordenado mediante instrucciones, en cuya ejecucion debe estar ocupada la UCP; mientras que el ADM es controlado por circuitería (hardware), sin ejecución de instrucciones.

En una PC predominan las E/S con transferencias por AIM.
De no existir limitaciones la velocidad de trasnferencia del bus utilizando -como courre en las PC- una E/S con trasnferencia por ADM es mucho más rápida que otra por AIM.

---

[^ Índice](README.md) | [Siguiente >](capitulo11.md)