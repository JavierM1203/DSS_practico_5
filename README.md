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


### Crear torneos - Elevation of Privilege.

Un atacante podría modificar sus privilegios para crear torneos.

**Damage (9):** Un atacante podría crear torneos no autorizados y afectar la información mostrada al público.

**Reproducibility (8):** Si se encuentran vulnerabilidades de escalamiento de privilegios, este ataque podría repetirse fácilmente.

**Exploitability (6):** Se requiere encontrar una vulnerabilidad de escalamiento, lo que podría no ser tan complejo si no se han implementado buenas prácticas de seguridad.

**Affected users (6):** Los participantes del torneo se verían afectados.

**Discoverability (4):** Este ataque podría no ser inmediatamente evidente, especialmente si los torneos son creados de forma encubierta.

**Riesgo total:** 33/5 = 6,6

**Mitigación:** Verificar los controles de acceso en el servidor, no solo en el cliente. Esto evita que los usuarios intenten obtener accesos adicionales manipulando el lado del cliente.


### Registrar puntajes - Tampering.

Un atacante podría alterar los puntajes enviados por la aplicación.

**Damage (8):** El impacto de puntajes alterados es grave, ya que puede afectar directamente el resultado del torneo y la credibilidad del sistema.

**Reproducibility (7):** Una vez comprometido el sistema, un atacante podría alterar múltiples puntajes con relativa facilidad.

**Exploitability (5):** El ataque es factible si la transmisión de datos o la base de datos no están adecuadamente protegidas.

**Affected users (8):** Todos los participantes y organizadores del torneo se verían afectados, ya que el resultado del torneo se distorsionaría.

**Discoverability (4):** A menos que se revisen manualmente los puntajes, podría ser difícil detectar que han sido manipulados.

**Riesgo total:** 32/5 = 6,4

**Mitigación:** Asegurar que la aplicación Android utilice cifrado completo de las comunicaciones con la API para evitar la interceptación de puntajes.


### Registrar puntajes - Repudiation.

Un juez podría negar que asignó un puntaje a un participante.

**Damage (8):** Esto puede afectar la integridad de los resultados del torneo, cambiando el puntaje total y el ganador.

**Reproducibility (8):** Sin medidas de autenticación adecuadas, cualquier juez podría asignar un puntaje y luego negar haberlo hecho.

**Exploitability (6):** Si no se cuenta con registros detallados sobre quién realizó cada acción, un atacante podría explotar la vulnerabilidad sin requerir mucho conocimiento técnico.

**Affected users (7):** Se ven adectados los participantes y el público del torneo.

**Discoverability (5):** Puede ser detectada por jueces o por otros actores. Sin embargo, si no se cuentan con registros de auditoría, la falta de rastreabilidad no es evidente.

**Riesgo total:** 34/5 = 6,8

**Mitigación:** Autenticación de jueces utilizando certificados digitales o biometría para garantizar que solo jueces autorizados puedan registrar puntajes.
