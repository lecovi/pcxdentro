[^ Índice](README.md) | [Siguiente >](capitulo07.md)

----

# 1.6 USO DEL PROGRAMA DEBUG DEL DOS PARA VISUALIZAR EL INTERIOR DEL COMPUTADOR

## ¿Cómo se usa el Debug para escribir datos e instrucciones en memoria?
---

A continuación se indican los pasos a dar para llamar al programa Debug desde el DOS (que tambien está en Windows 98 y NT), y luego poder leer y escribir los datos e instrucciones como se plantea en la figura 1.15. El procedimiento sirve en general para leer o escribir la memoria principal de una PC.
En negrita aparece aquello que escribe el DOSQ (y que interesa a los fines didácticos), y en cursiva mayúscula lo que debe escribir el usuario (con la tipografía que sea). El símbolo ![Enter](./img/f6-1.png)  indica la tecla “Enter”.
Los números que se tipean y los que aparecen en pantalla son hexadecimales, aunque como sabemos en el interior de un computador solo puede haber unos y ceros.

> C:\> DEBUG ![Enter](./img/f6-1.png) 
\_

Un guión que aparece titilante debajo de la C, indica que el Debug está listo para que a continuación del guión se escriba un comando. Para leer o escribir la memoria se tipea la letra E (examinar) seguida de la primer dirección que se quiere leer o escribir. Por ejemplo, si se quiere conocer el contenido de posiciones de memoria a partir de la  5000 H, primero se tipea el comando E 5000 seguido de un Enter (![Enter](./img/f6-1.png) ), con lo cual en la pantalla se verá, por ejemplo, lo siguiente:

> \- E 5000 ![Enter](./img/f6-1.png) 	(tipeado por el usuario para examinar memoria)
> 309D:5000 1F.	(mostrado por el Debug)

Esto nos dice que la direccion 5000H(0101 0000 0000 0000) de memoria [^1] tiene por contenido la combinación 1F H = 00011111. Esta combinación es la que estaba almacenadaenla dirección 5000H en la PC que hemos utilizado, pero que otro dia, o en otra PC será distinta [^2]. Lo mismo vale para 309D si luego de leer la 5000H se quiere leer el contenido de la posición siguiente 5001H, no hace falta repetir el comando E. Basta con pulsar la barra de espaciado luego del ultimo valor leido -en este caso 1F- para que en pantalla aparezca el número que guarda la posición 5001 (06 en est caso como aparece a continuación).

\- E 5000 ![Enter](./img/f6-1.png)  (Examinar memoria)

| 309D:5000 | 1F. | 06. | 50. | 8D. | 46. | B0. | A0. | 6A. | |
|---|---|---|---|---|---|---|---|---|---|
| 309D:5008 | 09. | 6A. | FF. | 9A. | 66. | 0E. | DF. | 00. | |
| 309D:5010 | FD. | 11. ![Enter](./img/f6-1.png)  | | | | | |
| - | | 5000 | 5001... | | | | |5006 | 5007 |


Del mísmo modo si se vuelve a pulsar la barra se conocerá el contenido de la posición 5002H, y asi de seguido para determinar contenidos de posiciones consecutivas de memoria. Por razones de claridad, aparecen hasta 8 lecturas de posiciones por renglón, y para no llenar la pantalla con numero, solo se muestra

---
[^1]: Aunque esto por el momento no es relevante conviene aclarar que realidad se trata de una zona (segmento) de memoria con más de 6400 posiciones (Bytes), numerados con direcciones que van de 0000H hasta FFFFH. La dirección 0000G es la primer posición de este segmento de memoria, y no el cero de la memoria. La dirección de memoria donde comienza este segmento está en relación con el valor 309D que aparece en la izquierda de 5000. Dicho 0000 corresponde a la dirección de memoria 309D0 H (309D con el agregado de un cero,
conforme a la convención para los 80x86 de Intel). Si a 309D0 le sumamos 5000H se tendria 359D0H = 0011 0101 1001 1101 0000 en binario (20 bits), que seria una dirección de memoria que esta 5000H posiciones después de 309D. Puesto que las direcciones de memoria ejemplificadas son de 20 bits, significa que se trata de una memoria de 1 megabyte, como se deduce en la figura 1.14 (2^20 = 1 MB)
Este es el tamaño de memoria que "ve" el DOS. desde la dirección 00000000000000000000 = 00000 H hasta la 1111111111111111111 = = FFFFF H. Este tema se verá en detalle al tratar este sistema operativo en la Unidad 3.
[^2]: Conforme al modelo de 8 llaves "si-no” por celda de memoria. las mismas siempre están formando una combinacion de unos y ceros determinada. No es factible que no haya "nada" en una posición. Cuando se enciende un computador. en cada posmión se forma un número al azar. que no tiene por que ser el 1F ejemplificado en esta obra.

