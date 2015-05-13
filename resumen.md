Arquitectura de computadoras.
=============================

Unidad 1: Arquitectura y organización de computadoras.

Concepto de arquitectura y su relación con organización.
--------------------------------------------------------

La arquitectura de computadoras se refiere a los atributos de un sistema que son
visibles para un programador, es decir, aquellos atributos que tienen un impacto
directo en la ejecución lógica de un programa (el conjunto de instrucciones,
número de bits usados para representar los tipos de datos). La organización de
computadoras se refiere a las unidades funcionales y sus interconexiones, que
dan lugar a especificaciones arquitectónicas (las señales de control, tecnología
de memoria usada).

Buses.
------

Una computadora está constituida por el procesador, la memoria y un módulo de
E/S, que se comunican entre sí. En efecto, es una red de módulos elementales,
y por consiguiente deben existir líneas para interconectar estos módulos. El
conjunto de líneas que conectan los diversos módulos se denomina estructura de
interconexión. El diseño de esta estructura dependerá de los intercambios que
deban producirse entre los módulos. Los que se necesitan son:

Memoria: Recibe y envía datos. Recibe direcciones. Recibe señales de control
(leer, escribir, temporizar).

Módulo de E/S: Recibe señales de control de la computadora. Envía las señales de
control a los periféricos. Recibe direcciones de la computadora. Envía señales
de interrupción. Recibe y envía datos.

Procesador: Lee instrucciones y datos. Escribe datos una vez los ha procesado.
Envía señales de control a otras unidades. Recibe señales de interrupción.

La estructura de interconexión debe dar cobertura a los siguientes tipos de
transferencias:

  * Memoria a procesador y viceversa.
  * E/S a procesador y viceversa.
  * Memoria a E/S y viceversa.

La estructura de interconexión más común son las de bus y buses múltiples. Un
bus es un camino de comunicación entre dos o más dispositivos ya que se trata
de un medio de transmisión compartido. Cualquier señal transmitida por uno de
esos dispositivos está disponible para que los otros dispositivos conectados
al bus puedan acceder a ella. Un bus está constituido por varios caminos de
comunicación capaces de transmitir señales binarias representadas por 1 y por 0.
El bus que conecta los componentes principales del computador se denomina bus
del sistema.

Estructura.
-----------

El bus del sistema es un conjunto de conductores eléctricos paralelos. Estos
conductores son líneas de metal grabadas en una tarjeta que se extiende a través
de todos los componentes del sistema, cada uno de los cuales se conecta a
algunas o a todas las líneas del bus.

Está constituido por entre 50 y 100 líneas que se pueden clasificar en tres
grupos funcionales: líneas de datos, de direcciones y de control.

Las líneas de datos proporcionan un camino para transmitir datos entre los
módulos del sistema. Generalmente consta de 8, 16 o 32 líneas distintas, cuyo
número se conoce como anchura. El número de líneas determina cuántos bits se
pueden transferir al mismo tiempo.

Las líneas de dirección se utilizan para designar la fuente o el destino del
dato situado en el bus de datos. La anchura del bus de direcciones determina la
máxima capacidad de memoria posible en el sistema. Las líneas de direcciones
generalmente se utilizan también para direccionar los puertos de E/S.

Las líneas de control se utilizan para controlar el acceso y el uso de las
líneas de datos y de direcciones. Las señales de control transmiten tanto
órdenes como información de temporización entre los módulos del sistema. Las
líneas de control típicas son: E/L en memoria, petición de interrupción, señales
de reloj.

En cuanto al funcionamiento del bus, si un módulo desea enviar un dato a otro
debe hacer dos cosas: obtener el uso del bus y transferir el dato a través del
bus. Si un módulo desea pedir un dato a otro módulo debe obtener el uso del
bus y transferir la petición al otro módulo mediante las líneas de control y
dirección apropiadas.

Jerarquías de buses.
--------------------

Si se conecta un gran número de dispositivos al bus, las prestaciones pueden
disminuir. Hay dos causas principales:

1. Cuanto más dispositivos se conectan al bus, mayor es el retardo de
   propagación.

2. El bus puede convertirse en un cuello de botella a medida que las peticiones
   de transferencia acumuladas se aproximan a la capacidad del bus. Sin
   embargo, este problema se puede resolver, por ejemplo, incrementando el bus
   de datos.

Por consiguiente, la mayoría de las computadoras utilizan varios buses,
normalmente organizados jerárquicamente.

Una estructura típica es donde hay un bus local que conecta el procesador a la
memoria cache. El controlador de memoria cache conecta la cache no sólo al bus
local, sino también al bus del sistema, donde se conectan todos los módulos de
memoria principal. Es posible conectar controladores de E/S directamente al bus
del sistema. Una solución más eficiente consiste en utilizar uno o más buses de
expansión. La interfaz del bus de expansión regula las transferencias de datos
entre el bus del sistema y los controladores conectados al bus de expansión.
Esta disposición permite conectar al sistema una amplia variedad de dispositivos
de E/S.

Esta arquitectura de buses tradicional es razonablemente eficiente, pero
muestra su debilidad a medida que los dispositivos de E/S ofrecen prestaciones
cada vez mayores. La respuesta a esta situación, ha sido proponer un bus de
alta velocidad. En este caso, hay un bus local que conecta el procesador a
un controlador de cache, que a su vez está conectado al bus de sistema que
soporta a la memoria principal. El controlador de cache está integrado junto
con el adaptador, que permite la conexión al bus de alta velocidad. Éste último
es un bus diseñado específicamente para conectar dispositivos de E/S de alta
capacidad. Los dispositivos de velocidad menor pueden conectarse al bus de
expansión, que utiliza una interfaz para adaptar el tráfico entre el bus de
expansión y el bus de alta velocidad. La ventaja de esta organización es que
el bus de alta velocidad acerca al procesador los dispositivos que exigen
prestaciones elevadas, y al mismo tiempo, es independiente del procesador.

Elementos de diseño de un bus.
------------------------------

* Tipos de buses: las líneas del bus se pueden dividir en dos tipos genéricos:
  dedicadas y multiplexadas. Una línea de bus dedicada está permanente asignada
  a una función o a un subconjunto físico de componentes de la computadora,
  como por ejemplo, el uso de líneas separadas para direcciones y para datos.
  Sin embargo, la información de dirección y datos podría transmitirse a través
  del mismo conjunto de líneas si se utiliza una línea de control de dirección
  válida. Este método de uso de las mismas líneas para usos diferentes se llama
  multiplexado en el tiempo. La ventaja del multiplexado en el tiempo es el uso
  de menos líneas, cosa que ahorra espacio y, normalmente, coste. La desventaja
  es que se necesita una circuitería más compleja en cada módulo. Existe una
  posible reducción en las prestaciones debido a que los eventos que deben
  compartir las mismas líneas no pueden producirse en paralelo. La dedicación
  física se refiere al uso de múltiples buses, cada uno de los cuales conecta
  sólo un subconjunto de módulos. La ventaja de la dedicación física es su
  elevado rendimiento, debido a que hay menos disputas por el acceso al bus. La
  desventaja es el incremento en el tamaño y el costo del sistema.

* Método de arbitraje: En todos los sistemas, más de un módulo puede necesita
  el control del bus. Puesto que, en un instante dado, sólo una unidad puede
  transmitir a través del bus, se requiere algún método de arbitraje. Los
  diversos métodos se pueden clasificar como centralizados o distribuidos. En
  un esquema centralizado, un único dispositivo hardware, denominado
  controlador del bus, es responsable de asignar tiempos en el bus. En un
  esquema distribuido, no existe un controlador central. En su lugar, cada
  módulo dispone de lógica para controlar el acceso, y los módulos actúan
  conjuntamente para compartir el bus.

* Temporización: el término temporización hace referencia a la forma en la que
  se coordinan los eventos en el bus. Con temporización síncrona, la presencia
  de un evento en el bus está determinada por un reloj. El bus incluye una
  línea de reloj a través de la que se transmite una secuencia en la que se
  alternan intervalos regulares de igual duración a uno y a cero, llamados
  ciclos de reloj. Todos los dispositivos del bus pueden leer la línea de
  reloj, y todos los eventos empiezan al principio del ciclo de reloj. Con la
  temporización asíncrona, la presencia de un evento en el bus es consecuencia
  y depende de que se produzca un evento previo. La temporización síncrona es
  más fácil de implementar y comprobar, pero es menos flexible que la
  asíncrona. Debido a que todos los dispositivos en un bus síncrono deben
  utilizar la misma frecuencia de reloj, el sistema no puede aprovechar las
  mejoras en las prestaciones de los dispositivos. Con la temporización
  asíncrona, pueden compartir el bus una mezcla de dispositivos lentos y
  rápidos, utilizando tanto las tecnologías más antiguas, como las más
  recientes.

