# App Configuration

Azure App Configuration proporciona un servicio para administrar la configuración de la aplicación y las marcas de características de forma centralizada.

## Exploración del servicio Azure App Configuration

Use App Configuration para almacenar toda la configuración de la aplicación y proteger sus accesos en un solo lugar.

Ventajas:

+ Un servicio totalmente administrado que puede configurar en cuestión de minutos.
+ Representaciones y asignaciones de claves flexibles.
+ Etiquetado con etiquetas.
+ Reproducción de la configuración en un momento dado.
+ Interfaz de usuario dedicada para la administración de marcas de características.
+ Comparación de dos conjuntos de configuraciones en dimensiones definidas de forma personalizada.
+ Seguridad mejorada mediante las identidades administradas de Azure.
+ Cifrado de información confidencial en reposo y en tránsito.
+ Integración nativa con plataformas conocidas.

__App Configuration complementa Azure Key Vault, que se usa para almacenar secretos de aplicación.__

Implementaciones:

+ La administración centralizada y la distribución de datos de configuración jerárquicos para diferentes entornos y regiones geográficas.
+ Los cambios de configuración dinámica sin necesidad de volver a implementar o reiniciar una aplicación.
+ El control de la disponibilidad de las características en tiempo real.

### Use de AppConfiguration

|Lenguaje y plataforma de programación|Conexión|
|-------------------------------------|--------|
|.NET Core y ASP.NET Core|[Proveedor](https://learn.microsoft.com/es-es/dotnet/api/Microsoft.Extensions.Configuration.AzureAppConfiguration) de AppConfiguration para .NET Core|
|.NET Framework y ASP.NET|[Generador](https://github.com/aspnet/MicrosoftConfigurationBuilders/blob/main/README.md#azureappconfigurationbuilder) de AppConfiguration para .NET Core|
|Java Spring|[Cliente](https://microsoft.github.io/spring-cloud-azure/docs/azure-app-configuration/2.9.0/reference/html/index.html) de App Configuration para Spring Cloud|
|JavaScript/Node.js|[Cliente](https://github.com/Azure/azure-sdk-for-js/tree/main/sdk/appconfiguration/app-configuration) de App Configuration para JavaScript|
|Python|[Cliente](https://github.com/Azure/azure-sdk-for-python/tree/main/sdk/appconfiguration/azure-appconfiguration) de App Configuration para Python|
|Otros|[API REST](https://learn.microsoft.com/es-es/rest/api/appconfiguration/) de App Configuration|