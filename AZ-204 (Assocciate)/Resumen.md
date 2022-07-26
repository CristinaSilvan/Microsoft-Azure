# ÍNDICE
>[App Service](#app-service)


# App Service

---
---
---
## Descripción

Es un **servicio PAAS** basado en **HTTP** (Protocolo de transferencia de datos a través de internet) para hospedar aplicaciones web, API de REST y back-ends para dispositivos móviles; **define la sintáxis y semántica de la comunicación entre aplicaciones web**

Pueden ser desarrolladas en **.NET, .NET Core, Java, Ruby, Node.js, PHP o Python**

Se **ejecutan y escalan en entornos Windows y Linux**

---
---
---
## App Service Plan

Para crear **Azure App Services o Azure Functions** es necesario un **App Service plan** del que cuelguen y en el que se establece la configuración, al igual que los recursos deben estar vinculados a un resource group

Un Azure App Service Plan es un **conjunto de recursos necesarios para tener una aplicación web**

**No se pueden mezclar las aplicaciones Windows y Linux en el mismo plan de App Service**, sin embargo sí en el mismo grupo de recursos

- Cada plan de App Service define:

    - **Región** (oeste de EE. UU., este de EE. UU., etc.)
    - **Número de instancias de VM**
    - **Tamaño de las instancias de VM** (pequeño, mediano, grande)
    - **Plan de tarifa** (Gratis, Compartido, Básico, Estándar, Premium, PremiumV2, PremiumV3 y Aislado)

**Muchos Web Apps pueden estar contenidos dentro de un mismo App Service Plan**. Lo mismo con las Azure Function

---
---
---
## Escalado

Permite el **escalado de recursos de forma manual o automática**

Como la mayoría de recursos en Azure, **los recursos de la máquina subyacente en la que se hospeda** la aplicación web pueden ser escalados vertical u horizontalmente

>NOTA: en los planes **Gratis y Compartido** no se puede escalar horizontalmente

## Integración e implementación

**El back-end de la solución normalmente se encuentra alojado en un repositorio de código** (Azure App Service me permite hacerlo de forma nativa ya que Azure portal proporciona **integración e implementación** con **Azure DevOps, GitHub, Bitbucket, FTP o un repositorio GIT local** en el equipo de desarrollo)

La App Service se encargará de la **sincronización automática** del código o futuros cambios en la aplicación web **con el repositorio enlazado**

---
---
---
## Ranuras de implementación 

Solo disponibles en el nivel **Estándar, Premium o Aislado**

Las ranuras de implementación son **aplicaciones activas con sus propios nombres de host**

- Existen dos tipos:
    - **Ranuras de implementación** (entorno de ensayo)
    - **Ranuras de producción** (entorno final)

Estas permiten **gestionar de una forma más efectiva las subidas de versiones al entorno de producción** ya que cada vez que actualizamos la web, hacen falta una serie de procesos que pueden hacer que nuestro servicio dejen de funcionar durante dicha actualización

La operación de **intercambio** prepara las instancias de trabajo necesarias para que coincidan con la escala de producción, **lo que elimina el tiempo de inactividad**
## Tarifas o planes

Los App Service Plan **deben tener una tarifa** en función de la cual se desplegará la Web App y que **especifica la cantidad de tiempo/peticiones que puede alcanzar**

- **Proceso compartido**: tanto **Gratis** como **Compartido** comparten grupos de recursos de sus aplicaciones con las **aplicaciones de otros clientes.** Estos planes asignan cuotas de CPU a cada aplicación que se ejecuta en los recursos compartidos, y **los recursos no se pueden escalar horizontalmente**

- **Proceso dedicado** (Dedicated compute): Los planes **Básico, Estándar, Premium, PremiumV2 y PremiumV3** ejecutan aplicaciones en VM de Azure dedicadas. **Solo las aplicaciones del mismo plan de App Service comparten los mismos recursos de proceso**. Cuanto mayor sea el plan, **más instancias** de VM estarán disponibles para la escalabilidad horizontal

- **Aislado**: Este nivel ejecuta **máquinas virtuales de Azure dedicadas** en instancias de Microsoft Azure Virtual Network. **Proporciona aislamiento de red**, además de **aislamiento de proceso a sus aplicaciones**. Proporciona las **máximas posibilidades de escalabilidad horizontal**

- **Consumo**: este plan **solo** está disponible para **Function Apps**. Escala las funciones de manera **dinámica según la carga de trabajo**

Los planes pueden ser **modificados en cualquier momento** según los requerimientos, ya que **una vez consumido su límite, la aplicación deja de funcionar**

---
---
---
## Autenticación y proveedores

Es posible añadir un **factor de autenticación a nuestra App Service** para la que el **usuario o programa** que quiera usar mi aplicación tenga que **pasar por un proveedor de autenticación** (ya que se hace de forma externa y este retorna la información a mi app)

También se puede especificar un **comportamiento de autorización**

Azure tiene **autenticaciones federadas integradas** que sin necesidad de que nosotros administremos

- (Plataforma - Punto de conexión)
- **Microsoft** - /.auth/login/aad
- **Facebook** - /.auth/login/facebook
- **Google** - /.auth/login/google
- **Twitter** - /.auth/login/twitter

>NOTA: la autenticación Microsoft se realiza mediante **Azure Active Directory o Azure AD**

Cuando el módulo de autenticación y autorización está habilitado, **cada solicitud HTTP entrante** pasa a través de este

Este módulo **controla varios aspectos de la aplicación web**:

- Autentica a los ususarios con el proveedor especificado

- Valida, almacena y actualida los tokens

- Administra la sesión autenticada

- Inyecta información de identidad en los encabezados de la solicitud

Se **ejecuta por separado del código** de la aplicación y se **configura mediante parámetros** 

No se necesitan **SDK o lenguajes específicos**

>NOTA: En **Linux y contenedores** el módulo se ejecuta en **un contenedor independiente aislado de la aplicación**. Puesto que no se ejecuta en proceso, **no es posible la integración directa con plataformas de lenguajes específicas**

---
---
---
## Flujo de autenticación 

Es **el mismo para todos los proveedores**, pero varía en función de si queremos **iniciar sesión con el SDK del proveedor**

Se lleva a cabo **mediante cookies** que transmiten información de forma **Segura** mediante el proveedor y nuestra Web App

- **Sin el SDK del proveedor**: la aplicación **delega el inicio de sesión federado a la App Service**. Suele ser el caso de las **aplicaciones de explorador**, que **pueden presentar la página de inicio de sesión** del proveedor al usuario. El código del servidor administra el proceso de inicio de sesión, por lo que también se denomina **flujo dirigido por el servidor o flujo del servidor**

- **Con el flujo SDK del proveedor**: la aplicación inicia manualmente la sesión del usuario con el proveedor y luego envía el token de autenticación a App Service para su validación. Suele ser el caso de las **aplicaciones sin explorador, que no pueden presentar la página de inicio de sesión** del proveedor al ususario. El código de la aplicación administra el proceso de inicio de sesión, por lo que también se denomina **flujo dirigido por el cliente o flujo de cliente**

---
---
---
## Porqué usar la autenticación integrada

Puede **ahorrar tiempo y esfuerzo** los cuales permiten centrarse en el resto de la aplicación

## Autenticación con otros proveedores

Existen otros proveedores al margen de los que nos proporciona Azure con los que también podemos iniciar sesión

Estos se **basan en OAuth o Open Authoritation**, que es un **estándar abierto** que define cómo de forma segura debe realizarse una autorización de una API

Es posisble **configurar el App Service** para esto

En la App Service **se puede controlar el acceso** mediante determinadas APIs o VPNs (filtrándo cuáles pueden acceder) e incluso controlar las salidas de datos de mi aplicación

---
---
---
## Comportamiento de la autorización

- **Permitir solicitudes no autenticadas**: **aplaza la autorización del tráfico no autenticado** al código de la aplicación en los **encabezados HTTP**. Esta opción **permite más flexibilidad** a la hora de controlar solicitudes **anónimas**

- **Requerir autenticación**: **rechaza todo tráfico no autenticado**

>NOTA: Este método de restricción del acceso se aplica a todas las llamadas a la aplicación, por lo que puede no ser deseable para las páginas que necesiten una página de inicio disponible públicamente, como muchas aplicaciones de una sola página


---
---
---
## Conexiones híbridas

Permiten a nuestra aplicación trabajar con **bases de datos que por motivos de seguridad, políticas u otros, se encuentran On-premise** 

>NOTA: No están disponibles para todos los planes SKU

---
---
---
## Acceso a las App Service

Las aplicaciones hospedadas en App Service **pueden ser accedidas** a través de internet mediante **puntos de conexión**

En el caso de **muchas aplicaciones en un mismo plan**, ha de controlarse **el tráfico entrante y saliente^**

Hay dos tipos de implementación principales:

- El servicio público **multiinquilino** que hospeda planes de App Service en las **SKU gratis, compartido, básico, estándar, premium, premiumv2, premiumv3**

- App Service Environment (ASE) de **un único inquilino**, que hospeda planes de App Service de **SKU aislada** directamente en su red virtual de Azure

---
---
---
## Multiinquilino

Azure App Service **es un sistema distribuido**, lo que significa que está repartido en roles los cuales controlan diferentes partes del servicio web

Los **roles que controlan las solicitudes HTTP o HTTPS** se denominan **servidores front-end**

Los **roles que hospedan la carga de trabajo del cliente** se denominan **roles de trabajo**

**Todos los roles** de un servicio App Service existen en una **red de varios inquilinos** por lo que necesita **características para administrar** los diversos aspectos de la comunicación de aplicaciones

Dichas características pueden ser usadas para **solucionar problemas al realizar llamadas desde la aplicación o a la aplicación**

Características de entrada:

- Dirección asignada a las aplicaciones
    - Restricciones de acceso
    - Puntos de conexión del servicio
    - Puntos de conexión privados

- Características de salida:
    - Conexiones híbridas
    - Integración de red virtual con requisito de puerta de enlace
    - Integración de la red virtual

---
---
---
## Configuración de la aplicación

En App Service las configuraciones de aplicaciones son **variables** que se pasan como **variables de entorno al código** de la aplicación

Para agregar o editar la configuración de la aplicación **de forma masiva**, se agrega dicha configuración en **formato JSON** de la siguiente forma:

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

La adición y edición de **cadenas de conexión** sigue los mismos principios

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