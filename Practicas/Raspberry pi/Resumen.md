<a href="https://es.cooltext.com"><img src="https://images.cooltext.com/5476099.png" width="261" height="65" alt="¿Qué es ARM?" /></a>
<a href="http://es.cooltext.com" target="_top"><img src="https://cooltext.com/images/ct_pixel.gif" width="80" height="15" alt="Cool Text: Generador de Logotipos y Gráficos." border="0" /></a>
<br>
### Es una arquitectura RISC licenciable, es decir, la empresa ARM Holdings diseña la arquitectura, pero otras compañias las fabrican y venden los chips.
## Chip que usa la Raspberry pi
### Es el BCM2835

--------------------------------------------
**Registros:** Son una porción de memoria ultrarápida, se emplean para:
* Controlar instrucciones en ejecución.
* Manejar direccionamiento de memoria.
* Proporcionar capacidad arimética.

<img src="https://scontent.ftij1-1.fna.fbcdn.net/v/t1.0-0/p180x540/123103296_1234664046905849_4487772967957974685_n.jpg?_nc_cat=105&ccb=2&_nc_sid=730e14&_nc_eui2=AeFcN6hLinz0qclqY_KoB9ZSAlUWBILn9yECVRYEguf3IQSHsnKhvhBfoB3cy0_x1REOjK5iULZgMLm0ELWppunt&_nc_ohc=YfIIy4Xgr20AX8j_68G&_nc_ht=scontent.ftij1-1.fna&tp=6&oh=2f4b9af8f221c8f3be4793b3294e3e33&oe=5FBD7C7B">

**Registros generales:** su función es el almacenamiento temporal de datos. Son los 13 registros que van R0 hasta R12.<br>
**Registros especiales:** son los últimos 3 registros principales, R13, R14, R15. como son de propósito especial, tienen nombres alternativos.
- **SP/R13.** Puntero de pila. Sirve como puntero para almacenar variables locales y registros en llamadas a funciones,
- **LR/R14.** Registro de enlace. Almaecena la dirección de retorno cuando una instrucción BL ó BLX ejecuta una llamada a una rutina.
- **PC/R15.** Contador de programa. Es un registro que indica la posicion donde esta el procesador en su secuencia de insutrcciones. **Se incrementa de 4 en 4** cada vez que se ejecuta una instrucción, a menos que esta provoque un salto.
**Registro CPSR:** Alamacena las banderas condicionales y los bits de control. Los bits de control definen la habilitación de interruptores normales (I), interrupciones rápidas (F), modo Thumb (T) y el modo de operación de la CPU.<br><br>
**Existen 4 banderas**
- **N.** Se activa cuando el resultado es negativo
- **Z.** Se activa cuando el resultdao es cero o una comparación es cierta.
- **C.** Indica acarreo en las operaciones aritméticas.
- **V.** Desbordamiento aritmético.<br><br>

## Introducción a ensamblador.
**Lenguaje ensamblador:** es un lenguaje de bajo nivel que permite un control directo de la CPU y todos los elementos asociados. Cada línea de un programa ensamblador consta de una instrucción del procesador y la posición que ocupan los datos de esa instrucción.

## Esquema de almacenamiento
El procesador es Bi-Endian, quiere decir que es configurable entre Big Endian y Little Endian. Aunque nuestro sistema operativo nos limita a Little Endian. Por tanto la regla que sigue es “el byte menos significativo ocupa la posición más baja”. Cuando escribimos un dato en una posición de memoria, dependiendo de si es byte, half word o word,... se ubica en memoria según el esquema de la figura 1.2.
