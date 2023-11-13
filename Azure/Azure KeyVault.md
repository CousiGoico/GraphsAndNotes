# Azure KeyVault

## Explorar Azure Key Vault

Admite dos tipo de contenedores: amaceneces y grupo de módules de seguridad de hardware administradores (HSM). Permiten almacenar software y claves, secretos y certificados de respaldo por HSM. Los gupos HSM adminsirados solo admiten claves respaldadas por HSM. 

+ Administración de secretos: almacena de forma segura y controla de maera estrica el acceso a los tokens, contraseñas, certificiados, claves de API y otros secretos.

+ Administración de claves: facilia la creación y control de las claves de cifrado utilizadas para cifrar los datos.

+ Administración de certificados: permite aprovisionar, administrar e implementar fácilmente certificados de la Capa de sockets seguros y la Seguridad de la capa de transporte (SSL y TLS) públicos y privados para su uso con Azure y los recursos internos conectados. 

__Tiene dos niveles de servicio: Estándar, que realiza el cifrado con una clave de software, y Prémium, que incluye claves protegidas mediante un módulo de seguridad de hardware (HSM).__

### Principales ventajas

+ Secretos de aplicación centralizados: permite controlar su distribución. Las aplicaciones pueden acceder de forma protegida a la información a través de URI. Estás URI permiten que las aplicaciones recuperen versiones específicas de un secreto.

+ Almacenamiento seguro de secretos y claves: requier autenticación y autorización que será autenticado por Microsoft Entra. La autorización se realiza mendiante el control de acceso basado en rol de Azure (RBAC). Los almacenes de claves pueden estar protegidos por software, con el nivel Premium de zure KeyVault o por hardware (módulos de seguridad HSM).

+ supervisión del acceso y uso: tiene el control de los registros y puede protegerlos restringiendo el acceso y eliminando aquellos que ya no necesita. Se puede configurar para:

    + Archivar en una cuenta de almacenamiento.

    + Transmitir a un centro de eventos.

    + Envíe los registro a los registro de Azure Monitor. 

+ Administración simplificada de secretos de aplicación: la información de seguridad debe protegerse, debe seguir un ciclo de vida y debe tener una disponibilidad alta. Simplifica el proceso de cumplimiento mediante:

    + La eliminación de la necesidad de poseer conocimientos internos sobre los módulos de seguridad de hardware (HSM).

    + El escalado vertical en un breve plazo de tiempo para adaptarse a los picos de uso de la organización.

    + La replicación del contenido de una instancia de Key Vault de una región en una región secundaria. La replicación de datos garantiza la alta disponibilidad y elimina la necesidad de intervención del administrador para desencadenar la conmutación por error.

    + La disposición de opciones estándar de administración de Azure a través del portal, la CLI de Azure y PowerShell.

    + La automatización de determinadas tareas de los certificados que adquiere de entidades de certificación públicas, como la inscripción y la renovación.


## Información sobre los procedimientos recomendados de Azure Key Vault

Azure Key Vault es una herramienta para almacenar y acceder a los secretos de forma segura. Un secreto es todo aquello cuyo acceso se quiere controlar de forma estrecha, como los certificados, las contraseñas o las claves de API. Un almacén es un grupo lógico de secretos.

### Authentication

Para realizar cualquier operación con Key Vault, primero deberá autenticarse: 

+ Identidades administradas de recursos de Azure: cuando implementa una aplicación en una máquina virtual en Azure, puede asignar una identidad a la máquina virtual que tiene acceso a Key Vault. También puede asignar identidades a otros recursos de Azure. La ventaja de este enfoque es que la aplicación o el servicio no administran la rotación del primer secreto. Azure rota automáticamente el secreto de cliente de la entidad de servicio asociado con la identidad. Este enfoque es un procedimiento recomendado.

+ Entidad de servicio y certificado: puede usar una entidad de servicio y un certificado asociado que tenga acceso a Key Vault. No se recomienda este enfoque porque el propietario o el desarrollador de la aplicación debe girar el certificado.

+ Entidad de servicio y secreto: aunque puede usar una entidad de servicio y un secreto para autenticarse en Key Vault, no se recomienda que lo haga. Es difícil girar automáticamente el secreto de arranque que se utiliza para autenticarse en Key Vault.

### Cifrado de datos en tránsito

Aplica el protocolo Seguridad de acpaa de transporte (TLS) para proteger los datos en el tránsito entre Azure Key Vault y los clientes. Los clientes negocian una conexión TLS con Azure Key Vault. TLS proporciona una autenticación sólida, privadidad de mensajes e integridad (lo que permite la detección de la manipulación, interceptación y falsificación de mensajes), interoperabilidad, flexibilidad de algoritmo, y facilidad de iplementación y uso. 

Confidencialidad directa total (PFS) protege las conexiones entre los sistemas cliente de los clientes y los servicios en la nube de Microsoft mediante claves únicas. Las conexiones también usan longitudes de clave de cifrado RSA de 2048 bits. Esta combinación hace difícil para un usuario interceptar y acceder a datos que están en tránsito.

### Procedimientos recomendados de Azure Key Vault

+ Uso de almacenes de claves distintos: se recomeienda usar un almacén por aplicaicón y por entorno (desarrollo, preproducción y producción). 

+ Control del acceso al almacén: los datos de Key Vault son confidenciales y críticos para la empresa; necesita proteger el acceso a sus almacenes de claves permitiéndoselo solo a aplicaciones y usuarios autorizados.

+ Copia de seguridad: cree copias de seguridad periódicas del almacén al actualizar, eliminar o crear objetos dentro de este.

+ Registro: asegúrese de activar el reigstro y las alertas.

+ Opciones de recuperación: active la *eliminación temporal* y la protección de purga si desea protegerse contra la eliminación forzada del secreto.