[^ Índice](README.md) | [Siguiente >](capitulo03.md)

---

## 1.2  BASES PREVIAS PARA EL ESTUDIO DEL INTERIOR DE UN COMPUTADOR##

**¿Que semejanzas tiene un computador con una fabrica que produce pedido?**

La unidad productiva (**UP**) de la fabrica de la fig 1.3 produce piezas de metal a pedido ( en este caso tornillos). Para ello se puede proveer ( a través de la Recepción) la materia prima y las instrucciones para cada pieza que irán a **bóxex** numerados de Depósito (**D**). Cada instrucción sera pedida al deposito y luego complementada por la Oficina de Control (**OC**), para los cuales debe llegar desde su box a la Mesa de Instrucciones (MI).

La materia prima (cilindro en este caso) ira desde el box donde se halla una estantería E, y de ésta el torno automático de la Unidad Transformadora (**UT**) comandada por la **OC** según lo que ordena en cada instrucción. **La OC no se puede ver que hay en cada box**. *Las instrucciones siempre se ubican en boxex numeradas consecutivamente* desde el 30. Para localizar cada instrucción de la **OC** tiene una mesa contador mecánico para localizar instrucciones (**CLI**), que siempre arranca el 30 con un pulsador para avanzarlo.

***Funcionamiento***: una vez que instrucciones y materia prima estan en **D** supera el timbre, con lo cual la OC pide la instrucción (**I1**), que esta en el box cuyo numero (30) es el que aparece en el **CLI** siendo que la misma ira hacia la **MI**. Luego desde la **OC** se pulsa el botón **CLI** para que el numero suma (31), a fin que permita localizar **I2** cuando suene otra vez el timbre. Cuando la **I1** llega la MI en la OC se lee que ordena "Pasar la pieza que esta en el box 44 (cilindro en este caso) hacia **E**". La **OC** por la que la OC impartirá directivas para que se cumpla de dichas orden. Cuando **I2** llega a **MI** para ser leída por la **OC** ordena "Pasar a la **UT** pieza que esta en **E**(el cilindro), darle forma cono y dejarlo en **E**". La **OC** ordenara los movimientos y la **UT** operación para realizar para ejecutar la orden, luego de la cual sonara el timbre. Entonces la **OC** pediría la instrucción (**I2**) que esta en box 32 indicado por el **CLI** y pulsara el botón para que se indique 33.
**I3** ordena "Pasar a la **UT** que esta en **E**( en este caso en el cono) darle forma en el tornillo en **E**". La OC llevara a cabo la orden, sonara el timbre, pedirá **I4** y el **CLI** pasara 34. **I4** ordena "Pasar lo que esta en **E** el box 21".

La OC cumplimentara **I4**, sonara el timbre pedirá **I5**y el **CLI** pasara a 35. **I5** ordena "Pasar lo que esta en el box 21 a Expedición". En Expedición el tornillo sera puesto en la caja para ser enviado al exterior. 

Con vistas al funcionamiento de un computador de proceso descrito para sintetizar y definir las funciones de subsistema tratados, existiendo los siguientes correspondencia en relación con la figura 1.6 y 1.7.

**UP = UCP** (Unidad Central de Proceso o Procesador)

**UT = UAL** (Unidad Aritmético-Lógica)

**CLI = IP** (Puntero de Instrucciones)

**E = AX** (Registro acumulador AX)

**O****C =** **UC** (Unidad de Control)

**MI = RI** (Registro de instrucciones)

Deposito **D** = Memoria

El Deposito (**Memoria**) sirve para almacenar para instrucciones y materia prima (datos) y piezas terminadas (resultados). Esta dividido en boxex (celdas) con números (direcciones) para localizarlos.
Las **UP** (**UCP**) opera confirme a una secuencia que las instrucciones que la **OC** (**UC**) obtiene, una por una, del Deposito (Memoria) para luego ejecutar bajo su control. Una instrucción ordena el movimiento o una operación y movimientos relacionados con ella. La operación realiza la **UT**(**UAL**) que recibe la materia prima (datos numéricos) y produce productos (resultados numéricos) que antes no existían, según la operación que ordena **OC**(**UC**)

***¿Cuales son las "reglas del juego" para que el proceso siga correctamente?***

Dado que la **OC**(**UC**) no sabe donde esta el deposito (**Memoria**) esta instrucción como tampoco donde esta la materia prima (datos) a operar, **se deben cumplir las siguientes reglas** para que el proceso siga correctamente:

