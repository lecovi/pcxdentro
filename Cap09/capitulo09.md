# Utilidad de las intrucciones de salto

### Como operan las instrucciones de salto condicionado y por que son esenciales?

---
> Las operaciones de salto condicionado son esenciales, pues permiten pasar en forma automatica de un programa (proceso) a otro, en funcion de ciertos resultados alcanzados en el primero, determinables mediante los indicadores.
---

A fin de entender como operan estas instrucciones, modificaremos ligeramente la secuencia I1, I2, I3, I4 que aparece codificado en la figura 1.15, (en las figuras 1.36 a 1.40 se recuerda que ordenan las mismas). Luego de la instruccion I3 de resta plantearemos 2 alternativas de ejecucion: si el resultado de efectuar P+P-Q es cero, debe guardarse en la direccion  5010H, como se hizo antes mediante I4.
De no valer cero, dicho resultado se asignara a la direccion 5012H, mediante una instruccion semejante a I4, que designaremos I4s (por que se la ubica mediante una instruccion de salto).
La posibilidad de dos alternativas de ejecucion en funcion de un resultado anterior (el de la resta en este caso) se realiza insertando una instruccion de salto Is entre I3 e I4.

---
> Una instruccion de salto, permite decidir cual es la proxima instruccion que se ejecutara luego de ella, entre dos instrucciones posibles: La que le sigue a continuacion en memoria u otra cuya direccion en memoria ella indica. Este salto de una zona a otro de memoria tendra lugar o no, segun el valor de uno o mas indicadores de un resultado anterior.
---

En lo que sigue, codificaremos las instrucciones que ejecutaremos usando un Debug. Para poder concretar las dos alternativas planteadas, primero ejecutaremos las instrucciones con los datos anteriores, para obtener un resultado igual a cero, y luego las volveremos a ejecutar, pero cambiando el valor de un dato, para que el resultado no sea cero.

Las intrucciones I1, I2 e I3 seran las mismas que en la figura 1.15, por lo cual conservaremos los codigos, escritos tambien a partir de la direccion 0200H, de modo de efectuar primero P+P-Q. Estos codigos vuelven a aparecer en la figura 1.35.
Ahora vamos a codificar la instruccion Is de salto que ordena: " Si como resultado de la instruccion anterior (I3) el indicador Z vale 1 (indicacion RZ de resultado cero en el Debug) la proxima instruccion a ejecutar es la escrita a continuacion en memoria (I4).
Si Z=0 (NZ en el Debug) saltar a ejecucion la instruccion (I4s) que esta en la direccion que resulta de sumar a la direccion de la instruccion escrita a continuacion (I4) el valor indicado en esta instruccion ". El codigo de operacion que ordena lo que esta escrito entre comillas es 75 en Hexa, y el codigo de la instruccion es 75 XX H, donde XX es el valor a sumar citado. Esta informacion puede obternerse utilizando el Debug, como se vera.
Para el caso que se cumpla la condicion de salto (Z=0), hemos elegido XX=08, por lo que se pasara a ejecutar la iunstruccion I4s que esta 8 posiciones abajo de la direccion de la instruccion I4, escrita abajo de Is. En las direcciones 020By 020C se han escrito los dos bytes del codigo 7508 de Is (intercalada entre I3 e I4).
Sintetizando, el codigo 7508 ordena: si Z=1 ejecutar la instruccion que sigue por debajo en memoria si Z=0 saltar a ejecutar la instruccion que esta 8 posiciones abajo de la que se ejecuta si Z=0.

Abajo de la direccion de salto (direccion 020D en este caso) se debe escribir en memoria intruccion I4 (de codigo A31050, como en 1.15) que debe ejecutarse luego de Is para el caso que se cumpla la condicion, osea si la instruccion anterior I3 (de resta) resulto Z=1 (ZR) por ser cero el resultado de la operacion que ordeno I3.
Recordemos que este codigo ordena enviar a la direccion 5010H una copia del numero que esta en AX.

Ahora hay que escribir la instruccion I4s a ejecutar en la alternativa que se cumpla la condicion de salto (Z=0 o sea si aparece NZ en el Debug). Debe escribirse 8 posiociones abajo de I4 que comienza con 020D, se tiene: 020E, 020F, 0210, 0211, 0212, 0213, 0214, 0215.O sea, en Hexa 020D + 8 = 0215 sera la direccion donde escribir I4s (figura 1.35)
Esta instruccion ordena lo mismo que I4, pero asignando el resultado (que esta en AX) a la direccion 5012 como se planteo. Entonces su codigo de operacion tambien sera A3, y su codigo de instruccion sera A31250.

