Final Arquitectura de Computadoras - Preguntas
==============================================

Interrupciones
--------------

  * Mecanismo de interrupcion. Fuentes de interrupcion y tratamiento de
    interrupciones multiples.

Buses
-----

  * Que es un Bus, tipos de buses, temporizacion y metodos de arbitraje
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
  * Memoria Caché. Describa el mapeo asociativo por conjuntos. Analice las
    políticas de escritura desde el punto de vista de la coherencia de datos.

Segmentacion de Cauce
---------------------

  * Que es la segmentacion de cauce. Tres motivos de retardo de cauce.
  * Que es la segmentacion de cauce. Describa los metodos y tecnicas utilizadas
    para disminuir o evitar las paradas que afectaran al funcionamiento de los
    cauces.
  * Describa las limitaciones existentes al paralelismo a nivel de
    instrucciones.
  * Cuanto mejora el rendimiento?

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
      El control de la pila se lleva mediante direcciones comunmente denominadas:
      - Stack Pointer: contiene la direccion del tope (cabecera) de la pila
      - Base Pointer: contiene la direccion inicial de la pila
      - Limite: contiene la direccion maxima utilizable del bloque de memoria reservado

  * Metodos de Pasaje de argumentos a las funciones/procedimientos. Que sucede
    cuando tenemos varias subrutinas anidadas?

    Metodos de Pasaje de argumentos:
    - Por Registros: es el metodo mas facil de implementar, los datos se
      guardan en los registros  y se llama a la subrutina, la cual podra
      accederlos directamente. La principal limitacion es la cantidad de
      argumentos q se pueden pasar ya que esta intrinsecamente relacionado a
      la cantidad de registros disponibles.

