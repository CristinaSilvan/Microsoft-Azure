# App Service

Es un **servicio PAAS** basado en **HTTP** (Protocolo de transferencia de datos a través de internet); **define la sintáxis y semántica de la comunicación entre aplicaciones web**

Pueden ser desarrolladas en **.NET, .NET Core, Java, Ruby, Node.js, PHP o Python**

Se **ejecutan y escalan en entornos Windows y Linux**

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

## Escalado

Permite el **escalado de recursos de forma manual o autoomática**


## Integración e implementación

**El back-end de la solución normalmente se encuentra alojado en un repositorio de código** (Azure App Service me permite hacerlo de forma nativa ya que Azure portal proporciona **integración e implementación** con **Azure DevOps, GitHub, Bitbucket, FTP o un repositorio GIT local** en el equipo de desarrollo)

## Ranuras de implementación 

Las ranuras de implementación son **aplicaciones activas con sus propios nombres de host**

- Existen dos tipos:
    - **Ranuras de implementación** (entorno de ensayo)
    - **Ranuras de producción** (entorno final)

Estas permiten **gestionar de una forma más efectiva las subidas de versiones al entorno de producción** ya que cada vez que actualizamos la web, hacen falta una serie de procesos que pueden hacer que nuestro servicio dejen de funcionar durante dicha actualización

Estás se **intercambian** para poder **reducir o eliminar el tiempo en el que deja de estar disponible el servicio**

## Tarifas o planes

Los App Service Plan **deben tener una tarifa** en función de la cual se desplegará la Web App y que **especifica la cantidad de tiempo/peticiones que puede alcanzar**

- **Proceso compartido**: tanto **Gratis** como **Compartido** comparten grupos de recursos de sus aplicaciones con las **aplicaciones de otros clientes.** Estos planes asignan cuotas de CPU a cada aplicación que se ejecuta en los recursos compartidos, y **los recursos no se pueden escalar horizontalmente**

- **Proceso dedicado** (Dedicated compute): Los planes **Básico, Estándar, Premium, PremiumV2 y PremiumV3** ejecutan aplicaciones en VM de Azure dedicadas. **Solo las aplicaciones del mismo plan de App Service comparten los mismos recursos de proceso**. Cuanto mayor sea el plan, **más instancias** de VM estarán disponibles para la escalabilidad horizontal

- **Aislado**: Este nivel ejecuta **máquinas virtuales de Azure dedicadas** en instancias de Microsoft Azure Virtual Network. **Proporciona aislamiento de red**, además de **aislamiento de proceso a sus aplicaciones**. Proporciona las **máximas posibilidades de escalabilidad horizontal**

- **Consumo**: este plan **solo** está disponible para **Function Apps**. Escala las funciones de manera **dinámica según la carga de trabajo**

Los planes pueden ser **modificados en cualquier momento** según los requerimientos, ya que **una vez consumido su límite, la aplicación deja de funcionar**

## Autenticación y proveedores


---
---
---