Habiendo codificado la secuencia de instrucciones a ejecutar, debemos escribirla en memoria usando el Debug, de la forma vista en la figura 1.16, a partir de la direccion 0200H. Una vez realizada la escritura, si verificamos la misma, debe obtenerse lo siguiente:

- E 200 [enter] (examinar memoria)
309D:0200   A1.     00.     50.     03.     06.     00.     50.     2B.
309D:0208   06.     06.     50.     75      08      A3      10      50  [enter]
-

Tambien habra que escribir en la direccion 0215 el codigo A3 12 50 (figura 1.35) sin importar (indicando XX) que esta escrito entre 0210 y 0214, debiendose a verificar que debe quedar:

- E 215 [enter]     (examinar memoria y escribir en ella)
309D:0215   A3.     12.     50.  [enter]
-

Conforme a lo establecido, primero ejecutaremos estas instrucciones con los datos del ejemplo anterior P = 1020H y Q = 2040H, que estan en las direcciones 5000 y 5006, respectivamente, de modo que no se cumpla la condicion de salto, o sea que se siga la secuencia I1, I2, I3, Is e I4. Entonces volvemos a escribir estos datos (pues los mismos antes escritos ya se borraron), debiendo quedar¹:
- E 5000 [enter]  (examinar memoria)
309D:5000   20.     10.     50.     8D.     46.     B0.     40.     20.  [enter]
-

Con estos datos y los codigos de instruccion escritos en memoria ejecutaremos instruccion por instruccion, siguiendo el mismo procedimiento llevado a cabo a tyraves de las figuras 1.19 a 1.22, que por tratarse de los mismos codif=gos y datos elegidos antes coincidiran hasta la figura 1.15.

- RIP  [enter]  (examinar IP)
IP 0100
:0200  [enter]
- 

-R  [enter] (examinar registros)
AX = 0000       BX = 0000       CX = 0000       DX = 0000       SP = FFEE       BP = 0000       SI = 0000       DI = 0000
DS = 309D       ES = 309D       SS = 309D       CS = 309D       IP = 0200   NV  UP  EI  PL  NZ² NA  PE  NC

309D:0200       A10050                   MOV        AX,[5000]                                   DS:5000 = 1020

--------------
(1) Tanto en esta version como en la version anterior de los codigos de instruccion, solo interesan los valores indicados en negrita.
(2) El flag Z que usaremos en este caso vale NZ (Z=0), pero podia haber sido en otro momento, o en otro computador: ZR (Z=1)
--------------

- T  [enter]  (orden de ejecucion de I1, que ordena designar al registro AX el contenido de la direccion 5000H)
AX = 1020       BX = 0000       CX = 0000       DX = 0000       SP = FFEE       BP = 0000       SI = 0000       DI = 0000
DS = 309D       ES = 309D       SS = 309D       CS = 309D       IP = 0203   NV  UP  EI  PL  NZ NA  PO  NC 

309D:0203       03060050                   ADD        AX,[5000]                                   DS:5000 = 1020
-

                                                    Figura 1.36
            


-T  [enter]  (Orden de ejecucion de I2 que ordena sumar  al registro AX el contenido de la direccion 5000H)
AX = 2040       BX = 0000       CX = 0000       DX = 0000       SP = FFEE       BP = 0000       SI = 0000       DI = 0000
DS = 309D       ES = 309D       SS = 309D       CS = 309D       IP = 0207   NV  UP  EI  PL  NZ NA  PO  NC 

309D:0207       2B060650                   SUB        AX,[5006]                                   DS:5006 = 2040

    
                                                    Figura 1.37
    

Hasta aca existe coincidencia total con las indicaciones de las figuras 1.19 y 1.20, como debe ser.

-T  [enter]  (Orden de ejecucion de I3 que ordena restar  al registro AX el contenido de la direccion 5006H)
AX = 0000       BX = 0000       CX = 0000       DX = 0000       SP = FFEE       BP = 0000       SI = 0000       DI = 0000
DS = 309D       ES = 309D       SS = 309D       CS = 309D       IP = 020B   NV  UP  EI  PL  ZR NA  PE  NC 

309D:020B       7508                    JNZ 0215¹


                                                    Figura 1.38 


El codigo 7508 indica que la proxima instruccion a ejecutar es la de salto (Is), y que de la resta efectuada resulto que el indicador Z cambio de NZ (N=0) a ZR (N=1), de resultado cero (pues al ejecutar I3 se hizo 2040 - 2040 = 0000), por lo cual podemos anticipar que luego de ejecutar Is la siguiente sera I4

