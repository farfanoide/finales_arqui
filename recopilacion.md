Final Arquitectura de Computadoras - Preguntas
==============================================

Interrupciones
--------------

1. Explique el mecanismo de interrupción.

2. Cual es la funcion de un controlador de interrupciones.

3. Describa las distintas fuentes de interrupción que conozca.

    - Programa: Generada por alguna condicion q se produce como resultado de la
      ejecucion de una instruccion (overflow, div / cero, iinstruccion fuera de
      espacio de memoria permitido).
    - Temporizacion: Generadas por un temporizador interno al procesador.
    - E/S: Generada por un controlador de E/S, para indicar la finalizacion sin
      problemas de una operacion o para avisar de ciertas condiciones de error.
    - Fallo de hardware: Fallo tal como una falta de potencia o un error de
      paridad en memoria.

4. Explique caracteristicas y tratamiento de interrupciónes multiples.

Buses
-----

1. Que es un Bus, tipos de buses, temporizacion y metodos de arbitraje

      > Un bus es un camino de comunicacion (hardware) entre dos o mas
      dispositivos.

      Tipos de buses:
        * Dedicado: Una linea de bus dedicada esta permanentemente asignada a
          una funcion o a un subconjunto fisico de componentes de computador.
        * Multiplexado: en un bus multiplexado se transmiten tanto los datos
          como las direcciones por la misma via, impidiendo que las
          transmisiones puedan hacerse en paralelo. Tambien implica el uso de
          una señal extra

      Metodos de arbitraje:

      * Centralizado: Un unico dispositivo de hardware (arbitro o controlador
        del bus) es responsable de asignar tiempos en el bus. Dicho
        dispositivo puede estar integrado en el procesador o ser un modulo
        separado.
      * Distribuido: Cada dispositivo cuenta con la logica necesaria para
        controlar el acceso al bus. Los modulos actuan conjuntamente para
        compartir el bus.

      En ambos metodos el proposito es designar un dispositivo (procesador o
      odulo E/S) como maestro, el cual podra iniciar una transferencia de datos
      on otro dispositivo (esclavo).

      Temporizacion: El termino temporizacion hace referencia a la forma en la
      que se coordinan los eventos en el bus. Los buses utilizan temporizacion
      sincrona o asincrona.

      * Sincrona: la presencia de un evento esta dada por un reloj.
      * Asincrona: la presencia de un evento en el bus es consecuencia y
        depende (si o si) de que se produzca un evento previo.

2. Jerarquia de buses.
3. Mencione diferencias entres bus PCI y bus SCSI.

E/S - DMA
---------

* Como es la estructura de un modulo de E/S.

  ![modulo entrada salida](img/modulo_e_s.png)

  Un modulo de E/S cuenta con dos interfaces, una interna y otra externa
  Contiene la logica necesaria para comunicar al procesador con otros
  dispositivos de forma simplificada. Dependiendo del nivel de abstraccion que
  le presente el modulo de E/S al procesador puede ser considerado un canal o un
  procesador de E/S (alto nivel de abstraccion) o un controlador de E/S (posee
  menos logica por lo cual presenta un menor nivel de abstraccion). Un modulo
  de E/S cuenta con una interfaz para comunicarse con el procesador en la cual
  recibira por un bus de datos el dispositivo al cual quiere comunicarse y la
  cantidad de palabras que espera recibir. dicha informacion es guardada en
  registros de datos y control respectivamente, los cuales funcionan como buffer
  en caso q el modulo E/S se encuentre atendiendo un requerimiento previo.
  Por medio de un bus de control recibira seniales acerca de la operacion
  requerida (lectura/escritura). Por ultimo, esta interfaz cuenta con un bus de
  direcciones por donde se recibira la direccion a utilizar para la transaccion.

