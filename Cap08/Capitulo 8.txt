#1.8 UAL: OPERACIONES LOGICAS, DE COMPARACION Y "FLAGS" EL COPROCESADOR MATEMATICO#


##**¿Cuáles son las operaciones lógicas que realiza la UAL, y cómo se comparan números en un computador por medio de ella?**##
___

> La denominación "**Lógica**" de la UAL se debe a que también efectúa operaciones **lógicas** como la **AND** (^), **OR** (v) y **la negación** (~). Es como la calculadora que brindan ciertos sistemas operativos, que además de tener teclas corrientes, tienen otras con los símbolos ^ v ~ que indican dichas operaciones lógicas. Los valores "*verdadero*" y "*falso*" se representan por  1  y 0.
> 

La operación **AND** queda definida así: **0^0 = 0	0^1 = 0		1^0 = 0 	1^1 = 1**.
Vale decir si en el visor hay un **0**, y se pulsa la tecla **^** seguida de la tecla **1**, al pulsar **=** resulta un **0** en el visor, etc.
También pueden entrarse más bits: como ser primero entrar al visor 10010110, después apretar la tecla de operación ^ luego entrar la combinación 00000010. Al apretar la tecla = resultaría 0000010, como puede verificarse haciendo la operación AND columna por columna, conforme ella fue definida, disponiendo los operandos como sigue:
~~~
      10010110
    ^ 00000010
    -----------
      00000010
~~~
esto mismo es lo que hace en esencia la UAL para hacer la operación lógica AND.
  
Aprovecharemos la operación realizada para mostrar cómo puede usarse ella en la práctica.
Supongamos que se realiza una encuesta con ocho preguntas que se contestan por “si” (1) o por "no" (0). Entonces la combinación 10010110 representaría las 8 respuestas de una persona. Si ahora se desea conocer entre todos los encuestados, cuántos contestaron por el “no” a la anteúltima pregunta, habría que detectar en cada grupo de 8 respuestas almacenadas (como la 10010110 anterior), si el bit anterior al de la extrema derecha es 0 ó 1. De ocurrir lo primero, el programa encargado de este procesamiento hará incrementar en uno un determinado registro que oficiará de contador.
	Para detectar si el anteúltimo bit citado vale 0 ó 1 (supuesto desconocido) hacemos la operación AND con la combinación 00000010 (llamada "*máscara*"). Puesto que en este caso dicho bit vale 1, se obtuvo un resultado distinto de cero. Cualquier otra combinación que tenga ese bit en 1, dará como resultado 00000010, como puede verificarse. Si el bit en cuestión valiera 0, la combinación que representa las respuestas sería 10010100. Haciendo la misma operación AND con la máscara 00000010, esta vez se obtendrá 00000000, en lugar de 00000010. Lo mismo sucederá para cualquier combinación que tenga 0 como anteúltimo bit. Entonces, si el resultado es cero implica que dicho bit es 0 (“no”). Si el resultado es distinto de cero implica que ese bit vale 1 (respuesta “si”), con lo cual se debe incrementar en uno el contador de respuestas positivas citado.

>Habiéndose ejemplificado una operación lógica, debe quedar claro que **la UAL es un simple circuito calculador** que realiza automáticamente operaciones aritméticas o lógicas. *La UAL no tiene "inteligencia" de tipo deductivo como puede insinuar su denominación "lógica"*.
>

---
>Para **comparar** dos números  A y B -a fin de saber si A es menor, igual o mayor que B- en la UAL **se resta** A-B. La indicación de la UAL de resultado negativo, cero o positivo, permitirá conocer (suponiendo que son enteros), como es A respecto de B.
> 

Cuando nos presentan dos números escritos, basta con observarlos para darnos cuenta en forma mecánica por los símbolos que los componen, cuál es el mayor, por la experiencia que hemos acumulado en cuanto al número de unidades que representan. La UC no “sabe" que está operando números, ni el valor de una combinación binaria.

