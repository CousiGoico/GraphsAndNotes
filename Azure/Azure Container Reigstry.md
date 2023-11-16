# Adminsitración de imágenes de contenedor en Azure Container Registry

Azure Container Registry (ACR) es un servicio de registro de Docker administrado y privado que se basa en Dcoker Registry 2.0 de código abierto. Cree y mantenga los registros de Azure Container para almacenar y adminsitrar las imágenes privad del contenedor Docker. 

## Información sobre Azure Container Registry

El servicio Azure Contianer Registry (ACR) dispone de canalizaciones de implementación y desarrollo de contenedores, y Auzre Container Reigstry Task para compilar imágenes de contenedor en Azure. Puedes compilar a petición o automatizar las compilaciones con desencadenadores como las ocnfirmaciones del código funete y las actualizaciones del a imagen de base.

### Caso de uso

Extraiga imágenes desde un registro de coenedores a varios destinos de implementación:

+ __Sistemas de orquestación esclables__ que administran aplicaciones en contenedores en clústeres de hosts, incluidos Kubernetes, DC/OS y Docker Swarm.
+ __servicios de Azure__ que admiten la creación y eejcucción de aplicaciones a escala, includos Azure Kubernetes Service (AKS), App Service, Batch, Service Fabric y otros. 

Los desarrolladores también pueden insertar en un registro de conteedores como parte de un flujo de trabajo de desarrollo de contenedor. 

Configure ACR Tasks para que recompile utomáticamente imágenes de aplicaciones cuando se actualicen sus imágenes base o automatice las compilaciones de imágenes cuando el equipo guarde el código en un repositorio de GIT. Cree tareas de vario pasos para automatizar la compilación, pureba y aplicación de revisiones de varias imágenes de contenedor en paralelo en la nube. 

### Niveles del servicio Azure Container Reigstry

Está disponbile en varios niveles:

|Nivel|Descripción|
|-----|-----------|
|Básico|Optimizado en costes para que los desarrolladores apredan.Los registros básicos tienen las mismas funcionalidades de programación que Estándar y Premum. El almacenamieo inlcuido y el rendimiento de las imágenes son más adecuadas para escenarios de uso inferior.|
|Estándar|Nivel básico pero con más almacenamiento y un mayor rendimiento de las imágenes. Los registros estándar deberían satisfacer las necesidades de la mayoría de los escenarios de producción.|
|Premium|Proporcionan la mayor cantidad de almacenamiento incluido, mayor rendimiento y operaciones simultáneas, por lo que permite trabajar con escenarios de mayor volumen. También agrega características como replicación geográfica para administrar en varias regiones, la confianza en el contenido para la firma de etieutas de imagen un vínculo privado con puntos de conexión privados para restringir el acceso al registro. |

### Imágenes y artefactos admitidos

Las imágenes se agrupan en un repositorio y cada una es una instantánea de solo elctura de un contenedor compatible con Docker. Los reigstros de contenedor de Azure pueden incluir imágenes de Windows y de Linux. Las imágenes también almacenan los formatos de contenido relacionados, como los *gráficos de Helm* y las imágenes creadas para la *especificación de formato de imagen de Open Container Initiative (OCI)*.

### Compilaciones de imágenes automatizadas

Use [Azure Container Registry Tasks (ACR Tasks)](https://learn.microsoft.com/es-es/azure/container-registry/container-registry-tasks-overview) para simplificar la creación, la pureba, el envío de cambios y la implentación de imágenes en Azure. Configure las tareas de compilación para automatizar el sistema operativo del contenedor y la canalización de aplicaciones de revsión de marcos, y compile imágenes de forma automática cuando el equipo guarde el código en el contrl de origen.