* Describa las posibles tecnicas que pueden utilizarse para realizar las
operaciones de E/S

  Tanto con E/S programada como con interrupciones el procesador es responsable
  de extraer los datos de la memoria ppal en una salida y de almacenar los datos
  en la memoria ppal en una entrada.

  * E/S Programada: el procesador ejecuta un programa q controla directamente
    la operacion de E/S, inlcuyendo la comprobacion de estado del dispositivo,
    el envio de una orden de lectura o escritura, asi como tambien la
    transferencia del dato. cuando el procesador envia una orden al modulo de
    E/S debe esperar hasta q la operacion concluya (pierde este tiempo).

  * E/S Mediante interrupciones: el procesador proporciona la orden de E/S, continua
    ejecutando otras instucciones y es interrumppido por el modulo de E/S
    cuando este ha terminado su trabajo.

  * E/S via DMA: el modulo E/S y la memoria principal intercambian datos
    directamente, sin la intervencion del procesador.

* Caracteristicas funcionales de DMA.

Cache
-----

1. Describa que se debe tener en cuenta para diseñar una cache(TODO).

El objetivo de la memoria cache es lograr que la velocidad de la memoria sea lo
mas rapida posible, consiguiendo al mismo tiempo un tamaño grande al precio de
memorias semiconductoras menos costosas.

Propiedades a cumplir
* Inclusión: Los datos almacenados en un nivel han de estar almacenados en los
  niveles inferiores a él
* Coherencia: Las copias de la misma información en los distintos niveles deben
  contener los mismos valores.

Tamaño de Cache: si bien es tentador incrementar el tamaño de la cache para
mejorar las prestaciones, nos vemos restringidos no solo por los elevados
costos sino tambien por otras limitaciones como por ejemplo el hecho que las
memorias caches mas grandes tienden a ser mas lentas que otras mas pequeñas
manufacturadas con los mismos materiales e incluso ubicadas en los mismos
lugares. esto se debe a que al incrementar el tamaño tambien incrementa el
circuiterio necesario para comunicarlas.
Es imposible predecir un tamaño **optimo** ya que las prestaciones de una
memoria cache son muy sensibles a las tareas desempeñadas por la misma.

Funciones de correspondencia:

  * Directa: Consiste en hacer corresponder cada bloque de memoria principal a
      solo una linea de cache. es la tecnica mas sencilla. se implementa
      facilmente utilizando la direccion. desde el punto de vista del acceso a
      cache, cada direccion de memoria ppal puede verse como dividida en tres
      campos: etiqueta, linea, palabra. Su principal desventaja es que hay una
      posicion concreta de cache para cada bloque dado.(dar ejemplo de
      thrashing)

  * Asociativa: Supera las desventajas de la directa permitiendo que cada
      bloque de memoria ppal pueda cargarse en cualquier linea de la cache. La
      direccion de memoria se interpreta tan solo como una etiqueta y un campo
      de palabra. el campo de etiqueta identifica univocamente un bloque de
      memoria ppal y para determinar si se encuentra en la cache se examina
      simultaneamente todas las etiquetas de lineas. esto marca su ppal
      desventaja ya que para lograr dicha busqueda en paralelo se precisa
      circuiteria de mayor cantidad y en mayor cantidad.

  * Asociativa por conjuntos: Es un hibrido entra la directa y la asociativa,
      es decir, recoge las aspectos positivos de ellas sin presentar sus
      desventajas. en este caso la direccion nuevamente se divide en tres
      campos, los cuales referencian etiqueta, conjunto, palabra. con este
      metodo la etiqueta es mucho mas corta y solo se compara con las etiquetas
      del conjunto al que pertenece.

  Algoritmos de sustitucion:

  * FIFO: El primero en entrar sera el primero en salir.
  * LRU (Least Recently Used): Se sustituye el bloque que se ha mantenido en la
      cache por mas tiempo sin haber sido referenciado.
  * LFU (Least Frequently Used): Se sustituye aquel bloque del conjunto que ha
      experimentado menos referencias.
  * RANDOM: Se toma una linea al azar. Sorprendentemente presenta prestaciones
      ligereamente menores a las de los anteriores algoritmos.

  Politicas de Escritura: antes de que pueda ser reemplazado un bloque q este
  en una linea de cache es necesario comprobar si se ha alterado en cache pero
  no en memoria ppal. si no lo ha sido, puede escribirse sobre la cache. si ha
  sido modificado esto significa que se ha realizado al menos una operacion de
  escritura sobre una palabra, lo cual implica que dicha informacion debe ser
  actualizada en memoria ppal.
    * Inmediata: la operacion de escritura se hace tanto en cache como en
      memoria ppal.
      Desventajas: genera trafico sustancial a memoria.
    * Post Escritura: las actualizaciones se hacen solo en cache. cuando tiene
      lugar una actualizacion se activa un bit 'actualizar' asociado a la
      linea. cuando el bloque es sustituido, se comprueba el estado de dicho
      bit para definir si debe ser actualizado en memoria ppal.
      Desventajas: el bloque de memoria ppal se mantiene desactualizado,
      obligando a modulos de E/S a acceder a memoria a traves de la cache, lo
      cual complica la circuiteria y genera potencialmente un cuello de
      botella.

