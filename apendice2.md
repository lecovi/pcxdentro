[^ Índice](README.md) | [Siguiente >](apendice3.md)

---

# Apéndice 2

# Sistemas operativos: su lugar y funciones como parte del software.
# SOFTWARE DAÑINO: VIRUS

## Clasificación del software
Podemos clasificar el software en tres categorías: **software de aplicación, software de base y software “dañino”** (virus).

### SOFTWARE DE APLICACIONES
> El software de aplicaciones son los programas que desarrolla ó adquiere un usuario para que un sistema de computación realice las tareas que requiere.

### SOFTWARE DE SISTEMA
> Junto con un computador se vende o entrega el denominado “software de sistema” (o parte del mismo) sin el cual su manejo sería bastante complicado para la realización de las tareas requeridas,y su programación estaría a cargo de especialistas en el hardware, amen de resultar muy lenta y engorrosa. También por seguridad no conviene en muchos sistemas que cualquier usuario acceda a discos o destruya información de otros.
Este software se compone, pues, de  programas para llevar a cabo funciones del sistema estrechamente relacionadas con el hardware de un sistema de computación (operaciones de E/S, supervisión de multitarea, traducción de lenguajes, manejo de archivos, etc).
La función de software del sistema es controlar y dirigir la operación de una computadora, de modo que al usuario le parezca estar frente a una potente máquina “virtual”, fácil de operar y programar, con la que se puede “diagnosticar”. Así no tiene que vérselas con la máquina “real”, electrónica.
Ésta en esencia sólo realiza un limitado número de operaciones elementales a gran velocidad pero “sobre ella” el software del sistema simula otra máquina virtual, que ante el usuario aparenta ser cualitativamente superior.
Vale decir que los programas del sistema sirven para que un computador pueda usarse para resolver los problemas de aplicaciones de los usuario, y en general han sido desarrollados para un determinado tipo de procesador.

Cuánto de este software necesita un computador depende de su aplicación. si está dedicado siempre a una misma tarea, ejecutando sólo un programa, lo más probable que no hagan falta programas del sistema. En cambio si es usado para múltiples usos, o sea para propósitos generales, es indispensable contar con una jerarquía de tales programas.
El software del sistema se puede  clasificar como sigue:
* el **“software de base”**
* el **“software de control de comunicaciones”**
* el **“software de administración de bases de datos”**

El _software de base_ (**sistema operativo + utilitarios**) es el principal encargado de transformar la máquina “desnuda” en otra virtual, con facilidades y potencialidades propias.
Fue el primero que se desarrolló para ayudar al usuario en el desarrollo y ejecución automática de programas de software de aplicaciones; así como para controlar dicha ejecución, y salvar errores que pueden subsanarse durante la misma (como los de lectura de disco y otros). La experiencia fue indicando que existe un conjunto de procesos, como los de E/S, la traducción de un lenguaje de programación de alto nivel (Cobol, Fortran, Basic, Pascal, C, ...) a instrucciones de máquina, ciertos cálculos rutinarios,  y otros, que independientemente del proceso de datos que realice un computador, siempre aparecen en alguna etapa del mismo.
Los fabricantes de computadoras desde un principio comenzaron a proveer los programas y subrutinas estándares para poder realizarlos, a la vez que tornaban más automático y fácil el manejo de las máquinas, merced a otros programas que también vendían. Su desarrollo implica muchas horas-hombre de trabajo, que un usuario común no puede concretar. Aparecieron así los primeros sistemas de (**SO**), como también se indica en el apéndice 3.
 
> Un **sistema operativo** puede definirse como un conjunto de programas que controlan la operación automática de un sistema de computación, con dos funcionarios complementaras.
> I.  Para que sea una máquina virtual _fácil de operar_ y programar.
> II. Para administrar los recursos de dicho sistema, a fin de optimizar su funcionamiento detectar errores e intentar salvarlos.
 
Según SO que se trate, se da distinta importancia a estas funciones.
Con el fin de facilitar la operación de un computador, un SO decodifica un conjunto de comandos que el usuario ordena por teclado, los cuales conforman un “lenguaje de control de trabajos”. En el presente, a través de programas interactivos como el windows, estos comandos se ordenan clickeando un botón del mouse sobre la porción de pantalla que representa el comando en cuestión.
> Un SO puede dividirse en módulos que administran los cuatro recursos de un sistema de cómputo UCP, MP, PERIFÉRICOS Y ARCHIVOS. 

