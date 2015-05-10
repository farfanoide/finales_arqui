Final Arquitectura de Computadoras - Preguntas
==============================================

Interrupciones
--------------

  * Explique el mecanismo de interrupción.

  * Cual es la funcion de un controlador de interrupciones.
  * Describa las distintas fuentes de interrupción que conozca.
    - Programa: Generada por alguna condicion q se produce como resultado de la
        ejecucion de una instruccion (overflow, div / cero, iinstruccion fuera
        de espacio de memoria permitido).
    - Temporizacion: Generadas por un temporizador interno al procesador.
    - E/S: Generada por un controlador de e/s, para indicar la finalizacion sin
        problemas de una operacion o para avisar de ciertas condiciones de
        error.
    - Fallo de hardware: Fallo tal como una falta de potencia o un error de
        paridad en memoria.

  * Explique caracteristicas y tratamiento de interrupciónes multiples.

Buses
-----

  * Que es un Bus, tipos de buses, temporizacion y metodos de arbitraje
    - Un bus es un camino de comunicacion (hardware) entre dos o mas
        dispositivos.
    - Tipos de buses:
        - Dedicado: Una linea de bus dedicada esta permanentemente asignada a
            una funcion o a un subconjunto fisico de componentes de computador.
        - Multiplexado: en un bus multiplexado se transmiten tanto los datos
            como las direcciones por la misma via, impidiendo que las
            transmisiones puedan hacerse en paralelo. Tambien implica el uso de
            una señal extra
    - Metodos de arbitraje:
      - Centralizado: Un unico dispositivo de hardware (arbitro o controlador
          del bus) es responsable de asignar tiempos en el bus. Dicho
          dispositivo puede estar integrado en el procesador o ser un modulo
          separado.
      - Distribuido: Cada dispositivo cuenta con la logica necesaria para
          controlar el acceso al bus. Los modulos actuan conjuntamente para
          compartir el bus.

      - En ambos metodos el proposito es designar un dispositivo (procesador o
          modulo e/s) como maestro, el cual podra iniciar una transferencia de
          datos con otro dispositivo (esclavo).

      - Temporizacion:
        El termino temporizacion hace referencia a la forma en la que se
        coordinan los eventos en el bus. Los buses utilizan temporizacion
        sincrona o asincrona.
        - Sincrona: la presencia de un evento esta dada por un reloj
        - Asincrona: la presencia de un evento en el bus es consecuencia y
            depende (si o si) de que se produzca un evento previo.

  * Mencione diferencias entres bus PCI y bus SCSI.

E/S - DMA
---------

  * Como es la estructura de un modulo de E/S.Describa las posibles tecnicas
    que pueden utilizarse para realizar las operaciones de E/S
  * Caracteristicas funcionales de DMA.

Cache
-----

  * Describa algoritmos de ubicacion y politica de escritura en cache.
  * Funciones de correspondencia entre memoria y memoria cache. Politicas de
    escritura desde el punto de vista de la coherencia de datos.
  * Describa las tecnicas de reemplazo de bloque, correspondencia y politicas
    de escritura en memoria cache.
  * Describa que se debe tener en cuenta para diseñar una cache(TODO).
  * Analice ventajas y desventajas de tener varios niveles de cache.

Segmentacion de Cauce
---------------------

  * Que es la segmentacion de cauce. Tres motivos de retardo de cauce.
  * Que ventajas proporciona su implementacion.
  * Describa los metodos y tecnicas utilizadas para disminuir o evitar las
    paradas que afectaran al funcionamiento de los cauces.
  * Describa las limitaciones existentes al paralelismo a nivel de
    instrucciones.
  * Cuanto mejora el rendimiento?
  * Describa tres (3) diferentes causas o motivos que pueden retardar un cauce
    de instrucciones segmentado

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

  * Describa las caracteristicas que diferencian los procesadores RISC de los
    CISC.

Subrutinas
----------

  * Metodos de Pasaje de argumentos a las funciones/procedimientos. Que sucede
    cuando tenemos varias subrutinas anidadas?
  * Describa el funcionamiento y uso de la pila.



  * Describa el funcionamiento y uso de la pila.
      Es un conjunto ordenado de elementos en el que solo uno de ellos es
      accesible en un instante dado (Estructura LIFO), las operaciones posibles
      son:  PUSH, POP
      El control de la pila se lleva mediante direcciones comunmente
      denominadas:
    - Stack Pointer: contiene la direccion del tope (cabecera) de la pila
    - Base Pointer: contiene la direccion inicial de la pila
    - Limite: contiene la direccion maxima utilizable del bloque de memoria
        reservado

  * Metodos de Pasaje de argumentos a las funciones/procedimientos. Que sucede
    cuando tenemos varias subrutinas anidadas?

    Metodos de Pasaje de argumentos:
    - Por Registros: es el metodo mas facil de implementar, los datos se
      guardan en los registros  y se llama a la subrutina, la cual podra
      accederlos directamente. La principal limitacion es la cantidad de
      argumentos q se pueden pasar ya que esta intrinsecamente relacionado a
      la cantidad de registros disponibles.