- T  [enter]  (orden de ejecucion de Is que ordena saltar si Z=0)
AX = 0000       BX = 0000       CX = 0000       DX = 0000       SP = FFEE       BP = 0000       SI = 0000       DI = 0000
DS = 309D       ES = 309D       SS = 309D       CS = 309D       IP = 020D   NV  UP  EI  PL  ZR NA  PE  NC 

309D:020D       A31050                   MOD [5010], AX                                   DS:5010 = XXXX


                                                    Figura 1.39
                                                    
                                                    
Verificamos que la ejecucion de Is ha resultado que la proxima instruccion a ejecutar es la que sigue por orden (direccion 020D) y tiene codigo A31050, o sea que es I4. Vale decir que no se ha producido un salto hacia I4s de direccion 0205. Esto era prevesible, por que al obtenerse Z=1 (ZR) en la instruccion anterior, no se cumple la condicion de salto (que exige Z=0). Luego de ejecutar Is los indicadores no cambian.
Esto es general: luego de ejecutarse una instruccion de salto no cambian los indicadores de estado, puesto que en ella no se realiza ninguna operacion aritmetica o logica.
Para terminar esta alternativa, ejecutamos la instruccion I4 de codigo A31050:

- T  [enter]  (orden de ejecucion de I4, que ordena escribir en la direcccion 5010H una copia del contenido AX)
AX = 0000       BX = 0000       CX = 0000       DX = 0000       SP = FFEE       BP = 0000       SI = 0000       DI = 0000
DS = 309D       ES = 309D       SS = 309D       CS = 309D       IP = 0210   NV  UP  EI  PL  ZR NA  PE  NC 

309D:0210           (no interesa lo que continua escrito en este renglon)


                                                    Figura 1.40
                                                    
                                                    
Como ya hemos ejecutado la alternativa I1, I2, I3, Is e I4 no seguimos ejecutando ninguna instruccion mas.

Si queremos verificar que en las instrucciones 5010 y 5011 se escribio el resultado que esta en AX.
Hacemos:

-------------------
(1) JNZ en assembler son las siglas del jump NZ, o sea Saltar si resulto NZ al ejecutarse la instruccion anterior.
-------------------

-E 5010  [enter]  (examinar memoria)
309D:5010       00.     00.   [enter]

A continuacion, haremos que se ejecute la alternativa I1, I2, I3, Is e I4s para lo cual cambiaremos el valor de un dato, haciendo Q = 2000H, de modo que P + P
- Q sea distinto de cero, para que se cumpla condicion de salto.
Entonces, si escribimos en 5006 y 5007 el nuevo valor asignado a Q debe resultar en memoria:

- E 5000  [enter]  (examinar memoria)
309D:5000       20.     10.     50.     8D.     46.     B0.     00.     20.  [enter]
-

En lo que sigue ejecutamos los mismos codigos de instruccion -antes escritos en memoria y que permaneceran en ella mientras sigamos con el Debug o no los borremos- con los datos modificados. Nuevamente se dara una coincidencia de valores con pasas similares realizados.

-RIP  [enter]  (Asignar a IP la direccion de la proxima direccion a ejecutar)
IP 0100
:0200  [enter]
-

-R  [enter]  (Verificacion general para control)
AX = 0000       BX = 0000       CX = 0000       DX = 0000       SP = FFEE       BP = 0000       SI = 0000       DI = 0000
DS = 309D       ES = 309D       SS = 309D       CS = 309D       IP = 0200   NV  UP  EI  PL  ZR¹ NA  PE  NC 

309D:0200       A10050                   MOD AX,[5000]                                   DS:5000 = 1020
-

-T  [enter]  (Orden de ejecucion I1)
AX = 1020       BX = 0000       CX = 0000       DX = 0000       SP = FFEE       BP = 0000       SI = 0000       DI = 0000
DS = 309D       ES = 309D       SS = 309D       CS = 309D       IP = 0203   NV  UP  EI  PL  ZR NA  PO  NC 

309D:0203       03060050                   MOD AX,[5000]                                   DS:5000 = 1020
-

-T  [enter]  (Orden de ejecucion I2)
AX = 2040       BX = 0000       CX = 0000       DX = 0000       SP = FFEE       BP = 0000       SI = 0000       DI = 0000
DS = 309D       ES = 309D       SS = 309D       CS = 309D       IP = 0207   NV  UP  EI  PL  NZ NA  PO  NC 

309D:0207       2B060650                   SUB AX,[5006]                                   DS:5006 = 2000

                                                Figura 1.41
                                                
                                                
Hasta aca, como debe ser, hay coincidencia con las indicaciones de las figuras 1.36 y 1.37, salvo que en 5006 hay 2000.

