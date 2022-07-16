`Siento la mala calidad de las imágenes, las capturas de pantalla de las grabaciones son horrorosas!`
`Ánimo con los estudios!!`

# Azure 204 - Developing Solutions for Microsoft Azure

>[Enlace al examen y las rutas de aprendizaje](https://docs.microsoft.com/en-us/learn/certifications/exams/az-204)

>[Enlace a los laboratorios de GitHub](https://github.com/MicrosoftLearning/AZ-204-DevelopingSolutionsforMicrosoftAzure)

>[Comandos de Azure CLI](https://github.com/CristinaSilvan/Microsoft-Azure/blob/main/AZ-204%20(Asscciate)/Comandos%20CLI.md)

>[Respuestas de los QUIZ de clase](https://github.com/CristinaSilvan/Microsoft-Azure/blob/main/AZ-204%20(Asscciate)/Respuestas%20de%20los%20QUIZ.md)

**Conceptos importantes**:
- *Software escalable*: applicación utilizada por infinidad de usuarios (lo opuesto a un software usado por uno o pocos miembros dentro de una misma organización)

- *SDLA o software development life cycle*: El ciclo de desarrollo, compilación, testeo, despliegue, versionamiento y demás que se lleva a cabo en la producción del software y que continua con la actualización del mismo

- *SLA (Service Level Agreement)*: Acuerdo de alta disponibilidad mínima de recursos medido en porcentaje

- *Planes SKU*: planes de tarifa para los diferentes servicios que se ajusta a las necesidades y difieren en los precios

- *Instancias en Azure Functions*: llamadas o solicitudes mediante protocolo hacia un servicio

>> NOTA: Es necesario conocer los distintos planes según lo que ofrecen **(Free (F), Basic (B), Standar (S))**

>> (El plan **Free** no contiene escalado automático)

---
---
---

# Índice

## [Intro](#introducción)
## [Ruta certificación](#ruta-completa-certificación)
## [Esquema módulos](#esquema-de-módulos)

---
---
---

## [Módulo 1: Creación de aplicaciones web](#módulo-1)

## [Módulo 2: Implementación de Azure Functions](#módulo-2)

## [Módulo 3: Desarrollo de soluciones que usan Blob Storage](#módulo-3)

## [Módulo 4: Desarrollo de soluciones que usan Azure Cosmos DB](#módulo-4)

## [Módulo 5: Implementación de soluciones de infraestructura como servicio](#módulo-5)

## [Módulo 6: Implementación de la autenticación y autorización de usuarios](#módulo-6)

## [Módulo 7: Implementación de soluciones en la nube seguras](#módulo-7)

## [Módulo 8: Implementación de API Management](#módulo-8)

## [Módulo 9: Desarrollo de soluciones basadas en eventos](#módulo-9)

## [Módulo 10: Desarrollo de soluciones basadas en mensajes](#módulo-10)

## [Módulo 11: Instrumentación de soluciones para admitir la supervisión y el registro](#módulo-11)

## [Módulo 12: Integración de almacenamiento en caché y entrega de contenido en las soluciones](#módulo-12)

---
---
---

# Introducción

![1](img/1.png)

# Ruta completa certificación

![2](img/2.png)

[AZ-900 Fundamentals](https://docs.microsoft.com/en-us/certifications/exams/az-900)

[AZ-204 Associate](https://docs.microsoft.com/en-us/certifications/exams/az-204)

[AZ-400 Expert](https://docs.microsoft.com/es-es/certifications/exams/az-400)

# Esquema de módulos

![3](img/3.png)
![4](img/4.png)

---
---
---

# Módulo 1
# (Creación de aplicaciones web)
>>`<Clase del 01/07/2022>`

[Enlace a documentación Microsoft](https://docs.microsoft.com/es-es/azure/app-service/)

[Enlace a documentación Microsoft](https://azure.conosur.tech/azurefundamentals-que-es-un-azure-app-service-plan-y-para-que-sirve/)

![5](img/5.png)

## Es un servicio **PAAS (Platform as a Service)**

![10](img/10.png)

- Servicio **basado HTTP** (Protocolo de transferencia de datos a través de internet, *Hypertext Transfer Protocol*); define la sintáxis y semántica de la **comunicación entre aplicaciones web**

- Permite **hospedar aplicaciones web, API de Rest y back-ends para dispositivos móviles**

- Alojar mi solución en una **Azure App Web** permite el **escalado de recursos** de forma manual o automática

- El **back-end** de la solución normalmente se encuentra alojado en un repositorio de código (**Azure App Service me permite hacerlo de forma nativa ya que se encuentra vínculado a Azure DevOps y aparte es compatible con GitHub y BitBucked**)

- En el repositorio es donde se lleva a cabo el **ciclo de vida** (SDLC, *software development life cycle*)

- Las **Ranuras de implementación** permiten gestionar de una forma más efectiva las subidas de versiones al entorno de producción. Cada vez que actualizamos la web, hacen falta una serie de procesos que pueden hacer que nuestro servicio dejen de funcionar durante dicha actualización. Debido al **SLA de Windows (Service Level Agreement)**, es necesario asegurar la alta disponibilidad del servicio

- Para poder tener un **App Service** es indispensable tener un **App Service Plan** del que colgará mi App; Al igual que los recursos deben estar vinculados a un **resource group**

- Un **Azure App Service Plan** es un conjunto de recursos necesarios para tener una aplicación web (es como una máquina de la que tira mi app web pero más complejo)

![6](img/6.png)

[Enlace a documentación Microsoft](https://docs.microsoft.com/es-es/azure/app-service/overview-hosting-plans)

## Tarifas o planes

- Los **App Service Plan** deben tener una tarifa en función de la cual se desplegará la **Web App** y que especifica la cantidad de tiempo/peticiones que puede alcanzar. Los distintos planes se serparan según la utilidad que tenga la aplicación web:
    - Proceso compartido
    - Proceso dedicado
    - Aislado
    - Consumo

(Los planes pueden ser modificados en cualquier momento según los requerimientos, ya que una vez consumido su límite, la aplicación deja de funcionar)

![7](img/7.png)

- Muchos **Web Apps** pueden estar contenidos dentro de un mismo **App Service Plan**, aunque puede haber problemas si abusamos

![8](img/8.png)

## El SDLA de nuestra solución

- Hay varios "caminos" para compilar el código del repositorio y llevarlo a mi App Service, aunque lo lógico es **hacerlo de una forma automatizada**. Lo ideal es que sea compilado en la nube con herramientas como **Azure DevOps** y demás antes mencionados para verificar que puede ser compilado en cualquier ordenador al margen del equipo o máquina que use el desarrollador (**que pueda tener instalados paquetes que el resto de usuarios finales no**)

- También llamado **CI CD (Contincontinuous integration and continuous delivery)** ya que todo el **SDLA** se produce en la nube

## Ranuras de implementación

- El uso de **ranuras de implementación** permite que los usuarios sigan utilizando la solución sin interrupciones de actualización exponiendo un **duplicado temporal de la solución** durante el transcurso de la actualización para que sea consumida en su lugar

![9](img/9.png)


## Autenticación y proveedores 

- Es posible añadir un **factor de autenticación** a nuestra App Service para la que el **usuario o programa** que quiera usar mi aplicación tenga que pasar por un **proveedor de autenticación** (ya que se hace de forma externa y este retorna la información a mi app)

- También se puede especificar un comportamiento de **autorización** para otorgar permisos y que dependiendo de este, mi solución se muestre de una forma u otra, o que permita o no ciertos comportamientos

- **Azure tiene autenticaciones integradas** que sin necesidad de que nosotros administremos, se comunican con los **proveedores**

- Proveedores que se encuentran de **forma predeterminada** en la plataforma:
    - Microsoft
    - Facebook
    - Google
    - Twitter

(Existen otros con los que podemos autenticar y que también se basan en **OAuth o Open Authoritation**, que es un **estándar abierto** que define cómo, de forma segura, se debe realizarse la autorización de una API para aplicaciones web, móviles o de escritorio)

- Es posible **configurar el App Service para que pueda utilizar otros proveedores** que cumplan con el **OAuth**, dando la opción a los usuarios de que se idenfiquen mediantes otras plataformas

- Azure App Service permite esta configuración de forma **automática y más rápida que de la manera convencional**

- La autenticación se lleva a cabo **mediante cookies** que transmiten la información de forma **Segura** mediante el proveedor y nuestra Web App

![11](img/11.png)

- Las **conexiones híbridas** permiten a nuestra aplicación web trabajar con **bases de datos que por motivos de seguridad, políticas u otros se encuentren On-premise** (No está disponible en todos los **planes de SKU**)

- En la App Service se puede controlar el acceso **mediante determinadas APIs o VPNs (filtrándo cuáles pueden acceder)** e incluso controlar las
**salidas de datos** de mi aplicación

![12](img/12.png)

>> [Vuelve al Índice o descansa y tómate un algo](#índice)

---
---
---

# Módulo 2
# (Implementación de Azure Functions)
>>`<Clase del 01/07/2022>`

## Qué es un Azure Function

[Enlace a documentación Microsoft](https://docs.microsoft.com/es-es/azure/azure-functions/functions-overview)

Es una solución que permite escribir menos código, mantener menos infraestructura para ahorrar costos. En lugar de preocuparse por implementar y mantener servidores (**Serverless**), la infraestructura en la nube proporciona todos los recursos actualizados necesarios para mantener las aplicaciones en ejecución

Como desarrolladores, nos centramos en los fragmentos de código que importan y Azure Functions se ocupa del resto de forma secundaria

En definitiva, permiten que se ejecute **una determinada lógica ante una acción que ocurra**

Cada Azure Function debe tener por fuerza **un desencadenador**

![13](img/13.png)

- Ejemplos de uso:

    - *Integrar sistemas*: es decir, **comunicación entre distintos sistemas** mediante pequeños trozos de código sin tener que levantar proyectos completos de desarrollo o máquinas virtuales (**una funcionalidad muy concreta**)
    
    - *IoT o Internet de las cosas*: para realizar la **comunicación vía internet con dispisitivos** o electrodomésticos por ejemplo, ya sea para supervisar u ordenar

    - *Implementación de microservicios*: en lugar de tener un proyecto gigantesco, **separo el código en pequeñas partes cada una con una funcionalidad** (estas últimas serían funcions) y permiten una actualización modular/alta tolerancia a fallos

    - *Procesamiento de imágenes o pedidos*: para **comprimir imágenes o lo que se considere** necesario según el caso

    - *Desencadenadores*: pueden ser utilizadas como **triggers** que desencadenen sucesos

![14](img/14.png)

## Qué es Azure Logic App

![15](img/15.png)

Utiliza conectores para llevar a cabo un flujo de trabajo que le especifiquemos

## Qué es WebJobs

![16](img/16.png)

Permite meter una pequeña funcionalidad que se ejecute cada cierto tiempo o ante cualquier determinada situación **dentro de una aplicación web .NET**

## Hospedaje de Azure Functions

Tarifas de planes según la carga de trabajo que tenga que sorportar nuestra App Service:

![17](img/17.png)

![18](img/18.png)

**Plan de Consumo**: tarifa predeterminada que se encarga de escalar los recursos (sin tener nosotros que definir el cómo se escala, ya que es el mismo Azure el que decide según la situación) en función de las llamadas que reciba por parte de los usuarios. Tomará más recursos cuando los necesita y los reducirá cuando no sean requeridos de forma dinámica

**Plan Premium**: también funciona bajo demanda pero tiene unas caracterísiticas más avanzadas que el plan de consumo. No tiene **retardo inicial** en responder a las llamadas ya que siempre está preparado para devolver la información necesaria

**Plan de App Service**: colgamos la Azure Function **como si fuera una App Service más**, y esta escalará o desescalará en función de la carga global que tenga el App Service

**RESUMEN**: En el plan de **consumo** y en el **premium**, es Azure quien decide el escalado según el consumo mediante un **controlador de escala** (en función del número de eventos, del consumo de recursos, el número de instancias, etc)

---

Si elegimos la tercera tarifa, el Plan App Service:

![19](img/19.png)

Si no configuramos el **Always On**, la App Service solo empezará una función tras un desencadenante (en algunos casos, puede no ser necesario; dependiendo de los requisitos)

Las Azure Functions pueden **necesitar cuentas de almacenamiento** para guardar información de seguimiento, de sincronización, de seguridad o de determinadas cosas que se requieran

## Escalado de Azure Functions

![20](img/20.png)

Evidentemente, podemos configurar el **número de instancias máxima** (llamadas o solicitudes) por segundo para que el servicio no colapse o se dispare el costo

El escalado se mide mediante el **número de instancias**, no de la **potencia**

![23](img/23.png)
![24](img/24.png)

## Partes de un Azure Function

![21](img/21.png)

En nuestros proyectos **.NET**, además de un **.exe** o un **.dll**, debemos tener un fichero **json con la configuración** que defina la **Azure Function**

![22](img/22.png)

**Azure Function** ofrece un **contexto de ejecución**, al igual que cuando ejecutamos una aplicación de escritorio tenemos el contexto de un sistema operativo. Esto quiere decir que, entre nuestra Azure Function y nuestro sistema operativo, se generan una **serie de funcionalidades** cuando **levantamos** nuestra Azure Function relacionadas con su finalidad y que ayudan a que esta se lleve a cabo. La duración de estas funcionalidades termina con la finalización del propósito del Azure Funcion (componentes configurados para permitir el objetivo de la function que nacen y mueren junto con esta)

**Todas las funciones** que se encuentran dentro de **un mismo proyecto, comparten el mismo plan de precios** por fuerza. También comparten **métodos de implementación e incluso la misma versión de tiempo de ejecución**

Esto sirve para **administrar las Azure Functions de forma conjunta**

![25](img/25.png)

Azure Function no solo es compatible con **.NET**

También lo es con **Node.js o Python** por ejemplo; es un servicio abierto a todo tipo de lenguajes y frameworks

![26](img/26.png)

Las **Azure Functions** permiten a los desarrolladores trabajar en nuestro equipo con nuestras herramientas elegidas y luego conectarlas con **Azure cuando sea necesario**

Es decir, tenemos la opción de **desarrollo local o en la nube** (es importante recordar que la compilación debe llevarse a cabo en la nube para evitar el problema antes mencionado sobre los paquetes del equipo local)

## Creación de desencadenadores y enlaces

![27](img/27.png)

El concepto es prácticamente el mismo que con los **triggeres** (un conector configurado), excepto que en el caso de las **Azure Function** el desencadenador es a **nivel de código** 

En dicho código, se define **cómo se invoca ese desencadenador** y **cada función debe estar relacionada con un desencadenador** que la haga ejecutarse)

No se puede tener un **Azure Function** sin un desencadencadenador

---

También podemos tener **enlaces o bindings** que nos permite **vincular una función con un determinado recurso (cola de almaceamiento, tabla de storage, blob storage, base de datos,...)**

Estos **enlaces pueden ser de entrada, salida o ambos**

Los enlaces sirven para **simplificar el código para determinar qué va a ocurrir** (si quiero tener una determinada función que se dispare cuando un usuario introduzca un fichero en un blob, necesito conectarme con ese blob para poder tener acceso a ese nuevo fichero; de la forma tradicional, sería necesario un bloque de código para llevarlo a cabo; sin embargo, los **enlaces** simplifican el desarrollo ahorrando el código y sustituyéndolo con variables relacionadas que permiten el acceso de forma **simplificada**)

Yo puedo tener en una misma **Function** varios **enlaces**

## Definir desencadenadores y enlaces

![28](img/28.png)

En el caso de **bibliotecas de C# y Java**, se definen mediante **atributos** (métodos y parámetros)

En el caso de **JavaScript/PowerShell/Python/TypeScript**, se definen dentro del **fichero JSON** como en el ejemplo de la imagen 

Es decir, en el caso de **.NET y Java**, no va a ser necesario que toquemos ni redactemos el fichero **JSON** ya que van a ser las mismas herramientas del framework las que se encargaran de crearlo y configurarlo (aunque hay que tener en cuenta que el fichero existe dentro del proyecto y se define automáticamente a raíz del código que diseñemos)

(Si sería necesario tocarlo en **los demás frameworks** como se expecifica arriba)

## Dirección de enlaces

![29](img/29.png)

Los enlaces permiten **vincular** nuestras Azure Functions con algunos **servicios de Azure**

La vinculación puede ser de **entrada, salida o ambas** (in, out o inout)

**RESUMEN: desencadenador (desencadena la funcón) y enlace (lo que necesita la función para llevar a cabo su objetivo)**

## Ejemplo 1
![30](img/30.png)

Este es un ejemplo de uso disparador/enlace (aquí vemos un JSON)

En el caso de la imagen **Azure Queue Storage** es el desencadenador y **Azure Table Storage** el enlace o blinding, lo que significa que cada vez que alguien introduzca información en la **Queu Storage**, va a añadirse una fila en la **Table Storage**

**Azure Table Storage** es un servicio que nos permite guardar información de forma **tabular** (como una hoja de excel)

## Ejemplo 2
![31](img/31.png)

Otro ejemplo de uso disparador/enlace en C# (aquí no es necesario configurar el JSON ya que este se crea automáticamente según el código que especifiquemos, por lo que en el ejemplo analizamos el código C#)

## Otros Ejemplos

![32](img/32.png)
![33](img/33.png)

## Conexiones con cuentas de almacenamiento

![34](img/34.png)
![35](img/35.png)

> **NOTA: el concepto de identidad se explica más adelante junto al tema de seguridad**

## Examinando código

Una **Queue o cola** es una serie de mensajes apilados que al ser recibidos y cumplir con su función, desaparecen

Si el **mensaje de la cola** intenta su cometido tres veces sin conseguirlo, pasa a una **poison queue**

>> [Vuelve al Índice o pégate una ducha fría](#índice)

---
---
---

# Módulo 3: 

>> [Vuelve al Índice o tómate un café por dios](#índice)

---
---
---

# Módulo 4: 

>> [Vuelve al Índice o descansa un rato la vista](#índice)

---
---
---

# Módulo 5: 

>> [Vuelve al Índice o sal con los amigos un rato](#índice)

---
---
---

# Módulo 6: 

>> [Vuelve al Índice o haz una maratón de una serie](#índice)


---
---
---

# Módulo 7: 

>> [Vuelve al Índice o date un chapuzón si tienes piscina](#índice)

---
---
---

# Módulo 8: 

>> [Vuelve al Índice o échate una siesta](#índice)

---
---
---

# Módulo 9: 

>> [Vuelve al Índice o date una vuelta en moto](#índice)

---
---
---

# Módulo 10: 

>> [Vuelve al Índice o dale caña a la play](#índice)


---
---
---

# Módulo 11: 

>> [Vuelve al Índice o vete a la playa a echar la tarde](#índice)


---
---
---

# Módulo 12: 

>> [Vuelve al Índice o date un respiro por haber llegado al final](#índice)

>> [ENHORABUENA](https://www.usameme.com/wp-content/uploads/2022/02/congratulations-meme-usameme.jpg)


---
---
---
---
---
---


``Notas personales:
    - Añadir ejemplos de decoración de Azure Functions
    - Es necesario una decoración para que sea una Azure Function
    - Añadir ?name=nombre a la url de la function, añade el nombre a la queue
``