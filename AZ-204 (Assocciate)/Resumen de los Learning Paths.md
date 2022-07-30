# ÍNDICE
>[App Service](#app-service)


# App Service

---
---
---
# Descripción
- Azure App Service es un servicio basado en HTTP para hospedar aplicaciones web, API de REST y back-ends para dispositivos móviles.

- Puede ser desarrollado en .NET, .NET Core, Java, Ruby, Node.js, PHP o Python

- Las aplicaciones se ejecutan y escalan en los entornos de Windows y Linux

# Escalado
- Como la mayoría de recursos en Azure, los recursos de la máquina subyacente en la que se hospeda la aplicación web pueden ser escalados vertical u horizontalmente

- Ni las App Service ni las Azure Function se escalan, sino el plan del que cuelgan


# Integrado y escalado
- Azure Portal proporciona integración e implementación continuas listas para usar con Azure DevOps, GitHub, Bitbucket, FTP o un repositorio de GIT local

- La App Service se encargará de la sincronización automática del código o futuros cambios en la aplicación web con el repositorio enlazado

- La aplicación web puede ser implementada en una ranura de implementación independiente en lugar de en la ranura de producción predeterminada si realiza la ejecución en el nivel de plan Estándar, Premium o Aislado de la App Service

- Las ranuras de implementación son aplicaciones activas con sus propios nombres de host

- Los elementos de contenido y configuraciones de aplicaciones se pueden intercambiar entre dos ranuras de implementación, incluida la ranura de producción

# Linux
- App Service también puede hospedar las aplicaciones Web de forma nativa en Linux

- No se admite el plan de tarifa compartido

- No se pueden mezclar las aplicaciones Windows y Linux en el mismo plan de App Service

- Se pueden mezclar aplicaciones Windows y Linux en el mismo grupo de recursos

# App Service Plan

- Las App service siempre se ejecuta en un App Service Plan

- Un App Service Plan es un conjunto de recursos de proceso necesarios para que una aplicaicón web se ejecute

- Pueden configurarse una o varias aplicaciones dentro del plan para que se ejecuten en los mismos recursos informáticos

- Las Azure Functions también se pueden ejecutar en un App Service Plan (únicamente en el plan de consumo)

- Cuando se crea un App Service Plan en una región determinada, se crea un conjunto de recursos de proceso para ese plan en dicha región. Todas las aplicaciones que se coloquen en este plan se ejecutan en estos recursos según lo definido

- Cada App Service Plan define:
    - Región
    - Número de instancias de VM
    - Tamaño de instancias de VM
    - Plan de tarifa (Gratis, Compartido, Básico, Estándar, Premium, PremiumV2, PremiumV3 y Aislado)

    - El App Service Plan determina qué características la aplicación obtendrá y cuánto pagar por ello

- Tipos de planes:
  - Proceso compartido: tanto el gratis como el compartido comparten grupos de recursos de sus aplicaciones con aplicaciones de otros clientes. Estos planes asignan cuotas de CPU a cada aplicación que se ejecuta en los recursos compartidos y estos no pueden escalar horizontalmente

  - Dedicated Compute o Proceso dedicado: Los planes Básico, Estándar, Premium, PremiumV2 y PremiunV3 ejecutan aplicaciones en VM. Solo las aplicaciones del mismo plan comparten los mismos recursos de proceso. Cuanto mayor sea el plan, más instancias de VM estarán disponibles para la escalabilidad horizontal

  - Aislado: Este nivel ejecuta máquinas virtuales de Azure en instancias de Microsoft Azure Virtual Network. Proporciona aislamiento de red, además de aislamiento de proceso a las aplicaciones. Proporciona las máximas posibilidades de escalabilidad horizontal

  - Consumo: este plan está solo disponible para las App Functions. Escala las funciones de manera dinámica según la carga de trabajo

>NOTA: los planes gratis y compartido corresponden a niveles básicos los cuales se ejecutan en la misma VM que otras aplicaciones. Es posible que algunas de estas pertenezcan a otros clientes. Por ello, estos niveles están pensados exclusivamente para el desarrollo y pruebas

# Cómo se escala mi aplicación

- En los planes Gratis y Compartido, una aplicación se hospeda en una VM compartida y no se puede escalar horizontalmente

- En los demás planes:
    - Una aplicación se ejecuta en todas las instancias de la VM configuradas en el App Service

    - Si hay varias apps en el mismo plan, comparten instancias de VM

    - Si tiene ranuras de implementación para una aplicación, todas las ranuras de implementación se ejecutan también en las mismas instancias de VM

    - Si habilita los registros de diagnóstico, realiza copias de seguridad o ejecuta WebJobs, también usan ciclos de CPU y memoria en estas instandias de VM

De esta manera, el App Service Plan es la unidad de escalado de aplicaciones de App Service, y según su configuración, las App Service se comportarán en consecuencia

# Necesidad de escalado

- El App Service Plan puede ser cambiado a otro plan de tarifa en cualquier momento. Si hay varias app services dentro del plan, pueden ser cambiadas a otro con un plan de tarifa a justado a sus necesidades ya que el cambio afecta a todas las app services dentro del plan

# Ejemplos de casos en los que cambiar de plan

- Una de las app service consume más recursos que las otras
- Quiere escalar la aplicación independientemente de las demás aplicaciones en el plan existente
- La app necesita recursos de una región geográficamente diferente

# Ranuras de implementación

- Siempre que sea posible, use ranuras de implementación al implementar una nueva compilación de producción. Cuando se usa un nivel de plan Estándar o superior, puede implementar la aplicación en un entorno de ansayo e intercambiar los espacios de ensayo y producción

- La operación de intercambio prepara las instancias de trabajo necesarias para que coincidan con la escala de producción, lo que elimina el tiempo de inactividad

# Autenticación y Autorización

Azure App Service inclute compatibilidad con autenticación y autorización para que pueda proporcionar inicio de sesión a los usuarios escribiendo una cantidad mínima de código o incluso sin código

# Porqué usar la autenticación integrada

No es necesario usar App Service para esto ya que muchos marcos web están incluidos en las características de seguridad y puede usarlos si desea. Si necesita más flexibilidad de la que App Service proporciona, también puede escribir sus propias utilidades

La característica de autenticación integrada para App Service y Azure FUnctions puede ahorrar tiempo y esfuerzo, ya que proporciona autenticación integrada con proveedores de identidades federados, lo que le permite centrarse en el resto de la aplicación

- Está integrado directamente en la plataforma y no requiere ningún lenguaje, SDK o experiencia en seguridad

- Varios proveedores como Azure AD, Facebook, Google y Twitter

# Proveedores de identidades

App Service usa la identidad federada, en la cual un proveedor de identidades de terceros almacena las identidades de usuario y el flujo de autenticación para usted

# Proveedores disponibles y su punto de conexión

- Microsoft /.auth/login/aad

- Facebook /.auth/login/facebook

- Google /.auth/login/google

- Twitter /.auth/login/twitter

- Nuevo proveedor de OpenID connect /.auth/login/<providerName>

Cuando habilita la autenticación y autorización con uno de estos proveedores, su punto de conexión de inicio de sesión está disponible para la autenticación de usuarios y para la validación de tokens de autenticación del proveedor. Se puede proporcionar a los usuarios cualquier número de estas opciones de inicio de sesión

# Funcionamiento

El módulo de autenticación y autorización se ejecutan en el mismo espacio aislado que el código de la aplicación. Cuando está habilitado, cada solicitud HTTP entrante pasa a través de él antes de que el código de la aplicación lo controle

Este módulo controla varios aspectos de la aplicación:

- Autentica a los usuarios con el proveedor especificado

- Valida, almacena y actualiza tokens

- Administra la sesión autenticada

- Inyecta información de identidad en los encabezados de solicitud

El módulo se ejecuta por separado del código de aplicación y se configura mediante los parámetros de la aplicación

>NOTA: en Linux y en los contenedores, el módulo de autenticación y autorización se ejecuta en un contenedor independiente, aislado del código de la aplicación. Puesto que no se ejecuta en proceso, no es posible la integración directa con plataformas de lenguajes específicas

# Flujo de autenticación

Es el mismo para todos los proveedores, pero varía en función de si se desea iniciar sesión con el SDK del proveedor

- Sin el SDK del proveedor: la aplicación delega el inicio de sesión federado a la App Service. Suele ser el caso de las aplicaciones de explorador, que pueden presentar la página de inicio de sesión del proveedor al usuario. El código del servidor administra el proceso de inicio de sesión, por lo que también se denomina flujo dirigido por el servidor o flujo del servidor

- Con el flujo SDK del proveedor: la aplicación inicia manualmente la sesión del usuario con el proveedor y luego envía el token de autenticación a App Service para su validación. Suele ser el caso de las aplicaciones sin explorador, que no pueden presentar la página de inicio de sesión del proveedor al ususario. El código de la aplicación administra el proceso de inicio de sesión, por lo que también se denomina flujo dirigido por el cliente o flujo de cliente. Esto se aplica a las API de REST, Azure Functions, los clientes del explorador JavaScript y las aplicaciones móviles nativas que inician la sesión de los usuarios mediante el SDK del proveedor

# Comportamiento de la autorización

En Azure se puede configurar el comportamiento cuando una solicitud entrante no esté autenticada:

- Permitir solicitudes no autenticadas: Aplaza la autorización del tráfico no autenticado al código de la aplicación. En el caso de las autenticadas también pasa información de autenticación en los encabezados HTTP. Esta opción proporciona más flexibilidad a la hora de controlar las solicitudes anónimas. Permite presentar varios proveedores de inicio de sesión a los usuarios

- Requerir autenticación: Rechazará todo tráfico no autenticado a la aplicación. Este rechazo puede ser una acción de redireccionamiento a uno de los proveedores de identidades configurados.

>NOTA: Este método de restricción del acceso se aplica a todas las llamadas a la aplicación, por lo que puede no ser deseable para las páginas que necesiten una página de inicio disponible públicamente, como muchas aplicaciones de una sola página

# Acceso a las App Service

De manera predeterminada, puede acceder a las aplicaciones hospedadas en App Service a través de internet, estas solo pueden acceder a los puntos de conexión

En el caso de muchas aplicaciones, ha de controlarse el tráfico de red entrante y saliente

Hay dos tipos de implementación principales:
- El servicio público multiinquilino que hospeda planes de App Service en las SKU gratis, compartido, básico, estándar, premium, premiumv2, premiumv3

- App Service Environment (ASE) de un único inquilino, que hospeda planes de App Service de SKU aislada directamente en su red virtual de Azure

# Multiinquilino

Azure App Service es un sistema distribuido. Los roles que controlan las solicitudes HTTP o HTTPS entrantes se denominan servidores front-end. LOs roles que hospedan la carga de trabajo del cliente se denominan roles de trabajo. Todos los roles de una implementación de App Service existen en una red de varios inquilinos. Puesto que hay muchos clientes diferentes en la misma unidad de escalado de App Service, no puede conectar la red de App Service directamente a su red

En su lugar, necesita características para administrar los diversos aspectos de la comunicación de aplicaciones

Dichas características no pueden ser usadas para solucionar plroblemas al realizar llamadas desde la aplicación. Del mismo modo, las características que resuelven los problemas para las llamadas desde la aplicación no se pueden usar para solucionar problemas de llamadas a la aplicación (sí, has leído correctamente este párrafo y sí, está bien escrito... fíjate bien en la diferencia y entenderás)

Características de entrada:
- Dirección asignada a las aplicaciones
- Restricciones de acceso
- Puntos de conexión del servicio
- Puntos de conexión privados

Características de salida:
- Conexiones híbridas
- Integración de red virtual con requisito de puerta de enlace
- Integración de la red virtual

Ejemplos de cómo usar características de redes de App Service para controlar el tráfico de entrada:

Caso de uso de entrada -> Característica

- Compatibilidad con las necesidades de SSL basado en IP de la aplicación -> Dirección asignada a las aplicaciones

- Compatibilidad con la dirección entrante dedicada no compartida para la aplicación -> Dirección asignada a las aplicaciones

- Restricción del acceso a la aplicación desde un conjunto de direcciones bien definidas -> Restricciones de acceso

# Comportamiento predeterminado de las redes

- Los planes SKU gratis y compartido hospedan cargas de trabajo de clientes en roles de trabajo multiinquilino

- EL plan básico y superiores hospedan cargas de trabajo dedicadas a un único plan de App Service

- En los planes estándar, todas las aplicaciones se ejecutarán bajo el mismo rol de trabajo

- Si escala horizontalmente el rol de trabajo, todas las aplicaciones de ese plan se replicarán en un rol de trabajo nuevo para cada instancia del plan de App Service

# Direcciones de salida

Las máquinas virtuales de trabajo se desglosan en gran medida a través de los planes de App Service

Cuando se cambia la familia de máquinas virtuales, obtiene un conjunto diferente de direcciones de salida, como cuando se realiza un escalado

Hay varias direcciones que se usan para las llamadas salientes. Las direcciones de salida que usa la aplicación para realizar llamadas salientes se muestran en las propiedades de la aplicación

Todas las aplicaciones que se ejecutan en la misma familia de máquinas virtuales de trabajo de la implementación de App Service comparten estas direcciones. Si quiere ver todas las direcciones que puede usar la aplicación en una unidad de escalado, existe una propiedad denominada possibleOutboundAddresses que puede enumerarlas

# Búsqueda de las direcciones IP de salida

Para buscar las direcciones IP de salida que usa actualmente su aplicación en Azure Portal, haga clic en Propiedades en el panel de navegación izquierdo de la aplicación

Puede encontrar la misma información si ejecuta el comando siguiente en Cloud Shell. Se enumeran en el campo Direcciones IP salientes adicionales

```
az webapp show \
    --resource-group <group_name> \
    --name <app_name> \ 
    --query outboundIpAddresses \
    --output tsv
```

Para buscar todas las posibles direcciones IP de salida para la aplicación, con independencia de los planes de tarifa, ejecute el siguiente comando en Cloud Shell

```
az webapp show \
    --resource-group <group_name> \ 
    --name <app_name> \ 
    --query possibleOutboundIpAddresses \
    --output tsv
```

[Ejercicio: Creación de una aplicación web HTML estática mediante Azure Cloud Shell](https://docs.microsoft.com/es-es/learn/modules/introduction-to-azure-app-service/7-create-html-web-app)

# Configuración de la aplicación 

En App Service, las configuraciones de aplicaciones son variables que se pasan como variables de entorno al código de la aplicación

En el caso de las aplicaciones Linux y de los contenedores personalizados, App Service pasa la configuración de la aplicación al contenedor mediante la marca --env para establecer la variable de entorno en el contenedor

Para los desarrolladores de ASP.NET y ASP.NET Core, la configuración de las opciones de aplicación en App Service es como configurarlas en appSettings en Web.config o appsettings.json, pero los valores de App Service reemplazan a los de Web.config o appsettings.json. Puede mantener segura la configuración de desarrollo (por ejemplo, la contraseña de MySQL local) en Web.config o appsettings.json, excepto los secretos de producción (por ejemplo, la contraseña de base de datos de Azure MySQL) en App Service. El mismo código usa la configuración de desarrollo cuando se depura localmente, y utiliza los secretos de producción cuando se implementa en Azure

# Edición masiva de la configuración

Para agregar o editar la configuración de la aplicación de forma masiva, se agrega dicha configuración en formato JSON 

La configuración de la aplicación tiene el formato JSON siguiente:
```
[
  {
    "name": "<key-1>",
    "value": "<value-1>",
    "slotSetting": false
  },
  {
    "name": "<key-2>",
    "value": "<value-2>",
    "slotSetting": false
  },
  ...
]
```

# Configurar cadenas de conexión

Para los desarrolladores de ASP.NET y ASP.NET Core, los valores establecidos en App Service invalidan los de Web.config. Para otras pilas de lenguaje, es mejor usar la configuración de la aplicación en su lugar, ya que las cadenas de conexión requieren un formato especial en las claves de variable para poder acceder a los valores. Las cadenas de conexión siempre se cifran cuando se almacenan (cifrado en reposo)

>NOTA: Hay un caso en el que puede que quiera usar cadenas de conexión en lugar de la configuración de la aplicación para los lenguajes que no son .NET: la copia de seguridad de determinados tipos de bases de datos de Azure se realiza junto con la aplicación solo si se configura una cadena de conexión para la base de datos en la aplicación de App Service

La adición y edición de cadenas de conexión sigue los mismos principios que otras configuraciones de la aplicación y también se puede vincular a ranuras de implementación. A continuación se muestra un ejemplo de cadenas de conexión en formato JSON que se usaría para la adición o edición de forma masiva:

```
[
  {
    "name": "name-1",
    "value": "conn-string-1",
    "type": "SQLServer",
    "slotSetting": false
  },
  {
    "name": "name-2",
    "value": "conn-string-2",
    "type": "PostgreSQL",
    "slotSetting": false
  },
  ...
]
```

# Configurar las opciones generales

Algunas configuraciones requieren escalar verticalmente hasta los planes de tarifa superiores

A continuación se muestra una lista de las opciones disponibles actualmente:

- Configuración de pila: La pila de software para ejecutar la aplicación, incluidos el lenguaje y las versiones del SDK. Para aplicaciones de Linux y aplicaciones de contenedor personalizadas, también puede establecer un archivo o un comando de inicio opcional

- Configuración de plataforma: Le permite configurar opciones para la plataforma de alojamiento, incluidas:
    - Valor de bits: 32 bits o 64 bits.
    - Protocolo de WebSocket: para ASP.NET SignalR o socket.io, por ejemplo
    - Always On: mantenga cargada la aplicación, incluso cuando no hay tráfico. De forma predeterminada, la opción Siempre activa no está habilitada y la aplicación se descarga tras 20 minutos sin ninguna solicitud entrante. Esto es necesario en los WebJobs continuos o WebJobs que se desencadenan mediante una expresión CRON
    - Versión de canalización administrada: el modo de canalización de IIS. Establézcalo en Clásico si tiene una aplicación heredada que requiere una versión anterior de IIS
    - Versión de HTTP: Establézcala en 2.0 para habilitar la compatibilidad con el protocolo HTTPS/2
    - Afinidad ARR: en una implementación de varias instancias, asegúrese de que el cliente esté enrutado a la misma instancia de la vida de la sesión. Puede establecer esta opción en Desactivada para las aplicaciones sin estado

- Depuración: habilite la depuración remota para las aplicaciones de ASP.NET, ASP.NET Core o Node.js. Esta opción se desactiva automáticamente después de 48 horas

- Certificados de cliente entrantes: requieren certificados de cliente en la autenticación mutua. La autenticación mutua TLS se usa para restringir el acceso a la aplicación mediante la habilitación de diferentes tipos de autenticación

# Configurar asignaciones de ruta de acceso

Puede configurar asignaciones de controladores y asignaciones de directorios y aplicaciones virtuales. La página Asignaciones de ruta mostrará distintas opciones según el tipo de sistema operativo

# Aplicaciones de WIndows (sin contenedor)

Para aplicaciones de Windows, puede personalizar las asignaciones de controlador de IIS, así como las aplicaciones y directorios virtuales.

Las asignaciones de controlador permiten agregar procesadores de script personalizados para controlar solicitudes de extensiones de archivo específicas. Para agregar un controlador personalizado, seleccione Nuevo controlador. Configure el controlador de la manera siguiente:

- Extensión: la extensión de archivo que quiere controlar, como *.php o handler.fcgi

- Procesador de scripts: la ruta de acceso absoluta del procesador de scripts. El procesador de script procesa las solicitudes a archivos que coincidan con esta extensión de archivo. Utilice la ruta de acceso D:\home\site\wwwroot para hacer referencia al directorio raíz de la aplicación

- Argumentos: argumentos de línea de comandos opcionales para el procesador de scripts

Cada aplicación tiene la ruta de acceso de la raíz predeterminada (/) asignada a D:\home\site\wwwroot, donde el código se implementa de forma predeterminada. Si la raíz de la aplicación está en una carpeta diferente o si el repositorio tiene más de una aplicación, puede editar o agregar directorios y aplicaciones virtuales

Puede configurar directorios y aplicaciones virtuales especificando cada directorio virtual y su ruta de acceso física correspondiente en relación con la raíz del sitio web (D:\home). Para marcar un directorio virtual como aplicación web, desactive la casilla Directorio

# Aplicaciones Linux y en contenedor

También puede agregar almacenamiento personalizado para la aplicación en contenedor. Las aplicaciones en contenedores incluyen todas las aplicaciones de Linux y también los contenedores personalizados de Windows y Linux que se ejecutan en App Service. Haga clic en Nuevo montaje de Azure Storage y configure el almacenamiento personalizado como sigue:

- Name: El nombre para mostrar

- Opciones de configuración: básica o avanzada

- Cuentas de almacenamiento: cuenta de almacenamiento con el contenedor que quiere

- Storage type (Tipo de almacenamiento): Azure Blobs o Azure Files Las aplicaciones de contenedor de Windows solo admiten Azure Files

- Contenedor de almacenamiento: para la configuración básica, el contenedor que quiera

- Nombre del recurso compartido: para la configuración avanzada, el nombre del recurso compartido

- Clave de acceso: para la configuración avanzada, la clave de acceso

- Ruta de acceso de montaje: La ruta de acceso absoluta en el contenedor para montar el almacenamiento personalizado

# Activación del registro de diagnóstico

Hay diagnósticos integrados que ayudan a depurar una aplicación de App Service. En esta unidad, aprenderá a habilitar el registro de diagnóstico y a agregar instrumentación a la aplicación, así como a acceder a la información que registra Azure

Tipos de registro:
    - Registro de aplicaciones (Windows, Linux)
      - Registra los mensajes generados por el código de aplicación. Los mensajes se pueden generar en el marco web que elija o directamente desde el código de aplicación mediante el patrón de registro estándar del lenguaje. A cada mensaje se le asigna una de las siguientes categorías: Crítico, Error, Advertencia, Información, Depuración y Seguimiento

    - Registro del servidor web (Windows)
      - Datos de solicitud HTTP sin procesar en el formato de archivo de registro extendido W3C. Cada mensaje de registro incluye datos como el método HTTP, el URI de recurso, la dirección IP del cliente, el puerto de cliente, el agente de usuario, el código de respuesta, etc

    - Registro del servidor web (Windows)
      - Copias de las páginas de error .htm que se habrían enviado al explorador del cliente. Por motivos de seguridad, no se deben enviar páginas de error detalladas a los clientes en producción, pero App Service puede guardar la página de error cada vez que se produzca un error de aplicación que tenga el código HTTP 400 o superior

    - Seguimiento de solicitudes con error (Windows)
      - Información de seguimiento detallada sobre las solicitudes con error, lo que incluye un seguimiento de los componentes de IIS usados para procesar la solicitud y el tiempo dedicado a cada componente. Se genera una carpeta para cada solicitud con error, que contiene el archivo de registro XML y la hoja de estilos XSL con la que ver el archivo de registro

    - Registro de implementación (Windows, Linux)
      - Ayuda a determinar por qué se ha producido un error en la implementación. El registro de implementación tiene lugar automáticamente, no hay valores configurables

[Enlace sobre configuración de registros](https://docs.microsoft.com/es-es/learn/modules/configure-web-app-settings/5-enable-diagnostic-logging)


# Configuración de certificados de seguridad

El certificado de seguridad es una medida de confianza que permite la protección de la confidencialidad de los datos que se transmiten mediante la red. De este modo, se evita que la información se exponga de manera pública y pueda ser utilizada para ciberdelitos y usos fraudulentos

Azure App Service tiene herramientas que le permiten crear, cargar o importar un certificado privado o un certificado público en App Service

Los certificados cargados en una aplicación se almacenan en una unidad de implementación enlazada a la combinación de región y grupo de recursos del plan de App Service (que internamente se denomina espacio web). De esta manera, los certificados son accesible para otras aplicaciones de la misma combinación de región y grupo de recursos

Opciones para agregar certificados:
  - Crear un certificado administrado de App Service gratuito
    - Certificado privado que es gratuito y fácil de usar si solo necesita proteger el dominio personalizado en App Service

  - Compra de un certificado de App Service
    - Es un certificado privado administrado por Azure. Combina la simplicidad de la administración automatizada de certificados con la flexibilidad de las opciones de renovación y exportación

  - Importación de un certificado de Key Vault
    - Resulta útil si usa Azure Key Vault para administrar los certificados

  - Carga de un certificado privado
    - Si ya tiene un certificado privado de un proveedor de terceros, puede cargarlo

  - Carga de un certificado público
    - Los certificados públicos no se usan para proteger los dominios personalizados, pero se pueden cargar en el código si se necesitan para acceder a recursos remotos

# Requisitos de certificados privados

El certificado administrado de App Service gratuito y el certificado de App Service ya cumplen los requisitos de App Service. Si quiere usar un certificado privado en App Service, el certificado debe cumplir los siguientes requisitos:

- Se exporta como un archivo PFX protegido por contraseña, que está cifrado con Triple DES.

- Contener una clave privada con una longitud de al menos 2048 bits

- Contener todos los certificados intermedios de la cadena de certificados

Para proteger un dominio personalizado en un enlace TLS, el certificado debe cumplir otros requisitos:

  - Contener un uso mejorado de clave para la autenticación de servidor (OID = 1.3.6.1.5.5.7.3.1)

  - Estar firmado por una entidad de certificación de confianza

# Creación de un certificado administrado gratuito

El certificado administrado de App Service gratuito es una solución inmediata para proteger el nombre DNS personalizado en App Service

Se trata de un certificado de servidor TLS/SSL totalmente administrado por App Service y que se renueva de manera continua y automática en incrementos de seis meses, 45 días antes de la expiración. Usted crea el certificado y lo enlaza a un dominio personalizado, y deja que App Service se encargue del resto

El certificado gratuito presenta las siguientes limitaciones:

  - No admite certificados comodín

  - No admite el uso como certificado de cliente mediante la huella digital de certificado

  - No se puede exportar

  - No puede utilizarse en App Service Environment (ASE)

  - No es compatible con los dominios raíz que se integran con Traffic Manager

  - Si un certificado es para un dominio asignado por CNAME, el CNAME debe asignarse directamente a ```app-name.azurewebsites.net```

[Enlace sobre certificados](https://docs.microsoft.com/es-es/learn/modules/configure-web-app-settings/6-configure-security-certificates)

# Administración de las características de la aplicación

La administración de características es una práctica moderna de desarrollo de software que separa el lanzamiento de las características de la implementación del código y permite hacer cambios rápidos relacionados con la disponibilidad de las características a petición

Usa una técnica denominada marcas de características (también conocida como activación/desactivación de funcionalidad o modificador de características, entre otros) para administrar el ciclo de vida de una característica dinámicamente

- Marca de característica: una marca de características es una variable con un estado binario de activado o desactivado. La marca de características también tiene un bloque de código asociado. El estado de la marca de características se desencadena tanto si el bloque de código se ejecuta como si no

- Administrador de características: un administrador de características es un paquete de aplicación que controla el ciclo de vida de todas las marcas de características de una aplicación. El administrador de características normalmente proporciona funcionalidad adicional, como el almacenamiento en caché de las marcas de características y la actualización de sus estados

- Filtro: Un filtro es una regla para evaluar el estado de una marca de características. Un grupo de usuarios, un tipo de explorador o dispositivo, una ubicación geográfica y un período de tiempo son todos ellos ejemplos de lo que puede representar un filtro

Una implementación eficaz de la administración de características consta de al menos dos componentes que funcionan conjuntamente:
  - Una aplicación que hace uso de las marcas de características
  - Un repositorio independiente que almacena las marcas de características y sus estados actuales

[Enlace sobre características](https://docs.microsoft.com/es-es/learn/modules/configure-web-app-settings/7-manage-app-features)

# Declaración de la marca de características

Cada marca de características tiene dos partes: un nombre y una lista de uno o varios filtros que se utilizan para evaluar si el estado de la característica está activo

Un filtro define un caso de uso en el que debe activarse una característica

Cuando una marca de características tiene varios filtros, la lista de filtros se recorre en orden hasta que uno de los filtros determina que se debe habilitar la característica. En ese momento, la marca de característica está activa y se omiten los resultados del filtro restantes

Si ningún filtro indica que se debe habilitar la característica, la marca de características está desactivada

El ejemplo siguiente muestra cómo establecer las marcas de características en un archivo JSON:

```
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
```

# Repositorio de marcas de características

Para usar marcas de características de forma eficaz, debe externalizar todas las marcas de características usadas en una aplicación

Ese enfoque le permite cambiar los estados de las marcas de características sin modificar y volver a implementar la propia aplicación

Azure App Configuration está diseñado para ser un repositorio centralizado para las marcas de características. Puede usarla para definir distintos tipos de marcas de características y manipular sus estados con rapidez y confianza

Luego, puede usar las bibliotecas de App Configuration con diversos marcos de lenguajes de programación para acceder fácilmente a estas marcas de características desde su aplicación

# Escalado de aplicaciones

El escalado automático requiere que se configuren reglas de escalabilidad automática que especifiquen las condiciones bajo las que se agregan o se quitan los recursos

Una regla especifica el umbral para una métrica y desencadena un evento de escalabilidad automática cuando se sobrepasa este umbral

Al hospedar una aplicación, es una solución adecuada cuando no se puede predecir con facilidad la carga de trabajo por adelantado, o bien cuando es probable que la carga de trabajo varíe en función de la fecha o la hora

El escalado automático mejora la disponibilidad y la tolerancia a errores. Puede ayudar a garantizar que las solicitudes cliente a un servicio no se denieguen porque una instancia no sea capaz de reconocer la solicitud de manera oportuna, o bien porque una instancia sobrecargada se haya bloqueado

El escalado automático funciona mediante la adición o eliminación de servidores web. Si las aplicaciones web realizan procesamientos que consumen muchos recursos como parte de cada solicitud, es posible que el escalado automático no sea un procedimiento eficaz

En estas situaciones, puede ser necesario el escalado manual ya que el escalamiento automático se produce de forma horizontal y puede ser necesario un escalamiento vertical

El escalado automático no es el enfoque óptimo para controlar el crecimiento a largo plazo

Para evitar el escalado automático descontrolado, el plan de App Service tiene un límite de instancias. Los planes de los planes de tarifa más caros tienen un límite mayor. El escalado automático no puede crear más instancias que las especificadas por este límite

>NOTA: No todos los planes de tarifa de plan de App Service admiten el escalado automático. Los planes de tarifa de desarrollo se limitan a una única instancia (los planes F1 y D1), o bien solo proporcionan escalado manual (el plan B1). Si ha seleccionado uno de estos planes, primero debe escalar verticalmente hasta S1 o cualquiera de los planes de producción del nivel P

[Enlace sobre escalado de aplicaciones](https://docs.microsoft.com/es-es/learn/modules/scale-apps-app-service/2-autoscale-factors)

# Ranuras de implementación 

Puede usar una ranura de implementación independiente en lugar del espacio de producción predeterminado si realiza la ejecución en el nivel de plan Estándar, Premium o Aislado de App Service

La implementación de la aplicación en un espacio que no sea de producción ofrece las siguientes ventajas:
  - Puede validar los cambios en la aplicación en una ranura de implementación de ensayo antes de intercambiarla con la ranura de producción

  - La implementación de una aplicación en un espacio y su posterior paso a producción garantiza que todas las instancias del espacio están preparadas antes de dicho paso a producción. Esto elimina tiempos de inactividad a la hora de implementar la aplicación. El redireccionamiento del tráfico es perfecta y no se pierde ninguna solicitud en las operaciones de intercambio. Todo este flujo de trabajo se puede automatizar mediante la configuración del intercambio automático cuando no sea necesario realizar ninguna validación antes del intercambio

  - Después del intercambio, la ranura con la aplicación de ensayo anterior ahora ocupa la aplicación de producción anterior. Si las modificaciones que se han intercambiado en el espacio de producción no son los que esperaba, puede volver a realizar un intercambio inmediatamente para tener el "último sitio que sabe que funciona correctamente"

Cada nivel del plan de App Service admite un número distinto de ranuras de implementación

El uso de las ranuras de implementación no tiene costo adicional

Para escalar la aplicación a un nivel diferente, asegúrese de que el nivel de destino admite el número de ranuras que la aplicación ya usa, ya que si la aplicación usa más ranuras que el plan al que quiere reducir, no podrá

[Enlace sobre ranuras de implementación](https://docs.microsoft.com/es-es/learn/modules/understand-app-service-deployment-slots/3-app-service-slot-swapping)

---
---
---