* Anchura del bus: la anchura del bus de datos afecta a las prestaciones del
  sistema: cuanto más ancho es el bus de datos, mayor es el número de bits que
  se transmiten a la vez. La anchura del bus de direcciones afecta a la
  capacidad del sistema: cuanto más ancho es el bus de direcciones, mayor es el
  rango de posiciones a las que se puede hacer referencia.

* Tipos de transferencia de datos: Todos los buses permiten tanto transferencia
  de escritura (dato de maestro a esclavo), como de lectura (dato de esclavo a
  maestro). En el caso de un bus con direcciones y datos multiplexados, el bus
  se utiliza primero para especificar la dirección y luego para transferir el
  dato. En el caso de que haya líneas dedicadas a datos y a direcciones, la
  dirección se sitúa en el bus de direcciones y se mantiene ahí, mientras que
  el dato se ubica en el bus de datos. En ciertos buses también son posibles
  algunas operaciones combinadas, como por ejemplo una operación de
  lectura-modificación-escritura es simplemente una lectura seguida
  inmediatamente de una escritura en la misma dirección.

Segmentación de instrucciones (pipelining).
-------------------------------------------

Estrategia de segmentación.

La segmentación de cauce es una forma particularmente efectiva de organizar el
hardware de la CPU para realizar más de una operación al mismo tiempo. Consiste
en descomponer el proceso de ejecución de las instrucciones en fases o etapas
que permitan una ejecución simultánea. Se hace referencia a segmentación de
cauce cuando se aceptan nuevas entradas antes de que algunas entradas aceptadas
con anterioridad aparezcan como salidas. En el procesamiento de una instrucción,
hay períodos en los que no se accede a memoria principal. Este tiempo podría
utilizarse en captar la siguiente instrucción en paralelo con la ejecución de la
actual. A esto se llama precaptación de instrucción.

Para conseguir una mayor aceleración, el cauce debe tener varias etapas:
Captación de instrucción. Decodificación de instrucción (decodificar la
instrucción, calcular operandos, captar operandos). Ejecución de instrucción.
Escritura de resultado. Con esta descomposición las diversas etapas tendrán casi
igual duración. Sin embargo, este diagrama supone que cada instrucción recorre
las seis etapas del cause, cuando no siempre se dará este caso. Por ejemplo, una
instrucción de carga no necesita escribir resultados. También supone que todas
las etapas pueden funcionar en paralelo y que no hay conflictos de memoria.
Sin embargo, la mayoría de los sistemas de memoria no permiten que se acceda
simultáneamente a la memoria.

Otra dificultad es la instrucción de bifurcación condicional, que puede
invalidar varias captaciones de instrucción. Un último problema, es que la etapa
de calcular operandos puede depender del contenido de un registro que podría
verse alterado por una instrucción previa que aún esté en el cauce. Hay dos
factores que frustran este patrón de diseño de altas prestaciones: En cada etapa
del cauce, hay algún gasto extra debido a la transferencia de datos de buffer a
buffer, lo que puede prolongar el tiempo de ejecución total de una instrucción
aislada. La cantidad de lógica de control necesaria para manejar dependencias de
memoria y registros, y para optimizar el uso del cauce aumenta con el número de
etapas.

Atascos de un cauce.
--------------------

Son las situaciones que impiden a la siguiente instrucción que se ejecute en el
ciclo que le corresponde.

Riesgos estructurales: son provocados por conflictos por los recursos, cuando
dos instrucciones necesitan utilizar el mismo recurso hardware en el mismo ciclo
(dos accesos simultáneos a memoria). Las posibles soluciones son la replicación
de unidades funcionales y cachés diferenciadas de datos e instrucciones.

Por dependencia de datos: ocurren cuando los operandos fuente o destino de
una instrucción no están disponibles en el momento en que se necesitan. Las
soluciones son el adelantamiento de operandos o instrucciones NOP y reordenación
de código.

Por dependencia de control: necesidad de tomar una decisión basada en los
resultados de una instrucción mientras las otras se están ejecutando.

Tratamiento de saltos.
----------------------

Se han considerado varias aproximaciones en el tratamiento de bifurcaciones
condicionales:

* Flujos múltiples: duplica las partes iniciales del cauce y deja que éste
  capte las dos instrucciones utilizando los dos caminos. Problemas: hay
  retardos debidos a la competencia por el acceso a los registros y a la
  memoria y pueden entrar en el cauce instrucciones de bifurcación adicionales
  antes de que se resuelva la decisión de la bifurcación original.

* Precaptar el destino del salto: cuando se identifica una instrucción de
  bifurcación condicional, se precapta la instrucción destino del salto, además
  de la siguiente a la de bifurcación. Se guarda esta instrucción hasta que se
  ejecute la instrucción de bifurcación. Si se produce el salto, el destino ya
  habrá sido precaptado.

* Buffer de bucles: es una memoria pequeña de gran velocidad que contiene un
  número de instrucciones captadas más recientemente. Si se va a producir un
  salto, el hardware comprueba en primer lugar si el destino del salto está en
  el buffer. En ese caso, la siguiente instrucción se capta del buffer. Esta
  estrategia se acomoda bien al tratamiento de bucles o iteraciones.

* Predicción de saltos: se pueden usar varias técnicas:

  * Predecir que nunca se salta (el procesador asume que el salto no se produce
    y continúa captando instrucciones).

  * Predecir que siempre se salta (el procesador asume que el salto se produce
    y siempre capta el destino del salto).

  * Predecir según el código de operación (el procesador asume que el salto se
    produce para ciertos códigos y no para otros).

  * Conmutador saltar/no saltar(a cada instrucción se asocian bits que reflejan
    su historial reciente y dirigen al procesador a tomar una decisión la
    próxima vez que encuentre la instrucción).

  * Tabla de historia de saltos (pequeña memoria caché donde cada elemento
    consta de la dirección de una instrucción de bifurcación, un número de bits
    de historia que guardan el estado de uso de esa instrucción e información
    sobre la instrucción destino).

  * Salto retardado: no hacer el salto hasta que sea necesario. Siempre se
    ejecuta la siguiente instrucción secuencial y el salto se ejecuta después
    del retardo de una instrucción. Requiere reordenar las instrucciones.

Llamadas y retornos de procedimientos.
--------------------------------------

Una técnica habitual para gestionar las llamadas y los retornos de los
procedimientos es utilizar una pila. Cuando el procesador ejecuta una
llamada, se almacena la dirección de retorno en la pila. Cuando se ejecuta
un retorno, se utiliza la dirección de la cima de la pila y se elimina esa
dirección. Es también necesario con frecuencia pasar parámetros en una llamada
a procedimiento. Estos se podrían pasar en los registros. Otra posibilidad es
almacenar los parámetros en la memoria justo después de las instrucciones de
llamada. Ambas técnicas tienen sus inconvenientes: si se utilizan los registros,
el programa llamado y el que realiza la llamada deben escribirse de manera que
se asegure que los registros se utilizan apropiadamente. El almacenamiento
de parámetros en memoria hace difícil intercambiar un número variable de
parámetros.

Una estrategia más flexible para el paso de parámetros es la pila. Cuando
el procesador ejecuta una llamada, no sólo apila la dirección de retorno,
sino también los parámetros que se desean pasar al procedimiento llamado. El
procedimiento invocado puede acceder a los parámetros en la pila. Al retornar
los parámetros de retorno se pueden almacenar también en la pila, debajo de
la dirección de retorno. El conjunto completo de parámetros, incluyendo la
dirección de retorno, se denomina marco de pila. 

Unidad 2: Subsistema Unidad Central de Procesos.
================================================

Computadoras de repertorio reducido de instrucciones (RISC).
------------------------------------------------------------

Características de las arquitecturas RISC.
------------------------------------------

Una instrucción por ciclo: un ciclo máquina se define como el tiempo que se
tarda en captar dos operandos desde dos registros, realizar una operación de
la ALU y almacenar el resultado en un registro. Así, las instrucciones máquina
de un RISC no deberían ser más complicadas que las microinstrucciones de las
máquinas CISC y deberían ejecutarse más o menos igual de rápido.