El método usado en un computador para conocer, por ejemplo, si un número binario es el 3192, es restarle 3192. Si el resultado es cero, será dicho número, caso contrario no. La UAL tampoc determina como es A respecto de B, sólo efectúa A-B e indica si el resultado fue cero o no. Se necesita luego considerar esta indicación para tal determinación.
Por lo tanto, la **comparación es una operación aritmética de resta**, no lógica, siendo que las otras operaciones aritméticas que realiza la Unidad Aritmético Lógica son la suma, la multiplicación y división de números enteros y naturales.

##¿Qué son los indicadores (“flags") de resultado generados por la UAL contenidos en el Registro de Estado de la UCP?##
___

>Al tratar los registros de un computador se estableció que junto con el resultado de una operación la UAL genere -*mediante indicadores ("flags") que pueden valer uno o cero*- un pequeño "resumen" de las características del mismo, que puede ser o no utilizado por la instrucción siguiente a la que ordenó dicha operación.
Estos indicadores constituyen **el Registro de Estado**. *Son esenciales para estipular* (mediante una instrucción de salto), *en función del valor de uno o varios de ellos, la condición para que la UC pase a ejecutar otra, que no es la que sigue a continuación en memoria. La dirección de esta instrucción debe ser indicada en la instrucción de salto.*

Esta indicación es semejante a la que aparece en el visor de un calculador, cuando al efectuar una resta de números naturales, aparece el resultado con un signo negativo, indicador que el minuendo es menor que el sustraendo. Si este signo no aparece deducimos que el resultado es positivo. Del mismo modo, si al hacer una resta aparece un cero implica que los números restados son iguales; y si el resultado es distinto de cero, que son distintos. Otro indicador aparece cuando el resultado sobrepasa el cuál valor máximo que se puede representar. Si el mismo no aparece, asumimos que el resultado está bien.
A continuación se definen tres indicadores importantes que genera la UAL, de los cuales en esta unidad daremos un ejemplo de utilización del primero en una instrucción de salto, condicionada al valor del mismo

El indicador **Z** (de “zero”) vale **1** (ZR) si el resultado fue cero, y vale **0** si el resultado *no* fue cero (NZ).

El indicador **S** (designo) para enteros vale **1** (NG) si el resultado fue negativo, y valor **0** si el resultado fue positivo (PL)

El indicador **V** (de “overflow”) vale **1** (OV) si el resultado como número entero supera el máximo valor representable; caso contrario vale **0** (NV). Este indicador y los otros se tratan en detalle en la Unidad 4.

Entre paréntesis se da la forma en que el Debug representa el valor de esos indicadores, como aparecen en las figuras 1.18 a 1.22 después de la ejecución de cada instrucción, acorde con el resultado obtenido.
En esa secuencia de instrucciones antes ejecutada, el indicador **Z** luego de ejecutar la instrucción **I1**, quedó en **0**(**NZ**- no Zero, en la figura 1.20), y después de ejecutar **I2**, cambió a **1** (**ZR** en la figura 1.21)

Los flags se definen en detalle en la Unidad 4 de esta obra, así como al tratar las instrucciones de salto (sección 1.19 y en el modelo circuital del Apéndice de esta unidad), donde se ve cómo *la máquina toma decisiones en función del valor de los flags*, tema también tratado en la Unidad 3 de esta obra.

##¿En qué se diferencian la UAL y el coprocesador matemático que opera con números reales representados en "punto flotante” y cómo opera éste?##
___

*La UAL sólo realiza operaciones aritméticas con números naturales o enteros*, siendo que las instrucciones para sumar y restar con estos números son muy rápidas de ejecutar. Para operar en la UAL números fraccionarios, el programa que ordena las operaciones aritméticas debe controlar el lugar donde está la coma, y operar los números como si fueran enteros. Esto es lo que hacemos con papel y lápiz cuando, por ejemplo, multiplicamos dos números y luego al final ubicamos la posición de la coma en el resultado, sumando la cantidad de dígitos fraccionarios que presentan cada uno de los operandos. Estas determinaciones y otras, demoran los resultados.

>El **coprocesador matemático** (“copro”) es un microprocesador dedicado entre otras funciones a realizar rápidamente operaciones con números enteros y fraccionarios, encargándose sus circuitos de controlar a cada instante el lugar donde debería ir la coma, También realiza operaciones trigonométricas y logarítmicas. 
>

