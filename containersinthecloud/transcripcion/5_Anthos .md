
# Anthos 

<p align="justify">
Es posible que haya escuchado mucho recientemente sobre la adopción de una arquitectura híbrida para potenciar los sistemas y servicios distribuidos 
</p>


<p align="justify">
Es posible que incluso haya oído hablar de la respuesta de Google a la gestión moderna de servicios y sistemas distribuidos híbridos y multinube, llamada Anthos.
</p>

Pero, ¿qué es exactamente Anthos?


<p align="justify">
Anthos es una solución híbrida y multinube impulsada por las últimas innovaciones en sistemas distribuidos y software de gestión de servicios de Google.
</p>


El marco de Anthos se basa en Kubernetes y GKE On-Prem.

<p align="justify">
Esto proporciona la base para una arquitectura que está completamente integrada y tiene una administración centralizada a través de un plano de control central que admite la entrega del ciclo de vida de la aplicación basada en políticas en entornos híbridos y de múltiples nubes.

Anthos también proporciona un amplio conjunto de herramientas para monitorear y mantener la coherencia de sus aplicaciones en toda su red, ya sea en las instalaciones, en la nube o en varias nubes.

Echemos un vistazo más profundo a este marco a medida que construimos una pila de infraestructura híbrida moderna, paso a paso, con Anthos.

Primero, veamos Google Kubernetes Engine en el lado de la nube de nuestra red híbrida.
</p>


<p align="justify">
Google Kubernetes Engine: es un entorno administrado y listo para producción para implementar aplicaciones en contenedores.
</p>

Funciona a la perfección con alta disponibilidad y un SLA.


<p align="justify">
Ejecuta Kubernetes certificados, lo que garantiza la portabilidad en las nubes y en las instalaciones.

incluye reparación automática de nodos, actualización automática y ajuste de escala automático.

Y usa clústeres regionales para alta disponibilidad con múltiples planos de control y replicación de almacenamiento de nodos en múltiples zonas.

Su contraparte en el lado local de nuestra red híbrida es GKE On-Prem.
</p>


<p align="justify">
GKE On-Prem: es una versión de Kubernetes llave en mano, de grado de producción y compatible con una configuración de mejores prácticas precargada.


Proporciona una ruta de actualización fácil a las últimas versiones de Kubernetes que han sido validadas y probadas por Google.


Brinda acceso a servicios de contenedores en Google Cloud, como Cloud Build, Container Registry y Cloud Audit Logs.


Se integra con las soluciones Istio, Knative y Cloud Marketplace.



Y garantiza una versión y una experiencia de Kubernetes coherentes en entornos locales y en la nube.


Tanto Google Kubernetes Engine como GKE On-Prem se integran con Marketplace para que todos los clústeres de su red, ya sea en las instalaciones o en la nube, tengan acceso al mismo repositorio de aplicaciones en contenedores.


Esto le permite usar las mismas configuraciones en ambos lados de la red, lo que reduce el tiempo dedicado a mantener la conformidad entre sus clústeres.


También pasa menos tiempo desarrollando aplicaciones debido a un enfoque de escritura única/replicación en cualquier lugar.


Las aplicaciones empresariales pueden usar cientos de microservicios para manejar cargas de trabajo informáticas.


Hacer un seguimiento de todos estos servicios y monitorear su salud puede convertirse rápidamente en un desafío.


Anthos Service Mesh e Istio Open Source Service Mesh eliminan todas las conjeturas a la hora de gestionar y proteger sus microservicios.


Estas capas de malla de servicios se comunican a través de la red híbrida mediante Cloud Interconnect para sincronizar y pasar sus datos.



Cloud Logging y Cloud Monitoring son las soluciones integradas de registro y monitoreo para Google Cloud.



El paquete de operaciones de Google Clouds ofrece una solución de registro, recopilación de métricas, monitoreo, tableros y alertas completamente administrada que vigila todos los lados de su red híbrida o de múltiples nubes.

Es la solución ideal para los clientes que desean una solución de observabilidad basada en la nube única, fácil de configurar y poderosa que también le brinde un panel de control único para monitorear todos sus entornos.


Por último, Anthos Configuration Management proporciona una única fuente autorizada de información para la configuración de sus clústeres.


Esto se guarda en el repositorio de políticas, que en realidad es un repositorio de git.


El repositorio puede estar ubicado en las instalaciones o alojado en la nube.


Los agentes de gestión de la configuración de Anthos utilizan el repositorio de políticas para hacer cumplir las configuraciones localmente en cada entorno, gestionando así la complejidad de poseer clústeres en todos los entornos.


Anthos Configuration Management también brinda a los administradores y desarrolladores la capacidad de implementar cambios de código con una sola confirmación de repositorio y la opción de implementar la herencia de configuración mediante el uso de espacios de nombres, que es una forma de evitar colisiones de nombres y permisos dentro de su aplicación.

Puede obtener más información sobre Anthos dirigiéndose a cloud.google.com/anthos
</p>