- Antes de iniciar el procesamiento de deposito (Memoria) deben entrar las instrucciones y la materia prima (datos) a procesar. Esto no se vio como no afecta el proceso a realizar, pues con el **CLI** se localiza cada instrucción y se indica donde esta lo que operara.
- Inicializar **CLI**(**IP**) con el numero de box (Dirección) que puede ser cualquiera donde se halla la primera instrucción.
- Ubicar las instrucciones en una secuencia en boxes (celdas) **consecutivos**, siendo que cada una se localiza por su numero de box dado por el **CLI** (**IP**), y luego pasa a **MI**(**RI**) donde es leida (descodificada) por la OC (**UC**). Si por ej. **CLI** pesa 33 a 34 se asume que 34 esta la instrucción que sigue. De no ser así, se pierde el hilo de proceso.
- Construir cada instrucción de modo que **proves** el numero (dirección) del box (celda) **donde encontrar la materia prima** (dato numérico)  que se ordena a operar, y que indica implícita  y explícitamente el lugar   donde Irán resultados.

Caja de Construcción: 

1. Ordena una operación;
2. Permite localizar aquello que se va a operar;
3. Indica donde va a el resultado;
4. A partir de su localización permite que encuentre la siguiente instrucción a ejecutar mediante el CLI (IP).

En la **UP**(**UCP**) existe una tercer zona para alamacenamiento temporario donde están **E**(**AX**), **MI**(**RI**), **CLI**(**IP**). La **UP**(**UCP**) y el deposito (Memoria) -de una sola abertura cada una -se comunican con un pasillo )lineas de datos de un bus) por el que pasa cada instrucción seguido (o no) de materia prima (datos) o resultados este pasillo (bus) a su vez conecta a pasillos para la comunicación con el deposito de la recepción o la expedición (**periféricos**).

Cuando en la fabrica la materia prima pasa de un box hacia E, deja estar en box, pero con los datos (símbolos) es distinto. En el acto leer, una copia de lo que vemos pasa nuestra retina hasta desaparezcan del papel los papeles leídos. En los proceso de datos *incluidos lo que hace un computador* siempre que se lee información almacenada **una copia de la misma** pasa el lugar destino, quedando sin modificar la información leída. En un computador dicha copia destruye la información existente en el destino.

Es definitiva continuamente 
se repite el siguiente ciclo: con el **CLI(**I**P**) se localiza instrucción a ejecutar que va a **MI**(**RI**) y luego **CLI**(**IP**) toma el valor para localizar instrucción siguiente una vez que se ejecute la que llego a **MI**(**RI**). Esta a su vez permite localizar la materia prima (dato) a operar según la operación ordenada cuyo resultado ira al destino indicado en dicha instrucción. Luego otra ves con el **CLI**(**IP**) se localiza la instrucción a ejecutar a **MI**(**RI**), etc.

###¿Que es lo basico que se necesita conocer acerca de los bits, bytes y de la equivalencia entre binario y hexa para operar en el programa debug?###

El **apendice 1** trata que un detalle de un sistema numérico, el sistema binario, el hexadecimal, la suma y resta binarias y codificación  ASCII caracteres titeados. En lo que siguen se dan conceptos básicos para entender el sistema binario y poder operar en hexa para experimentar el debug (sección 1.6).  **100101**

En el sistema decimal **3 0 9** simboliza en un cojunto con ese numero de elementos se formaron 3 grupos de 100 (3x100), y que con los  309 - 309 - 9 elementos restantes no se pudo formar ningún (0) grupo de 10(0x10), pero si 9 grupos de 1(9x1). O sea: 3x100 + 0x10 + 9x1 = 309. Los grupos son de 1, 10, 100, 1000....elementos. Cada uso de 10 veces el interior, siendo 10 la cantidad de símbolos usados (0 al 9) para simbolizar cualquier numero. Pueden formarse hasta 9 grupos de cada tipo. 

En general, en cada sistema numérico posicional, partiendo de grupos de un elemento cada tipo de grupo es tantas veces mayor que el anterior como la cantidad de símbolos empleada un sistema (10 veces el decimal y dos veces en binario).
Cada sistema es una manera distinta en dividir en grupos de sistemas de conjunto de elementos cuyo numero se quiere simbolizar. Se pueden formar hasta k de grupos de cada tipo, siendo el símbolo mayor de sistema: hasta 9 en decimal; solo hasta un grupo de cada tipo; o ninguno, en binario, y hasta 15 = F en hexadecimal.

          8421 

    0     0000  0 = 0X8 + 0X4 + 0X2 + 0X1

    1     0001  1  = 0X8 + 0X4 + 0X2 + 1X1

    2     0010  2  = 0X8 + 0X4 + 1X2 + 0X1

    3     0011  3  = 0X8 + 0X4 + 1X2 + 1X1

    4     0100  4  = 0X8 + 1X4 + 0X2 + 0X1

    5     0101  5  = 0X8 + 1X4 + 0X2 + 1X1

    6     0110  6  = 0X8 + 1X4 + 1X2 + 0X1

    7     0111  7  = 0X8 + 1X4 + 1X2 + 1X1

    8     1000  8  = 1X8 + 0X4 + 0X2 + 0X1

    9     1001  9  = 1X8 + 0X4 + 0X2 + 1X1

    A     1010  10  = 1X8 + 0X4 + 1X2 + 0X1

    B     1011  11  = 1X8 + 0X4 + 1X2 + 1X1

    C     1100  12  = 1X8 + 1X4 + 0X2 + 0X1

    D     1101  13  = 1X8 + 1X4 + 0X2 + 1X1

    E     1110  14  = 1X8 + 1X4 + 1X2 + 0X1

    F     1111  15  = 1X8 + 1X4 + 1X2 + 1X1
 
