# Análisis de equivalencia entre planes de estudio de universidades diferentes

## Problema

### Contexto

Los estudiantes del programa SICUE (Sistema de Intercambio entre Centros Universitarios de España) tienen que elaborar un acuerdo académico con las asignaturas que cursarán en la universidad de destino, y este proceso les causa problemas de forma habitual.

### Descripción del proceso actual

Seleccionar, en la universidad de destino, asignaturas equivalentes a las del plan de estudios de la universidad de origen es un proceso agotador. El estudiante tiene que:

1. Leer y analizar las guías docentes de todas las asignaturas que pueda elegir, así como las de su titulación en la universidad de origen.
2. Seleccionar aquellas que desee y que considere equivalentes, y recogerlas en el **acuerdo académico**, que deben firmar el propio estudiante y los coordinadores SICUE de ambos centros.

El acuerdo académico es vinculante: una vez firmado por las tres partes, lo que el estudiante curse en destino se reconoce automáticamente en origen, y el acuerdo solo puede modificarse durante el primer mes desde el inicio del semestre ([normas del programa SICUE, CRUE](https://www.crue.org/sicue/)). Por eso la decisión clave es la del coordinador de origen al firmar: en ese momento se juzga si las asignaturas elegidas son equivalentes.

### Criterio de equivalencia

La equivalencia entre asignaturas se evalúa por **competencias y contenidos**. El [Real Decreto 822/2021](https://www.boe.es/buscar/act.php?id=BOE-A-2021-15781) (art. 10) regula el reconocimiento de créditos entre títulos universitarios oficiales y encarga a cada universidad aprobar su propia normativa. Estas normativas concretan el criterio con la misma fórmula: la adecuación entre las competencias y conocimientos asociados a las asignaturas cursadas y los previstos en el plan de estudios. Las [normas del programa SICUE](https://www.crue.org/sicue/) añaden dos cosas. El intercambio debe adecuarse al perfil curricular del estudiante. Además, las optativas de destino que no existan en el plan de origen pueden incorporarse al expediente como optativas.

En este proyecto, ese criterio se traduce en las siguientes reglas:

- Una asignatura de origen queda **cubierta** por una o varias asignaturas de destino si se cumplen dos condiciones: la similitud entre sus competencias y contenidos supera un umbral, y la suma de sus ECTS es igual o mayor que los ECTS de la asignatura de origen.
- Cada asignatura de destino cubre, como máximo, una asignatura de origen.
- La optativa de origen puede cubrirse con cualquier asignatura de destino con ECTS suficientes, ya que puede incorporarse como optativa.
- El plan debe sumar al menos 24 ECTS en una estancia de medio curso o 45 ECTS en una de curso completo.
- El **grado de equivalencia** de un plan es el porcentaje de ECTS de origen cubiertos. Un plan es equivalente cuando cubre todas las asignaturas obligatorias de origen.

### Por qué es un problema

- El proceso es lento y puede tener que repetirse por falta de plazas en las asignaturas, conflictos de horarios, entre otras causas. Como el acuerdo solo puede modificarse durante el primer mes del semestre, cada contratiempo obliga a rehacer el análisis con prisa.
- Las plazas SICUE se ofertan mediante convenios bilaterales entre centros: el estudiante elige destino meses antes de conocer la disponibilidad real de plazas en cada asignatura y los horarios definitivos.
- Es un problema muy habitual entre los estudiantes de programas de movilidad, y supone una pérdida de tiempo y de oportunidades para que el estudiante pueda cursar las asignaturas que realmente desea.

### Datos disponibles

Las guías docentes de las asignaturas son públicas, al igual que otros criterios de equivalencia, como el número de créditos ECTS. Las guías están en formato textual en páginas web, en español y con una estructura muy similar entre universidades españolas (competencias, resultados de aprendizaje, contenidos, metodología y evaluación).

### Escala del problema

Una titulación de grado de 240 ECTS puede tener unas 60 guías docentes. Para elaborar el acuerdo académico, el estudiante tiene que comparar cada asignatura de origen que va a sustituir con todas las asignaturas elegibles en destino, y después escoger una combinación.

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

Como una asignatura de origen puede quedar cubierta por varias de destino, el número real de planes posibles es aún mayor. Además, cada falta de plazas o conflicto de horarios obliga a repetir la búsqueda.

## Lógica de negocio

El enfoque elegido es **TF-IDF con similitud del coseno, calculada por separado para las competencias y para los contenidos de cada guía docente**. La similitud de una pareja de asignaturas es la media ponderada de ambas: w · sim(competencias) + (1 − w) · sim(contenidos). La pareja se considera equivalente si esa similitud supera un umbral θ. Los motivos para usar esta lógica son los siguientes:

- **TF-IDF frente a Jaccard.** El índice de Jaccard da el mismo peso a todos los términos. Las guías docentes están llenas de vocabulario común a cualquier asignatura (competencia, evaluación, alumnado, prácticas), que inflaría la similitud entre asignaturas sin relación. TF-IDF reduce el peso de esos términos, porque aparecen en casi todas las guías.
- **Similitud del coseno.** No depende de la longitud del texto, y la extensión de las guías varía mucho entre universidades.
- **Comparación por secciones.** Separa las dos dimensiones del criterio de la normativa: competencias y contenidos.
- **Explicabilidad.** Para cada pareja de asignaturas se pueden mostrar los términos que más aportan a la similitud. Eso es lo que el estudiante puede presentar al coordinador para justificar el acuerdo.

## Validación

Los parámetros θ y w se ajustan, y la solución se evalúa, con dos tipos de casos:

- **Casos positivos.** Son acuerdos académicos SICUE ya aprobados, es decir, firmados por el coordinador de origen. La solución tiene que darlos como válidos. Se pueden obtener de estudiantes SICUE de cursos anteriores, que no son pocos: según CRUE, el programa sumó 63.268 movilidades en sus primeros veinte años ([CRUE, 2019](https://www.crue.org/2019/10/aniversario-sicue-20/)), una media de unas 3.000 al año.
- **Casos negativos.** Son planes que el coordinador de origen no firmaría. Se obtienen preguntándole por propuestas concretas, por ejemplo variantes de acuerdos aprobados en las que una asignatura se sustituye por otra sin relación. La solución tiene que rechazarlos.

La métrica es el porcentaje de casos de cada tipo clasificados correctamente. Una parte de los casos se reserva para comprobar los parámetros elegidos, no solo para ajustarlos.

## Planificación

- [User journeys](docs/user-journeys.md)
- [Personas](docs/personas.md)
- [Historias de usuario](docs/historias.md) ([issues](https://github.com/diego-vigil-sosa/IV-equivalencia-de-planes-de-estudios/issues?q=label%3Auser-stories))
- [Milestones](docs/milestones.md) ([en GitHub](https://github.com/diego-vigil-sosa/IV-equivalencia-de-planes-de-estudios/milestones))

## Documentación adicional

- [Configuración de git y GitHub](docs/configuracion.md)
- [Fotografía de la tarjeta del juego de rol](docs/img/tarjeta.jpeg)