De sesta forma no se pierde tiempo en la ejecución de instrucciones, que llevan la cuenta de la ubicación de la coma, como se requiere si se usa la UAL.
Un programa con muchas instrucciones que ordenen operaciones con el “copro”, puede obtener resultados hasta cien veces más rápido que otro programa que realice los mismos cálculos simulando números con coma  y usando la UAL. Esto se hacía cuando un “copro” se costoso. 
Los números enteros y fraccionarios (racionales) y lo irracionales (pi, raíz, de dos etc.) constituyen los números “**reales**”. Para que el coprocesador pueda operarlos deben estar codificados en “**punto flotante**” (“*floting point*” - **FP**), que en castellano sería “coma flotante o desplazable”. Por tal motivo el “copro” también se denomina “*Unidad de Punto Flotante*” (**FPU** las siglas en inglés). 
Esta convención –similar a la notación científica- implica que todos los números que llegan al “copro” deben representarse de una manera normalizada, que ejemplificaremos en decimal, siendo que en realidad el interior del computador se representa sólo con números binarios, sin  comas.
Cuando el viso de un cierta calculadora “científica” aparece 3.078 E 3 se conviene que es 3,078x10 ³ = 3078 ó sea que desplazamos la coma tres lugares hacia la derecha. De manera inversa, partiendo del 3078, este número queda representado con la notación científica anterior compuesto por dos números, de los cuales uno es l exponente de diez.
Del mismo modo 243,78 = 2,3478x100 =2,4378x10² = 2.437 E 02 es, en decimal, una notación semejante a la de punto flotante en binario. Esta se ve en detalle en la Unidad 4 de esta obra. 
Siempre será factible, corriendo la coma, representar un número “*normalizado*” de la forma anterior, con un solo digito como parte entera, seguida de otra fraccionaria y otro número independiente que indique cuantos lugares se debe correr la coma para obtener el numero originario en lugar del “normalizado”. 

>**Existen instrucciones para cada tipo de números a procesar**, cuyo códigos determinan, si la operación aritmética se realizará en la UAL o en el “copro”. Igualmente, dado un umero binario en memoria, si el mismo se quiere imprimir en decimal, **según sea el tipo de datos que esté operando el programa en ejecución** (Integers, Reales, etc.) **será interpretado** dicho número. 
Del mismo modo que 260850 puede interpretarse como número  260.850 ó como la fecha 26/08/50
>

Por otra parte, por ejemplo el “copro” de un Pentium permite operar en doble precisión *extendida* con números de 80 bits, mientras que la UAL del mismo puede operar dos números de 32 bits. 
Esto permite realizar con un “copro” cálculos que requieran una *mayor precisión* (apreciar mayor números de dígitos), que de realizarse en la UAL requerirían tiempos adicionales, puesto que números que superan el tamaño que la AUL maneja, debe operarse por partes según este tamaño. 
Con el mismo fin, almacena en su interior con muchas cifras, números como PI.