fig 1.4.

Así en el **sistema binario** que usa dos símbolos 0 y 1 representar cualquier numero (con el mismo significado de dichos símbolos en decimal) cada grupo sera el doble que el anterior. Simbolizados en decimal serian: 1, 2, 4, 8, 16, 32, 64, 128 ... Como el símbolo mayor es 1, solo se puede formar hasta un grupo de cada tipo. Un conjunto que en decimal simboliza 13 (formado por un grupo de 10 y 3 grupos de 1) en binario sera:

 **8 4 2 1**
 
 **1 1 0 1**

Ello significa que se pudo formar un grupo de 8 (1x8), y que con los 13 - 8 = 5 elementos restantes se pueden formar un grupo de 4 de (1x4), y que son los 5 - 4 = 1 restantes no se pudo formar ningún (0), grupo de 2, pero si un grupo de 1 1(1x1) de este modo 1x8 + 1x4 + 0x2 + 1x1 = 13.
Por lo tanto ahora el mismo conjunto que en decimal se había dividido en el grupo de 10 y 3 grupos de 1, en binario se ha dividido en grupo de 8, grupo de 4 y un grupo de 1  en la fig 1.4 aparecen formados como cuartetos los números binarios que en decimal  se corresponde con los números binarios que en decimal se corresponde con los números del 0 al 15.

El 130 decimal en binario seria:

     128 64 32 16 8 4 2 1 

      1  0   0  0 0 0 1 0




Cada uno de los símbolos que compone un numero binario en ingles *Bynari digit* abreviado **bit**.
Vale que un bit puede valer 0 a 1. 1101 tiene 4 bits, y el 1000010 tiene 8 bits. Cualquier conjunto de 8 bits se denomina byte (octeto en castellano).

El sistema numérico de hexadecimal ("hexa") usa 16 símbolos, del   **0 a F** ( con su correspondencia en decimal y binario indicada en la fig 1.4), con los cuales se puede formar cualquier numero. Los símbolos del 0 al 9 tienen el mismo significado que los análogos decimales. 

Puesto que en binario requiere representar un mismo numero algo mas de triple de dígitos que en decimal, dado que la información en el anterior de un computador es de 8, 16, 32, 64, y hasta 128 bits resulta engorrosa de ver en pantalla, en libros, en otro medios, y también para escribirlos. La tabla de fig 1.4 permite pasar rápidamente, por simple reemplazo cualquier numero binario a hexa y viceversa. Para ello se separa visualmente el numero binario, suponiendo que sea 11000000  en cuarteles 1100 0000.

En la figura 1.4 vemos 1100 en hexa es **C** y que 0000 es **0**; por lo tanto **11000000 = C0.**

Si usando el Debug, en la pantalla que un registro contiene A5B4, hallando el cuarteto a cuarteto que lo corresponde a cada símbolo y remplazado, resulta: 

A 5 B 4 = 1010 0101 1011 0100.

O sea si leemos A5B4, en el interior del computador existen esos 16 bits.  
Vale la pena recalcar que el interior del computador no puede existir "hexa". Solo hay binario.

##¿Cual es la ventaja de operar en el interior de un computador con dos estados eléctricos correspondientes al 0 y 1 binarios?##

La breve explicación que sigue hace hincapié en la complejidad tecnológica y la menor confiabilidad que implicaría diez estados eléctricos necesarios para representar dígitos decimales.
Los millones de transiciones que hoy componen hoy día los circuitos de un computador funcionan como la llave de dos estados "si-no" usadas para la electricidad hogareña; pero por ser los transistores dispositivos electrónicos, pueden cambiar de un estado al otro millones de veces por segundo. Esto es cada transistor opera uno de dos estados perfectamente definidos deja pasar la corriente eléctrica (**1**) o no (**0**).

Operar tecnológicamente  con dos estados es mucho mas simple, y también mas confiable, que hacer trabajar los transistores con diez valores de corrientes o tensiones eléctricas distintos, con el fin de generar diez estados diferentes, para poder representar los dígitos 0 al 9 sistema decimal.

Por otra parte, dichos valores deberían aparecer fijos con la temperatura, con la complicación que ademas, debido a las dispersiones propia del proceso fabricación de circuitos integrados ("chips"), valores de corrientes generadas  variarían naturalmente en mas o menos -dentro de un cierto rango respecto a valores nominales promedio - con cada circuito que sale la fabrica. 

---

[^ Índice](README.md) | [Siguiente >](capitulo03.md)