---

una dirección a la izquierda de cada renglón. Así, luego de la 5000 no aparecerán en pantalla 5001 a 5007 (que debe determirarse visualmente, como señalan las flechas dibujadas con los valores), y luego aparece 5008
Entonces, si a partir de la indicación anterior pulsamos repetidamente la barra de espaciado, se obtendría un vuelco de memoria del tipo siguiente (distinto para cada oportunidad y computador):
Cuando se quiere dejar de leer se pulsa Enter ![Enter](./img/f6-1.png)  como se indica en el último renglón, con lo cual vuelve a aparecer el guión titilante del Debug, esperando un nuevo comando. En general se debe pulsar Enter luego de escribir un comando o cuando se quiere que aparezca el guión titilante, para indicarle un nuevo comando al Debug. Los valores que aparecen varían de un computador a otro, y en un mismo computador. Con el Debug es factible leer cualquier zona de memoria, sea RAM o ROM.

 **Escritura de los datos en memoria mediante el Debug:**

El ejemplo anterior mostró la lectura de posiciones consecutivas de memoria. También es posible luego de leer una posición cambiar su contenido, o sea escribirle un número de dos dígitos en hexa (equivalente a un byte binario). Este número se debe escribir a continuación del punto que acompaña a cada valor leído, en el espacio que para tal fin se ha reservado. Luego de escribir el nuevo contenido que tendrá una posición, se puede leer la siguiente pulsando la barra de la forma vista. Si también se desea cambiar el contenido de esta posición, debe escribirse el nuevo valor después del punto del contenido anterior, y así de seguido.
Volviendo al proceso de datos de la figura 1.15 escribiremos en 5000 y 5001 los contenidos 20 y 10 (que corresponden al dato P =1020 H, y en 5006 y 5007, los contenidos 40 y 20, correspondientes a Q = 2040 H

-E 5000 ![Enter](./img/f6-1.png) 	(Examinar memoria y escribir en ella)

| 309D:5000	|	1F.20	|	06.10	|	50.	|	8D.	|	46.	|	B0.	|	A0.40	|	6A.20 ![Enter](./img/f6-1.png)|
|---|---|---|---|---|---|---|---|---|

_

   Figura 1.16[^3]

Si se quiere corroborar que los valores recién escritos son los nuevos contenidos de las posiciones modificadas, nuevamente se ordena examinar, debiendo resultar:

-E 5000 ![Enter](./img/f6-1.png)  (Examinar memoria)

| 309D:5000 |  20. | 10. |  50. | 8D. |  46. |  BO. |  40. |  20. ![Enter](./img/f6-1.png)|
|---|---|---|---|---|---|---|---|---|

_

De esta manera se han escrito en las posiciones 5000, 5001, 5006 y 5007 los datos que en la figura 1.15 aparecen escritos en la "escalera" (que representa las posiciones de memoria). En las posiciones 5010 y 5011 deberá ir el resultado de la operación a realizar, en reemplazo de los contenidos que existan (en este caso FD y 11, como surge de la primer lectura realizada), por lo que no interesa estos valores (FD y 11)
***Con el mismo procedimiento se escriben en memoria los códigos de máquina de las instrucciones, a partir de la dirección elegida 0200H***

-E 200 ![Enter](./img/f6-1.png)  (Examinar memoria y escribir en ella)

|309D:0200 | 25.A1 | F3.00 | AA.S0 | DD.03 | 09.06 | 56.00 | 00.50 | AB.2B |
|---|---|---|---|---|---|---|---|---|
| 309D:0208 | 49.06 | FF.06 | 00.50 | 12.A3 | FF.10 | FA.50 ![Enter](./img/f6-1.png)| 

_


Verificando luego si la escritura anterior es correcta, resulta:

-E 200 ![Enter](./img/f6-1.png)  (Examinar memoria)

| 309D:0200 | Al. | 00. |  50. | 03. | 06. | OO. | 50. | 2B. |
|---|---|---|---|---|---|---|---|---|
|309D:0208 | 06. | 06. | 50. | A3 | 10 | 50 ![Enter](./img/f6-1.png)|

_

De esta forma hemos realizado la escritura en memoria de las instrucciones.
Suponiendo que se quiera salir del Debug, se debe tipear Q (Quit) para volver al DOS:

-Q ![Enter](./img/f6-1.png)  (para salir del Debug)
C:\>   (el DOS espera comando)

---
[^3]: De acá en adelante se designa con la palabra "figura" a porciones de la pantalla que se verían usando cl programa Debug.

---

###¿Cómo encuentra la UC en memoria la primer instrucción y las siguientes de un programa a ejecutar, mediante registro IP?
---
Anteriormente se estableció que el registro puntero de instrucción (IP) tiene la función de indicar la dirección de memoria donde se encuentra la próxima instrucción a ejecutar.
En el programa codificado (figura 1.15) la primer instrucción comienza en la dirección 0200H, y las dos siguientes en 0203H y en 0207H. Por lo tanto, en este caso IP deberá contener sucesivamente los valores binarios que en hexa son: 0200H, 0203H y 0207H, como se verificará cuando se ejecuten esas instrucciones.
Suponiendo que IP empiece con el valor 0200H —ya veremos cómo— puesto que el código de I(1) ocupa 3 bytes, (esto lo "conocerá" la UC al ejecutar 1(1)), si la UC hace la suma (con su calculador que es la UAL) 0200 + 3 = 0203, podrá determinar el nuevo valor que debe tener IP, que es la dirección donde está I(2)] Del mismo modo, cuando ejecuta I(2) —que ocupa 4 bytes—, podrá calcular 0203 + 4 = 0207 para ubicar I(3).
Por último si a 0207 le sumamos 4 (cantidad de bytes de I(3)), obtenemos 020B, dirección de I(4) (en hexa después de 7 siguen 8, 9, A, B) Así sucesivamente la UC va cambiando el valor de IP [^4] para ir localizando en memoria las sucesivas instrucciones que debe ejecutar.
Esta es la forma pensada para que la UC localice y ejecute, en el orden establecido, cada una de las instrucciones que forman una secuencia. Por lo tanto, para respetar estas "reglas de juego" las instrucciones a ejecutar deben estar escritas en posiciones'consecutivas de memoria.
Una "> instrucción de salto " —a tratar— permite no seguir la ejecución de un programa con la instrucción que está escrita a continuación de ella en memoria, sino continuar con otra instrucción, cuya dirección debe permitir formar instrucción de salto. El valor de esta dirección debe pasar al IP.
O sea que igualmente esta instrucción permite encontrar la que le sigue.
 

