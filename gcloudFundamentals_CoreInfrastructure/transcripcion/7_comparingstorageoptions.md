# Comparing storage options

<p align="justify">
Ahora que hemos cubierto las opciones de almacenamiento central de Google Cloud, hagamos una comparación para ayudar a resaltar el servicio más adecuado para una aplicación o flujo de trabajo específico.

Considere usar Cloud Storage si necesita almacenar blobs inmutables de más de 10 megabytes, como imágenes o películas grandes.

Este servicio de almacenamiento proporciona petabytes de capacidad con un tamaño de unidad máximo de 5 terabytes por objeto.

Considere usar Cloud SQL o Cloud Spanner si necesita compatibilidad completa con SQL para un sistema de procesamiento de transacciones en línea.

Cloud SQL proporciona hasta 30 720 gigabytes, según el tipo de máquina, y Cloud Spanner proporciona petabytes.

Cloud SQL es mejor para marcos web y aplicaciones existentes, como el almacenamiento de credenciales de usuario y pedidos de clientes.

Si Cloud SQL no se ajusta a sus requisitos porque necesita escalabilidad horizontal, no solo a través de réplicas de lectura, considere usar Cloud Spanner.

Cloud Spanner es mejor para aplicaciones de bases de datos a gran escala que superan los 2 terabytes, por ejemplo, al planificar casos de uso de comercio financiero y comercio electrónico.

Considere Firestore si necesita escalamiento masivo y previsibilidad junto con resultados de consultas en tiempo real y soporte de consultas fuera de línea.

Este servicio de almacenamiento proporciona terabytes de capacidad con un tamaño máximo de unidad de 1 megabyte por entidad.

Firestore es mejor para almacenar, sincronizar y consultar datos para aplicaciones móviles y web.

Finalmente, considere usar Cloud Bigtable si necesita almacenar una gran cantidad de objetos estructurados.

Cloud Bigtable no admite consultas SQL ni transacciones de varias filas.

Este servicio de almacenamiento proporciona petabytes de capacidad con un tamaño máximo de unidad de 10 megabytes por celda y 100 megabytes por fila.

Bigtable es mejor para datos analíticos con muchos eventos de lectura y escritura, como datos de AdTech, financieros o IoT.

Dependiendo de su aplicación, es posible que pueda usar uno o varios de estos servicios para hacer el trabajo.

Es posible que haya notado que BigQuery no se ha mencionado en esta sección del curso.

Esto se debe a que se encuentra en el límite entre el almacenamiento y el procesamiento de datos, y se trata con mayor profundidad en otros cursos.

La razón habitual para almacenar datos en BigQuery es para que pueda usar sus capacidades de análisis de big data y consultas interactivas, pero no es simplemente un producto de almacenamiento de datos.
</p>