Tamaño de Linea:



* Describa algoritmos de ubicacion y politica de escritura en cache.
* Funciones de correspondencia entre memoria y memoria cache. Politicas de
  escritura desde el punto de vista de la coherencia de datos.
* Describa las tecnicas de reemplazo de bloque, correspondencia y politicas
* Analice ventajas y desventajas de tener varios niveles de cache.
  de escritura en memoria cache.

Segmentacion de Cauce
---------------------

1. Que es la segmentacion de cauce.

  > La segmentación de cauce (pipelining) es una forma particularmente
  > efectiva de organizar el hardware de la CPU para realizar más de una
  > operación al mismo tiempo. Consiste en descomponer el proceso de
  > ejecución de las instrucciones en fases o etapas que permitan una
  > ejecución simultánea. Explota el paralelismo entre las instrucciones de
  > un flujo secuencial.

  Motivos de retardo de cauce.

  * Estructurales: Provocados por conflictos por los recursos
    ej: Dos o mas instrucciones necesitan utilizar el mismo recurso
    hardware en el mismo ciclo. (IF y MA con memoria unificada)

  * Por dependencia de datos: Ocurren cuando dos instrucciones se comunican
    por medio de un dato (ej.: una lo produce y la otra lo usa) ej:
    Condición en la que los operandos fuente o destino de una instrucción
    no están disponibles en el momento en que se necesitan en una etapa
    determinada del cauce.

    * Lectura después de Escritura (RAW, dependencia verdadera): una
    instrucción genera un dato que lee otra posterior
    * Escritura después de Escritura (WAW, dependencia en salida): una
    instrucción escribe un dato después que otra posterior sólo se da si se
    deja que las instrucciones se adelanten unas a otras
    * Escritura después de Lectura (WAR, antidependencia): una instrucción
    modifica un valor antes de que otra anterior que lo tiene que leer, lo
    lea. ( no se puede dar en nuestro cauce simple )

  * Por dependencia de control: Ocurren cuando la ejecución de una
    instrucción depende de cómo se ejecute otra (ej.: un salto y los 2
    posibles caminos)

2. Que ventajas proporciona su implementacion.