Operaciones registro a registro: las operaciones deben ser del tipo registro a
registro, con la excepción de sencillas operaciones LOAD y STORE. Esta forma
de diseño simplifica el repertorio de instrucciones y la unidad de control,
fomentando la optimización del uso de registros.

Modos de direccionamiento sencillos: casi todas las instrucciones RISC usan
el sencillo direccionamiento a registro. Se pueden incluir varios modos
adicionales, como el desplazamiento y el relativo al contador de programa. Esta
característica de diseño simplifica el repertorio de instrucciones y la unidad
de control.

Formatos de instrucción sencillos: generalmente sólo se usa un formato o
unos pocos. La longitud de las instrucciones es fija. Las posiciones de los
campos, especialmente la del código de operación, son fijas, permitiendo que la
decodificación del código de operación y el acceso a los operandos en registros
puedan tener lugar simultáneamente. Todo esto simplifica la unidad de control.

Las ventajas potenciales de la aproximación RISC son:

* Se pueden desarrollar compiladores optimizadotes más eficaces.
* La mayoría de las instrucciones generadas por un compilador son relativamente
  sencillas.
* El uso de la segmentación de las instrucciones más eficientemente.
* Los programas RISC deberían ser más sensibles a las interrupciones, ya que
  éstas se comprueban entre operaciones bastante elementales.
* Utilización de un amplio banco de registros.

Se necesita una estrategia que permita que los operandos a los que se accede con
mayor frecuencia se encuentren en registros, y que se minimicen las operaciones
registro-memoria. Hay dos aproximaciones básicas: una basada en software y la
otra en hardware. La primera consiste en confiar al compilador la maximización
del uso de los registros, asignando registros a las variables que se usen más
en un período de tiempo dado. La segunda, consiste sencillamente en usar más
registros.

Ventanas de registros.
----------------------

La labor del diseño es organizar los registros de tal modo que se reduzca la
necesidad de acceder a memoria. Un procedimiento típico emplea sólo unos pocos
parámetros de llamada y variables locales. Además, la profundidad de activación
de procedimientos fluctúa dentro de un rango relativamente pequeño.

Para explotar estas propiedades, se usan múltiples conjuntos pequeños de
registros, cada uno asignado a un procedimiento distinto. Una llamada a un
procedimiento hace que el procesador conmute automáticamente a una ventana de
registros distinta de tamaño fijo. Las ventanas de procedimientos adyacentes
están parcialmente solapadas para permitir el paso de parámetros.

La ventana se divide en tres áreas de tamaño fijo. Los registros de parámetros
contienen parámetros pasados al procedimiento en curso desde el procedimiento
que lo llamó. Los registros locales se usan para variables locales. Los
registros temporales se usan para intercambiar parámetros y resultados con el
siguiente nivel más bajo. Los registros temporales de un nivel son físicamente
los mismos que los registros de parámetros del nivel más bajo adyacente.

La organización real del banco de registros es un buffer circular de ventanas
solapadas.

Variables globales.
-------------------

El esquema de ventanas no trata la necesidad de almacenar las variables
globales. Es por ello que se sugieren dos opciones.

La primera es que el compilador asigne posiciones de memoria a las variables
declaradas como globales en un lenguaje de alto nivel, y que todas las
instrucciones máquina que reverencien esas variables usen operandos
referenciados en memoria. Para variables globales a las que se accede
frecuentemente, este esquema es ineficiente.


La alternativa, es incorporar al procesador un conjunto de registros globales.
Estos registros serían fijos en cuanto a su número, y accesibles a todos los
procedimientos.

Un amplio banco de registros frente a una cache.
------------------------------------------------

El banco de registros organizado en ventanas funciona como un buffer pequeño y
rápido, que contiene un subconjunto de todas las variables que probablemente
se usen mucho. Desde este punto de vista, el banco de registros se comporta
de manera muy similar a una memoria caché. Surge por tanto la cuestión de si
sería más sencillo y mejor, usar una caché y un tradicional banco de registros
pequeño.

Banco de registros amplio                | Cache
-----------------------------------------|----------------------------------------------
Todos los datos escalares locales.       | Datos escalares locales recientemente usados.
Variables individuales.                  | Bloques de memoria.
Variables globales asignadas por el      | Variables globales usadas recientemente.
compilador.                              |
Salvaguarda y restauración basadas en la | Salvaguarda y restauración basadas en el
profundidad de anidamiento.              | algoritmo de reemplazo.
Direccionamiento de registros.           | Direccionamiento de memoria.

Existe una característica en la cual la aproximación de los registros es
claramente superior, y que nos indica que un sistema basado en caché será
notablemente más lento. La distinción viene dada por la sobrecarga de
direccionamiento experimentada por cada una de las dos aproximaciones.

Para referenciar un dato escalar local en un banco de registros basado en
ventanas, se usan un número de registro "virtual" y un número de ventana. Los
dos pueden proporcionarse a un decodificador sencillo para seleccionar uno de
los registros físicos. Para referenciar una posición de memoria en la caché, hay
que generar una dirección de memoria completa. La complejidad de esta operación
depende del modo de direccionamiento. Por consiguiente, desde el punto de vista
de las prestaciones, el banco de registros basado en ventanas es superior para
datos escalares locales.

Optimización de registros basada en el compilador.
--------------------------------------------------

Si disponemos de una máquina RISC que contiene únicamente un pequeño número de
registros, en ese caso, el uso optimizado de registros es responsabilidad del
compilador. El objetivo del compilador es mantener en registros, en lugar de
en memoria, los operandos necesarios para tantos cálculos como sea posible, y
minimizar las operaciones de carga y almacenamiento.

Cada cantidad del programa candidata para residir en un registro se asigna a
un registro simbólico o virtual. El compilador asigna el número ilimitado de
registros simbólicos a un número fijo de registros reales. Si en una parte
concreta del programa hay más cantidades a tratar que registros reales, algunas
de las cantidades se asignan a posiciones de memoria.

Lo esencial de la labor de optimización es decidir qué cantidades tienen que ser
asignadas a registros en cualquier punto determinado del programa. Para ellos,
se utiliza una técnica conocida como "coloreado de grafos".

Optimización de la segmentación.
--------------------------------

Dada la naturaleza sencilla y regular de las instrucciones RISC, los esquemas de
segmentación se pueden emplear eficientemente, sin embargo, las dependencias de
datos y bifurcaciones reducen la velocidad de ejecución global. Para compensar
estas dependencias se han desarrollado técnicas de reorganización del código.

El salto retardado utiliza un salto que no tiene lugar hasta después de que se
ejecute la siguiente instrucción. Este intercambio de instrucciones funcionará
con éxito con saltos incondicionales, llamadas y retornos. Para bifurcaciones
condicionales, el procedimiento no se puede aplicar a ciegas.

Un tipo de táctica similar, llamada "carga retardad", se puede usar con las
instrucciones LOAD. En las instrucciones LOAD, el procesador bloquea el registro
destino de la carga. Después, el procesador continúa la ejecución del flujo
de instrucciones hasta que alcanza una instrucción que necesite ese registro,
deteniéndose hasta que la carga finalice.

¿Por qué CISC?
--------------

La tendencia hacia repertorios de instrucciones más ricos ha sido motivada
por dos razones principales: el deseo de simplificar los compiladores, y el
deseo de mejorar las prestaciones. Lo siguiente señala algunos de los peligros
potenciales de la aproximación CISC y proporciona cierta comprensión de la
motivación de los partidarios de los RISC:

La primera de las razones parece obvia, ya que si existen instrucciones máquina
que se parezcan a sentencias del lenguaje de alto nivel, la tarea se simplifica.
Las instrucciones máquina complejas son con frecuencia difíciles de aprovechar.
Los programas más pequeños ocupan menos memoria, aunque esta ventaja ya no es
primordial, y mejoran las prestaciones ya que menos instrucciones significa
que hay que captar menos bytes de instrucciones y en un entorno paginado los
programas más pequeños ocupan menos páginas. Un programa para el CISC, expresado
en lenguaje máquina simbólico, puede ser más corto (tener menos instrucciones),
peor el número de bits de memoria que ocupa no tiene por qué ser más pequeño.
Debido a que hay más instrucciones en un CISC, son precisos códigos de operación
más largos, produciendo instrucciones más largas.

