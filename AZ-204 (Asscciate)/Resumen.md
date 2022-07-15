# Azure 204 - Developing Solutions for Microsoft Azure

**Conceptos**:
- *Software escalable*: applicación utilizada por infinidad de usuarios (lo opuesto a un software usado por uno o pocos miembros dentro de una misma organización)
- *SDLA o software development life cycle*: El ciclo de desarrollo, compilación, testeo, despliegue, versionamiento y demás que se lleva a cabo en la producción del software y que continua con la actualización del mismo
- *SLA (Service Level Agreement)*: Acuerdo de alta disponibilidad mínima de recursos medido en porcentaje

---
---
---

# Índice

## [Intro](#introducción)
## [Ruta certificación](#ruta-completa-certificación)
## [Esquema módulos](#esquema-de-módulos)

---

## [Módulo 1: Creación de aplicaciones web](#módulo-1-creación-de-aplicaciones-web)

---
---
---

# Introducción

![1](img/1.png)

# Ruta completa certificación

![2](img/2.png)

# Esquema de módulos

![3](img/3.png)
![4](img/4.png)

# Módulo 1: Creación de aplicaciones web

![5](img/5.png)

- Servicio **basado HTTP** (Protocolo de transferencia de datos a través de internet, *Hypertext Transfer Protocol*); define la sintáxis y semántica de la **comunicación entre aplicaciones web**

- Permite **hospedar aplicaciones web, API de Rest y back-ends para dispositivos móviles**

- Alojar mi solución en una **Azure App Web** permite el **escalado de recursos** de forma manual o automática

- El **back-end** de la solución normalmente se encuentra alojado en un repositorio de código (**Azure App Service me permite hacerlo de forma nativa ya que se encuentra vínculado a Azure DevOps y aparte es compatible con GitHub y BitBucked**)

- En el repositorio es donde se lleva a cabo el **ciclo de vida** (SDLC, *software development life cycle*)

- Las **Ranuras de implementación** permiten gestionar de una forma más efectiva las subidas de versiones al entorno de producción. Cada vez que actualizamos la web, hacen falta una serie de procesos que pueden hacer que nuestro servicio dejen de funcionar durante dicha actualización. Debido al **SLA de Windows (Service Level Agreement)**, es necesario asegurar la alta disponibilidad del servicio

- Para poder tener un **App Service** es indispensable tener un **App Service Plan** del que colgará mi App; Al igual que los recursos deben estar vinculados a un **resource group**

- Un **Azure App Service Plan** es un conjunto de recursos necesarios para tener una aplicación web (es como una máquina de la que tira mi app web pero más complejo)

![6](img/6.png)

- Los **App Service Plan** deben tener una tarifa en función de la cual se desplegará la **Web App** y que especifica la cantidad de tiempo/peticiones que puede alcanzar. Los distintos planes se serparan según la utilidad que tenga la aplicación web:
    - Proceso compartido
    - Proceso dedicado
    - Aislado
    - Consumo

(Los planes pueden ser modificados en cualquier momento según los requerimientos, ya que una vez consumido su límite, la aplicación deja de funcionar)

![7](img/7.png)

- Muchos **Web Apps** pueden estar contenidos dentro de un mismo **App Service Plan**, aunque puede haber problemas si abusamos

![8](img/8.png)

- Hay varios "caminos" para compilar el código del repositorio y llevarlo a mi App Service, aunque lo lógico es **hacerlo de una forma automatizada**. Lo ideal es que sea compilado en la nube con herramientas como **Azure DevOps** y demás antes mencionados para verificar que puede ser compilado en cualquier ordenador al margen del equipo o máquina que use el desarrollador (**que pueda tener instalados paquetes que el resto de usuarios finales no**)

- También llamado **CI CD (Contincontinuous integration and continuous delivery)** ya que todo el **SDLA** se produce en la nube

![9](img/9.png)