# Supervisión del rendimiento de la aplicación

La instrumentación y supervisión de las aplicaciones le permitirá maximizar su disponibilidad y rendimiento.

## Exploración de Application Insights

Application Insights es una extensión de Azure Monitor y proporciona características de Supervisión de rendimiento de aplicaciones (también conocida como "APM"). Las herramientas de APM son útiles para supervisar aplicaciones de desarrollo, pruebas y producción de las siguientes maneras:

+ De manera proactiva comprende cómo funciona una aplicación.
+ De manera reactiva revisa los datos de ejecución de la aplicación para determinar la causa de un incidente.

Además de recopilar métricas y datos de telemetría de las aplicaciones, que describen las actividades y el estado de la aplicación, Application Insights también se puede usar para recopilar y almacenar datos de registro de seguimiento de aplicaciones.

El seguimiento del registro está asociado a otros datos de telemetría para proporcionar una vista detallada de la actividad. Agregar registro de seguimiento a las aplicaciones existentes solo requiere proporcionar un destino para los registros; rara vez es necesario cambiar la plataforma de registro.

### Información general de características de Application Insights

|Característica|Descripción|
|--------------|-----------|
|Live Metrics|Observe la actividad de la aplicación implementada en tiempo real sin ningún efecto en el entorno de host.|
|Disponibilidad|También se conoce como "Supervisión de transacciones sintéticas"; sondee los puntos de conexión externos de las aplicaciones para probar la disponibilidad general y la capacidad de respuesta a lo largo del tiempo.|
|Integración de GitHub o Azure DevOps|Cree elementos de trabajo de GitHub o Azure DevOps en el contexto de los datos de Application Insights.|
|Uso|Conozca qué características son populares para los usuarios y cómo estos interactúan con la aplicación y la usan.|
|Detección inteligente|Detección automática de errores y anomalías mediante análisis de telemetría proactivos.|
|Mapa de aplicación|Vista de arriba abajo de alto nivel de la arquitectura de la aplicación y referencias visuales de un vistazo al estado y la capacidad de respuesta de los componentes.|
|Seguimiento distribuido|Busque y visualice un flujo de un extremo a otro de una ejecución o transacción determinada.|

### Qué supervisa Application Insights

Application Insights recopila datos de telemetría de aplicación y métricas, que describen las actividades y el estado de la aplicación, así como datos de registro de seguimiento.

+ __Tasas de solicitud, tiempos de respuesta y tasas de error__ - Averigüe qué páginas que son las más conocidas, en qué momento del día y dónde están los usuarios. Vea qué páginas presentan mejor rendimiento. Si los tiempos de respuesta y las tasas de error aumentan cuando hay más solicitudes, quizás tiene un problema de recursos.
+ __Tasas de dependencia, tiempos de respuesta y tasa de error__ - Averigüe si los servicios externos le ralentizan.
+ __Excepciones__ - Analice las estadísticas agregadas o seleccione instancias concretas y profundice en el seguimiento de la pila y las solicitudes relacionadas. Se notifican tanto las excepciones de servidor como las de explorador.
+ __Vistas de página y rendimiento de carga__ - Notificados por los exploradores de los usuarios.
+ __Llamadas AJAX desde páginas web__ - Tasas, tiempos de respuesta y tasas de error.
+ __Número de usuarios y sesiones.__
+ __Contadores de rendimiento__ de las máquinas de servidor de Windows o Linux, como CPU, memoria y uso de la red.
+ __Diagnóstico de host__ de Docker o Azure.
+ __Registros de seguimiento de diagnóstico de la aplicación__ - De esta forma puede correlacionar eventos de seguimiento con las solicitudes.
+ __Métricas y eventos personalizados__ que usted mismo escribe en el código de cliente o servidor para realizar un seguimiento de eventos empresariales, como artículos vendidos o partidas ganadas.

### Introducción a Application Insights

Application Insights es uno de los muchos servicios hospedados en Microsoft Azure y los datos de telemetría se envían ahí para analizarlos y mostrarlos. El registro es gratuito y, si elige el plan de precios básico de Application Insights, no habrá cargo alguno hasta que la aplicación tenga un uso considerable.

Hay varias maneras de empezar a supervisar y analizar el rendimiento de las aplicaciones:

+ __En tiempo de ejecución__: instrumente la aplicación web en el servidor. Ideal para las aplicaciones ya implementadas. Evita toda actualización del código.
+ __En tiempo de desarrollo__: agregue Application Insights al código. Le permite personalizar la recopilación de telemetría y enviar más telemetría.
+ __Instrumente sus páginas web__ para la vista de la página, AJAX y otros datos de telemetría del lado cliente.
+ __Analice el uso de aplicaciones móviles__ mediante la integración con Visual Studio App Center.
+ __Pruebas de disponibilidad__: haga ping a su sitio web de manera regular desde nuestros servidores.