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