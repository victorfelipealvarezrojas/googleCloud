# Kubernetes

<p align="justify">
Un producto que ayuda a administrar y escalar aplicaciones en contenedores es Kubernetes. Por lo tanto, para ahorrar tiempo y esfuerzo al escalar aplicaciones y cargas de trabajo, Kubernetes se puede arrancar con <font color='Aliceblue'>Google Kubernetes Engine o GKE</font>. Entonces, ¿qué es Kubernetes? Kubernetes es una plataforma de código abierto para administrar cargas de trabajo y servicios en contenedores. Facilita la orquestación de muchos contenedores en muchos hosts, escalarlos como microservicios, e implemente implementaciones y reversiones fácilmente. En el nivel más alto, Kubernetes es un conjunto de API que puede usar para implementar contenedores en un conjunto de nodos denominado <font color='Aliceblue'>Cluster</font>. El sistema se divide en un conjunto de componentes principales que se ejecutan como plano de control y un conjunto de nodos que ejecutan contenedores.
</p>

<p align="justify">
En Kubernetes, un nodo representa una instancia informática, como una máquina. Tenga en cuenta que esto es diferente a un nodo en Google Cloud, que es una máquina virtual que se ejecuta en Compute Engine. Puede describir un conjunto de aplicaciones y cómo deberían interactuar entre sí, y Kubernetes determina cómo hacer que eso suceda.
</p>

<p align="justify">
La implementación de contenedores en nodos mediante el uso de un contenedor alrededor de uno o más contenedores es lo que define un Pod. Un Pod es la unidad más pequeña en Kubernetes que crea o implementa. Representa un proceso en ejecución en su clúster como un componente de su aplicación o como una aplicación completa.

</p>

<p align="justify">
Por lo general, solo tiene un contenedor por Pod, pero si tiene varios contenedores con una dependencia fuerte, puede empaquetarlos en un solo Pod y compartir recursos de red y almacenamiento entre ellos. El Pod proporciona una IP de red única y un conjunto de puertos para sus contenedores y configurable opciones que rigen cómo deben ejecutarse sus contenedores. Una forma de ejecutar un contenedor en un pod en Kubernetes es usar el comando kubectl run, que inicia una implementación con un contenedor ejecutándose dentro de un pod. Una implementación representa un grupo de réplicas del mismo pod y mantiene sus pods en funcionamiento incluso cuando fallan los nodos en los que se ejecutan. Una implementación podría representar un componente de una aplicación o incluso una aplicación completa. Para ver una lista de los pods en ejecución en su proyecto, ejecute el comando: $ kubectl get pods Kubernetes crea un servicio con una dirección IP fija para sus pods y un controlador dice "Necesito adjuntar un balanceador de carga externo con una dirección IP pública a ese servicio para que otros fuera del clúster puedan acceder a él". En GKE, el balanceador de carga se crea como un balanceador de carga de red. Cualquier cliente que llegue a esa dirección IP será enrutado a un Pod detrás del Servicio.
</p>

<p align="justify">
Un Servicio es una abstracción que define un conjunto lógico de Pods y una política para acceder a ellos. A medida que las implementaciones crean y destruyen pods, a los pods se les asignarán sus propias direcciones IP, pero esas direcciones no se mantienen estables con el tiempo. Un grupo de servicios es un conjunto de pods y proporciona un punto final estable (o dirección IP fija) para a ellos. Por ejemplo, si crea dos conjuntos de pods llamados frontend y backend y los coloca detrás de sus propios servicios, los pods de backend pueden cambiar, pero los pods de frontend no son conscientes de esto. Simplemente se refieren al servicio backend. Para escalar una implementación, ejecute el comando kubectl scale.

</p>
En este ejemplo, se crean tres pods en su implementación, se colocan detrás del servicio y comparten una dirección IP fija. También puede usar el ajuste de escala automático con otros tipos de parámetros; por ejemplo, puede especificar que la cantidad de pods aumente cuando la utilización de la CPU alcance un límite determinado.
<p align="justify">

</p>
Hasta ahora, hemos visto cómo ejecutar comandos imperativos como exponer y escalar. Esto funciona bien para aprender y probar Kubernetes paso a paso. Pero la verdadera fuerza de Kubernetes surge cuando trabaja de forma declarativa. En lugar de emitir comandos, proporciona un archivo de configuración que le dice a Kubernetes cómo desea que se vea su estado deseado, y Kubernetes determina cómo hacerlo.
<p align="justify">

</p>
Esto se logra mediante el uso de un archivo de configuración de implementación. Para obtener este archivo, puede ejecutar un comando kubectl get pods y obtendrá un archivo de configuración de implementación similar a este. Puede verificar su Implementación para asegurarse de que se está ejecutando la cantidad adecuada de réplicas mediante kubectl get deployments o kubectl describe deployments.

<p align="justify">
Para ejecutar cinco réplicas en lugar de tres, todo lo que debe hacer es actualizar el archivo de configuración de implementación y ejecutar el comando kubectl apply para usar el archivo de configuración actualizado. Todavía puede llegar a su punto final como antes usando kubectl get services para obtener la IP externa del Servicio y llegar a la dirección IP pública de un cliente.
</p>

<p align="justify">
La última pregunta es, ¿qué sucede cuando desea actualizar una nueva versión de su aplicación? Bueno, desea actualizar su contenedor para obtener un nuevo código frente a los usuarios, pero implementar todos esos cambios a la vez sería arriesgado. Entonces, en este caso, usaría la implementación de kubectl o cambiaría su archivo de configuración de implementación

y luego aplique el cambio usando kubectl apply. Luego se crearán nuevos Pods de acuerdo con su nueva estrategia de actualización. Aquí hay una configuración de ejemplo que creará nuevas versiones.
</p>