Así se tiene:
* Programas para determinar cuál será el próximo programa que ejecutará la UCP, y ordenar su ejecución sin intervención del operador.
* Programas para establecer los lugares disponibles de la MP donde se almacenarán programas a ejecutar y sus datos.
* Programas para procesos E/S de datos entre MP y periféricos. (Para leer/Escribir un sector de un disco, para leer/ escribir un port de interfaz, borrar pantalla, etc.
* Programas para manejar archivos en discos y cintas. (creación, borrado, apertura, cierre, escritura, lectura, etc de archivos).

En **multiprogramación** (_“multitasking” - multitarea_) varios programas presentes en MP dan lugar a procesos que se disputan los 4 recursos citados. El SO optimiza el funcionamiento del conjunto, oficializando de “árbitro”, posibilitando que al mismo tiempo, mientras la UCP ejecuta uno de los programas de usuario, se realicen también procesos de E/S correspondientes a otros programas de usuario, almacenados en MP.
_Los programas de un SO están constituidos básicamente por las mismas instrucciones que los programas de usuario, sólo que organizadas para cumplir distintos propósitos (como los de arriba indicados)._ Asimismo, _estos programas_ -como cualquier otro- _son ejecutados por la UC de la forma vista._
Por ejemplo, no existe una instrucción “ especial” del SO, que ordene controlar si hay o no papel en una impresora, sino una _secuencia_ de instrucciones _simples_ que combinadas adecuadamente cumplen dicho cometido, formando parte de una subrutina del SO.
Los SO pueden clasificarse como sigue:

* **SO monotarea**: sólo pueden controlar la ejecución de una tarea del usuario por vez. Simplemente cargan y ubican en MP la aplicación en curso, posibilitando que pueda usar los recursos del sistema. Cuando aparece un comando tipo EXIT el SO da por finalizada la aplicación y se encarga de encadenar la siguiente. Ejemplo D.O.S.
* **SO multitarea**: permite la multiprogramación, cargando y ubicando en MP diversas aplicaciones, pro-porcionando a cada aplicación la posibilidad de usar los recursos existentes. Controla que la UCP ejecute sucesivamente porciones de cada una, con la suficiente rapidez para dar la impresión que cada tarea o usuario tiene todo el sistema a su disposición. Ejemplos: los SO “UNIX” y “OS/2” y “WINDOWS NT”.

> 1. Las rutinas de manejo de cada periférico, que contemplan temporizaciones, sincronizaciones, detalles circuitales del mismo, se conocen como el driver del periférico en cuestión

Existen dos clases de SO multitarea:
a. **SO de “tiempo compartido”** (_“time sharing”_) que asignan a cada aplicación el tiempo que periódicamente, en una “ronda” de procesos, tiene asignado para que la UCO ejecute parte del mismo.
b. **SO de “tiempo real”**: cada tarea se ejecuta durante un tiempo que depende de determinados eventos -como ser la realización de una E/S- que ocasionan la _conmutación_ de una tarea a otra, volviendo más tarde a completarse el proceso de una actividad inconclusa.

Los **programas utilitarios** agilizan ciertos procesos que requiere el uso normal de un computador. Así entre otros tenemos:

* **Programas traductores** (**compiladores** e intérpretes) a código de máquina de programas escritos en lenguajes de alto nivel (Fortran, Cobol, Basic, etc).
* **Programas editores de enlace** (**“link-editores”**) que acoplan subrutinas a programas compilados, de modo que pueden ejecutarse como un todo.
* **Programas editores de texto** o de programas en curso de desarrollo.
* **Programas cargadores**, que pasan programas de discos a MP.
* **Programas de servicio**, como los que pasan datos de disco a cinta.
* **Programas** para manejar “hojas electrónicas” y “menús”.
* **Programas para depurar errores** en otros programas en desarrollo.

Se trata de programas que dan “apoyo”, en el sentido que preparan la ejecución de otros programas, ayudan al usuario a desarrollar programas. Estos programas coordinados por el SO. Mediante un “lenguaje de comandos” el usuario especifica al SO qué desea realizar, para que sea éste el que tome el control del proceso a partir de dicha orden, quedando el usuario libre de esa responsabilidad.

Con el advenimiento del teleprocesamiento en gran escala, con computadores conectados a redes, se fueros desarrollando **“software de control de comunicaciones”**, encargado de la gestión y manejo de las comunicaciones a distancia. Gracias al mismo, cuestiones tales como los protocolos para establecer y concluir una comunicación entre computadores y/o terminales, la verificación de errores en la transmisión de datos, y el pedido de retransmisión en caso de error, son “transparentes” para el usuario, que así no debe desarrollar un software para comunicaciones a distancia. En general este software se activa a través del SO, ante un requerimiento de un programa de usuario de hacer una entrada o salida desde o hacia una terminal o computadora remota.

El concepto de **“base de datos”** o **“banco de datos”** se refiere a una colección de datos sobre un mismo tema, interrelacionados, almacenados con un mínimo de redundancia, tales que los mismos puedan ser usados por tantas aplicaciones como sea posible.
En una primera etapa,las denominadas bases de datos eran varios archivos relacionados, diseñados para una aplicación determinada, o para un grupo de aplicaciones muy semejantes, a las que un programa accedía a través del módulo administrador del SO.
Así el archivo del departamento de compras de una empresa servía en menor grado para producción, pero no era muy útil para otras gerencias, A medida que las bases de datos se emplearon para múltiples aplicaciones fue necesario asegurar que su crecimiento, al variar la estructura general de los datos, no requiera modificar los programas de la aplicación que la utilizaban, y viceversa.
por otra parte, surgieron nuevas exigencias para las bases de los datos: deberían permitir que los usuarios utilicen los datos de una manera que no fuera siempre la prevista por los diseñadores para poder responder a distintos tipos de consultas. No es lo mismo pedir un listado de personal de una empresa por apellido, edad, cargo y sueldo, que solicitar una a base qué empleados ganan más de X pesos, su nombre y edad. Esto último supone un programa “inteligente”, con capacidad para deducción lógica y para dar respuestas a consultas de alto grado de abstracción.
Fue necesario desarrollar programas complejos para crear y mantener bases de datos, que relacionaran entre sí los distintos archivos de una base para que ella se comporte frente al usuario como si virtualmente tuviera “inteligencia”. Apareció así el **“software de administración o manejo de base de datos”** (sus siglas en inglés son **DBMS**).
 
Diferenciación en MP de software y datos:
Los datos a procesar y los resultados son registrados en Mp y registros de la misma manera que los programas mediante estados eléctricos de los circuitos. Si bien resulta claro que los datos no forman parte del hardware, en cada aplicación es menester distinguir cuáles son los datos y cuál es el software requerido para procesarlos.
_En general, los datos se almacenan en zonas de MP separadas de la zona donde está el programa que indica cómo procesarlos y ubicarlos._
En cada procesamiento los datos a tratar no forman parte del software que describe su tratamiento. _Es factible que un programa oficie de datos para otro programa._ Por ejemplo un programa que está en un lenguaje de UCP no puede ejecutar directamente (Cobol, C, Fortran, Basic, Pascal,...) debe traducirse a instrucciones en código de máquina, mediante un programa traductor correspondiente, el compliador.

### SOFTWARE DAÑINO (“VIRUS”)
> El **software “dañino”** está constituido por los **“virus”**, que son programas. Un programa ”virus” consta de dos partes.
Una de ellas al ser ejecutada por la UCP, sirve para autocopia del programa, con el fin de autorreproducirse tantas veces como pueda, para pasar de un computador a otro. La otra parte, al ser ejecutada produce daños para el que ha sido concebido el virus.

El “contagio” de un virus consiste en pasar subrepticiamente a formar parte de otro programa o de un programa en disco (archivo “ejecutable”, tipo .EXE, .COM, .SYS, .BIN, .BAT, los programas que están en los sectores de booteo de un disco y otros). Luego tiene lugar una fase de “incubación” o propagación durante la cual sólo se ejecuta la porción que autoreproduce el programa virus. Cuando se autocopió un cierto número de veces, o en una fecha prefijada, o cuando el usuario realiza algo especificado, se ejecuta la porción que provoca el daño objeto del virus.
Por ejemplo una forma típica de entrar un virus es cuando un disquete con un “game” infectado (programa ejecutable conteniendo un programa virus) es copiado de un disquete al disco rígido. Cuando se quiere usar el “game” se ejecuta éste y el programa virus, que así se auto reproduce, y copia del mismo se instalan en otros programas del usuario. Asimismo cualquier copia del “game” que se pase a mi amigo propagara el virus, y aunque luego el “game” se borre del disco, ya copias del mismo infectaron otros programas. Otros virus pasan a memoria cada vez que un archivo infectado se ejecuta, y residen en memoria esperando que se ejecute otro archivo, para infectarlo. Otra forma de contagio es encender el computador con un disquete en cuyo sector de booteo se ha introducido un programa virus. Puesto que cuando un computador arranca primero intenta hacerlo desde el programa de booteo del disquete, una copia del programa virus pasará luego al sector de booteo del disco rígido. D esta forma, cada vez que luego se encienda el equipo, se generará en memoria una copia del programa virus. Existen virus que suprimen la protección contra escritura de archivos y que restauran la última fecha de actualización de un archivo para que no se detecte que lo han cambiado. Asimismo pueden detectar las llamadas que se hacen a un archivo, de modo de simular la información que se obtendría si el archivo no estuviera infectado. Los virus “polimórficos” encriptan los códigos de las instrucciones que los componen de una manera distinta en los archivos que infectan. Con este auto encriptamiento evitan ser detectados por los programas “anti-virus”.
El daño de un virus puede tener como objetivo el borrado de información (archivos o discos completos), la alteración de tablas o parámetros que utiliza el SO (como la FAT -tabla de localización de archivos-), o directamente la modificación archivos con programas del SO. Existen virus que suplantan al SO en funciones claves, como la lectura/escritura del disco, asignación de memoria, obtención de información acerca de la configuración del sistema, etc.
También pueden destruir hardware, como ser obligar al cabezal del disco rígido que salte continuamente entre dos posiciones extremas (lo cual a su vez produce la pérdida de la información contenida en el disco), o intensificar la acción del haz de rayos catódicos, para producir un daño irreparable en la pantalla del monitor.




---

[^ Índice](README.md) | [Siguiente >](apendice3.md)