> Por la tanto, cada instrucción permite determinar donde está la siguiente a ejecutar, y por consiguiente, establecer el valor que tendrá el registro IP


### ¿Quién se encarga de proporcionar la dirección de la primer instrucción de cada programa a ejecutar?
---
En las prácticas que realizaremos con el Debug, seremos nosotros quienes nos encargaremos de escribir en el IP la dirección de la primer instrucción de una secuencia que queremos ejecutar.
Puesto que un computador pasa automáticamente de la ejecución de un programa a otro, se supone que tiene que existir un mecanismo para hacer esto. A continuación daremos un esbozo acerca de cómo esto último tiene lugar, o sea quién se encarga de dar al IP la dirección donde comienza cada nuevo programa a ejecutar, una vez que el mismo y los datos se han escrito en memoria.
Cuando se enciende un computador, el primer programa que se ejecuta es siempre el mismo. Los códigos de sus instrucciones están permanentemente en la porción ROM de memoria principal,
siendo que el hardware (circuitería) provee la dirección de la primer instrucción a ejecutar.O sea que el hardware inicializa el valor del IP al encender el equipo, así como el valor de otros registros [^5] Las primeras generaciones de computadoras que se construyeron —hoy visibles en fotos o museos— presentaban un gran panel frontal lleno de llaves "si-no". El operador tenía que cargar mediante dichas llaves, un registro equivalente al IP con la dirección donde estaba la primera instrucción del primer programa a ejecutar. Algo semejante haremos muy pronto mediante el teclado y el programa Debug.
Como resultado de la ejecución de dicho programa almacenado en ROM, se escribe en memoria principal una copia de programas que están en el disco. Estos al ser ejecutados traen a memoria los programas del "sistema operativo", que también están en el disco como archivos. Luego de lo cual en pantalla aparece C> o alguna imagen con opciones, para indicar al sistema operativo mediante un comando, qué programa se desea traer a memoria.
***Esto es, un programa del sistema operativo permite traer del disco a memoria, una copia del programa que necesita el usuario, y se encarga de que en el IP aparezca la dirección de la primer instrucción del programa a ejecutar.***
Esto se consigue si la última instrucción del programa del SO que se encarga de esta tarea, es una instrucción de salto, que indique la dirección donde está la primer instrucción del programa del usuario a ejecutar. 

