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
El procesador es Bi-Endian, quiere decir que es configurable entre Big Endian y Little Endian. Aunque nuestro sistema operativo nos limita a Little Endian. Por tanto la regla que sigue es “el byte menos significativo ocupa la posición más baja”. Cuando escribimos un dato en una posición de memoria, dependiendo de si es byte, half word o word,... se ubica en memoria según el esquema de la figura 1.2.<br>
<img src="https://raw.githubusercontent.com/EduardoWhite/Interfaz/main/Captura.PNG"><br>
## Aspecto de un programa en ensamblador
En la siguiete imagen se muestra el código de la primera práctica que probaremos. En el código hay una serie de elementos que aparecerán en todos los programas y que estudiaremos a continuación.<br>
<img src="https://raw.githubusercontent.com/EduardoWhite/Interfaz/main/codigo.png"><br>
La principal característica de un módulo fuente en ensamblador es que existe una clara separación entre las instrucciones y los datos. La estructura más general de un módulo fuente es:

* Sección de datos. Viene identificada por la directiva .data. En esta zona se definen todas las variables que utiliza el programa con el objeto de reservar memoria para contener los valores asignados. Hay que tener especial cuidado para que los datos estén alineados en palabras de 4 bytes, sobre todo después de las cadenas. Alinear significa rellenar con ceros el final de un dato para que el siguiente dato comience en una dirección múltiplo de 4 (con los dos bits menos significativos a cero). Los datos son modificables.

* Sección de código. Se indica con la directiva .text, y sólo puede contener código o datos no modificables. Como todas las instrucciones son de 32 bits no hay que tener especial cuidado en que estén alineadas. Si tratamos de escribir en esta zona el ensamblador nos mostrará un mensaje de error

### Datos
Los datos se pueden representar de distintas maneras. Para representar números tenemos 4 bases. La más habitual es en su forma decimal, la cual no lleva ningún delimitador especial. Luego tenemos otra muy útil que es la representación hexadecimal, que indicaremos con el prefijo 0x. Otra interesante es la binaria, que emplea el prefijo 0b antes del número en binario. La cuarta y última base es la octal, que usaremos en raras ocasiones y se especifica con el prefijo 0. Sí, un cero a la izquierda de cualquier valor convierte en octal dicho número. Por ejemplo 015 equivale a 13 en decimal. Todas estas bases pueden ir con un signo menos delante, codificando el valor negativo en complemento a dos. Para representar carácteres y cadenas emplearemos las comillas simples y las comillas dobles respectivamente.

### Símbolos
Como las etiquetas se pueden ubicar tanto en la sección de datos como en la de código, la versatilidad que nos dan las mismas es enorme. En la zona de datos, las etiquetas pueden representar variables, constantes y cadenas. En la zona de código podemos usar etiquetas de salto, funciones y punteros a zona de datos. Las macros y las constantes simbólicas son símbolos cuyo ámbito pertenece al preprocesador, a diferencia de las etiquetas que pertenecen al del ensamblador. Se especifican con las directivas .macro y .equ respectivamente y permiten que el código sea más legible y menos repetitivo.

