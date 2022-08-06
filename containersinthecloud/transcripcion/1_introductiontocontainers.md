# Google Cloud storage options

<p align="justify">
    Ya hemos hablado de <font color='Aliceblue'>Compute Engine</font> , que es la infraestructura de <font color='Aliceblue'>Google Cloud</font> como oferta de servicio, con acceso a servidores, sistemas de archivos y redes, y <font color='Aliceblue'>App Engine</font>, que es la plataforma de <font color='Aliceblue'>Google Cloud</font> como oferta de servicio.  
    En esta sección del curso, exploraremos los contenedores y lo ayudaremos a comprender cómo se usan.
</p>

<p align="justify">
La infraestructura como servicio, o <font color='Aliceblue'>IaaS</font> , le permite compartir recursos informáticos con otros desarrolladores mediante el uso de máquinas virtuales para virtualizar el hardware.
</p>

<p align="justify">
Esto permite que cada desarrollador implemente su propio sistema operativo (SO), acceda al hardware y cree sus aplicaciones en un entorno autónomo con acceso a RAM, sistemas de archivos, interfaces de red, etc.

</p>

Aquí es donde entran los contenedores.

<p align="justify">La idea de un contenedor es brindar la escalabilidad independiente de las cargas de trabajo en  <font color='Aliceblue'>PaaS</font> y una capa de abstracción del sistema operativo y el hardware en <font color='Aliceblue'>IaaS</font> .</p>

<p align="justify">
Un sistema configurable le permite instalar su tiempo de ejecución, servidor web, base de datos o middleware favoritos, configurar los recursos del sistema subyacentes, como espacio en disco, E/S de disco o redes, y compilar a su gusto
<p>

Pero la flexibilidad tiene un costo.

La unidad de cálculo más pequeña es una aplicación con su máquina virtual.

El sistema operativo invitado puede ser grande, incluso de gigabytes, y tardar unos minutos en arrancar.

<p align="justify">
A medida que aumenta la demanda de su aplicación, debe copiar una máquina virtual completa e iniciar el sistema operativo invitado para cada instancia de su aplicación, lo que puede ser lento y costoso
<p>

<p align="justify">

Ahora, con <font color='Aliceblue'>App Engine</font>, obtiene acceso a los servicios de programación, por lo que solo necesita escribir su código en cargas de trabajo independientes que usan estos servicios e incluyen bibliotecas dependientes.
</p>

<p align="justify">
Esto significa que a medida que aumenta la demanda de su aplicación, la plataforma escala su aplicación de manera transparente e independiente según la carga de trabajo y la infraestructura
</p>

Esto escala rápidamente, pero no hay opción para ajustar la arquitectura subyacente para ahorrar costos.

<p align="justify">
Un contenedor es un cuadro invisible alrededor de su código y sus dependencias con acceso limitado a su propia partición del sistema de archivos y el hardware.
</p>

Solo requiere unas pocas llamadas al sistema para crear y comienza tan rápido como un proceso.

<p align="justify">
Todo lo que se necesita en cada host es un kernel de sistema operativo que admita contenedores y un tiempo de ejecución de contenedor.
</p>

En esencia, el sistema operativo se está virtualizando.

Se escala como <font color='Aliceblue'>PaaS</font> pero le brinda casi la misma flexibilidad que <font color='Aliceblue'>IaaS.</font> 

Esto hace que el código sea ultraportátil, y el sistema operativo y el hardware pueden tratarse como una caja negra.

<p align="justify">
De modo que puede pasar del desarrollo a la puesta en escena, a la producción o de su computadora portátil a la nube, sin cambiar ni reconstruir nada.
</p>

Como ejemplo, digamos que desea escalar un servidor web.

<p align="justify">
Con un contenedor, puede hacer esto en segundos e implementar docenas o cientos de ellos, según el tamaño o la carga de trabajo, en un solo host.
</p>

Ese es solo un ejemplo simple de escalar un contenedor que ejecuta toda la aplicación en un solo host.

<p align="justify">
Sin embargo, probablemente querrá crear sus aplicaciones usando muchos contenedores, cada uno realizando su propia función como microservicios.
</p>

<p align="justify">
Si los construye de esta manera y los conecta con conexiones de red, puede modularlos, implementarlos fácilmente y escalarlos de forma independiente en un grupo de hosts.
</p>

<p align="justify">
Los hosts pueden escalar hacia arriba y hacia abajo e iniciar y detener contenedores a medida que cambia la demanda de su aplicación o cuando fallan los hosts.
</p>