---

[^4] La UC necesita "anotar" en IP el valor de la dirección que calculó mediante la UAL De no memorizado en IP, se perdería dicho valor
[^5] Como el registro CS (code segment) de la UCP que junto con IP constituyen un contador de programa (CP)

---

Como se describió, esta dirección se instala en el IP, con lo cual en forma automática, sin intervención humana, la próxima instrucción que la UC ejecuta - luego que ejecutó la última instrucción de salto citada será la primera del programa de usuario. A partir de ésta se hallan las siguientes de la forma vista.
Debe consignarse que el sistema operativo registra la dirección dónde dejó la memoria la primera instrucción del programa que trajo del disco, la cual es proporcionada al IP por la isntrucción de salto citada.
***Cuando termina de ejecutarse este programa, la última instrucción del mismo llamará al sistema operativo.***
***Será una instrucción que en esencia ordena saltar a la dirección de memoria donde está la primer instrucción de un programa del SO. Este decidirá cuál es el próximo programa que debe ejercutar la UC.***
De esta forma se pasa automáticamente de la ejecución de un programa a otro, sin intervención humana.
Las instrucciones de salto, son pues las que permiten cambiar automáticamente el valor del IP, y pasar a ejecutar una instrucción que está en cualquier lugar de la memoria, que será la primera de una secuencia escrita en posiciones sucesivas de memoria. Esta secuencia puede ser el propio programa en ejecución, o pertenecer a otro programa que debe ejecutarse a continaución.

### ¿Cómo se cambia la dirección de instrucción que indica el IP?
---

Conforme a lo anticipado mas arriba, mediante el Debug cargaremos en el IP la dirección de la primera instrucción a ejecutar, que como hemos establecido es 0200H. Para realizar esto, una vez que mediante el Debug hemos escrito los datos y las instrucciones, le damos la orden:

-R IP ![Enter](./img/f6-1.png)      (comando al debug para examinar el valor del Registro IP y cambiarlo si se desea)

IP 0100                             (el Debug informa que actualmente el IP contine 0100)

: 0200 ![Enter](./img/f6-1.png)    (al lado de los dos puntos se deja el Debug escribimos 0200, nuevo valor que debe tener IP)

_										
 
 Figura 1.17

Teniendo en el IP la dirección de L, ya se puede ejecutar la secuencia de instrucciones escritas, como sigue.

### ¿Cómo puede visualizarse mediante el Debug la forma en que se van procesando los datos, al ejercutarse las instrucciones en una PC?
---

