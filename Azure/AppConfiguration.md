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

## Creación de claves y valores emparejados

Azure App Configuration almacena los datos de configuración como pares clave-valor.

### Claves

Las claves sirven como nombre de los pares clave-valor y se usan para almacenar y recuperar los valores correspondientes. Es una práctica habitual la organización de las claves en un espacio de nombres jerárquico mediante un delimitador de caracteres como / o :. 

Las claves almacenadas en App Configuration distinguen entre mayúsculas y minúsculas y son cadenas basadas en Unicode, excepto los caráceteres reservados ('*', ',' y '\'). Si tiene que usar un carácter reservado, deberá especificar un carácter de escape con \{Reserved Character}.

Hay un límite de tamaño combinado de diez mil caracteres en un par clave-valor

### Diseño de espacios de nombres de clave

Hay dos enfoques generales en relación con la nomenclatura de las claves que se usa en los datos de configuración: plano o jerárquico. La nomenclatura jerárquica ofrece varias ventajas:

+ Es más fácil de leer. En lugar de una secuencia larga de caracteres, los delimitadores de una función de nombre de clave jerárquico funciona como los espacios de una frase.
+ Es más fácil de administrar. Un nombre de clave jerárquico representa grupos lógicos de datos de configuración.
+ Es más fácil de usar. Resulta más fácil escribir una consulta cuyos patrones coinciden con las claves de una estructura jerárquica y que recupera solo una porción de los datos de configuración.

En los ejemplos siguientes se muestra cómo puede estructurar los nombres de clave en una jerarquía:

+ Según los servicios de los componentes.

        AppName:Service1:ApiEndpoint
        AppName:Service2:ApiEndpoint

+ Según las regiones de implementación.

        AppName:Region1:DbEndpoint
        AppName:Region2:DbEndpoint

### Claves de etiqueta

Los valores de clave de App Configuration pueden tener un atributo de etiqueta. Las etiquetas se utilizan para diferenciar los valores de clave con la misma clave. De forma predeterminada, la etiqueta de un valor de clave está vacía o es null.

Las etiquetas proporcionan una manera cómoda de crear variantes de una clave. Un uso habitual de las etiquetas consiste en especificar varios entornos para la misma clave:

        Key = AppName:DbEndpoint & Label = Test
        Key = AppName:DbEndpoint & Label = Staging
        Key = AppName:DbEndpoint & Label = Production

### Valores de clave de versión

App Configuration no crea valores de clave de versión automáticamente a medida que se modifican. Use etiquetas como una manera de crear varias versiones de un valor de clave. Por ejemplo, puede escribir un número de versión de la aplicación o un identificador de confirmación de Git en las etiquetas para identificar los valores de clave asociados con una compilación de software en particular.

### Valores de clave de consulta

Cada valor de clave se identifica por su clave más una etiqueta que puede ser null. Si desea consultar los valores de las claves en un almacén de App Configuration, especifique un modelo. El almacén de App Configuration devuelve todos los valores de claves que coincidan con el modelo, así como sus valores y atributos correspondientes.

### Valores

Los valores asignados a las claves también son cadenas unicode. Hay un tipo de contenido opcional definido por el usuario que se asocia a cada valor. Utilice este atributo para almacenar información.

Los datos de configuración que se encuentran en un almacén de App Configuration, entre los que se incluyen todas las claves y los valores, se cifran tanto en reposo como en tránsito. App Configuration no es una solución de reemplazo para Azure Key Vault. No almacene secretos de aplicación en ella.