En cuanto a la segunda de las razones, debido a la propensión a usar las
instrucciones más sencillas, la unidad de control completa debe hacerse más
compleja y la memoria de control del microprograma ha de hacerse más grande,
para proveer un repertorio de instrucciones más rico. Cualquiera de los dos
factores aumenta el tiempo de ejecución de las instrucciones simples.

No está nada claro que la tendencia hacia repertorios de instrucciones de
complejidad creciente sea apropiada.

La controversia entre RISC y SISC.
----------------------------------

El movimiento RISC representa una ruptura fundamental con la filosofía que hay
detrás de la tendencia general de incrementar la complejidad del procesador. El
trabajo que se ha hecho para evaluar las ventajas de la aproximación RISC se
puede agrupar en dos categorías:

* Cuantitativa: intentos de comparar el tamaño de los programas y su velocidad
  de ejecución, en máquinas RISC y CISC de similar tecnología.

* Cualitativa: revisión de asuntos tales como soporte de lenguajes de alto
  nivel y uso óptimo de los recursos VLSI.

Sin embargo, surgen varios problemas cuando se intentan realizar comparaciones:
No hay una pareja de máquinas RISC y SISC que sean comparables. No existe un
conjunto de programas de prueba definitivo. Es difícil separar los efectos del
hardware de los efectos debidos a la habilidad en el diseño del compilador.

La mayor parte de los análisis comparativos con RISC se han hecho con máquinas
"de juguete" en vez de con productos comerciales. La mayoría de las máquinas
comerciales anunciadas como RISC poseen una mezcla de características RISC y
CISC.

Interrupciones.
---------------

Prácticamente todas las computadoras disponen de un mecanismo mediante el
que otros módulos pueden interrumpir el procesamiento normal de la CPU.
Principalmente, las interrupciones proporcionan una forma de mejorar la
eficiencia del procesador, ya que con el uso de interrupciones, el procesador
puede dedicarse a ejecutar otras instrucciones mientras una operación de E/S
está en curso.

Hay cuatro tipos de interrupciones:

1. Programa: generadas por alguna condición que se produce como resultado de la
   ejecución de una instrucción, tal como desbordamiento aritmético.
2. Temporización: generadas por un temporizador interno al procesador.
3. E/S: generadas por un controlador de E/S, para indicar la finalización sin
   problemas de una operación o para avisar de errores.
4. Fallo de hardware: generadas por un fallo tal como la falta de potencia de
   alimentación.

Para permitir el uso de interrupciones, se añade un ciclo de interrupción al
ciclo de instrucción. En el ciclo de interrupción, el procesador comprueba si
se ha generado alguna interrupción, indicada por la presencia de una señal
de interrupción. Si no hay señales de interrupción pendientes, el procesador
continúa con el ciclo de captación y accede a la siguiente instrucción del
programa en curso. Si hay alguna interrupción pendiente, el procesador hace lo
siguiente:

1. Suspende la ejecución del programa en curso y guarda su contexto. Esto
   significa almacenar el contenido actual del contador de programa, que
   contiene la dirección de la siguiente instrucción y el registro palabra de
   estado.
2. Carga el contador de programa con la dirección de comienzo de una rutina de
   gestión de interrupción.

A continuación, el procesador prosigue con el ciclo de captación y accede a la
primera instrucción del programa de gestión de interrupción, que dará servicio a
la interrupción. Este programa determina el origen de la misma y realiza todas
las acciones que sean necesarias. Cuando la rutina de gestión de interrupción se
completa, el procesador puede proseguir la ejecución del programa de usuario en
el punto en el que se interrumpió.

Interrupciones múltiples.
-------------------------

Se pueden seguir dos alternativas para tratar las interrupciones múltiples.
La primera es desactivar las interrupciones mientras se está procesando una
interrupción. Una interrupción inhabilitada simplemente significa que el
procesador puede y debe ignorar la señal de petición de interrupción. Se si
produce una interrupción en ese momento, generalmente se mantiene pendiente, y
será examinada por el procesador una vez ésta haya activado las interrupciones.

El inconveniente de este sistema es que no tiene en cuenta la prioridad
relativa. Es por eso que la segunda alternativa consiste en definir prioridades
para las interrupciones, y permitir que una interrupción de prioridad más alta
pueda interrumpir a un gestor de interrupción de prioridad menor.

Unidad 3: Subsistema E/S.
=========================

Junto con el procesador y la memoria, el tercer elemento clave de una
computadora es un conjunto de módulos de E/S. Cada módulo se conecta al bus
del sistema o a un conmutador central, y controla uno o más dispositivos
periféricos. Un módulo de E/S está dotado de cierta "inteligencia", ya que
contiene la lógica necesaria para permitir la comunicación entre el periférico y
el bus.

Los periféricos no se conectan directamente al bus del sistema debido a que:

* Hay una amplia variedad de periféricos con formas de funcionamiento
  diferentes.
* La velocidad de transferencia de datos de los periféricos es mucho menor que
  la de la memoria o el procesador, por lo que no es práctico utilizar un bus
  del sistema de alta velocidad para comunicarse directamente con un
  periférico.
* Los periféricos utilizan datos con formatos y tamaños de palabra diferentes
  de los de la computadora a los que se conectan.

El módulo de E/S tiene dos funciones principales:

* Realizar la interfaz entre el procesador y la memoria a través del bus del
  sistema o un conmutador central.
* Realizar la interfaz entre uno o más dispositivos periféricos mediante
  enlaces de datos específicos.

Dispositivos externos.
----------------------

Las operaciones de E/S se realizan a través de una amplia gama de dispositivos,
que proporcionan una forma de intercambiar datos entre el exterior y la
computadora. Un dispositivo externo se conecta a la computadora mediante un
enlace a un módulo de E/S que se utiliza para intercambiar señales de control,
estado y datos entre el módulo de E/S y el dispositivo externo.

Los dispositivos externos se pueden clasificar en tres categorías:

* De interacción con humanos: permiten la comunicación con el usuario de la
  computadora.
* De interacción con máquinas: permiten la comunicación con elementos del
  equipo.
* De comunicación: permiten la comunicación con dispositivos remotos.

La conexión del dispositivo externo con el módulo de E/S se realiza a través
de señales de control, estado y datos. Los datos se intercambian en forma de
un conjunto de bits que son enviados a, o recibidos desde, el módulo de E/S.
Las señales de control determinan la función que debe realizar el dispositivo.
Las señales de estado indican el estado del dispositivo, que indica si el
dispositivo está preparado para la transferencia de datos.

La lógica de control asociada al dispositivo controla su operación en respuesta
a las indicaciones del módulo de E/S. El transductor convierte las señales
eléctricas asociadas al dato a otra forma de energía en el caso de una salida,
y viceversa en el caso de una entrada. Usualmente, existe un buffer asociado al
transductor para almacenar temporalmente el dato que se está transfiriendo entre
el módulo de E/S y el exterior. Módulos de E/S.

Funciones de un módulo.
-----------------------

Las principales funciones y requisitos de un módulo de E/S se encuentran dentro
de las siguientes categorías:

* Control y temporización: los recursos internos, tales como la memoria
  principal y el bus del sistema, deben compartirse entre distintas
  actividades, incluyendo la E/S de datos. Así, la función de E/S incluye
  ciertos requisitos de control y temporización, para coordinar el tráfico
  entre los recursos internos y los dispositivos externos.
* Comunicación con el procesador: esta comunicación implica decodificación de
  órdenes, intercambio de datos, información de estado y reconocimiento de
  dirección.
* Comunicación con los dispositivos: implica intercambiar órdenes, información
  de estado y datos.
* Almacenamiento temporal de datos: la velocidad de transferencia desde y hacia
  la memoria principal o el procesador es bastante alta, dicha velocidad puede
  ser varios órdenes de magnitud menor para la mayoría de los dispositivos
  periféricos. Los datos provenientes de la memoria se envían al módulo de E/S
  en ráfagas rápidas. Los datos se almacenan temporalmente en el módulo de E/S
  y después se envían al periférico a la velocidad de éste.
* Detección de errores: estos errores pueden ser defectos mecánicos y
  eléctricos en el funcionamiento del dispositivo. Cuando se encuentra un
  error, el módulo debe informarle al procesador.

Estructura de un módulo.
------------------------

El módulo se conecta al resto de la computadora a través de un conjunto
de líneas. Los datos que se transfieren a y desde el módulo se almacenan
temporalmente en uno o más registros de datos. Además, puede haber uno o más
registros de estado que proporcionan información del estado presente.