El 486DX y el Pentium I ya presentan el “copro” incorporado en un chip, (el de un Pentium es 5 veces más rápido que el del 486). En el 80286 y 80386 su “copros” 80287 y 80387 en chips separados las siglas 80x87 se refieren a “copros” de Intel. Estos tienen estructuras distintas a los de otros fabricantes. Poseen 8 registros de 80 bits que el programador los ve como formando parte de una pila, con un registro oficiando de cima. O sea que los 80x87 con máquinas para datos apilados (existen microprocesadores de este tipo). Las instrucciones para llevar datos de memoria al “copro” los van apilando de forma que l último en entrar quede siempre en el registro que es la cima. Los 7 registros debajo de la cima de designan ST (i). 
Los números son más largos en los registros de la pila (80 bits)  que cando están en memoria (64 bits). 
Realizan las cuatro operaciones aritméticas básicas, calculan raíz cuadrada, exponenciaciones, valor absoluto, logaritmos, funciones trigonométricas y trascendentales en general (o sea aquellas que no son polinómicas). 
Procesan datos como números FP (reales) de 32, 64 y 80 bits, enteros de 16, 32 y 64 bits, y datos BCD de 18 dígitos decimales. En los 8 registros citados **sólo puede haber datos traducidos a FP**, existiendo instrucciones indicadas para ello (como ser cargar en la pilo en FP un número que en memoria es un entero).
Las instrucciones indicadas para el Pentium y para el “copro” pueden se ejecutadas por ambos en forma simultánea. Cada uno intercepta y ejecuta sus instrucciones. Si l instrucción empieza con 11011 (ascii de ESC) la ejecuta el “copro”. En la pila de registros citada están los operandos y se guardan resultados. Al respecto, al final de la unidad 4 de esta obra se da un ejercicio integrador donde ejecutan instrucciones para el "copro" usando el registro que oficia de cima de la pila.
El Registro de estado del "copro” informa entre otras, si un resultado no está fuera de rango de representación, o si un operando está mal representado, y acerca del valor de los flags del "copro". 
Estos últimos permiten determinar si un número es >=< que el de la cima (top) de la pila.
Un Registro de Control Permite seleccionar la precisión (simple, doble) y el redondeo a utilizar
Existe una Instrucción del "copro" que transfiere el contenido del Registro de Estado del “copro” registro AX de un Pentium. Asimismo “copro” y Pentium se pueden comunicar a través de "ports direccionales reservados, que no pueden usarse para el manejo de periféricos. Así, cuando el 38 detecta una instrucción del "copro" la pasa a este a través de un port mediante un ciclo de E/S.
El "copro" solo puede acceder a memoria a través del 80x86 o Pentium.
Las extensiones para multimedia (MMX™) de los actuales Pentium se realizan mediante instrucciones para ese tipo de datos, las cuales se ejecutan en un coprocesador dedicado a MMX, el cual comparte los 8 registros del "copro".
En un computador pueden existir otros coprocesadores, como ser para video, para Entradas/Salidas, etc.
Un coprocesador es una extensión de procesador central, que colabora con este trabajando en paralelo y proporcionando registros extras.


##¿Que son los MIPS y las MFLOPS?##
___

Actualmente un procesador puede ejecutar millones de instrucciones por segundo. Estas últimas palabras se abrevian con la sigla **MIPS** [^Cap.1.8Nota1]. Este dato puede servir relativamente para comparar, a una misma frecuencia de operación, la performance de un mismo procesador o de distintos procesadores entre sí, ejecutando instrucciones de tipo semejante, siendo que los MIPS de un mismo procesador varían de un programa a otro. La ejecución de distintos tipos de programas es siempre la mejor medida de comparación.
Los procesadores 80x86 de Intel aumentaron sus MIPS en promedio como sigue:

8088 y 8086: o,33 MIPS a 5 MHz.
80286: 1,2 MIPS a 8 MHz.
80386 SX: 2,5 MIPS a 16 MHz.
80386 DX: 6 MIPS a 16 MHz.
80486 SX: 20 MIPS a 25 MHz.
80486 DX: 20 MIPS a 25 MHz y 40 MIPS a 50 MHz.
80586 (Pentium I): 100 MIPS a 66 MHz.


Un Pentium actual de 1 Ghz en promedio puede terminar de ejecutar hasta 3 instrucciones por ciclo, lo cual extrapolando implicaría unos 3000 MIPS!

Dados los requerimientos actuales de las operaciones en punto flotantes, la evaluación de la performance de procesadores para las mismas, paso a ser importante. Los **MFLOPS** --pronunciados "megaFLOPS"-- (de inglés *mega floating points operations per second*) son las millones de operaciones en punto flotante por segundo que puede realizar un procesador, calculados como el cociente:
Número de operaciones en punto flotante de un programa/tiempo de ejecución x 106
Conforme a esta definición --a diferencia de los MIPS-- teóricamente la evaluación de los MFLOPS dependerá del procesador y del programa elegido. O sea que se debieran comparar los MFLOPS de distintos procesadores ejecutando una misma tarea con igual número de operaciones en punto flotante del mismo tipo, aunque un mismo programa en cada procesador en general tendrá distinto número de instrucciones.

___

[^Cap.1.8Nota1]: Esta unidad se acuño con los computadores IBM 370 y VAX-11-780 de DEC, que comercialmente fueron los primeros de 1MIPS. Debe consignarse que existe la MIPS Computer Systems, Inc propietaria de las arquitecturas RISC MIPS R2000 y MIPS R3000