Así como el debug permite examinar y modificar la memoria, también puede mostrar en pantalla una "radiografía" del contenido de registros del microprocesador (UCP). Observando los datos a procesar en memoria, y como a partir de ellos se obtienen resultados, puede seguirse la evolución de un proceso de datos.
Además con el Debug esto puede hacerse paso a paso, dado que permite ejecutar en "cámara lenta" una a una las instrucciones de un programa o secuencia de modo de poder ver como van cambiando de valor los registro de la UCP y posiciones de memoria. Esto es lo que haremos a continaución, con las instrucciones escritas anteriormente, experiencia que puede hacerse con cualquier PC. Antes de ejecutar dichas instrucciones, y por método, primero conviene examinar los registros de la UCP y otros datos que muestra el Debug[^6], de los cuales sólo nos interesan en esta etapa los que indicaremos en negrita.
Hemos usado el comando R IP - para conocer el valor de un registro particular[^7] y poder luego cambiarlo.
Si se usa el comando R a secas, se visualiza el valor de registros de la UCP sin poder modificarlos:


R ![Enter](./img/f6-1.png)  (Examinar registros)									

| AX=0000 |	BX=0000 | CX=0000 | DX=0000 | SP=FFEE | BP=0000|	SI=0000 | DI=0000 | |
|---|---|---|---|---|---|---|---|---|
| DS=309D |ES=309D |SS=309D | CS=309D | ***IP=0200*** | NV UP | EI PL | NZ NA | PE NC |	
| 309D:0200 |	10050 | | MOV AC.[5000][^8]  | | | DS:5000=1020 |

\_ 

 Figura 1.18

