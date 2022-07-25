# Descripción
- Azure App Service es un servicio basado en HTTP para hospedar aplicaciones web, API de REST y back-ends para dispositivos móviles.

- Puede ser desarrollada en .NET, .NET Core, Java, Ruby, Node.js, PHP o PYthon

- Las aplicaciones se ejecutan y escalan en los entornos de Windows y Linux

# Escalado
- Como la mayoría de recursos en Azure, los recursos de la máquina subyacente en la que se hospeda la aplicación web pueden ser escalados vertical u horizontalmente

>NOTA: El escalado horizontal es la capacidad de aumentar o disminuir el número de instancias de máquinas que ejecutan la aplicación

# Integrado y escalado
- Azure Portal proporciona integración e implementación continuas listas para usar con Azure DevOps, GitHub, Bitbucket, FTP o un repositorio de GIT local

- La App Service se encargará de la sincronización automática del código o futuros cambios en la aplicación web con el repositorio enlazado

- La aplicación web puede ser implementada en una ranura de implementación independiente en lugar de en la ranura de producción predeterminada si realiza la ejecución en el nivel de plan Estándar, Premium o Aislado de la App Service

- Lasranuras de implementación son aplicaciones activas con sus propior nombres de host

- Los elementos de contenido y configuraciones de aplicaciones se pueden intercambiar entre dos ranuras de implementación, incluida la ranura de producción

# Linux
- App Service también puede hospedar las aplicaciones Web de forma nativa en Linux

- No se admite el plan de tarifa compartido

- No se pueden mezclar las aplicaciones Windows y Linux en el mismo plan de App Service

- Se pueden mezclar aplicaciones Windows y LInux en el mismo grupo de recursos

# App Service Plan

- Las App service, una aplicación web, siempre se ejecuta en un App Service Plan

- Un App Service Plan es un conjunto de recursos de proceso para que una web se ejecute

- Pueden configurarse una o varias aplicaciones dentro del plan para que se ejecuten en los mismos recursos informáticos

- LAs Azure Functions también se pueden ejecutar en un App Service Plan

- Cuando se crea un App Service Plan en una región determinada, se crea un conjunto de recursos de proceso para ese plan en dicha región. Todas las aplicaciones que se coloquen en este planm se ejecutan en estos recursos según lo definido por el plan

- Cada App Service Plan define:
    - Región
    - Número de instancias de VM
    - Tamaño de instancias de VM
    - Plan de tarifa (GRatis, Compartido, Básico, Estándar, Premium, PremiumV2, PremiumV3 y Aislado)

    - El App Service Plan determina qué características la aplicación obtendrá y cuánto pagar por ello

    Tipos de planes:
        - Proceso compartido: tanto el gratis como el compartido comparten grupos de recursos de sus aplicaciones con aplicaciones de otros clientes. Estos planes asignan cuotas de CPU a cada aplicación que se ejecuta en los recursos compartidos y esos no pueden escalar horizontalmente

        - Dedicated Compute o Proceso dedicado: LOs planes Básico, Estándar, Premium, PremiumV2 y PremiunV3 ejecutan aplicaciones en VM. Solo as aplicaciones del mismo plan comparten los mismos recursos de proceso. Cuanto mayor sea el plan, más instancias de VM estarán disponibles para la escalabilidad horizontal

        - Aislado: Este nivel ejecuta máquinas virtuales de Azure en instancias de Microsoft Azure Virtual Network. Proporciona aislamiento de red, además de aislamiento de proceso a las aplicaciones. Proporciona las máximas posibilidades de escalabilidad horizontal

        - Consumo: este plan está solo disponible para las App Functions. Escala las funciones de manera dinámica según la carga de trabajo

>NOTA: los planis gratis y compartido corresponden a niveles básidoc los cuales se ejecutan en la misma VM que otras aplicaciones. Es posible que algunas de estas pertenezcan a otros clientes. Por ello, estos niveles están pensados para exclusivamente para el desarrollo y pruebas

# Cómo se escala mi aplicación

- En los planes Gratis y Compartido, una aplicación se hospeda en una VM compartida y no se puede escalas horizontalmente

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

- GOogle /.auth/login/google

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