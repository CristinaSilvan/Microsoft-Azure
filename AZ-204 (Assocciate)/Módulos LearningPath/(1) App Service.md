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