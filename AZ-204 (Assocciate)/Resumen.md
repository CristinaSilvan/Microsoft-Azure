`Siento la mala calidad de las im谩genes, las capturas de pantalla de las grabaciones son horrorosas!`
`脕nimo con los estudios!!`馃槄

# Azure 204 - Developing Solutions for Microsoft Azure
[Notas personales](#notas-personales)

>[Enlace al examen y las rutas de aprendizaje](https://docs.microsoft.com/en-us/learn/certifications/exams/az-204)

>[Enlace a los laboratorios de GitHub](https://github.com/MicrosoftLearning/AZ-204-DevelopingSolutionsforMicrosoftAzure)

>[Comandos de Azure CLI](https://github.com/CristinaSilvan/Microsoft-Azure/blob/main/AZ-204%20(Asscciate)/Otros%20apuntes/Comandos%20CLI.md)

>[Respuestas de los QUIZ de clase](https://github.com/CristinaSilvan/Microsoft-Azure/blob/main/AZ-204%20(Asscciate)/Otros%20apuntes/Respuestas%20de%20los%20QUIZ.md)

>[Respuestas Ex谩menes](https://github.com/CristinaSilvan/Microsoft-Azure/blob/main/AZ-204%20(Asscciate)/Otros%20apuntes/Respuestas%20Ex%C3%A1menes.md)

**Conceptos importantes**:
- *Software escalable*: applicaci贸n utilizada por infinidad de usuarios (lo opuesto a un software usado por uno o pocos miembros dentro de una misma organizaci贸n)

- *SDLA o software development life cycle*: El ciclo de desarrollo, compilaci贸n, testeo, despliegue, versionamiento y dem谩s que se lleva a cabo en la producci贸n del software y que continua con la actualizaci贸n del mismo

- *SLA (Service Level Agreement)*: Acuerdo de alta disponibilidad m铆nima de recursos medido en porcentaje

- *Planes SKU*: planes de tarifa para los diferentes servicios que se ajusta a las necesidades y difieren en los precios

- *Instancias en Azure Functions*: llamadas o solicitudes mediante protocolo hacia un servicio

- *SDK o Software Development Kit*: es un grupo de herramientas que permiten a la programaci贸n de aplicaciones

>> NOTA: Es necesario conocer los distintos planes seg煤n lo que ofrecen **(Free (F), Basic (B), Standar (S))**

>> (El plan **Free** no contiene escalado autom谩tico)

---
---
---

# 脥ndice

## [Intro](#introducci贸n)
## [Ruta certificaci贸n](#ruta-completa-certificaci贸n)
## [Esquema m贸dulos](#esquema-de-m贸dulos)

---
---
---

## [M贸dulo 1: Creaci贸n de aplicaciones web](#m贸dulo-1)

## [M贸dulo 2: Implementaci贸n de Azure Functions](#m贸dulo-2)

## [M贸dulo 3: Desarrollo de soluciones que usan Blob Storage](#m贸dulo-3)

## [M贸dulo 4: Desarrollo de soluciones que usan Azure Cosmos DB](#m贸dulo-4)

## [M贸dulo 5: Implementaci贸n de soluciones de infraestructura como servicio](#m贸dulo-5)

## [M贸dulo 6: Implementaci贸n de la autenticaci贸n y autorizaci贸n de usuarios](#m贸dulo-6)

## [M贸dulo 7: Implementaci贸n de soluciones en la nube seguras](#m贸dulo-7)

## [M贸dulo 8: Implementaci贸n de API Management](#m贸dulo-8)

## [M贸dulo 9: Desarrollo de soluciones basadas en eventos](#m贸dulo-9)

## [M贸dulo 10: Desarrollo de soluciones basadas en mensajes](#m贸dulo-10)

## [M贸dulo 11: Instrumentaci贸n de soluciones para admitir la supervisi贸n y el registro](#m贸dulo-11)

## [M贸dulo 12: Integraci贸n de almacenamiento en cach茅 y entrega de contenido en las soluciones](#m贸dulo-12)

---
---
---

# Introducci贸n

![1](img/1.png)

# Ruta completa certificaci贸n

![2](img/2.png)

[AZ-900 Fundamentals](https://docs.microsoft.com/en-us/certifications/exams/az-900)

[AZ-204 Associate](https://docs.microsoft.com/en-us/certifications/exams/az-204)

[AZ-400 Expert](https://docs.microsoft.com/es-es/certifications/exams/az-400)

# Esquema de m贸dulos

![3](img/3.png)
![4](img/4.png)

---
---
---

# M贸dulo 1
# (Creaci贸n de aplicaciones web)
>>`<Clase del 01/07/2022>`

[Enlace a documentaci贸n Microsoft](https://docs.microsoft.com/es-es/azure/app-service/)

[Enlace a documentaci贸n Microsoft](https://azure.conosur.tech/azurefundamentals-que-es-un-azure-app-service-plan-y-para-que-sirve/)

![5](img/5.png)

## Es un servicio **PAAS (Platform as a Service)**

![10](img/10.png)

Servicio **basado HTTP** (Protocolo de transferencia de datos a trav茅s de internet, *Hypertext Transfer Protocol*); define la sint谩xis y sem谩ntica de la **comunicaci贸n entre aplicaciones web**. Puede desarrollarlo en su lenguaje preferido, ya sea. NET, .NET Core, Java, Ruby, Node.js, PHP o Python. Las aplicaciones se ejecutan y escalan f谩cilmente en los entornos Windows y Linux.

## Compatibilidad integrada con el escalado autom谩tico

Permite **hospedar aplicaciones web, API de Rest y back-ends para dispositivos m贸viles**

Alojar mi soluci贸n en una **Azure App Web** permite el **escalado de recursos** de forma manual o autom谩tica

Azure Portal proporciona **integraci贸n e implementaci贸n** continuas listas para usar con A**zure DevOps, GitHub, Bitbucket, FTP o un repositorio de GIT local** en el equipo de desarrollo

El **back-end** de la soluci贸n normalmente se encuentra alojado en un repositorio de c贸digo (**Azure App Service me permite hacerlo de forma nativa ya que se encuentra v铆nculado a Azure DevOps y aparte es compatible con GitHub y BitBucked**)

En el repositorio es donde se lleva a cabo el **ciclo de vida** (SDLC, *software development life cycle*)

## Ranuras de implementaci贸n 

Las ranuras de implementaci贸n son a**plicaciones activas con sus propios nombres de host**. Los elementos de contenido y configuraciones de aplicaciones se pueden intercambiar entre dos ranuras de implementaci贸n, incluida la ranura de producci贸n.

Las **Ranuras de implementaci贸n** permiten gestionar de una forma m谩s efectiva las subidas de versiones al entorno de producci贸n. Cada vez que actualizamos la web, hacen falta una serie de procesos que pueden hacer que nuestro servicio dejen de funcionar durante dicha actualizaci贸n. Debido al **SLA de Windows (Service Level Agreement)**, es necesario asegurar la alta disponibilidad del servicio

Para poder tener un **App Service** es indispensable tener un **App Service Plan** del que colgar谩 mi App; Al igual que los recursos deben estar vinculados a un **resource group**

Un **Azure App Service Plan** es un conjunto de recursos necesarios para tener una aplicaci贸n web (es como una m谩quina de la que tira mi app web pero m谩s complejo)

**No se pueden mezclar las aplicaciones Windows y Linux** en el mismo plan de App Service, sin embargo **s铆 en el mismo grupo de recursos**

![6](img/6.png)

[Enlace a documentaci贸n Microsoft](https://docs.microsoft.com/es-es/azure/app-service/overview-hosting-plans)

## Tarifas o planes

- Los **App Service Plan** deben tener una tarifa en funci贸n de la cual se desplegar谩 la **Web App** y que especifica la cantidad de tiempo/peticiones que puede alcanzar. Los distintos planes se serparan seg煤n la utilidad que tenga la aplicaci贸n web:
    - **Proceso compartido**: tanto **Gratis** como **Compartido** comparten grupos de recursos de sus aplicaciones con las aplicaciones de otros clientes. Estos planes asignan cuotas de CPU a cada aplicaci贸n que se ejecuta en los recursos compartidos, y los recursos **no se pueden escalar horizontalmente**

    - **Proceso dedicado (Dedicated compute)**: Los planes **B谩sico, Est谩ndar, Premium, PremiumV2 y PremiumV3** ejecutan aplicaciones en VM de Azure dedicadas. Solo las aplicaciones del mismo plan de App Service comparten los mismos recursos de proceso. Cuanto mayor sea el plan, m谩s instancias de VM estar谩n **disponibles para la escalabilidad horizontal**

    - **Aislado**: Este nivel ejecuta m谩quinas virtuales de Azure dedicadas en instancias de Microsoft Azure Virtual Network. **Proporciona aislamiento de red, adem谩s de aislamiento de proceso a sus aplicaciones**. Proporciona **las m谩ximas posibilidades de escalabilidad horizontal**

    - **Consumo**: este plan solo est谩 disponible para **Function Apps**. Escala las funciones de manera din谩mica seg煤n la carga de trabajo

(Los planes pueden ser modificados en cualquier momento seg煤n los requerimientos, ya que una vez consumido su l铆mite, la aplicaci贸n deja de funcionar)

## Razones por las que cambiar de tarifa

- La aplicaci贸n **consume muchos recursos**

- Quiere **escalar la aplicaci贸n** independientemente de las dem谩s aplicaciones del plan existente

- La aplicaci贸n **necesita recursos de una regi贸n geogr谩fica diferente**

![7](img/7.png)

Muchos **Web Apps** pueden estar contenidos dentro de un mismo **App Service Plan**, aunque puede haber problemas si abusamos. Lo mismo con las **Azure Function**

Un plan de **App Service define un conjunto de recursos de proceso para que una aplicaci贸n web se ejecute**

Cuando se crea un plan de App Service **en una regi贸n determinada**, se crea un conjunto de **recursos de proceso para ese plan en dicha regi贸n**. Todas las aplicaciones que coloque en este plan de App Service se ejecutan en estos recursos de proceso seg煤n lo definido por el plan de App Service

## Cada plan de App Service define:
- Regi贸n (oeste de EE. UU., este de EE. UU., etc.)
- N煤mero de instancias de VM
- Tama帽o de las instancias de VM (peque帽o, mediano, grande)
- Plan de tarifa (Gratis, Compartido, B谩sico, Est谩ndar, Premium, PremiumV2, PremiumV3 y Aislado)

![8](img/8.png)

## El SDLA de nuestra soluci贸n (IMPLEMENTACI脫N)

Hay varios "caminos" para compilar el c贸digo del repositorio y llevarlo a mi App Service, aunque lo l贸gico es **hacerlo de una forma automatizada**. Lo ideal es que sea compilado en la nube con herramientas como **Azure DevOps** y dem谩s antes mencionados para verificar que puede ser compilado en cualquier ordenador al margen del equipo o m谩quina que use el desarrollador (**que pueda tener instalados paquetes que el resto de usuarios finales no**)

Tambi茅n llamado **CI CD (Contincontinuous integration and continuous delivery)** ya que todo el **SDLA** se produce en la nube

## Ranuras de implementaci贸n

El uso de **ranuras de implementaci贸n** permite que los usuarios sigan utilizando la soluci贸n sin interrupciones de actualizaci贸n exponiendo un **duplicado temporal de la soluci贸n** durante el transcurso de la actualizaci贸n para que sea consumida en su lugar

Siempre que sea posible, use ranuras de implementaci贸n al implementar una nueva compilaci贸n de producci贸n. Cuando se usa un nivel de plan de App Service Est谩ndar o superior, puede implementar la aplicaci贸n en un entorno de ensayo y, a continuaci贸n, intercambiar los espacios de ensayo y producci贸n. La operaci贸n de intercambio prepara las instancias de trabajo necesarias para que coincidan con la escala de producci贸n, lo que elimina el tiempo de inactividad.

![9](img/9.png)


## Autenticaci贸n y proveedores 

Es posible a帽adir un **factor de autenticaci贸n** a nuestra App Service para la que el **usuario o programa** que quiera usar mi aplicaci贸n tenga que pasar por un **proveedor de autenticaci贸n** (ya que se hace de forma externa y este retorna la informaci贸n a mi app)

Tambi茅n se puede especificar un comportamiento de **autorizaci贸n** para otorgar permisos y que dependiendo de este, mi soluci贸n se muestre de una forma u otra, o que permita o no ciertos comportamientos

**Azure tiene autenticaciones integradas** que sin necesidad de que nosotros administremos, se comunican con los **proveedores**

- Proveedores que se encuentran de **forma predeterminada** en la plataforma:
    - **Plataforma - Punto de conexi贸n**
    - Microsoft - `/.auth/login/aad`
    - Facebook - `/.auth/login/facebook`
    - Google - `/.auth/login/google`
    - Twitter - `/.auth/login/twitter`

(Cuando habilita la autenticaci贸n y autorizaci贸n con uno de estos proveedores, **su punto de conexi贸n de inicio de sesi贸n est谩 disponible** para la autenticaci贸n de usuarios y para la validaci贸n de tokens de autenticaci贸n del proveedor. Se puede proporcionar a los usuarios cualquier n煤mero de estas opciones de inicio de sesi贸n)

## Funcionamiento

El m贸dulo de autenticaci贸n y autorizaci贸n se ejecuta **en el mismo espacio aislado que el c贸digo de la aplicaci贸n**

Cuando est谩 habilitado, **cada solicitud HTTP entrante** pasa a trav茅s de 茅l **antes de que el c贸digo de la aplicaci贸n lo controle**

Este m贸dulo **controla varios aspectos de la aplicaci贸n**:

- Autentica a los ususarios con el proveedor especificado

- Valida, almacena y actualida los tokens

- Administra la sesi贸n autenticada

- Inyecta informaci贸n de identidad en los encabezados de la solicitud

> NOTA: el m贸dulo **se ejecuta por separado del c贸digo** de la aplicaci贸n y se configura mediante **par谩metros de la aplicaci贸n. **No se necesitan SDK, idiomas espec铆ficos o cambios en el c贸digo**

> NOTA: En **linux y los contenedores**, el m贸dulo de autenticaci贸n y autorizaci贸n se ejecuta en un **contenedor independiente** aislado de la aplicaci贸n. Puesto que no se ejecuta en proceso, **no es posible la integraci贸n directa con plataformas de lenguajes espec铆ficas**

## Flujo de autenticaci贸n

Es el mismo **para todos los proveedores**, pero var铆a en dunci贸n de si queremos **iniciar sesi贸n con el SDK del proveedor**

## Porqu茅 usar la autenticaci贸n integrada

La caracter铆stica de autenticaci贸n integrada para App Service y Azure Functions **puede ahorrar tiempo y esfuerzo**, ya que proporciona autenticaci贸n integrada con **proveedores de identidades federados**, lo que le permite centrarse en el resto de la aplicaci贸n

- Azure App Service le permite integrar numerosas funcionalidades de autenticaci贸n en su aplicaci贸n web o API sin implementarlas usted mismo

- Est谩 integrado directamente en la plataforma y **no requiere ning煤n idioma, SDK, experiencia en seguridad** ni ning煤n c贸digo en particular

(Existen otros con los que podemos autenticar y que tambi茅n se basan en **OAuth o Open Authoritation**, que es un **est谩ndar abierto** que define c贸mo, de forma segura, se debe realizarse la autorizaci贸n de una API para aplicaciones web, m贸viles o de escritorio)

Es posible **configurar el App Service para que pueda utilizar otros proveedores** que cumplan con el **OAuth**, dando la opci贸n a los usuarios de que se idenfiquen mediantes otras plataformas

Azure App Service permite esta configuraci贸n de forma **autom谩tica y m谩s r谩pida que de la manera convencional**

La autenticaci贸n se lleva a cabo **mediante cookies** que transmiten la informaci贸n de forma **Segura** mediante el proveedor y nuestra Web App

![11](img/11.png)

Las **conexiones h铆bridas** permiten a nuestra aplicaci贸n web trabajar con **bases de datos que por motivos de seguridad, pol铆ticas u otros se encuentren On-premise** (No est谩 disponible en todos los **planes de SKU**)

En la App Service se puede controlar el acceso **mediante determinadas APIs o VPNs (filtr谩ndo cu谩les pueden acceder)** e incluso controlar las
**salidas de datos** de mi aplicaci贸n

![12](img/12.png)

>> [Vuelve al 脥ndice o descansa y t贸mate un algo](#铆ndice)馃槑

---
---
---

# M贸dulo 2
# (Implementaci贸n de Azure Functions)
>>`<Clase del 01/07/2022>`

## Qu茅 es un Azure Function

[Enlace a documentaci贸n Microsoft](https://docs.microsoft.com/es-es/azure/azure-functions/functions-overview)

Es una soluci贸n que permite escribir menos c贸digo, mantener menos infraestructura para ahorrar costos. En lugar de preocuparse por implementar y mantener servidores (**Serverless**), la infraestructura en la nube proporciona todos los recursos actualizados necesarios para mantener las aplicaciones en ejecuci贸n

Como desarrolladores, nos centramos en los fragmentos de c贸digo que importan y Azure Functions se ocupa del resto de forma secundaria

En definitiva, permiten que se ejecute **una determinada l贸gica ante una acci贸n que ocurra**

Cada Azure Function debe tener por fuerza **un desencadenador**

![13](img/13.png)

- Ejemplos de uso:

    - *Integrar sistemas*: es decir, **comunicaci贸n entre distintos sistemas** mediante peque帽os trozos de c贸digo sin tener que levantar proyectos completos de desarrollo o m谩quinas virtuales (**una funcionalidad muy concreta**)
    
    - *IoT o Internet de las cosas*: para realizar la **comunicaci贸n v铆a internet con dispisitivos** o electrodom茅sticos por ejemplo, ya sea para supervisar u ordenar

    - *Implementaci贸n de microservicios*: en lugar de tener un proyecto gigantesco, **separo el c贸digo en peque帽as partes cada una con una funcionalidad** (estas 煤ltimas ser铆an funcions) y permiten una actualizaci贸n modular/alta tolerancia a fallos

    - *Procesamiento de im谩genes o pedidos*: para **comprimir im谩genes o lo que se considere** necesario seg煤n el caso

    - *Desencadenadores*: pueden ser utilizadas como **triggers** que desencadenen sucesos

![14](img/14.png)

## Qu茅 es Azure Logic App

![15](img/15.png)

Utiliza conectores para llevar a cabo un flujo de trabajo que le especifiquemos

## Qu茅 es WebJobs

![16](img/16.png)

Permite meter una peque帽a funcionalidad que se ejecute cada cierto tiempo o ante cualquier determinada situaci贸n **dentro de una aplicaci贸n web .NET**

## Hospedaje de Azure Functions

Tarifas de planes seg煤n la carga de trabajo que tenga que sorportar nuestra App Service:

![17](img/17.png)

![18](img/18.png)

**Plan de Consumo**: tarifa predeterminada que se encarga de escalar los recursos (sin tener nosotros que definir el c贸mo se escala, ya que es el mismo Azure el que decide seg煤n la situaci贸n) en funci贸n de las llamadas que reciba por parte de los usuarios. Tomar谩 m谩s recursos cuando los necesita y los reducir谩 cuando no sean requeridos de forma din谩mica

**Plan Premium**: tambi茅n funciona bajo demanda pero tiene unas caracter铆siticas m谩s avanzadas que el plan de consumo. No tiene **retardo inicial** en responder a las llamadas ya que siempre est谩 preparado para devolver la informaci贸n necesaria

**Plan de App Service**: colgamos la Azure Function **como si fuera una App Service m谩s**, y esta escalar谩 o desescalar谩 en funci贸n de la carga global que tenga el App Service

**RESUMEN**: En el plan de **consumo** y en el **premium**, es Azure quien decide el escalado seg煤n el consumo mediante un **controlador de escala** (en funci贸n del n煤mero de eventos, del consumo de recursos, el n煤mero de instancias, etc)

---

Si elegimos la tercera tarifa, el Plan App Service:

![19](img/19.png)

Si no configuramos el **Always On**, la App Service solo empezar谩 una funci贸n tras un desencadenante (en algunos casos, puede no ser necesario; dependiendo de los requisitos)

Las Azure Functions pueden **necesitar cuentas de almacenamiento** para guardar informaci贸n de seguimiento, de sincronizaci贸n, de seguridad o de determinadas cosas que se requieran

## Escalado de Azure Functions

![20](img/20.png)

Evidentemente, podemos configurar el **n煤mero de instancias m谩xima** (llamadas o solicitudes) por segundo para que el servicio no colapse o se dispare el costo

El escalado se mide mediante el **n煤mero de instancias**, no de la **potencia**

![23](img/23.png)
![24](img/24.png)

## Partes de un Azure Function

![21](img/21.png)

En nuestros proyectos **.NET**, adem谩s de un **.exe** o un **.dll**, debemos tener un fichero **json con la configuraci贸n** que defina la **Azure Function**

![22](img/22.png)

**Azure Function** ofrece un **contexto de ejecuci贸n**, al igual que cuando ejecutamos una aplicaci贸n de escritorio tenemos el contexto de un sistema operativo. Esto quiere decir que, entre nuestra Azure Function y nuestro sistema operativo, se generan una **serie de funcionalidades** cuando **levantamos** nuestra Azure Function relacionadas con su finalidad y que ayudan a que esta se lleve a cabo. La duraci贸n de estas funcionalidades termina con la finalizaci贸n del prop贸sito del Azure Funcion (componentes configurados para permitir el objetivo de la function que nacen y mueren junto con esta)

**Todas las funciones** que se encuentran dentro de **un mismo proyecto, comparten el mismo plan de precios** por fuerza. Tambi茅n comparten **m茅todos de implementaci贸n e incluso la misma versi贸n de tiempo de ejecuci贸n**

Esto sirve para **administrar las Azure Functions de forma conjunta**

![25](img/25.png)

Azure Function no solo es compatible con **.NET**

Tambi茅n lo es con **Node.js o Python** por ejemplo; es un servicio abierto a todo tipo de lenguajes y frameworks

![26](img/26.png)

Las **Azure Functions** permiten a los desarrolladores trabajar en nuestro equipo con nuestras herramientas elegidas y luego conectarlas con **Azure cuando sea necesario**

Es decir, tenemos la opci贸n de **desarrollo local o en la nube** (es importante recordar que la compilaci贸n debe llevarse a cabo en la nube para evitar el problema antes mencionado sobre los paquetes del equipo local)

## Creaci贸n de desencadenadores y enlaces

![27](img/27.png)

El concepto es pr谩cticamente el mismo que con los **triggeres** (un conector configurado), excepto que en el caso de las **Azure Function** el desencadenador es a **nivel de c贸digo** 

En dicho c贸digo, se define **c贸mo se invoca ese desencadenador** y **cada funci贸n debe estar relacionada con un desencadenador** que la haga ejecutarse)

No se puede tener un **Azure Function** sin un desencadencadenador

---

Tambi茅n podemos tener **enlaces o bindings** que nos permite **vincular una funci贸n con un determinado recurso (cola de almaceamiento, tabla de storage, blob storage, base de datos,...)**

Estos **enlaces pueden ser de entrada, salida o ambos**

Los enlaces sirven para **simplificar el c贸digo para determinar qu茅 va a ocurrir** (si quiero tener una determinada funci贸n que se dispare cuando un usuario introduzca un fichero en un blob, necesito conectarme con ese blob para poder tener acceso a ese nuevo fichero; de la forma tradicional, ser铆a necesario un bloque de c贸digo para llevarlo a cabo; sin embargo, los **enlaces** simplifican el desarrollo ahorrando el c贸digo y sustituy茅ndolo con variables relacionadas que permiten el acceso de forma **simplificada**)

Yo puedo tener en una misma **Function** varios **enlaces**

## Definir desencadenadores y enlaces

![28](img/28.png)

En el caso de **bibliotecas de C# y Java**, se definen mediante **atributos** (m茅todos y par谩metros)

En el caso de **JavaScript/PowerShell/Python/TypeScript**, se definen dentro del **fichero JSON** como en el ejemplo de la imagen 

Es decir, en el caso de **.NET y Java**, no va a ser necesario que toquemos ni redactemos el fichero **JSON** ya que van a ser las mismas herramientas del framework las que se encargaran de crearlo y configurarlo (aunque hay que tener en cuenta que el fichero existe dentro del proyecto y se define autom谩ticamente a ra铆z del c贸digo que dise帽emos)

(Si ser铆a necesario tocarlo en **los dem谩s frameworks** como se expecifica arriba)

## Direcci贸n de enlaces

![29](img/29.png)

Los enlaces permiten **vincular** nuestras Azure Functions con algunos **servicios de Azure**

La vinculaci贸n puede ser de **entrada, salida o ambas** (in, out o inout)

**RESUMEN: desencadenador (desencadena la func贸n) y enlace (lo que necesita la funci贸n para llevar a cabo su objetivo)**

## Ejemplo 1
![30](img/30.png)

Este es un ejemplo de uso disparador/enlace (aqu铆 vemos un JSON)

En el caso de la imagen **Azure Queue Storage** es el desencadenador y **Azure Table Storage** el enlace o binding, lo que significa que cada vez que alguien introduzca informaci贸n en la **Queu Storage**, va a a帽adirse una fila en la **Table Storage**

**Azure Table Storage** es un servicio que nos permite guardar informaci贸n de forma **tabular** (como una hoja de excel)

## Ejemplo 2
![31](img/31.png)

Otro ejemplo de uso disparador/enlace en C# (aqu铆 no es necesario configurar el JSON ya que este se crea autom谩ticamente seg煤n el c贸digo que especifiquemos, por lo que en el ejemplo analizamos el c贸digo C#)

## Otros Ejemplos

![32](img/32.png)
![33](img/33.png)

## Conexiones con cuentas de almacenamiento

![34](img/34.png)
![35](img/35.png)

> **NOTA: el concepto de identidad se explica m谩s adelante junto al tema de seguridad**

## Examinando c贸digo


Una **Queue o cola** es una serie de mensajes apilados que al ser recibidos y cumplir con su funci贸n, desaparecen

Si el **mensaje de la cola** intenta su cometido tres veces sin conseguirlo, pasa a una **poison queue**

Cuando a帽adimos un mensaje a la **queue**, podemos indicarle el **tiempo de expiraci贸n**. Es decir, si despu茅s de dicho tiempo el mensaje no es le铆do, desaparecer谩 autom谩ticamente

## Implementaci贸n de Durable Functions o Funciones Durareras

![36](img/36.png)

Un **patr贸n de dise帽o** es la definici贸n de c贸mo resolver un problema mediante un programa

Las **Durable Function** son b谩sicamente **Functions** cuyas ejecuciones son **durables en el tiempo** (es decir, que no se completen de forma instant谩nea, sino que necesita por ejemplo esperar respuestas o aprobaciones para finalizar)

Las **Durable Function**, para no ocupar recursos mientras sucede la espera, **se desactiva**

![37](img/37.png)


## Ejemplos de Patrones existentes:

![38](img/38.png)


Ejemplo de procesamiento del pedido (PATR脫N DE FUNCIONAMIENTO):

    F1: 驴El cliente est谩 al corriente de los pagos? S铆

    Almacenamiento: Guarda que est谩 al corriente de los pagos

    F2: 驴Hay suficiente mercanc铆a en el almac茅n? S铆

    Almacenamiento: Reserva la mercanc铆a

    F3: 驴Est谩 preparado el pedido?

    Almacenamiento: S铆, el pedido est谩 prepadado

    F4: Llama a la empresa de mensajer铆a para que venga a recogerlo

**Azure Durable Function** se encarga de que el ejemplo anterior funcione con coherencia

El **tiempo total** en este caso es la suma de los tiempos que tarda cada parte en acabar

![39](img/39.png)

Ejemplo de procesamiento de pedido EN PARALELO (pedido con mercanc铆a de cada uno de los almacenes):
    
    La F1 consulta la existencia de la mercanc铆a necesaria para realizar el pedido completo

    La F2 lanza una tarea a cada uno de los almacenes para que preparen el producto del pedido que les corresponde

    La F3 llama al servicio de recogida

El **tiempo total** en este caso la suma de los componentes que m谩s tiempo tardan en cada fase, dado que el pedido no puede ser completado hasta que todas las partes han hecho su trabajo

![40](img/40.png)

    En este caso, lanzo una funci贸n pero se habilita una opci贸n para preguntar por el estado de dicha funci贸n

![41](img/41.png)

    En este caso, lanzo una funci贸n y compruebo su estado e incluso puedo llegar a cancelarla o pausarla

![42](img/42.png)

    En este caso, lanzo una Durable Function y esta espera a ser aprobada o denegada (se encuentra desactivada durante el proceso)

## Tipos de Durable Function

![43](img/43.png)

- **Funci贸n Orquestador**: se encarga de hacer que todo funcione

- **Funci贸n de Actividad**: las distinas functions que se ejecutan, los F anteriores

- **Funci贸n de Entidad**: los elementos con los que se comunican, donde se guarda la informaci贸n

- **Funci贸n Cliente**: el que solicita la ejecuci贸n del proceso

![44](img/44.png)

![45](img/45.png)

## Centros de tareas

![46](img/46.png)

Dado que las **Azure Functions** se pueden alargar en el tiempo (**Durable Function**), es necesario alg煤n tipo de almacenamiento de informaci贸n

Cuando se queda pendiente de volver a ser activada, la informaci贸n se guarda en el **Azure Storage** en el cual se encuentra el centro de tareas

En definitiva, **un centro de tareas**, es un conjunto de recursos de **Azure** necesarios para el correcto funcionamiento de las **Azure Functions**. Estos recursos son:

En el Azure Storage, se encuentra el centro de tareas cuyos recursos son:
- Una o m谩s colas de control
- Una cola de elementos de trabajo
- Una tabla de historial
- Una tabla de instancias
- Un contenedor de almacenamiento que contiene uno o varios blobs
- Un conetenedor de almacenamiento que contiene cargas de mensajes grandes, en caso de que sea necesario

El nombre del **centro de tareas** se declara en el archivo **json**
![47](img/47.png)

## Orquestador 

![48](img/48.png)

Cada orquestador tiene un **identificador 煤nico** por el cu谩l podemos buscar

Se encarga de concatenar los procesos

![49](img/49.png)

## Timer

Existen mecanismos por los que podemos hacer a la Durable Function deje de hacer nada durante un tiempo, pero sin consumir recursos

El orquestador genera un mensaje dentro del tiempo que queramos, que reactive la durable function

![50](img/50.png)

## C贸mo se lleva a cabo dicha espera:

![51](img/51.png)
![52](img/52.png)

## Otro ejemplo ser铆a que en lugar de esperar un tiempo o que termine un trabajo, espere una aprobaci贸n:

![53](img/53.png)

## Esperar a eventos externos:
![54](img/54.png)

>> [Vuelve al 脥ndice o date una ducha fr铆a](#铆ndice)馃槑

---
---
---

# M贸dulo 3: 
# (Desarrollo de soluciones que usan Blob Storage)
>>`<Clase del 04/07/2022>`

![55](img/55.png)

Las cuentas **Azure Storage** internamente tienen una serie de **subservicios**:
- Archivos **(File Storage)**
- **Blob Storage**
- Tablas **(Table Storage)**
- Colas **(Queue Storage)**

Hay otro **Servicio de almacenamiento llamado Discos**, pero hacen referencia a los discos que utilizamos para levantar m谩quinas virtuales

## Tipos de Blob

- Basados en **bloque** (Block Blob)
- Basados en **p谩ginas** (Page Blob)
- Basados en **anexos** (Append Blob)

## Tarifas de las Azure Storage

![56](img/56.png)

## Esquema de un Azure Storage (para los sistemas BLOB)

![57](img/57.png)

## Seguridad en un Azure Storage 

![58](img/58.png)

La seguridad a **nivel global** en Azure est谩 basada en **Azure Active Directory (AD)**, que se encarga de comprobar los permisos mediante **Control de Acceso Basado en roles (RBAC)**

Dado que mediante el uso de Azure Storage, se produce **tr谩nsito de datos (descarga o subida)**, estos se protegen mediante **cifrado**

El **cifrado** no se puede desactivar y est谩 activo para **todos los datos independientemente del plan de servicios**

## Redundancia en Azure Storage

Redundancia primaria:
- Redundancia local **LRS**: Replica de los datos en **tres sitios** distintos **dentro del mismo centro de datos**
- Reduncia de zona **ZRS**: Replica de los datos en **las otras zonas disponibles de la regi贸n**

Redundancia secundaria:
- Redundancia geogr谩fica **GRS**: Replica **LRS** de los datos en **otra geograf铆a**
- Redundancia de zona geogr谩fica **GZRS**: Replica **LRS** de los datos **en otras zonas disponibles de la regi贸n, adem谩s una r茅plica extra en otra geograf铆a**

> NOTA: Las **redundancias secundarias** SOLO PERMITEN LEER, **no escribir** (Si mi sistema principal cae o es destruido, puedo recuperar los datos de la redundancia secundaria, pero no podr铆a modificar los datos de all铆)

![60](img/60.png)
![61](img/61.png)
![62](img/62.png)
![63](img/63.png)

[Enlace a documentaci贸n Microsoft](https://docs.microsoft.com/es-es/azure/storage/common/storage-redundancy)

![59](img/59.png)

## Exploraci贸n del ciclo de vida

![64](img/64.png)

Dependiendo de **la frecuencia con la que se accede a los datos**, elegimos diferentes **niveles de acceso** para nuestro Blob Storage que difieren en **latencia y costo**

Estos niveles o **lyfe cycle policies** son:
- Frecuente (HOT)
- Espor谩dico (Cool)
- De Archivo (Archive)

> NOTA: solo las cuentas de **prop贸sito general v2 (GENERAL PURPOSE V2)** soportan las pol铆ticas del ciclo de vida

![65](img/65.png)

Las **directivas de administraci贸n del ciclo de vida** son en definitiva:
- La elecci贸n del tipo de **nivel** (**frecuente (HOT), espor谩dico (Cool) o de archivo (ARCHIVE)**) y el **intercambio entre estos** seg煤n vaya necesitando el almacenamiento (seg煤n cambie la frecuencia de uso)

- La eliminaci贸n del almacenamiento al final de su ciclo de vida o uso (**muere**)

- Definir una **serie de reglas** que se ejecutan **una vez al d铆a como m铆nimo** y que decicen lo mejor para el uso de dichos ficheros
(ejemplo, si tengo un servicio cuyo acceso a ciertos archivos crece de pronto, una regla detectar谩 esta anomal铆a y cambiar谩 de nivel el almacenamiento para que los usuarios reciban los datos con mayor rapidez)


> NOTA: Por defecto, el almacenamiento se encuentra en el nivel **frecuente**
> NOTA: Puede realizarse la transici贸n de informaci贸n entre niveles en cualquier momento como si de un escalado de recursos se tratase

![66](img/66.png)

## Directivas

![67](img/67.png)

Una **directiva es un conjunto de reglas** y cada una de estas tiene a su vez **un conjunto de filtros y acciones**

Una **ruta** es la **url con la que accedo a la informaci贸n en almacenamiento**
(ejemplo, https://cuentadealmacenamiento.blob.core.windows.net/carpeta/imagenes/ficheroenelblob.png)

Un **Filtro** define la ruta a la cual afecta **una determinada regla**
(ejemplo, en la ruta anterior, puedo ordenar mediante el filtro que la regla afecte al contenido que se encuentre dentro de la **carpeta**; es decir, a todos los ficheros que se encuentren dentro de la ruta https://cuentadealmacenamiento.blob.core.windows.net/carpeta/...)

Las **acciones se aplican al conjunto filtrado de archivos o ficheros** antes mencionado. Todos los **objetos que se encuentren dentro de la url filtrada**, se comportaran seg煤n la **regla especificada** (ejemplo, los objetos del filtro visto arriba, se guardar谩n en nivel espor谩dico)

## C贸mo se definen las reglas de un ciclo de vida

Se definen mediante un **JSON**

![68](img/68.png)
![69](img/69.png)

Los **par谩metros para definir una directiva son**:
- name
- enable
- type
- definition

Este tipo de **implementaci贸n se lleva a cabo en Azure CLI o en el PowerShell**

## Rehidrataci贸n de un Blob

![70](img/70.png)

Los **archivos** que se encuentran en el **nivel archivo o arquive** (el nivel m谩s bajo), necesitan ser **rehidratados** para poder ser accedidos de nuevo

## Bibliotecas de Azure Storage

Las **clases de .NET** para interactuar de una forma m谩s f谩cil con el Azure Blob Storage

![71](img/71.png)
![72](img/72.png)
![73](img/73.png)

> NOTA: Las propiedades se pueden recuperar mediante el uri solo si el contenedor es p煤blico

>> [Vuelve al 脥ndice o t贸mate un caf茅 por dios](#铆ndice)馃槑

---
---
---

# M贸dulo 4: 
# (Desarrollo de soluciones que usan Azure Cosmos DB)
>>`<Clase del 05/07/2022>`

## Principales ventajas de Azure CosmoDB

![74](img/74.png)
Pretende dar soluci贸n a la necesidad de bases de dato **NoSQL** (no sequencial), ya que dentro del porfolio de recursos que ofrece Azure, ya est谩n cubiertas las bases de datos **SQL** mediante otros servicios

**Azure CosmosDB** es una marca en la cual se engloba **tecnolog铆a NoSQL** que comparten ciertas caracter铆sticas:
- **Replica Global autom谩tica** en varias regiones en Azure (en caso de error de cualquier tipo, podemos programar manual o autom谩ticamente que se produzca una conmutaci贸n, es decir, que el sistema salte autom谩ticamente a otra regi贸n para que no se produzca interrupci贸n en mi servicio)
- **Niveles de coherencia variados**, dado que los datos se encuentran replicados como se menciona anteriormente, deben estar todos actualizados para poder ver la misma informaci贸n. Esto es denominado **coherencia** en cuanto a bases de datos y podemos elegir **el nivel** que 

- **Baja latencia** asegurada, medida de tal forma que las solicitudes de **lectura y escritura de informaci贸n, son inferiores a 10ms**

- **Escalabilidad horizontal el谩stica** al igual que en otros servicios, autom谩ticamente me concede m谩s potencia si lo necesitamos

## Jerarqu铆a de recursos de CosmosDB

![75](img/75.png)

1. Primero es necesario tener **una cuenta de Azure Cosmos**
- **Azure Cosmos es el servicio como tal** y nos va a permitir establecer una configuraci贸n que especifique la forma de uso que vamos a hacer de este

2. Es posible crear **una o varias bases de datos** en la cuenta de **Azure Cosmos** (una analog铆a de un **namespace** y una **unidad de administraci贸n para todos los contenedores desplegados dentro de esa base de datos**)

3. Varios servicios en Azure se denominan **Contenedores**, pero estos son diferentes unos de otros. En este caso son **Contenedores de Azure CosmoDB**, la **unidad de escalabilidad, del rendimiento** y del  **almacenamiento** (a ra铆s de ellos vamos a poder medir el rendimiento de Azure CosmosDB y va a significar el coste de lo que aprovisionemos; Si queremos m谩s potencia, **aumentamos el rendimiento DEL CONTENEDOR**)

4. En **funci贸n de la API** que se use (la tecnolog铆a con la que despleguemos la cuenta), **los elementos de Azure Cosmos** pueden ser **documentos** en una colecci贸n, **filas** en una tabla, un **nodo** o un **borde en un grafo** (dicha tecnolog铆a no puede ser modificada una vez creada, pero s铆 podemos crear otras cuentas de **Azure Cosmos** con otras distintas)

![76](img/76.png)

```
     Cuenta de Azure Cosmos
               |
         Base de Datos
               |
           Contenedor
               |
  Colecci贸n, tabla, grafo, ...
               |
Elementos (documentos, filas, ...)
```

**Adicionalmente** el container almacena otros datos como **procedimientos almacenados, funciones definidas por el usuario, desencadenadores, conflictos y dem谩s** pero que no entran dentro de esta certificaci贸n conocerlos

## Exploraci贸n de niveles de coherencia

![77](img/77.png)

La coherencia entonces hace referencia a **la sincronizaci贸n de informaci贸n entre los distintos accesos**

La **Coherencia** dentro de CosmosDB se miden en 5 niveles de **mayor a menor coherencia**:

- **Alta o Fuerte** (Strong): Cuando una operaci贸n de escritura se realiza en la base de datos principal, se replica en los instancias de r茅plica. La operaci贸n de escritura no se confirma (y est谩 visible) en la base de datos principal hasta que todas las r茅plicas han confirmado

- **Obsolescencia limitada** (Bounded stanless): Este nivel es similar al anterior. Su principal diferencia es que se puede configurar c贸mo pueden estar los documentos obsoletos dentro de las r茅plicas. El t茅rmino obsolescencia significa la cantidad de tiempo (o el n煤mero de versiones) que un documento de una r茅plica puede estar detr谩s del documento principal

- **Sesi贸n** (Session): Este nivel garantiza que una sesi贸n de usuario todas las operaciones de lectura y escritura son coherentes. En la sesi贸n de usuario, todas las operaciones de lectura y escritura son monot贸nicas y est谩 garantizado que son coherentes en las instancias principal y de la r茅plica

- **Prefijo coherente** (Consistent prefix): Este nivel tiene una coherencia flexible, pero garantiza que cuando las actualizaciones se muestren en las r茅plicas, lo har谩n en el orden correcto (es decir, como prefijos de otras actualizaciones) y sin espacios

- **Ocasional** (Eventual): Este nivel tiene la coherencia m谩s flexible y esencialmente confirma de inmediato todas las operaciones de escritura que se realicen en la base de datos principal. Las transacciones de r茅plica se controlan de forma asincr贸nica y, eventualmente (con el tiempo), ser谩n coherentes con la base de datos principal. Este nivel es el que tiene el mejor rendimiento, ya que la base de datos principal no necesita esperar hasta que se confirmen las r茅plicas para finalizar sus transacciones

> NOTA: Cu谩nto **menor coherencia**, mayor la **disponibilidad**, menor la **latencia** y **rendimiento** m谩s alto

![78](img/78.png)

>> [Vuelve al 脥ndice o descansa un rato la vista](#铆ndice)馃槑

---
---
---

# M贸dulo 5: 
# (Implementaci贸n de soluciones de infraestructura como servicio)
>>`<Clase del x/07/2022>`


>> [Vuelve al 脥ndice o sal con los amigos un rato](#铆ndice)馃槑

---
---
---

# M贸dulo 6: 
# (Implementaci贸n de la autenticaci贸n y autorizaci贸n de usuarios)
>>`<Clase del x/07/2022>`


>> [Vuelve al 脥ndice o haz una marat贸n de una serie](#铆ndice)馃槑


---
---
---

# M贸dulo 7: 
# (Implementaci贸n de soluciones en la nube seguras)
>>`<Clase del x/07/2022>`


>> [Vuelve al 脥ndice o date un chapuz贸n si tienes piscina](#铆ndice)馃槑

---
---
---

# M贸dulo 8: 
# (Implementaci贸n de API Management)
>>`<Clase del x/07/2022>`


>> [Vuelve al 脥ndice o 茅chate una siesta](#铆ndice)馃槑

---
---
---

# M贸dulo 9: 
# (Desarrollo de soluciones basadas en eventos)
>>`<Clase del x/07/2022>`


>> [Vuelve al 脥ndice o date una vuelta en moto](#铆ndice)馃槑

---
---
---

# M贸dulo 10: 
# (Desarrollo de soluciones basadas en mensajes)
>>`<Clase del x/07/2022>`


>> [Vuelve al 脥ndice o dale ca帽a a la play](#铆ndice)馃槑


---
---
---

# M贸dulo 11: 
# (Instrumentaci贸n de soluciones para admitir la supervisi贸n y el registro)
>>`<Clase del x/07/2022>`


>> [Vuelve al 脥ndice o vete a la playa a echar la tarde](#铆ndice)馃槑


---
---
---

# M贸dulo 12: 
# (Integraci贸n de almacenamiento en cach茅 y entrega de contenido en las soluciones)
>>`<Clase del x/07/2022>`


>> [Vuelve al 脥ndice o date un respiro por haber llegado al final](#铆ndice)馃槑

>> [ENHORABUENA](https://www.usameme.com/wp-content/uploads/2022/02/congratulations-meme-usameme.jpg) 馃憦 馃憦 馃憦


---
---
---
---
---
---


# Notas personales:
```
M贸dulo2:
- A帽adir ejemplos de decoraci贸n de Azure Functions

- Es necesario una decoraci贸n para que sea una Azure Function

- A帽adir ?name=nombre a la url de la function, a帽ade el nombre a la queue

- Diferencia visual entre binding y triggered en el c贸digo

- Desarrollar el apartado "examinando c贸digo"

```