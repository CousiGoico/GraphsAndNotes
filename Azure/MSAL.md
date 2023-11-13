# MSAL

Proporciona acceso seguro a Microsoft Graph, otras API de Microsoft, API web de terceros a su propia API web. Es compatible con muchas arquitecturas y plataformas: .NET, JavaSCript, JAva, Python, Android e iOS.

Ventajas:

+ No es necesario usar directamente las bibliotecas de OAuth ni el código en el protocolo en la aplicación.
+ Adquiere tokens en nombre de un usuario o en nombre de una aplicación (cuando se aplica a la plataforma).
+ Mantiene una caché de tokens y actualiza los tokens de forma automática cuando están próximos a expirar. No es necesario que el usuario controle la expiración de los tokens.
+ Le ayuda a especificar qué audiencia quiere que inicie sesión en la aplicación.
+ Lo ayuda a configurar la aplicación a partir de archivos de configuración.
+ Lo ayuda a solucionar problemas de la aplicación mediante la exposición de excepciones, registros y telemetría que requieren acción.

## Flujos de autenticación

|Flujo|Descripción|
|-----|-----------|
|Código de autorización|Las aplicaciones nativas y web obtienen tokens de forma segura en el nombre del usuario|
|Credenciales de clientes|Las aplicaciones de servicio se ejecutan sin interacción del usuario|
|En nombre de|La aplicación llama a una API web o de servicio, que a su vez llama a Microsoft Graph|
|Impícita|Se usa en aplicacios basadas en el navegador|
|Código del dispositivo|Habilita el inicio de sessión en un dispositivo mediante otro dispositivo que tiene un explorador|
|Integrado en Windows|Los equipos Window adquieren de ofrma silenciosa un token de acceso cuando están unidos a un dominio|
|Interactive|Las aplicacionemóviles y de escritorio llaman a Microsoft Grap nombre de un usuario|
|Nombre de usuario y contraseña|La aplicación inicia la sesión de un uusario con su nombre de usuario y contraseña|

### Aplicaciones clientes públicas y confidenciales

+ Aplicaciones cliente públicas: aplicaciones que no son de confianza para mantener de manera segura secretos, por lo que solo tienen acceso a aPI web en nombre del uaurio. Los clientes públicos no pueden contener secretos de tiempo de configuración, por lo que no tienen secretos de cliente.
+ Aplicaciones cliente confidenciales: aplicaciones ejecutadas en servidores, que se consideran de difícil acceso y pueden mantener un secreto de aplicación. Pueden contener secretos en tiempo de configuración y cada instancia del cliente puede tener una configuración diferente. 