
# Cloud Storage: Storage classes and data transfer
<p  align="justify">
    Hay cuatro clases de almacenamiento principales en Cloud Storage.

El primero es el almacenamiento estándar.

El almacenamiento estándar se considera mejor para los datos de acceso frecuente o calientes.
También es ideal para datos que se almacenan solo por breves períodos de tiempo.

La segunda clase de almacenamiento es Nearline Storage.
Esto es mejor para almacenar datos a los que se accede con poca frecuencia, como leer o modificar datos en promedio una vez al mes o menos.
Los ejemplos pueden incluir copias de seguridad de datos, contenido multimedia de cola larga o archivo de datos.

La tercera clase de almacenamiento es Coldline Storage.

Esta es también una opción de bajo costo para almacenar datos a los que se accede con poca frecuencia.
Sin embargo, en comparación con Nearline Storage, Coldline Storage está diseñado para leer o modificar datos, como máximo, una vez cada 90 días.

La cuarta clase de almacenamiento es Archive Storage.
Esta es la opción de menor costo, utilizada idealmente para archivado de datos, copias de seguridad en línea y recuperación ante desastres.
Es la mejor opción para los datos a los que planea acceder menos de una vez al año, porque tiene costos más altos para el acceso a los datos y las operaciones y una duración mínima de almacenamiento de 365 días.

Aunque cada una de estas cuatro clases tiene diferencias, vale la pena señalar que hay varias características que se aplican a todas estas clases de almacenamiento.
Estos incluyen: almacenamiento ilimitado sin requisito de tamaño mínimo de objeto, accesibilidad y ubicaciones en todo el mundo, baja latencia y alta durabilidad, una experiencia uniforme, que se extiende a la seguridad, herramientas y API, y redundancia geográfica si los datos se almacenan en un región o doble región.

Esto significa colocar servidores físicos en centros de datos geográficamente diversos para protegerlos contra eventos catastróficos y desastres naturales, y equilibrar la carga del tráfico para lograr un rendimiento óptimo.


Cloud Storage no tiene una tarifa mínima porque solo paga por lo que usa y no es necesario aprovisionar previamente la capacidad.


Y desde una perspectiva de seguridad, Cloud Storage siempre cifra los datos en el lado del servidor, antes de que se escriban en el disco, sin cargo adicional.
 
Los datos que viajan entre el dispositivo de un cliente y Google se cifran de forma predeterminada mediante HTTPS/TLS (Seguridad de la capa de transporte).
 
Independientemente de la clase de almacenamiento que elija, hay varias formas de llevar datos a Cloud Storage.

Muchos clientes simplemente realizan su propia transferencia en línea usando gsutil, que es el comando de Cloud Storage del SDK de Cloud.

Los datos también se pueden mover usando una opción de arrastrar y soltar en Cloud Console, si se accede a través del navegador web Google Chrome.

Pero, ¿qué sucede si tiene que cargar terabytes o incluso petabytes de datos?

El servicio de transferencia de almacenamiento le permite importar grandes cantidades de datos en línea a Cloud Storage de forma rápida y rentable.

El servicio de transferencia de almacenamiento le permite programar y administrar transferencias por lotes a Cloud Storage desde otro proveedor de nube, desde una región diferente de Cloud Storage o desde un extremo HTTP(S).

Y luego está Transfer Appliance, que es un servidor de almacenamiento de alta capacidad que se puede montar en rack y alquilar de Google Cloud.

Lo conecta a su red, lo carga con datos y luego lo envía a una instalación de carga donde los datos se cargan en Cloud Storage.

Puede transferir hasta un petabyte de datos en un solo dispositivo.

La estrecha integración de Cloud Storage con otros productos y servicios de Google Cloud significa que hay muchas formas adicionales de transferir datos al servicio.

Por ejemplo, puede importar y exportar tablas desde y hacia BigQuery y Cloud SQL.

También puede acceder a los registros de App Engine, las copias de seguridad de Firestore y los objetos utilizados por las aplicaciones de App Engine, como las imágenes.

Cloud Storage también puede almacenar scripts de inicio de instancias, imágenes de Compute Engine y objetos que usan las aplicaciones de Compute Engine.
</p>