3. Describa los metodos y tecnicas utilizadas para disminuir o evitar las
   paradas que afectaran al funcionamiento de los cauces.

  Soluciones a riesgos estructurales:
  Duplicación de recursos hardware
  - Sumadores o restadores además de la ALU
  - Separación en memorias de instrucciones y datos
  - Turnar el acceso al banco de registros
  - Escrituras en la 1o mitad de los ciclos de reloj • Lecturas en la 2o mitad de los ciclos de reloj
  Soluciones a riesgos de datos:
  Para riesgos RAW: se debe determinar cómo y cuando aparecen esos riesgos

    * por hardware: adelantamiento de operandos. consiste en pasar directamente
      el resultado obtenido con una instrucción a las instrucciones que lo
      necesitan como operando.
      * por software: uso de instrucciones NOP o reordenamiento de instrucciones.
      es ejecutada por el compilador. evita los riesgos reordenando las
      instrucciones del código sin afectar los resultados

    - Soluciones a riesgos de Control:
    - para saltos incondicionales la unica solucion es resolver lo mas
        rapidamente posible la direccion de la proxima instruccion a ejecutar.
    - para saltos condicionales es mas complejo ya que se depende del resultado
        de la instruccion anterior para determinar el orden de ejecucion.

    Soluciones:
      - Flujos Multiples
      - Precaptar el destino del salto
      - Buffer de bucles
      - Prediccion de saltos
      - Salto retardado

    - Precaptar el destino del salto: (hardware) una solucion sencilla es adelantar la
        resolucion de la direccion de salto a la misma etapa de decode,
        donde ya se puede definir q una operacion es de salto. con este
        metodo se reduce la cantidad de paradas del cauce a solamente una.

    - Flujos Multiples: (hardware)
        Varios cauces (uno por cada opción de salto). •
        Precaptan cada salto en diferentes cauces.
        • Se debe utilizar el cauce correcto.
        • Desventajas:
        • Provoca retardos en el acceso al bus y a los registros.
        • Si hay múltiples saltos, se necesita un mayor número de cauces.

    - Buffer de bucles: (hardware)
        un buffer de bucles es una memoria pequeña de gran velocidad,
        gestinoada por la etapa de captacion de instruccion. contiene,
        secuencialmente las n instrucciones captadas mas recientemente. si
        se va a producir un salto, el hardware comprueba en primer lugar si
        el destino de salto esta en el buffer.

    - Salto retardado (software): se pueden mejorar las prestaciones de un
        cauce reordenando automaticamente las instrucciones de un programa
        de forma que las instrucciones de salto tengan lugar despues de lo
        realmente deseado.

    - Prediccion de saltos:
        soluciones estaticas:
        - predecir q nunca se salta: supone q el salto no se producira y continuara captando instrucciones secuencialmente.
        - predecir q siempre se salta: supone q el salto se producira y siempre captara la instruccion destino del salto.
        - predecir segun el codigo de operacion: el procesador asume que el salto se producira para ciertos codigos de operacion de bifurcacion y no para otros.
        soluciones dinamicas:
        buscan mejorar la exactitud de la prediccion, registrando la
        historia de las instrucciones de bifurcadcion condicional en un
        programa. A cada instruccion se le asocian uno o mas bits q
        reflejen su historia reciente. dichas instrucciones pueden ser
        guardadas en la memoria cache o alguna memoria rapida dedicada.
        - conmutador saltar/no saltar: el procesador referencia los bits asociados a la instruccion para tomar una desicion al momento de captar la proxima instruccion.
        - Tabla de historia de salto: similar a la tecnica previa pero agrega tmb a la tabla la direccion de la proxima instruccion o incluso puede guardar directamente la instruccion a ejecutar.


* Cuanto mejora el rendimiento?

  > El máximo rendimiento  teorico es completar una instrucción con cada
  > ciclo de reloj.
  > Incrementa la productividad (throughput), pero no reduce el tiempo de
  > ejecución de la instrucción



Superescalares/SMP
------------------

  * Describa las caracteristicas que diferencian los SMTP respecto a los
    clusters
  * Caracteristicas de los clusters.
  * ¿Qué características posee un procesador supersegmentado frente a un
    superescalar?
  * Que caracteristicas posee un multiprocesador simetrico (SMP)?

Repertorio de instrucciones
---------------------------

1. Describa las caracteristicas que diferencian los procesadores RISC de los
   CISC.

Subrutinas
----------

1. Metodos de Pasaje de argumentos a las funciones/procedimientos. Que sucede
   cuando tenemos varias subrutinas anidadas?
2. Describa el funcionamiento y uso de la pila.

  > Es un conjunto ordenado de elementos en el que solo uno de ellos es
  > accesible en un instante dado (Estructura LIFO), las operaciones posibles
  > son:  PUSH, POP
  > El control de la pila se lleva mediante direcciones comunmente denominadas:

    * Stack Pointer: contiene la direccion del tope (cabecera) de la pila
    * Base Pointer: contiene la direccion inicial de la pila
    * Limite: contiene la direccion maxima utilizable del bloque de memoria
        reservado

2. Metodos de Pasaje de argumentos a las funciones/procedimientos. Que sucede
   cuando tenemos varias subrutinas anidadas?

  Metodos de Pasaje de argumentos:
  * Por Registros: es el metodo mas facil de implementar, los datos se
  guardan en los registros  y se llama a la subrutina, la cual podra
  accederlos directamente. La principal limitacion es la cantidad de
  argumentos q se pueden pasar ya que esta intrinsecamente relacionado a
  la cantidad de registros disponibles.

