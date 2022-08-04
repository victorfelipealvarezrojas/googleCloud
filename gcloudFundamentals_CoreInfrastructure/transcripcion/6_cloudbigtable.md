# Cloud Bigtable

<p  align="justify">

La última de las opciones de almacenamiento central de Google Clouds que vamos a explorar es Cloud Bigtable.

Es la misma base de datos que impulsa muchos servicios principales de Google, incluidos Search, Analytics, Maps y Gmail.

Bigtable está diseñado para manejar cargas de trabajo masivas con baja latencia constante y alto rendimiento, por lo que es una excelente opción para aplicaciones operativas y analíticas, incluido el Internet de las cosas, el análisis de usuarios y el análisis de datos financieros.

Al decidir qué opción de almacenamiento es la mejor, los clientes suelen elegir Bigtable si: Están trabajando con más de 1 TB de datos semiestructurados o estructurados.

Los datos son rápidos con un alto rendimiento o cambian rápidamente.

Están trabajando con datos NoSQL.

Esto generalmente significa transacciones en las que no se requiere una semántica relacional fuerte.

Los datos son una serie temporal o tienen un orden semántico natural.

Están trabajando con big data, ejecutando procesamiento por lotes asíncrono o síncrono en tiempo real en los datos.

O están ejecutando algoritmos de aprendizaje automático en los datos.

Cloud Bigtable puede interactuar con otros servicios de Google Cloud y clientes de terceros.

Con las API, los datos se pueden leer y escribir en Cloud Bigtable a través de una capa de servicio de datos como máquinas virtuales administradas, el servidor HBase REST o un servidor Java que usa el cliente HBase.

Por lo general, esto se usa para entregar datos a aplicaciones, tableros y servicios de datos.

Los datos también se pueden transmitir a través de una variedad de marcos de procesamiento de flujo populares como Dataflow Streaming, Spark Streaming y Storm.

Y si la transmisión no es una opción, los datos también se pueden leer y escribir en Cloud Bigtable a través de procesos por lotes como Hadoop MapReduce, Dataflow o Spark.

A menudo, los datos resumidos o recién calculados se vuelven a escribir en Cloud Bigtable o en una base de datos descendente.

</p>