---
[^6] El Dubug simula un 80286, pero como éste es compatible con el 386, 486 y el Pentium (que tienen registros de 32 bits) puede
usarse con cualquier PC. Hay programas más completos que el Debug, pero lo hemos elegido por que está a la mano en cualquier PC.
[^7] Este comando, seguido del nombre de cualquier registro de la UCP, permite leer su valor y poderlo cambiar. Así R AX permite
leer y cambiar AC. La lista de todos los comandos del Debug se obtiene mediante la tecla ? seguida de Enter.
[^8] En cada tercer renglón, a la derecha del código de máquina de la próxima instrucción que se ejecutará(en este caso A10050), siempre
aparece su codificación equivalente en lenguaje Assembler (en este caso MOV AC,[5000]. a tratar en la Unidad 3 de la presente obra.


---

Los dos primeros renglones indican el estado de registros de la UCP. De éstos en primer lugar por el momento únicamente importan AX e IP[^9]. 
Como primer medida verificamos qué IP está con el valor 0200 que le habíamos asignado mediante R IP. Si bien AX contiene 000H (16 ceros en binario), este valor particular no interesa, pues I(1) ordena escribir 1020H, destruyendo el valor anterior (000H).
El tercer renglón se refiere a la memoria principal. El valor 0200 (igual al de IP) corrobora la dirección donde empieza la próxima instrucción a ejecutar, y al lado del mismo el código A10050, que es el que habíamos escrito en memoria para I¹, como puede verificarse (que será el valor que tendrá el registro RI) O sea que es la instrucción que queremos ejecutar en primer lugar. 
En la parte derecha indica que en la dirección 5000 (involucrada en la instrucción) se tiene el valor 1020 (dato antes escrito) Puesto que IP=0200, el dato 1020 y el código A10050 de la instrucción son correctos, podemos ejecutar ésta. Para ello simplemente se da el comando T, y luego el Debug visualiza la misma información que la figura 1.18, pero con los cambios habidos luego de la ejecución de la instrucción:

—T ![Enter](./img/f6-1.png)  + (Ejecución de la instrucción I¹) 

| AX=1020 |  BX=0000 | CX=0000 | DX=0000 | SP=FFEE | BP=0000 | SI=0000 | DI=0000  |
|---|---|---|---|---|---|---|---|
| DS=309D | ES=309D | SS=309D | CS=309D | IP=0203 |NV UP EI | PL  NZ | NA PO NC |
| 309D: 0203 | 03060050 | | ADD AX, [5000]² | | | DS: 5000=1020 |

\_

  Figura 1.19
  

Constatamos que I(1) se ha ejecutado correctamente, pues se ha cumplido la orden que portaba su código: escribir en AX una copia del contenido de la posición 5000, que era 1020. 
Si observamos el tercer renglón vemos que en 5000 sigue estando 1020. También ha cambiado IP a 0203, para apuntar la dirección de I(2), 
como habíamos previsto al hablar de IP. Asimismo vemos que 
el código 03060050 de I2 es el correcto, por lo que podemos ejecutar I(2)[^10]:

—T ![Enter](./img/f6-1.png)   + (Ejecución de la instrucción I2)

| AX=2040 | BX=0000 | CX=0000 | DX=0000 | SP=FFEE | BP=0000 | S1=0000 | DI=0000 | |
|---|---|---|---|---|---|---|---|---|
| DS=309D | ES=309D | SS=309D | CS=309D | IP=0207 |  NV UP | El  PL NZ | NA PO | NC |
| 309D: 0207 | 2B060650 |  SUB |   AX. [5006]2 |||  DS: > 5006=2040 |

\_

  Figura 1.20
  
Se ha realizado lo que ordenaba I(2): sumar al valor 1020 de AX el contenido de 5000 (que es 1020), 
y el resultado (2040) escribirlo en lugar de 1020. 
También se verifica que el dato es 2040, y que 2B060650 es el código de I3, instrucción de resta que pasaremos a ejecutar:

—T ![Enter](./img/f6-1.png)   + (Ejecución de la instrucción I(3))

| AX=0000 |	BX=0000 | CX=0000 | DX=0000 | SP=FFEE | BP=0000 | S1=0000 | DI=0000 | |
|---|---|---|---|---|---|---|---|---|
| DS=309D | ES=309D |  SS=309D | CS=309D | IP=020B |   NV   UP | El   PL |  ZR   NA |  PE   NC |
| 309D:  020B |   A31050  |  MOV [15010],| AXD  |  DS:  5010=FD11 |

\_

   Figura 1.21
  
I(3) ordenaba restar a AX el contenido de 5006, que es 2040H, o sea que se ha efectuado 2040H - 2040H = = 000H, como aparece en AX.

—T ![Enter](./img/f6-1.png)    + (Ejecución de la instrucción I4)

| AX=0000 | BX=0000 | CX=0000 | DX=0000 | SP=FFEE | BP=0000 | SI=0000 | DI=0000 | |
|---|---|---|---|---|---|---|---|---|
| DS=309D | ES=309D | SS=309D | CS=309D	| IP=020E | NV UP | El PL | ZR NA | PE NC |
| 309D:020B | BB1026 ||| MOV BX, 2610 |

\_


  Figura 1.22

---
[^9] En la Unidad 3 al ejemplificar secuencias más complejas, usaremos casi todos ellos, al igual que muy pronto los “flags" o indicadores de estado (NV UP El. etc.). Los registros DS. CS. SS. ES, todos con el valor de referencia 309D mencionado en un pie de página anterior.
De tener valores diferentes cada un, permiten definir para Datos. Código, Stack y Extensión, cuatro zonas independientes de memoria de 64000 direcciones (posiciones de un byte). Como todos tienen igual valor, las cuatro zonas (“segmentos ") están superpuestas en una sola. 
[^10] Por razones didácticas se ha elegido el mismo dato para I¹ e I². pudiendo estar en otra dirección el dato que se opera en I²

---
El registro IP pasó a 020E H. En esa posición y en las dos siguientes quedaron al azar los valores BBj _y_26. .(como resulta de leer el tercer renglón) que el Debug interpreta como correspondientes a instrucción. Como ya hemos ejecutado I(1) I(2),I(3), e I(4) no seguimos ejecutando ninguna instrucción mas.

---
> Un programa termina con una instrucción (que no hemos usado) cuyo código ordena que se pase a ej< un programa del sistema operativo, para que éste decida cuál es el próximo programa que se debe ejecutar.

---
Si queremos verificar que en las direcciones 5010 y 5011 se escribió el 
resultado que está en AX. Hacemos:

> -E5010 ![Enter](./img/f6-1.png)  (Examinar memoria)

> 309D- > 5010  00.  -/ 	00. ![Enter](./img/f6-1.png) 

con lo cual constatamos que efectivamente se cumplió lo que ordena I(4)

### ¿Cómo ordenar que los códigos de máquina dei proceso anterior sea ejecutados una tras otro automáticamente, conforme sucede realmente?
---

Por razones didácticas se ha ejecutado instrucción por instrucción, para ver luego de cada ejecución coa cambiaba el interior del computador. 
Fue necesario antes de ejecutar cada instrucción la intervención humana para pulsar T ![Enter](./img/f6-1.png)  entre otras cosas. Esto se parece al manejo de una calculadora cada vez que apretamos una tecla = . Si las computadoras funcionaran de esa manera, no tendría mucho sentido su existencia, puesto qf justamente su velocidad de procesamiento de datos es quizás el mayor de sus atributos.
Con el Debug también es factible hacer que se ejecuten, una tras otra, a la velocidad del computador, fc instrucciones escritas en memoria, y así obtener casi instantáneamente los resultados requeridos.

> Así puede corroborarse que una vez que datos e instrucciones están en memoria, la UCP realiza u proceso de datos en forma automática, sin intervención humana, merced a la acción de circuitos electrónicos que responden a las órdenes que portan las instrucciones.

Luego de haber ejecutado las instrucciones una por una, puesto que los datos e instrucciones permanecen a memoria sin cambios, y que I(1) no requiere que AX esté en cero, si se ejecutan nuevamente dichas instrucciones se obtendrán los mismos resultados. Esto es lo que haremos, pero en vez de ejecutarlas una por una, daremos la orden de ejecutar una tras otra, I(1), I(2), I(3) e I(4) Antes de dar el comando debemos hacer que I -que quedó en 020B— pase a tener el valor 0200 H, para apuntar a la dirección donde comienza I(1), para lo cual debemos ordenar R IP de la forma vista. Después, como paso previo a la ejecución, para constatar que todo está en orden podemos hacer como antes:

-R ![Enter](./img/f6-1.png)  (Examinar registros)

| AX=0000 |	BX=0000 | CX=0000 | DX=0000 | SP=FFEE | BP=0000 | S1=0000 | DI=0000 | |
|---|---|---|---|---|---|---|---|---|
| DS=309D |	ES=309D | SS=309D | CS=309D | IP=0200 |	NV	UP | El	PL | NZ NA | PO NC |
|309D: 0200	 | AI0050 |||	MOV AX,[5000j |||	DS:> 5000=I020 |

El comando para ejecutar las instrucciones que van de la dirección 200 a la 20F [^11] es

-G =0200 020E ![Enter](./img/f6-1.png) 

| AX=0000 |	BX=0000 | CX=0000 | DX=0000 | SP=FFEE | BP=0000 | SI=0000 | DI=0000 | |
|---|---|---|---|---|---|---|---|---|
| DS=309D | ES=309D | SS=309D | CS=309D | IP=020E | NV	UP | El	PL | ZR NA | PE NC |
|309D:020B | BB1026 ||| MOV BX.2610 |


Puede verificarse que se ha obtenido el mismo resultado que en la figura 1.22, correspondiente al mismo proceso realizado instrucción por instrucción con intervención del operador.

---
> Es importante aclarar que G -02(X) 020E - es una orden para el Debug, para que se ejecute el progrant que comienza en la dirección indicada, y no una orden para la UC, que permanentemente está ejecutando programas. Sin ir más lejos se ejecuta un programa cada vez que pulsamos o soltamos cada tecla de comando G = 0200 020E, así como se ejecuta otro cada 0,018 seg. para actualizar la hora y el calendario del computador, entre otros. Como se estableció, es mediante instrucciones de salto, antes citadas, que se cambia el valor del IP para que la UC en forma automática pase de la ejecución de un programa a otro.

---
[^11] Dirección donde comienza una instrucción que sigue a I(5) que no queremos ejecutar.

---

----

[^ Índice](README.md) | [Siguiente >](capitulo07.md)