De la ejecucion de la instruccion de resta resulta:

T  [enter]  (Orden de ejecucion I3)
AX = 0040       BX = 00000       CX = 0000       DX = 0000       SP = FFEE       BP = 0000       SI = 0000       DI = 0000
DS = 309D       ES = 309D       SS = 309D       CS = 309D       IP = 020B   NV  UP  EI  PL  NZ  NA  PE  NC 

309D:020B       7508                   JNZ 0215


                                                Figura 1.42
                                                
                                                
El codigo 7508 indica que la proxima instruccion a ejecutar es la de salto (Is), y que de la resta efectuda resulto la indicacion NZ (Z=0) de resultado no cero, por los cual es prevesible que luego de ejecutar Is la siguiente sera I4s

-------------------
(1) Este valor ZR (Z=1) del indicador Z, podia haber sido en otra oportunidad o en otra PC, el valor NZ (N=0)
-------------------


-T  [enter]  (Orden de ejecucion de la instruccion de salto Is)
AX = 0040       BX = 0000       CX = 0000       DX = 0000       SP = FFEE       BP = 0000       SI = 0000       DI = 0000
DS = 309D       ES = 309D       SS = 309D       CS = 309D       IP = 0215   NV  UP  EI  PL  NZ  NA  PE  NC 

309D:0215       A31250                   MOD [5012], AX                                   DS:5012 = XXXX


                                                Figura 1.43
                                            
                                            
Verificamos luego de ejecutar Is, que la proxima instruccion a ejecutar es la que esta en 0215 y tiene codigo A31250, o sea que es I4s. Vale decir, que se ha producido un salto hacia I4s de direccion 0215. Esto era pronosticable, por que al ser Z=0 (NZ) en la instruccion anterior, se cumple la condicion de salto. Lo anterior equivale a verificar que el valor de P + P = 2040 es distinto al valor de Q = 2000. De ser iguales apareceria ZR, como fue antes.
Para terminar esta alternativa, ejecutamos la instruccion I4s, de codigo A31250:

-T  [enter]  (Orden de ejecucion I4s)
AX = 0040       BX = 0000       CX = 0000       DX = 0000       SP = FFEE       BP = 0000       SI = 0000       DI = 0000
DS = 309D       ES = 309D       SS = 309D       CS = 309D       IP = 0218   NV  UP  EI  PL  NZ  NA  PE  NC 

309D:0218                   (no interesa lo que continua escrito en este renglon, pues no se utilizara)


                                                Figura 1.44                                            
                                                
                                                
Dado que hemos ejecutado la alternativa I1, I2, I3, Is e I4s no ejecutamos ninguna instruccion mas.

Para verificar que las direcciones 5012 y 5013 se escribio el resultado (0040) que esta en AX, hacemos:

- E 5012  [enter]  (examinar memoria)
309D:5012       40.     00.  [enter]  (recordar que los numeros se escriben con los bytes transpuestos)

---
> De esta forma se ha comprobado como una instruccion de salto condicionado permite que se ejecute una secuencia u otra segun un resultdo interno alcanzado (en nuestro ejemplo el resultado cero o no cero de una resta). Esto es fundamental para poder pasar automaticamente, por programa, de un proceso a otro.
---

Las instrucciones de salto para llamar subrutinas operan en esencia como Is de la figura 1.35, siendo que ordenan saltar a una instruccion que es la primera de una subrutina que esta en otra zona de memoria.
La ejecucion de la subrutina termina con otra instruccion de salto, que ordena retornar a la instruccion que en memoria sigue a Is. Tambien Is puede ordenar saltar hacia atras (figura 1.45) ¹ para permitir, por ejemplo, repetir N veces una secuencia de instrucciones de calculo, y luego pasar automaticamente a otra de impresion.
El valor N se escribe primero en memoria, y se le resta uno cada vez que se ejecuta la secuencia de calculo, mediante la instruccion Ir, de modo que ella se habra repetido N veces cuando N=0.
A la instruccion que ordena restar uno (Ir), le sigue una instruccion de salto Is (ubicada entre las dos secuencias). Esta en esencia determina luego que se le resta uno a N, si el resultado es cero o no.
Mientras no sea cero (Z=0), Is ordena saltar a la direccion 2500 donde esta I1, para que se vuelva a ejecutar la secuencia de calculo.
Cuando la resta resulte cero, no se cumple la condicion e Is ordena seguir con la secuencia de impresion de resultados, cuya primera instruccion (I400) esta escrita debajo de la instruccion de salto Is.

----------------
(1) En esta se ha supuesto, por simplicidad, que las instrucciones ocupan un byte
----------------
                                                



                                        


 