La lógica que hay en el módulo interactúa con el procesador a través de una
serie de líneas de control utilizadas por el procesador para proporcionar las
órdenes al módulo.

También debe ser capaz de reconocer y generar las direcciones asociadas a los
dispositivos que controla.

Por último, posee la lógica específica para la interfaz con cada uno de los
dispositivos que controla.

El funcionamiento de un módulo de E/S permite que el procesador vea a una
amplia gama de dispositivos de una forma simplificada, ocultado los detalles de
temporización, formatos y electromecánica de los dispositivos externos.

E/S Programada.
---------------

En la E/S programada, los datos se intercambian entre el procesador y el módulo
de E/S. El procesador ejecuta un programa que controla directamente la operación
de E/S. Cuando el procesador envía una orden al módulo, debe esperar hasta que
la operación de E/S concluya. Si el procesador es más rápido que el módulo de
E/S, el procesador desperdicia este tiempo.

Ordenes de E/S.
---------------

Al ejecutar una instrucción relacionada con una E/S, el procesador proporciona
una dirección especificando el módulo en particular y el dispositivo externo, y
una orden de E/S. Hay cuatro tipos de órdenes que puede recibir un módulo:
* Control: se utiliza para activar el periférico e indicarle qué hacer.
* Test: se utiliza para comprobar diversas condiciones de estado asociadas con
  el módulo y sus periféricos.
* Lectura: hace que el módulo capte un dato de un periférico y lo sitúe en un
  buffer interno. El procesador puede obtener el dato solicitando que el módulo
  lo ponga en el bus de datos.
* Escritura: hace que el módulo capte un dato del bus de datos y posteriormente
  lo transmita al periférico.

Instrucciones de E/S.
---------------------

Cuando el procesador, la memoria principal y las E/S comparten un bus común,
son posibles dos modos de direccionamiento: asignado en memoria y aislado.
Con las E/S asignadas en memoria, existe un único espacio de direcciones para
las posiciones de memoria y los dispositivos de E/S. La CPU considera los
registros de estado y de datos de los módulos de E/S como posiciones de memoria,
y utiliza las mismas instrucciones máquina para acceder tanto a memoria como a
los dispositivos de E/S. En este caso se necesita una sola línea de lectura y
una sola línea de escritura en el bus.

Alternativamente, el bus puede disponer de líneas de lectura y escritura en
memoria junto con las líneas para órdenes de entrada y salida. En este caso,
las líneas de órdenes especifican si la dirección se refiere a una posición de
memoria o a un dispositivo de E/S. Puesto que el espacio de direcciones de E/S
está aislado del de memoria, éste método se conoce con el nombre de E/S aislada.

E/S mediante interrupciones.
----------------------------

Consiste en que el procesador, tras enviar una orden de E/S a un módulo,
continúe realizando algún trabajo útil. Después, el módulo de E/S interrumpirá
al procesador para solicitar su servicio cuando esté preparado para intercambiar
datos con él. El procesador ejecuta entonces la transferencia de datos como
antes, y después continúa con el procesamiento previo.

Funcionamiento desde el punto de vista del módulo de E/S: para una entrada,
el módulo recibe una orden READ del procesador. El módulo procede a leer el
dato desde el periférico asociado. Una vez que el dato está en el registro de
datos del módulo, el módulo envía una interrupción al procesador a través de una
línea de control y espera hasta que el procesador solicite su dato. Cuando ha
recibido la solicitud, el módulo sitúa su dato en el bus de datos y pasa a estar
preparado para otra operación de E/S.

Funcionamiento desde el punto de vista del procesador: el procesador envía una
orden READ de lectura y pasa a realizar otro trabajo. Al final de cada ciclo
de instrucción, el procesador comprueba las interrupciones. Cuando se pide la
interrupción desde el módulo, el procesador guarda el contexto del programa en
curso, y procesa la interrupción. En este caso, el procesador lee la palabra de
datos del módulo y la almacena en memoria. Después, recupera el contexto del
programa que estaba ejecutando y continúa su ejecución.

Cuestiones de diseño.
---------------------

En la implementación de las E/S mediante interrupciones, aparecen dos
cuestiones: ¿cómo determina el procesador qué dispositivo ha provocado la
interrupción?, y, si se han producido varias interrupciones, ¿cómo decide el
procesador la que debe atender?

Para la identificación del dispositivo hay cuatro tipos de técnicas:
* Múltiples líneas de interrupción (no resulta práctico ya que si se utilizan
  varias líneas, es probable que a cada una se conecten varios módulos de E/S).
* Consulta software (cuando el procesador detecta una interrupción, se produce
  una bifurcación a una rutina de servicio de interrupción que se encarga de
  consultar a cada módulo de E/S para determinar el módulo que la ha provocado.
  Una vez identificado, se produce una bifurcación para que el procesador
  ejecute la rutina de servicio específica para ese dispositivo. La desventaja
  está en el tiempo que consume).
* Conexión en cadena (todos los módulos de E/S comparten una línea común para
  solicitar interrupciones y se conectan encadenándose uno tras otro. Cuando el
  procesador recibe una interrupción, activa el reconocimiento de interrupción.
  Esta señal se propaga a través de la secuencia de módulos de E/S hasta que
  alcanza un módulo que solicitó interrupción, quien responde colocando una
  palabra (denominado vector) en las líneas de datos. El procesador utiliza el
  vector como un puntero a la rutina de servicio de dispositivo apropiada).
* Arbitraje de bus (un módulo de E/S debe disponer del control del bus antes de
  poder activar la línea de petición de interrupción. Cuando el procesador
  detecta la interrupción, responde mediante la línea de reconocimiento de
  interrupción. Después, el módulo que solicitó la interrupción sitúa su vector
  en las líneas de datos).

Las técnicas anteriores sirven para identificar el módulo de E/S que solicita la
interrupción, pero además proporcionan una forma de asignar prioridades cuando
más de un dispositivo está pidiendo que se sirva su interrupción. Con varias
líneas de interrupción, el procesador simplemente selecciona la línea con más
prioridad. Con la consulta software, el orden en el que se consultan los módulos
determina su prioridad, al igual que en la conexión en cadena. Finalmente,
en el arbitraje de bus, si existe un maestro del bus, sólo el maestro puede
interrumpir.

Acceso directo a memoria. (DMA)
-------------------------------

La E/S con interrupciones y la E/S programada, presentan dos inconvenientes
inherentes:

* La velocidad de transferencia de E/S está limitada por la velocidad a la cual
  el procesador puede comprobar y dar servicio a un dispositivo.
* El procesador debe dedicarse a la gestión de las transferencias de E/S.

Ambos métodos tienen un impacto negativo, tanto en la actividad del procesador
como en la velocidad de transferencia de E/S. Cuando hay que transferir grandes
volúmenes de datos, se requiere una técnica más eficiente: el acceso directo a
memoria.

El DMA requiere un módulo adicional en el bus del sistema. El módulo de DMA es
capaz de imitar al procesador y es capaz de recibir el control del sistema,
cedido por el procesador. Necesita dicho control para transferir datos a, y
desde memoria a través del bus del sistema, usándolo sólo cuando el procesador
no lo necesita, o debe forzar al procesador a que suspenda temporalmente su
funcionamiento. Esta última técnica es la más común y se denomina robo de ciclo.

Cuando el procesador desea leer o escribir un bloque de datos, envía una orden
al módulo de DMA, incluyendo la siguiente información:

* Si se solicita una lectura o una escritura, utilizando la línea de control de
  lectura o escritura entre el procesador y el módulo de DMA.
* La dirección del dispositivo de E/S, a través de las líneas de datos.
* La posición inicial de memoria a partir de donde se lee o se escribe,
  indicada a través de las líneas de datos y almacenada por el módulo de DMA en
  su registro de direcciones.
* El número de palabras a leer o escribir, también indicado a través de las
  líneas de datos y almacenado en el registro de cuenta de datos.

Después, el procesador continúa con otro trabajo. El módulo de DMA transfiere
el bloque completo de datos, palabra a palabra, directamente desde, o hacia
la memoria, sin que tenga que pasar a través del procesador. Cuando la
transferencia se ha terminado, el módulo de DMA envía una señal de interrupción
al procesador. Así pues, el procesador sólo interviene al comienzo y al final de
la transferencia.

