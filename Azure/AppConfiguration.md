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

## Administración de características de la aplicación

La administración de características es una práctica moderna de desarrollo de software que separa el lanzamiento de las características de la implementación del código y permite hacer cambios rápidos relacionados con la disponibilidad de las características a petición. Usa una técnica denominada marcas de características (también conocida como activación/desactivación de funcionalidad o modificador de características, entre otros) para administrar el ciclo de vida de una característica dinámicamente.

### Conceptos básicos

+ __Marca de característica__: una marca de características es una variable con un estado binario de activado o desactivado. La marca de características también tiene un bloque de código asociado. El estado de la marca de características se desencadena tanto si el bloque de código se ejecuta como si no.

+ __Administrador de características__: un administrador de características es un paquete de aplicación que controla el ciclo de vida de todas las marcas de características de una aplicación. Normalmente, el administrador de características proporciona funcionalidad adicional, como el almacenamiento en caché de las marcas de características y la actualización de sus estados.

+ __Filtro__: Un filtro es una regla para evaluar el estado de una marca de características. Un grupo de usuarios, un tipo de explorador o dispositivo, una ubicación geográfica y un período de tiempo son todos ellos ejemplos de lo que puede representar un filtro.

Una implementación eficaz de la administración de características consta de al menos dos componentes que funcionan conjuntamente:

+ Una aplicación que hace uso de las marcas de características.
+ Un repositorio independiente que almacena las marcas de características y sus estados actuales.

### Uso de la marca de características en el código

El patrón básico para implementar las marcas de características en una aplicación es sencillo. Puede considerar una marca de características como una variable de estado booleana usada con una declaración condicional if en su código:

        if (featureFlag) {
           // Run the following code
        }

Si featureFlag está establecido en True, se ejecuta el bloque de código incluido; en caso contrario, se omite. Puede establecer el valor de featureFlag estáticamente, como se muestra en el ejemplo de código siguiente:

        bool featureFlag = true;

También puede evaluar el estado de la marca según ciertas reglas:

        bool featureFlag = isBetaUser();

Un patrón de marca de características un poco más complicado incluye también una instrucción else:

        if (featureFlag) {
            // This following code will run if the featureFlag value is true
        } else {
            // This following code will run if the featureFlag value is false
        }

### Declaración de la marca de características

Cada marca de características tiene dos partes: un nombre y una lista de uno o varios filtros que se utilizan para evaluar si el estado de la característica está activo. Un filtro define un caso de uso en el que debe activarse una característica.

Cuando una marca de características tiene varios filtros, la lista de filtros se recorre en orden hasta que uno de los filtros determina que se debe habilitar la característica. En ese momento, la marca de característica está activa y se omiten los resultados del filtro restantes. Si ningún filtro indica que se debe habilitar la característica, la marca de características está desactivada.

El administrador de la característica admite appsettings.json como origen de configuración para las marcas de características. El ejemplo siguiente muestra cómo establecer las marcas de características en un archivo JSON:

        "FeatureManagement": {
            "FeatureA": true, // Feature flag set to on
            "FeatureB": false, // Feature flag set to off
            "FeatureC": {
                "EnabledFor": [
                    {
                        "Name": "Percentage",
                        "Parameters": {
                            "Value": 50
                        }
                    }
                ]
            }
        }

### Repositorio de marcas de características

Para usar marcas de características de forma eficaz, debe externalizar todas las marcas de características usadas en una aplicación. Ese enfoque le permite cambiar los estados de las marcas de características sin modificar y volver a implementar la propia aplicación.

Azure App Configuration está diseñado para ser un repositorio centralizado para las marcas de características. Puede usarla para definir distintos tipos de marcas de características y manipular sus estados con rapidez y confianza. Luego, puede usar las bibliotecas de App Configuration con diversos marcos de lenguajes de programación para acceder fácilmente a estas marcas de características desde su aplicación.