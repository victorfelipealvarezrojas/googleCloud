# Google Cloud storage options

<p align="justify">
    Cada aplicación necesita almacenar datos, como medios para transmitir o tal vez incluso datos de sensores de dispositivos, y diferentes aplicaciones y cargas de trabajo requieren diferentes soluciones de bases de datos de almacenamiento.
</p>

<p align="justify">
Google Cloud tiene opciones de almacenamiento para datos estructurados, no estructurados, transaccionales y relacionales.
</p>

<p align="justify">
En esta sección del curso, explore bien los cinco productos de almacenamiento principales de Google Clouds: Cloud Storage, Cloud SQL, Cloud Spanner, Firestore y Cloud Bigtable.
</p>


<p align="justify">
Dependiendo de su aplicación, puede usar uno o varios de estos servicios para hacer el trabajo.
</p>

<p align="justify">
Comencemos con Cloud Storage, que es un servicio que ofrece a los desarrolladores y organizaciones de TI almacenamiento de objetos duradero y de alta disponibilidad.

Pero, ¿qué es el almacenamiento de objetos?

El almacenamiento de objetos es una arquitectura de almacenamiento de datos informáticos que gestiona los datos como objetos y no como una jerarquía de archivos y carpetas (almacenamiento de archivos), o como fragmentos de un disco (almacenamiento en bloque).

Estos objetos se almacenan en un formato empaquetado que contiene la forma binaria de los datos reales en sí, así como los metadatos asociados relevantes (como la fecha de creación, el autor, el tipo de recurso y los permisos) y un identificador único global.

Estas claves únicas tienen la forma de URL, lo que significa que el almacenamiento de objetos interactúa bien con las tecnologías web.


Los datos comúnmente almacenados como objetos incluyen videos, imágenes y grabaciones de audio.


Cloud Storage es el producto de almacenamiento de objetos de Google.


Permite a los clientes almacenar cualquier cantidad de datos y recuperarlos con la frecuencia necesaria.


Es un servicio escalable totalmente administrado que tiene una amplia variedad de usos.


Algunos ejemplos incluyen servir contenido de sitios web, almacenar datos para archivado y recuperación ante desastres y distribuir objetos de datos de gran tamaño a los usuarios finales a través de la descarga directa.


El uso principal de Cloud Storage es cuando se necesita almacenamiento binario de objetos grandes (también conocido como BLOB) para contenido en línea, como videos y fotos, para copias de seguridad y datos archivados, y para el almacenamiento de resultados intermedios en flujos de trabajo de procesamiento.


Los archivos de Cloud Storage se organizan en depósitos.


Un depósito necesita un nombre global único y una ubicación geográfica específica para almacenarlo, y una ubicación ideal para un depósito es donde se minimiza la latencia.


Por ejemplo, si la mayoría de sus usuarios se encuentran en Europa, probablemente desee elegir una ubicación europea, ya sea una región específica de Google Cloud en Europa o la región múltiple de la UE.


Los objetos de almacenamiento que ofrece Cloud Storage son inmutables, lo que significa que no los edita, sino que se crea una nueva versión con cada cambio realizado.


pero en su lugar se crea una nueva versión con cada cambio realizado.


Los administradores tienen la opción de permitir que cada nueva versión sobrescriba por completo la anterior o de realizar un seguimiento de cada cambio realizado en un objeto en particular al habilitar el control de versiones dentro de un depósito.


Si elige usar el control de versiones, Cloud Storage mantendrá un historial detallado de las modificaciones (es decir, sobrescrituras o eliminaciones) de todos los objetos contenidos en ese depósito.


Si no activa el control de versiones de objetos, de forma predeterminada, las nuevas versiones siempre sobrescribirán las versiones anteriores.


Con el control de versiones de objetos habilitado, puede enumerar las versiones archivadas de un objeto, restaurar un objeto a un estado anterior o eliminar permanentemente una versión de un objeto, según sea necesario.


En muchos casos, la información de identificación personal puede estar contenida en objetos de datos, por lo que controlar el acceso a los datos almacenados es esencial para garantizar que se mantenga la seguridad y la privacidad.


Usando roles de IAM y, cuando sea necesario, listas de control de acceso (ACL), las organizaciones pueden cumplir con las mejores prácticas de seguridad, que requieren que cada usuario tenga acceso y permisos solo a los recursos que necesita para hacer su trabajo, y nada más.


Hay un par de opciones para controlar el acceso de los usuarios a objetos y depósitos.


Para la mayoría de los propósitos, IAM es suficiente.


Los roles se heredan del proyecto al depósito y al objeto.


Si necesita un control más preciso, puede crear listas de control de acceso.


Cada lista de control de acceso consta de dos piezas de información.


El primero es un ámbito, que define quién puede acceder y realizar una acción.


Puede ser un usuario específico o un grupo de usuarios.


El segundo es un permiso, que define qué acciones se pueden realizar, como leer o escribir.


Debido a que almacenar y recuperar grandes cantidades de datos de objetos puede volverse costoso rápidamente, Cloud Storage también ofrece políticas de administración del ciclo de vida.


Por ejemplo, podría indicarle a Cloud Storage que elimine objetos que tengan más de 365 días; o para eliminar objetos creados antes del 1 de enero de 2013; o para mantener solo las 3 versiones más recientes de cada objeto en un depósito que tiene habilitado el control de versiones.


Tener este control asegura que no está pagando más de lo que realmente necesita.
</p>