El mecanismo de DMA puede configurarse de diversas formas:
Bus único, DMA independiente: todos los módulos comparten el mismo bus
del sistema. El módulo de DMA, actuando como un procesador suplementario, utiliza
E/S programada para intercambiar datos entre la memoria y un módulo de E/S a través
del módulo de DMA. Esta configuración es la más económica, pero es claramente
ineficiente.
Bus único, DMA-E/S integrados: en este caso, se integran las funciones de
DMA y de E/S, lo que significa que existe un camino entre el módulo de DMA y uno o
más módulos de E/S que no incluye al bus del sistema. La lógica del DMA puede ser
parte de un módulo de E/S o puede ser un módulo separado que controla a uno o mas
módulos de E/S.
Bus de E/S: se conectan los módulos de E/S a un módulo de DMA mediante
un bus de E/S. Esto reduce a uno el número de interfaces de E/S en el módulo de DMA,
y permite una configuración fácilmente ampliable.
En todos estos casos, el bus del sistema es usado por el módulo de DMA sólo para
intercambiar datos con la memoria. El intercambio de datos entre los módulos de DMA
y E/S se produce fuera del bus del sistema.

Canales de E/S.

Características.
El canal de E/S representa una ampliación del concepto de DMA. Un canal de E/S
puede ejecutar instrucciones de E/S, lo que le confiere un control completo sobre las
operaciones de E/S. En este caso, la CPU no ejecuta instrucciones de E/S; éstas se
almacenan en memoria principal para ser ejecutadas por un procesador de uso
específico contenido en el propio canal de E/S.
La CPU inicia una transferencia de E/S, indicando al canal de E/S que debe
ejecutar un programa de la memoria. El programa especifica el dispositivo, el área de
memoria para almacenamiento, la prioridad y las acciones a realizar en ciertas
situaciones de error. El canal de E/S sigue estas instrucciones y controla la transferencia
de datos.
Son comunes dos tipos de canales de E/S:
Un canal selector, que controla varios dispositivos de velocidad elevada y, en un
instante dado, se dedica a transferir datos a uno de esos dispositivos. Cada dispositivo o
grupo de dispositivos es manejado por un controlador de E/S.
Un canal multiplexor puede manejar las E/S de varios dispositivos al mismo
tiempo. Para dispositivos de velocidad reducida, un multiplexor de a byte acepta o
transmite caracteres tan rápido como es posible a varios dispositivos. Para dispositivos
de velocidad elevada, un multiplexor de bloque entrelaza bloques de datos de los
distintos dispositivos.

La interfaz externa.

Tipos de interfaces.
La interfaz entre el periférico y el módulo de E/S debe ajustarse a la naturaleza y
la forma de funcionar del periférico. Una de las principales características de la interfaz
es si es serie o paralela. En una interfaz paralela, hay varias líneas que conectan el
módulo de E/S y el periférico, y se transfieren varios bits simultáneamente a través del
bus de datos. En una interfaz serie, hay sólo una línea para transmitir los datos, y los
bits deben transmitirse uno a uno. Las interfaces paralelas se utilizan usualmente para
los dispositivos de alta velocidad, como una cinta o un disco. Las serie son más propias
de impresoras y terminales.
La transmisión serial es más lenta que la paralela puesto que se envía un bit a la
vez. Una ventaja significativa de la transmisión serial en relación a la paralela es un
menor costo del cableado puesto que se necesita un solo cable. Este ahorro en costo se
vuelve más significativo conforme sean mayores las distancias requeridas para la
comunicación.
Otra ventaja importante de la transmisión serial es la habilidad de transmitir a
través de líneas telefónicas convencionales a mucha distancia, mientras que la
transmisión en paralelo esta limitada en distancia en un rango de metros.

En cualquier caso, el módulo de E/S debe establecer un diálogo con el periférico
como el que sigue:

El módulo de E/S envía una señal de control solicitando permiso para enviar
datos.

El periférico reconoce la solicitud.
El módulo de E/S transfiere los datos.
El periférico reconoce la recepción de los datos.

Para el funcionamiento del módulo de E/S, es clave disponer de un buffer interno
que pueda almacenar los datos a transferir entre el periférico y el resto del sistema. Este
buffer permite que el módulo de E/S pueda compensar las diferencias de velocidad entre
el bus del sistema y sus líneas externas.

La conexión entre un módulo de E/S del computador y los dispositivos externos
puede ser punto-a-punto o multipunto. Una interfaz punto-a-punto proporciona una
línea específica entre el módulo de E/S y el dispositivo externo. Existen usualmente este
tipo de enlaces para el teclado, la impresora y el módem externo.

Las interfaces externas multipunto, utilizadas para soportar dispositivos de
almacenamiento masivos y dispositivos multimedia son, de hecho, buses externos, y
poseen el mismo tipo de lógica que los mismos.
Unidad 4: Subsistema de memoria.

Memoria caché.

El objetivo de la memoria caché es lograr que la velocidad de la memoria sea lo
más rápida posible. Hay una memoria principal relativamente grande y más lenta, junto
con una memoria caché más pequeña y rápida. La caché contiene una copia de partes de
la memoria principal. Cuando el procesador intenta leer una palabra de memoria, se
hace una comprobación para determinar si la palabra está en la caché. Si es así, se
entrega dicha palabra al procesador. Si no, un bloque de memoria principal, consistente
en un cierto número de palabras, se transfiere a la caché y, después, la palabra es
entregada al procesador. Debido al fenómeno de localidad de las referencias, cuando un
bloque de datos es captado por la caché para satisfacer una referencia a memoria simple,
es probable que se hagan referencias futuras a otras palabras del mismo bloque.

La localidad espacial se refiere a la tendencia durante la ejecución a involucrar
múltiples posiciones de memoria que estén agrupadas. La localidad espacial refleja la
tendencia del procesador a acceder a las instrucciones secuencialmente, y también la
tendencia de los programas a acceder a posiciones de datos consecutivas, como por
ejemplo cuando se procesa una tabla de datos. La localidad temporal hace referencia a
la tendencia del procesador a acceder a posiciones de memoria que han sido utilizadas
recientemente. Por ejemplo, cuando se ejecutan iteraciones de un bucle, el procesador
ejecuta repetidamente el mismo conjunto de instrucciones.

La caché se conecta con el procesador mediante líneas de datos, de control y de
direcciones. Las líneas de datos y de direcciones conectan también con buffers de datos
y de direcciones que las comunican con un bus del sistema, a través del cual se accede a
la memoria principal. Cuando ocurre un acierto de caché, los buffers de datos y de
direcciones se inhabilitan, y la comunicación tiene lugar sólo entre el procesador y
caché, sin tráfico en el bus. Cuando ocurre un fallo de caché, la dirección deseada se
carga en el bus del sistema, y el dato es llevado, a través del buffer de datos, tanto a la
caché como al procesador.

Elementos de diseño de la caché.
Tamaño de caché: nos gustaría que el tamaño fuera lo suficientemente pequeño
como para que el coste total medio por bit se aproximara al de la memoria principal
sola, y que fuera lo suficientemente grande como para que el tiempo de acceso medio
total fuera próximo al de la caché. El resultado es que cachés grandes tienden a ser
ligeramente más lentas que las pequeñas. El tamaño está también limitado por las
superficies disponibles de chip y de tarjeta. Los tamaños óptimos de caché se
encuentran entre 1K y 512K palabras.
Función de correspondencia: ya que hay menos líneas de caché que bloques de
memoria principal, se necesita un algoritmo que haga corresponder bloques de memoria
principal a líneas de caché. Pueden utilizarse tres técnicas:

Correspondencia directa: consiste en hacer corresponder cada bloque de
memoria principal a sólo una línea posible de caché. Desde el punto de vista del
acceso a caché, cada dirección de memoria principal puede verse como dividida
en dos campos. Los bits menos significativos identifican cada palabra dentro de
un bloque de memoria principal. Los bits restantes especifican uno de los bloques
de memoria principal. Esta técnica es simple y poco costosa de implementar. Su
principal desventaja es que hay una posición concreta de caché para cada bloque
dado. Por ello, si un programa referencia repetidas veces a palabras de dos
bloques diferentes asignados en la misma línea, dichos bloques se estarían
intercambiando continuamente en la caché, y la tasa de aciertos sería baja.

