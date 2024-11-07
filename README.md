# Practico 5
# Índice

- [Introducción](#introducción)
- [Funciones seleccionadas:](#Funciones-seleccionadas)
- [Diagrama-de-flujo-de-datos-de-alto-nivel:](#Diagrama-de-flujo-de-datos-de-alto-nivel)
- [Diagrama-de-flujo-de-datos-de-segundo-nivel-por-función:](#Diagrama-de-flujo-de-datos-de-segundo-nivel-por-función)
- [Crear torneos](#Crear-torneos)
- [Asignar jueces](#Asignar-jueces)
- [Inscribir participantes](#Inscribir-participantes)
- [Registrar puntajes](#Registrar-puntajes)
- [Mostrar ranking](#Mostrar-ranking)
- [Amenzas por función:](#Amenzas-por-función)
- [Asignar jueces: Spoofing:](#Asignar-jueces-Spoofing)
- [Registrar puntajes - Tampering:](#Registrar-puntajes-Tampering)
- [Registrar puntajes - Repudiation:](#Registrar-puntajes-Repudiation)
- [Mostrar ranking - Information Disclosure:](#Mostrar-ranking-Information-Disclosure)
- [Inscribir participantes - Denegación de Servicio (DoS):](#Inscribir-participantes-Denegación-de-Servicio-(DoS))
- [Crear torneos - Elevation of Privilege:](#Crear-torneos-Elevation-of-Privilege)



## Introducción:


## Funciones seleccionadas:

* Crear torneos
* Asignar jueces
* Inscribir participantes
* Registrar puntajes
* Mostrar ranking

## Diagrama de flujo de datos de alto nivel:

![alt text](images/dfd_alto_nivel.png)


## Diagrama de flujo de datos de segundo nivel por función:

* ### Crear torneos

![alt text](images/crear_torneos.png)

* ### Asignar jueces

![alt text](images/asignar_jueces.png)

* ### Inscribir participantes

![alt text](images/inscribir.png)

* ### Registrar puntajes

![alt text](images/puntaje.png)

* ### Mostrar ranking

![alt text](images/ranking.png)


## Amenzas por función:
### Asignar jueces: Spoofing:

Un atacante podría suplantar la identidad de un funcionario autorizado y asignar jueces a un torneo sin autorización

**Damage (8):** La asignación de jueces no autorizados puede afectar la legitimidad y credibilidad del torneo.

**Reproducibility (7):** Una vez que el atacante consigue los datos de autenticación del funcionario, podría realizar este ataque repetidamente.

**Exploitability (5):** Este ataque es posible si no se implementan controles de autenticación robustos.

**Affected users (6):** Los organizadores y participantes se verían afectados, ya que el torneo podría ser manipulado.

**Discoverability (4):** Podría pasar desapercibido si no se revisan los registros de asignación.

**Riesgo total:** 30/5 = 6,0

**Mitigación:** Implementar autenticación de dos factores para los funcionarios y registros de auditoría detallados para todas las asignaciones de jueces. 


### Registrar puntajes: Tampering:

Un atacante podría alterar los puntajes enviados por la aplicación.

**Damage (8):** El impacto de puntajes alterados es grave, ya que puede afectar directamente el resultado del torneo y la credibilidad del sistema.

**Reproducibility (7):** Una vez comprometido el sistema, un atacante podría alterar múltiples puntajes con relativa facilidad.

**Exploitability (5):** El ataque es factible si la transmisión de datos o la base de datos no están adecuadamente protegidas.

**Affected users (8):** Todos los participantes y organizadores del torneo se verían afectados, ya que el resultado del torneo se distorsionaría.

**Discoverability (4):** A menos que se revisen manualmente los puntajes, podría ser difícil detectar que han sido manipulados.

**Riesgo total:** 32/5 = 6,4

**Mitigación:** Asegurar que la aplicación Android utilice cifrado completo de las comunicaciones con la API para evitar la interceptación de puntajes.
Implementar alertas automáticas que notifiquen cambios inusuales en los puntajes, y auditorías en tiempo real que revisen la integridad de los datos.


### Registrar puntajes: Repudiation:

Un juez podría negar que asignó un puntaje a un participante.

**Damage (8):** Esto puede afectar la integridad de los resultados del torneo, cambiando el puntaje total y el ganador.

**Reproducibility (8):** Sin medidas de autenticación adecuadas, cualquier juez podría asignar un puntaje y luego negar haberlo hecho.

**Exploitability (6):** Si no se cuenta con registros detallados sobre quién realizó cada acción, un atacante podría explotar la vulnerabilidad sin requerir mucho conocimiento técnico.

**Affected users (7):** Se ven adectados los participantes y el público del torneo.

**Discoverability (5):** Puede ser detectada por jueces o por otros actores. Sin embargo, si no se cuentan con registros de auditoría, la falta de rastreabilidad no es evidente.

**Riesgo total:** 34/5 = 6,8

**Mitigación:** Autenticación de jueces utilizando certificados digitales o biometría para garantizar que solo jueces autorizados puedan registrar puntajes.
Cada acción realizada por los jueces debe registrarse con un identificador único y una marca de tiempo, lo cual permite rastrear quién asignó cada puntaje.


### Mostrar ranking: Information Disclosure:

Un atacante podría obtener acceso no autorizado a los datos del ranking, exponiendo la información de puntajes antes de su publicación oficial.

**Damage (6):** La divulgación no autorizada de puntajes podría afectar la transparencia y confianza en el sistema.

**Reproducibility (7):** Una vez que el atacante obtiene acceso, puede repetir el ataque.

**Exploitability (5):** El ataque es posible si no se controlan adecuadamente los permisos de acceso a los datos del ranking.

**Affected users (5):** Participantes y el público se ven afectados, ya que la información filtrada puede manipular la percepción del torneo.

**Discoverability (5):** La exposición puede ser difícil de detectar si no se realizan auditorías en los accesos al ranking.

**Riesgo total:** 27/5 = 5,4

**Mitigación:** Restringir el acceso a los datos del ranking a usuarios autorizados y utilizar cifrado en las comunicaciones y el almacenamiento de datos sensibles. 


### Inscribir participantes: Denegación de Servicio (DoS): 
Un atacante podría sobrecargar el sistema de inscripción, impidiendo que los usuarios legítimos completen el proceso.

**Damage (6):** Si el sistema de inscripción queda fuera de servicio, los participantes legítimos no podrán inscribirse, afectando el desarrollo del torneo. Esto impactaría la integridad y la disponibilidad del sistema, aunque el daño directo a los datos es limitado.

**Reproducibility (5):** Un ataque de denegación de servicio puede ser replicado fácilmente si se encuentra un punto débil en la infraestructura o configuración del sistema.

**Exploitability (6):** Dependiendo de la arquitectura y medidas de seguridad, un atacante podría explotar esta vulnerabilidad enviando una gran cantidad de solicitudes de inscripción.

**Affected users (6):** Afecta a todos los participantes y usuarios legítimos que intenten utilizar el sistema de inscripción durante el ataque, ya que el sistema no estará disponible.

**Discoverability (5):** Un ataque DoS suele ser evidente cuando el sistema comienza a tener problemas de rendimiento o queda completamente fuera de servicio, aunque identificar el origen puede ser complicado.

Riesgo total: 28/5 = 5,6
**Mitigación:** Limitar la cantidad de solicitudes permitidas por usuario en un intervalo de tiempo específico, para prevenir que un solo usuario  realice múltiples solicitudes en un corto período. Implementar un sistema de CAPTCHA en el formulario de inscripción para evitar que bots o scripts automáticos generen múltiples solicitudes de inscripción simultáneamente.




### Crear torneos: Elevation of Privilege:

Un atacante podría modificar sus privilegios para crear torneos.

**Damage (9):** Un atacante podría crear torneos no autorizados y afectar la información mostrada al público.

**Reproducibility (8):** Si se encuentran vulnerabilidades de escalamiento de privilegios, este ataque podría repetirse fácilmente.

**Exploitability (6):** Se requiere encontrar una vulnerabilidad de escalamiento, lo que podría no ser tan complejo si no se han implementado buenas prácticas de seguridad.

**Affected users (6):** Los participantes del torneo se verían afectados.

**Discoverability (4):** Este ataque podría no ser inmediatamente evidente, especialmente si los torneos son creados de forma encubierta.

**Riesgo total:** 33/5 = 6,6

**Mitigación:** Verificar los controles de acceso en el servidor, no solo en el cliente. Esto evita que los usuarios intenten obtener accesos adicionales manipulando el lado del cliente. Respetar el Principio de Mínimo Privilegios, configurar los permisos de usuario de manera que solo los roles absolutamente necesarios puedan crear torneos.



