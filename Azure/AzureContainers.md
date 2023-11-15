# Azure Containers Apps

Azure Container Apps proporciona la flexibilidad que necesita con un servicio de contenedor sin servidor creado para aplicaciones de microservicios y sólidas funcionalidades de escalado automático sin la sobrecarga de administrar una infraestructura compleja.

## Exploración de Azure Container App

Azure Container Apps permite ejecutar microservicios y aplicaciones en contenedor en una plataforma sin servidor que se ejecuta sobre Azure Kubernetes Service. Entre los usos comunes de Azure Container Apps se incluyen:

+ Implementación de puntos de conexión de API.
+ Hospedaje de aplicaciones de procesamiento en segundo plano.
+ Control del procesamiento controlado por eventos.
+ Ejecución de microservicios.

Se pueden escalar de forma dinámica en función del tráfico HTTP, el procesamiento controlado por eventos, la CPU o la carga de memoria.

Con Azure Container Apps, puede:

+ Ejecutar varias revisiones del contenedor y administrar el ciclo de vida de la aplicación del contenedor.
+ Escalar automáticamente las aplicaciones en función de cualquier desencadenador de escalado compatible con KEDA.
+ Habilitar la entrada HTTPS sin tener que administrar otra infraestructura de Azure.
+ Dividir el tráfico entre varias versiones de una aplicación para las implementaciones azul-verde y los escenarios de prueba A-B.
+ Usar la entrada interna y la detección de servicios para proteger los puntos de conexión solo internos con la detección de servicios basada en DNS integrada.
+ Crear microservicios con Dapr y acceder a su amplio conjunto de API.
+ Ejecutar contenedores desde cualquier registro, público o privado, incluidos Docker Hub y Azure Container Registry (ACR).
+ Usar la extensión de la CLI de Azure, Azure Portal o plantillas de ARM para administrar las aplicaciones.
+ Proporcionar una red virtual existente al crear un entorno para las aplicaciones de contenedor.
+ Administrar secretos de forma segura directamente en una aplicación.
+ Supervisar registros mediante Azure Log Analytics.

### Entornos de Azure Container Apps

Las aplicaciones de contenedor individuales se implementan en un único entorno de Container Apps, que actúa como un límite seguro alrededor de los grupos de aplicaciones de contenedor. La instancia de Container Apps en el mismo entorno se implementa en la misma red virtual y escribe registros en la misma área de trabajo de Log Analytics. Puede proporcionar una red virtual existente al crear un entorno.

Las razones para implementar aplicaciones de contenedor en el mismo entorno incluyen situaciones en las que necesita:

+ Administrar servicios relacionados.
+ Implementar aplicaciones diferentes en la misma red virtual.
+ Instrumentación de aplicaciones Dapr que se comunican mediante la API de invocación del servicio Dapr
+ Hacer que las aplicaciones compartan la misma configuración de Dapr.
+ Hacer que las aplicaciones compartan la misma área de trabajo de Log Analytics.

Las razones para implementar aplicaciones de contenedor en distintos entornos:

+ Que dos aplicaciones nunca comparten los mismos recursos del proceso.
+ Dos aplicaciones Dapr no se pueden comunicar a través de la API de invocación del servicio Dapr

### Microservicios con Azure Container Apps

Las arquitecturas de microservicios permiten desarrollar, actualizar, controlar versiones y escalar áreas básicas de funcionalidad de forma independiente en un sistema general. Azure Container Apps proporciona la base para implementar microservicios con las siguientes características:

+ Escalado, control de versiones y actualizaciones independientes
+ Detección de servicios
+ Integración de Dapr nativa

### Intgración de Dapr

Al implementar un sistema compuesto de microservicios, las llamadas de función se reparten por la red. Para dar cabida a la naturaleza distribuida de los microservicios, debe tener en cuenta los errores, reintentos y tiempos de espera. Dapr incluye características como la observabilidad, la publicación/suscripción y la invocación de servicio a servicio con TLS mutuo, reintentos, etc.