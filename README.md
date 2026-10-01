# Análisis de equivalencia entre planes de estudio de universidades diferentes

## Problema

### Contexto

Los estudiantes del programa SICUE (Sistema de Intercambio entre Centros Universitarios de España) tienen que elaborar un [acuerdo académico](docs/conceptos.md#acuerdo-académico) con las asignaturas que cursarán en la universidad de destino, y este proceso les causa problemas de forma habitual.

### Descripción del proceso actual

Seleccionar, en la universidad de destino, asignaturas equivalentes a las del plan de estudios de la universidad de origen es un proceso agotador. El estudiante tiene que:

1. Leer y analizar las [guías docentes](docs/conceptos.md#guía-docente) de todas las asignaturas que pueda elegir, así como las de su titulación en la universidad de origen.
2. Seleccionar aquellas que desee y que considere equivalentes, y recogerlas en el acuerdo académico, que deben firmar el propio estudiante y los coordinadores SICUE de ambos centros.

El acuerdo académico es vinculante y solo puede modificarse durante un plazo corto (ver la [definición](docs/conceptos.md#acuerdo-académico)). Por eso la decisión clave es la del coordinador de origen al firmar: en ese momento se juzga si las asignaturas elegidas son equivalentes.

### Criterio de equivalencia

La [equivalencia](docs/conceptos.md#equivalencia) entre asignaturas se evalúa por **competencias y contenidos**, no por el nombre. El marco normativo y las reglas que el proyecto deriva de él están definidos en [Conceptos](docs/conceptos.md), que es la única fuente de estas reglas:

- qué es una [correspondencia](docs/conceptos.md#correspondencia) entre asignaturas y cuándo una asignatura queda [cubierta](docs/conceptos.md#asignatura-cubierta);
- cuándo un [plan es válido y cuándo es completo](docs/conceptos.md#plan-válido-y-plan-completo);
- cómo se calcula el [grado de equivalencia](docs/conceptos.md#grado-de-equivalencia);
- cuál es el [mínimo de ECTS](docs/conceptos.md#mínimo-de-ects) según la estancia.

### Por qué es un problema

- El proceso es lento y puede tener que repetirse porque una asignatura deja de ser [viable](docs/conceptos.md#asignatura-viable-y-no-viable) (falta de plazas, conflictos de horarios, entre otras causas). Como el acuerdo solo puede modificarse durante el primer mes del semestre, cada contratiempo obliga a rehacer el análisis con prisa.
- Las plazas SICUE se ofertan mediante convenios bilaterales entre centros: el estudiante elige destino meses antes de conocer la disponibilidad real de plazas en cada asignatura y los horarios definitivos.
- Es un problema muy habitual entre los estudiantes de programas de movilidad, y supone una pérdida de tiempo y de oportunidades para que el estudiante pueda cursar las asignaturas que realmente desea.

### Datos disponibles

Las guías docentes de las asignaturas son públicas, al igual que otros criterios de equivalencia, como el número de créditos ECTS. Las guías están en formato textual en páginas web, en español y con una estructura muy similar entre universidades españolas (competencias, resultados de aprendizaje, contenidos, metodología y evaluación).

### Escala del problema

Una titulación de grado de 240 ECTS puede tener unas 60 guías docentes. Para elaborar el acuerdo académico, el estudiante tiene que comparar cada una de las [asignaturas que le faltan](docs/conceptos.md#asignaturas-que-me-faltan) con todas las asignaturas elegibles en destino, y después escoger una combinación.

**Asignaturas de la ETSIIT que se pueden escoger por año del grado en el primer semestre**

| Curso | Asignaturas en el 1er semestre |
|---|---|
| 1º | 5 (todas troncales) |
| 2º | 5 (todas obligatorias) |
| 3º | 5 (comunes; las de especialidad son del 2º semestre) |
| 4º | 28: 15 obligatorias de especialidad (3 por mención) + 13 optativas de especialidad |
| **Total** | **43** |

Un estudiante de último curso solo puede escoger asignaturas de 3º y 4º, es decir, 33.

| | Medio curso (ETSIIT, último curso) | Curso completo (estimación) |
|---|---|---|
| Asignaturas de origen a sustituir | 5 (30 ECTS) | 10 (60 ECTS) |
| Asignaturas elegibles en destino | 33 | ~60 |
| Guías docentes que leer | 38 | ~70 |
| Comparaciones asignatura a asignatura | 165 | ~600 |
| Combinaciones posibles de asignaturas de destino | C(33, 5) = 237 336 | C(60, 10) ≈ 7,5 · 10¹⁰ |

Como una correspondencia puede agrupar varias asignaturas, tanto de origen como de destino, el número real de planes posibles es aún mayor. Además, cada falta de plazas o conflicto de horarios obliga a repetir la búsqueda.

## Lógica de negocio

El enfoque elegido para medir la [similitud](docs/conceptos.md#similitud-y-umbral) es **TF-IDF con similitud del coseno, calculada por separado para las competencias y para los contenidos de cada guía docente**. La similitud combinada de una pareja es la media ponderada de ambas: w · sim(competencias) + (1 − w) · sim(contenidos). Cómo se calcula la similitud de un grupo de asignaturas se definirá al modelar el problema (M0).

Con ella:

- una pareja es [equivalente plausible](docs/conceptos.md#equivalente-plausible) por similitud si su similitud combinada alcanza el umbral θ;
- es [débil](docs/conceptos.md#pareja-débil) si su similitud combinada queda en [θ, θ + δ) o si la de alguna dimensión queda por debajo de θ.

### Parámetros

θ, w y δ son únicos para todo el sistema y se ajustan con los casos de [validación](#validación). No se ajusta un θ por centro o por coordinador porque los casos disponibles para cada uno serían pocos y el ajuste se sobreajustaría. δ se fija como el intervalo por encima de θ en el que la solución todavía clasifica mal casos de validación.

### Por qué este enfoque

- **TF-IDF frente a Jaccard.** El índice de Jaccard da el mismo peso a todos los términos. Las guías docentes están llenas de vocabulario común a cualquier asignatura (competencia, evaluación, alumnado, prácticas), que inflaría la similitud entre asignaturas sin relación. TF-IDF reduce el peso de esos términos, porque aparecen en casi todas las guías.
- **Similitud del coseno.** No depende de la longitud del texto, y la extensión de las guías varía mucho entre universidades.
- **Comparación por secciones.** Separa las dos dimensiones del criterio de la normativa: competencias y contenidos.
- **Explicabilidad.** Para cada pareja débil se muestra la similitud de cada dimensión y su distancia a θ. También se muestran los términos que más aportan a la similitud y los términos de mayor peso de la asignatura de origen que no aparecen en la de destino. Ese es el «porqué» de la pareja débil, y lo que el estudiante puede presentar al coordinador.

## Validación

Los parámetros θ, w y δ se ajustan, y la solución se evalúa, con dos tipos de casos:

- **Casos positivos.** Son acuerdos académicos SICUE ya aprobados, es decir, firmados por el coordinador de origen. La solución tiene que aceptar todas sus correspondencias. Se pueden obtener de estudiantes SICUE de cursos anteriores, que no son pocos: según CRUE, el programa sumó 63.268 movilidades en sus primeros veinte años ([CRUE, 2019](https://www.crue.org/2019/10/aniversario-sicue-20/)), una media de unas 3.000 al año.
- **Casos negativos.** Son correspondencias que el coordinador de origen no firmaría. Se obtienen preguntándole por propuestas concretas, por ejemplo variantes de acuerdos aprobados en las que una asignatura se sustituye por otra sin relación. La solución tiene que rechazarlas.

En los casos de validación no se aplican [precedentes](docs/conceptos.md#precedente): el ajuste y la evaluación usan solo la similitud. Si se aplicaran, los casos positivos se aceptarían por ser ellos mismos precedentes y la validación sería circular.

La métrica es el porcentaje de casos de cada tipo clasificados correctamente. Una parte de los casos se reserva para comprobar los parámetros elegidos, no solo para ajustarlos.

## Planificación

- [User journeys](docs/user-journeys.md)
- [Personas](docs/personas.md)
- [Historias de usuario](docs/historias-de-usuario.md) ([issues](https://github.com/diego-vigil-sosa/IV-equivalencia-de-planes-de-estudios/issues?q=label%3Auser-stories))
- [Milestones](docs/milestones.md) ([en GitHub](https://github.com/diego-vigil-sosa/IV-equivalencia-de-planes-de-estudios/milestones))
- [Conceptos](docs/conceptos.md)

## Documentación adicional

- [Configuración de git y GitHub](docs/configuracion.md)
- [Fotografía de la tarjeta del juego de rol](docs/img/tarjeta.jpeg)