Correspondencia asociativa: permite que cada bloque de memoria
principal pueda cargarse en cualquier línea de la cache. La lógica de control de la
caché interpreta una dirección de memoria simplemente como una etiqueta y un
campo de palabra. El campo de etiqueta identifica unívocamente un bloque de
memoria principal. Para determinar si un bloque está en la caché, su lógica de
control debe examinar simultáneamente todas las etiquetas de líneas para buscar
una coincidencia. Hay flexibilidad para que cualquier bloque sea reemplazado
cuando se va a escribir uno nuevo en la caché. La principal desventaja es la
compleja circuitería necesaria para examinar en paralelo las etiquetas de todas las
líneas de caché.

Correspondencia asociativa por conjuntos: es una solución de
compromiso que recoge lo positivo de las correspondencias directa y asociativa,
sin presentar sus desventajas. En este caso, la caché se divide en conjuntos, cada
uno de un número x de líneas. Un bloque puede asignarse en cualquiera de las
líneas del conjunto. En este caso, la lógica de control de la caché interpreta una
dirección de memoria como tres campos: etiqueta, conjunto y palabra. Los bits de
conjunto especifican uno de los conjuntos. Los bits de campos de etiqueta y de
palabra especifican uno de los bloques de memoria principal. Con la
correspondencia asociativa por conjuntos, la etiqueta de una dirección de memoria
es mucho más corta, y se compara sólo con las etiquetas dentro de un mismo
conjunto. El uso de dos líneas por conjuntos es el caso más común, mejorando
significativamente la tasa de aciertos respecto de la correspondencia directa.

Algoritmos de sustitución.
Cuando se introduce un nuevo bloque en la caché, debe sustituirse uno de los
bloques existentes. Para el caso de correspondencia directa, sólo hay una posible línea
para cada bloque particular, y no hay elección posible. Para las técnicas asociativas, se
requieren algoritmos de sustitución que deben implementarse en hardware.
El más efectivo es probablemente el denominado "utilizado menos recientemente"
(LRU): se sustituye el bloque que se ha mantenido en la caché por más tiempo sin haber
sido referenciado. Esto es fácil de implementar para la asociativa por conjuntos de dos
vías.
Otra posibilidad es el "primero en entrar-primero en salir" (FIFO): se sustituye
aquel bloque del conjunto que ha estado más tiempo en la caché. El algoritmo FIFO
puede implementarse fácilmente mediante una técnica cíclica.
En la política de "utilizado menos frecuentemente" (LFU), se sustituye aquel
bloque del conjunto que ha experimentado menos referencias. LFU podría
implementarse asociando un contador a cada línea.
La última posibilidad es elegir una línea al azar entre las posibles candidatas.

Política de escritura.
Antes de que pueda ser reemplazado un bloque que está en una línea de caché, es
necesario comprobar si ha sido alterado en caché pero no en memoria principal. Si no lo
ha sido, puede escribirse sobre la línea de caché. Si ha sido modificado, esto significa
que se ha realizado al menos una operación de escritura sobre una palabra de la línea
correspondiente de la caché, y la memoria principal debe actualizarse de acuerdo con
ello.
La técnica más sencilla se denomina escritura inmediata. Utilizando esta técnica,
todas las operaciones de escritura se hacen tanto en caché como en memoria principal,
asegurando que el contenido de la memoria principal siempre es válido. La principal
desventaja de esta técnica es que genera un tráfico sustancial a memoria que puede
originar un cuello de botella.

Una técnica alternativa, es la post-escritura, que minimiza las escrituras en
memoria. Las actualizaciones se hacen sólo en la caché. Cuando tiene lugar una
actualización, se activa un bit ACTUALIZAR asociado a la línea. Después, cuando el
bloque es sustituido, es escrito en memoria principal sólo si el bit ACTUALIZAR está
activo. El problema es que a veces porciones de memoria principal no son válidas, y los
accesos por parte de los módulos de E/S sólo podrían hacerse a través de la cache,
complicando la circuitería.

Tamaño de línea.
Cuando se recupera y ubica en caché un bloque de datos, se recuperan no sólo la
palabra deseada, sino además algunas palabras adyacentes. A medida que aumenta el
tamaño de bloque, la tasa de aciertos primero aumenta debido al principio de localidad y
más datos útiles son llevados a la caché. Sin embargo, la tasa de aciertos comenzará a
decrecer.
Dos efectos concretos entran en juego:
Bloques más grandes reducen el número de bloques que caben en la caché.
A medida que un bloque se hace más grande, cada palabra adicional está más
lejos de la requerida, y por tanto es más improbable que sea necesaria a corto plazo.
Un tamaño entre 4 y 8 unidades direccionables parece estar razonablemente
próximo al óptimo

Número de cachés.
Cuando se introdujeron originalmente las cachés, un sistema tenía sólo una caché.
Más recientemente, se ha convertido en una norma el uso de múltiples cachés.
Ha sido posible tener una caché en el mismo chip del procesador, reduciendo la
actividad del bus externo del procesador y los tiempos de ejecución e incrementando las
prestaciones globales de sistema. Cuando la instrucción o dato requeridos se encuentran
en la caché on-chip, se elimina el acceso al bus. Los accesos a la caché on-chip se
efectúan apreciablemente más rápidos que los ciclos de bus y durante ese período el bus
está libre para realizar otras transferencias.
Los diseños más actuales incluyen tanto caché on-chip como externa. La
estructura resultante se conoce como caché de dos niveles. Si no hay caché 2 y el
procesador hace una petición de acceso a una posición de memoria que no está en la
caché 1, entonces el procesador debe acceder a la RAM o la ROM a través del bus,
obteniendo bajas prestaciones.
Si se utiliza una caché 2, entonces, con frecuencia, la información puede
recuperarse fácilmente. La mejora potencial del uso de una caché de dos niveles
depende de las tasas de aciertos en ambas cachés. En general, el uso de un segundo
nivel de caché mejora las prestaciones.

¿Unificada o partida?
Al principio, se usaba una sola caché para almacenar las referencias, tanto a datos
como a instrucciones. Actualmente se ha hecho normal separar la caché en dos: una
dedicada a instrucciones y otra a datos.
Una caché unificada tiene varias ventajas potenciales:
Para un tamaño dado de caché, una unificada tiene una tasa de aciertos mayor
que una partida, ya que nivela automáticamente la carga entre captación de
instrucciones y de datos.

Sólo se necesita diseñar e implementar una caché.
La ventaja del diseño de caché partida es que elimina la competición por la caché
entre el procesador de instrucciones y la unidad de ejecución. Esto es importante en
diseños que cuentan con segmentación de cauce de instrucciones. Esta disputa por la
caché puede degradar las prestaciones, interfiriendo con el uso eficiente del cauce
segmentado de instrucciones. La caché partida supera esta dificultad.
Unidad 5: Paralelismo y mejora de prestaciones.

El paralelismo adopta dos formas generales: paralelismo en el nivel de
instrucciones y paralelismo en el nivel de procesador. En el primero, se aprovecha el
paralelismo dentro de las instrucciones individuales para lograr que la máquina ejecute
más instrucciones por segundo. En el segundo, múltiples CPU trabajan juntas en el
mismo problema.

Procesadores superescalares.

Visión de conjunto.

Una implementación superescalar de la arquitectura de un procesador es aquella
en la que las instrucciones comunes pueden iniciar su ejecución simultáneamente.

El término superescalar hace referencia a una máquina diseñada para mejorar la
velocidad de ejecución de las instrucciones escalares.

Lo esencial del enfoque superescalar es su habilidad para ejecutar instrucciones de
manera independiente en diferentes cauces. El concepto puede llevarse más lejos,
permitiendo que las instrucciones se ejecuten en un orden diferente al del programa.

Superescalar frente a supersegmentado.
Una solución alternativa para alcanzar mayores prestaciones es la llamada
supersegmentación, que aprovecha el hecho de que muchas etapas del cauce realizan
tareas que requieren menos de la mitad de un ciclo de reloj. De este modo, se dobla la
velocidad de reloj interna, lo que permite la realización de dos tareas en un ciclo de reloj
externo.
Las dos realizaciones, supersegmentada y superescalar, ejecutan el mismo número
de instrucciones en el mismo tiempo cuando funcionan de forma ininterrumpida. El
Procesador supersegmentado se queda atrás con respecto al procesador superescalar al
comienzo del programa y en cada destino de un salto.

