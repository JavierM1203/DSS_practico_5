# Practico 5

## Introducción.

## Funciones seleccionadas.

* Crear torneos
* Asignar jueces
* Inscribir participantes
* Registrar puntajes
* Mostrar ranking

## Diagrama de flujo de datos de alto nivel.

![alt text](images/dfd_alto_nivel.png)

## Diagrama de flujo de datos de segundo nivel por función.

* Crear torneos

* Asignar jueces

* Inscribir participantes

* Registrar puntajes

* Mostrar ranking

## Amenzas por función.

### Crear torneos - Tampering. -  VER SI QUITAR

Un atacante podría modificar los datos del torneo como fechas o participantes, si no se implementan los controles suficientes sobre los usuarios que deben poder modificar datos de torneos.

**Damage (8):** Modificar los datos podría alterar el flujo de los torneos y afectar a los participantes y jueces.

**Reproducibility (5):** Si se accede a la base de datos o a la API sin los controles adecuados, puede ser sencillo modificar los datos.

**Exploitability (6):** Requiere conocimiento del sistema, pero no es demasiado complejo si se encuentran vulnerabilidades.

**Affected users (7):** Los participantes y jueces en los torneos modificados se verían directamente afectados.

**Discoverability (4):** Este tipo de ataque podría pasar desapercibido durante un tiempo, hasta que se detecten incoherencias.

**Riesgo total:** 30/5 = 6

**Mitigación:** 

### Crear torneos - Elevation of Privilege.

Un atacante sin privilegios suficientes podría crear torneos.

**Damage (9):** Un atacante podría crear torneos no autorizados y afectar la información mostrada al público.

**Reproducibility (5):** Si se encuentran vulnerabilidades de escalamiento de privilegios, este ataque podría repetirse fácilmente.

**Exploitability (6):** Se requiere encontrar una vulnerabilidad de escalamiento, lo que podría no ser tan complejo si no se han implementado buenas prácticas de seguridad.

**Affected users (6):** Los participantes del torneo se verían afectados.

**Discoverability (4):** Este ataque podría no ser inmediatamente evidente, especialmente si los torneos son creados de forma encubierta.

**Riesgo total:** 28/5 = 

**Mitigación:** 


### Registrar puntajes - Tampering.

Un atacante podría alterar los puntajes enviados por la aplicación.

**Damage (8):** El impacto de puntajes alterados es grave, ya que puede afectar directamente el resultado del torneo y la credibilidad del sistema.

**Reproducibility (6):** Una vez comprometido el sistema, un atacante podría alterar múltiples puntajes con relativa facilidad.

**Exploitability (5):** El ataque es factible si la transmisión de datos o la base de datos no están adecuadamente protegidas.

**Affected users (8):** Todos los participantes y organizadores del torneo se verían afectados, ya que el resultado del torneo se distorsionaría.

**Discoverability (4):** A menos que se revisen manualmente los puntajes, podría ser difícil detectar que han sido manipulados.

**Riesgo total:** 31/5 = 

**Mitigación:** 

### Registrar puntajes - Repudiation.

Un juez podría negar que asignó un puntaje a un participante.

**Damage ():** 

**Reproducibility ():** 

**Exploitability ():** 

**Affected users ():** 

**Discoverability ():** 

**Riesgo total:** /5 = 

**Mitigación:** 