Limitaciones.
La aproximación superescalar depende de la habilidad para ejecutar múltiples
instrucciones en paralelo. Para maximizar el paralelismo a nivel de instrucciones, se
puede usar una combinación de optimizaciones realizadas por el compilador y de
técnicas hardware.
Las limitaciones fundamentales del paralelismo a las que el sistema tiene que
enfrentarse son:
Dependencia de datos verdadera: una instrucción necesita un dato producido por
una instrucción anterior. Cuando existe dependencia de datos, se retrasa la segunda
instrucción tantos ciclos de reloj como sea necesario para eliminar la dependencia.
Dependencia relativa al procedimiento: las instrucciones que siguen a una
bifurcación tienen una dependencia relativa al procedimiento en esa bifurcación, y no
pueden ejecutarse hasta que ésta lo haga.
Conflictos por los recursos: pugna de dos o más instrucciones por el mismo
recurso al mismo tiempo, como por ejemplo la memoria, caché, buses.
Dependencia de salida: dos instrucciones S1 y S2 presentan dependencia de
salida cuando ambas modifican el mismo recurso y S1 precede a S2.
Antidependencia: una instrucción S2 es antidependiente de otra S1 si S2
modifica un recurso que S1 lee y S1 precede a S2 en el orden de ejecución.
Cuestiones relacionadas con el diseño.

Paralelismo a nivel de instrucciones y paralelismo de la máquina.
Existe paralelismo a nivel de instrucciones cuando las instrucciones de una
secuencia son independientes y, por tanto, pueden ejecutarse en paralelo solapándose.
El paralelismo a nivel de instrucciones depende de la frecuencia de dependencias
de datos verdaderas y dependencias relativas al procedimiento que haya en el código.
Estos factores dependen a su vez de la arquitectura del repertorio de instrucciones y de
la aplicación. El paralelismo a nivel de instrucciones depende también de el tiempo que
transcurre hasta que el resultado de una instrucción está disponible para ser usado como
operando de una instrucción posterior.
El paralelismo de la máquina es una medida de la capacidad del procesador para
sacar partido al paralelismo a nivel de instrucciones. Esto depende del número de
instrucciones que pueden captarse y ejecutarse al mismo tiempo, y de la velocidad y
sofisticación del mecanismo que usa el procesador para localizar instrucciones
independientes.

Políticas de emisión de instrucciones.
Las políticas de emisión de instrucciones de los procesadores superescales son las
siguientes:
Emisión en orden y finalización en orden: consiste en emitir instrucciones en el
orden exacto en que lo haría una ejecución secuencial y escribir los resultados en ese
mismo orden. Para garantizar la finalización en orden, cuando hay una pugna por una
unidad funcional o cuando una unidad funcional necesita más de un ciclo para generar
un resultado, la emisión de instrucciones se detiene temporalmente.
Emisión en orden y finalización desordenada: con la finalización desordenada,
puede haber cualquier número de instrucciones en la etapa de ejecución en un momento
dado, hasta alcanzar el máximo grado de paralelismo de la máquina, ocupando todas las
unidades funcionales. La emisión de instrucciones se para cuando hay una pugna por un
recurso, una dependencia de datos o una relativa al procedimiento. También surge la
dependencia de salida. Necesita una lógica de emisión de instrucciones más compleja
que la finalización en orden y es más difícil ocuparse de las interrupciones.
Emisión desordenada y finalización desordenada: para permitir la emisión
desordenada, es necesario desacoplar las etapas del cauce de decodificación y ejecución.
Esto se hace mediante un buffer llamado ventana de instrucciones. Con esta
organización, cuando un procesador termina de decodificar una instrucción, coloca ésta
en la ventana de instrucciones. Mientras el buffer no se llene, el procesador puede
continuar captando y decodificando nuevas instrucciones. Cuando una unidad funcional
de la etapa de ejecución queda disponible, se puede emitir una instrucción desde la
ventana de instrucciones a la etapa de ejecución. Cualquier instrucción puede emitirse
siempre que necesite la unidad funcional particular que está disponible y ningún
conflicto ni dependencia la bloqueen.

Renombramiento de registros.
La emisión desordenada de instrucciones y la finalización desordenada, puede dar
origen a dependencias de salida y antidependencias, que surgen porque los valores de
los registros no pueden reflejar ya la secuencia de valores dictada por el flujo del
programa.
Las antidependencias y las dependencias de salida son conflictos de
almacenamiento. Varias instrucciones compiten por el uso de los mismos registros. Para
hacer frente a este tipo de conflictos de almacenamiento, se usa una solución
tradicional: el renombramiento de registros. En esta estrategia, el hardware del
procesador asigna dinámicamente los registros. Cuando se ejecuta una instrucción que
tiene un registro como operando destino, se asigna un nuevo registro para ese valor. Las
instrucciones posteriores que accedan a ese valor como operando fuente en ese registro,
tienen que sufrir un procedo de renombramiento: las referencias a registros de esas
instrucciones han de revisarse para referenciar el registro que contiene el valor que se
necesita. De este modo, las referencias a un mismo registro original en diferentes
instrucciones, pueden referirse a distintos registros reales.

Ejecución superescalar.
El proceso de captación de instrucciones, que incluye la predicción de saltos, se
usa para formar un flujo dinámico de instrucciones. Se examinan las dependencias de
este flujo, y el procesador puede eliminar las que sean artificiales.
El procesador envía entonces las instrucciones a una ventana de ejecución. En esta
ventana, las instrucciones ya no forman un flujo secuencial, sino que están estructuradas
de acuerdo a sus dependencias de datos verdaderas. El procesador lleva a cabo la etapa
de ejecución de cada instrucción en un orden determinado por las dependencias de datos
verdaderas y la disponibilidad de los recursos hardware. Por último, las instrucciones se
vuelven a poner conceptualmente en un orden secuencial y sus resultados se registran.

Implementación superescalar.
El hardware que requiere el procesador en la aproximación escalar debe cubrir los
siguientes elementos principales:
Estrategias de captación de instrucciones simultáneas.
Lógica para determinar dependencias verdaderas entre valores de registros, y
mecanismos para comunicar esos valores a donde sean necesarios durante la ejecución.
Mecanismos para iniciar y emitir múltiples instrucciones en paralelo.
Recursos para la ejecución en paralelo de múltiples instrucciones.
Mecanismos para entregar el estado del procesador en un orden correcto.

Procesamiento paralelo.

Tipos de sistemas paralelos.
Una secuencia de instrucciones y una secuencia de datos (SISD): un único
procesador interpreta una única secuencia de instrucciones, para operar con los datos
almacenados en una única memoria. Ejemplo: computadora monoprocesador.
Una secuencia de instrucciones y múltiples secuencias de datos (SIMD): una
única instrucción máquina controla paso a paso la ejecución, simultánea y sincronizada
de un cierto número de elementos de proceso. Cada elemento de proceso tiene una
memoria asociada, de forma que cada instrucción es ejecutada por cada procesador, con
un conjunto de datos diferentes. Ejemplos: procesadores vectoriales y matriciales.
Múltiples secuencias de instrucciones y una secuencia de datos (MISD): se
transmite una secuencia de datos a un conjunto de procesadores, cada uno de los cuales
ejecuta una secuencia de instrucciones diferente. Esta estructura nunca ha sido
implementada.
Múltiples secuencias de instrucciones y múltiples secuencias de datos (MIMD):
un conjunto de procesadores ejecuta simultáneamente secuencias de instrucciones
diferentes con conjuntos de datos diferentes. Pueden ser de memoria compartida
(ejemplos: SMP, sistemas NUMA) o de memoria distribuida (ejemplo: "clusters").

Procesadores vectoriales.

Un procesador vectorial es un diseño de CPU capaz de ejecutar operaciones
matemáticas sobre múltiples datos de forma simultánea. La gran mayoría de las CPU de
hoy en día son escalares o superescalares. Los procesadores vectoriales son muy
comunes en el área de la computación científica, formando la base de la mayor parte de
las supercomputadoras durante los años 80 y 90.

Los procesadores vectoriales proporcionan operaciones de alto nivel que trabajan
sobre vectores. Una máquina vectorial consta de una unidad escalar segmentada y una
unidad vectorial. La unidad vectorial dispone de M registros vectoriales de N elementos
y de unidades funcionales vectoriales (de suma/resta, multiplicación, división, de
carga/almacenamiento) que trabajan sobre los registros vectoriales, y un conjunto de
registros escalares.

Una operación vectorial equivale a un bucle completo que procesaría los N
elementos del registro vectorial.
