# Historias de usuario

Las dos historias son problemas de [Pablo](personas.md) y salen de su [user journey](user-journeys.md#estudiante-sicue-de-curso-completo-ugr--upm). Están numeradas en el orden en que le ocurren: primero elige destino y después, con el destino ya elegido, construye el acuerdo académico.

En las dos, la equivalencia entre una asignatura de origen y una de destino se juzga como lo hace el coordinador de origen al firmar: por la adecuación de sus **competencias y** sus **contenidos**, no por el nombre (ver [Criterio de equivalencia](../README.md#criterio-de-equivalencia)). La normativa exige las dos cosas; parecerse solo en una no basta.

La fuente de datos común son las guías docentes. Son públicas y están en las webs de cada universidad, una por asignatura y curso académico, en texto y con una estructura muy similar. De ellas se usan las competencias, los contenidos, los ECTS y el carácter (obligatoria u optativa).

### HU1. Elección de destino ([#3](https://github.com/diego-vigil-sosa/IV-equivalencia-de-planes-de-estudios/issues/3))

**Problema.** Pablo eligió la UPM por la ciudad y por su oferta de Informática, sin saber cuáles de las asignaturas que le faltaban para terminar la carrera no tendrían allí ninguna asignatura que se les pareciera en competencias y contenidos. Lo descubrió al elaborar el acuerdo, cuando ya tenía el destino asignado y no podía cambiarlo: Análisis Funcional no tenía un equivalente claro en la UPM. El riesgo se concentra en la titulación con menos oferta en destino; en su doble grado, Matemáticas en una universidad elegida por su Informática. Para saberlo antes de elegir tendría que haber leído las guías de todas las universidades candidatas, y cada una supone decenas de guías (ver [Escala del problema](../README.md#escala-del-problema)).

Una asignatura de origen optativa no tiene este problema: cualquier asignatura de destino con ECTS suficientes puede incorporarse como optativa.

**Datos.**

- Asignaturas que le faltan: las elige el estudiante del plan de estudios de su titulación en origen.
- Guías docentes de las asignaturas que le faltan y de las que oferta cada universidad candidata.
- Universidades candidatas: las plazas de la convocatoria SICUE de su centro, que publica el centro de origen.
- Caso real: de las asignaturas que le faltaban a Pablo, todas tenían equivalente en la UPM salvo Análisis Funcional.

**Contexto.** [Etapa 1 del user journey: elección de destino](user-journeys.md#1-elección-de-destino).

### HU2. Construcción del acuerdo ([#2](https://github.com/diego-vigil-sosa/IV-equivalencia-de-planes-de-estudios/issues/2))

**Problema.** Con el destino ya elegido, Pablo tardó entre 6 y 8 horas en combinar a mano las asignaturas que le faltaban con las de la UPM. Aun así, no sabía si su combinación cumplía las reglas del acuerdo (ver [Criterio de equivalencia](../README.md#criterio-de-equivalencia)): que cada asignatura de origen quede cubierta por asignaturas de destino equivalentes con ECTS suficientes, que cada asignatura de destino cubra como máximo una de origen y que el total llegue al mínimo de ECTS de la estancia. Tampoco sabía si había otra combinación que cubriera más créditos, porque el número de combinaciones posibles hace imposible probarlas todas.

Para Análisis Funcional no encontró un equivalente claro. La asignatura de la UPM que propuso se parecía, pero el coordinador de origen la rechazó porque «la guía no coincidía del todo con la de la UGR», y hicieron falta 2 versiones del acuerdo hasta la firma. Pablo se enteró en la firma, después de haber invertido el tiempo de análisis. La salida fue cursar Análisis Funcional en la UGR mediante evaluación única final: el acuerdo puede dejar en origen una asignatura sin equivalente, pero él tuvo que dar solo con esa opción.

El mismo problema vuelve después de la firma. La semana antes de empezar las clases, un conflicto de horario hizo que una asignatura del acuerdo dejara de poder cursarse, y tuvo que rehacer la combinación con la oferta que quedaba y dentro del plazo de modificación (el primer mes del semestre).

**Datos.**

- Asignaturas que le faltan y guías docentes de esas asignaturas y de las que oferta el destino elegido.
- Oferta del destino elegido para la estancia (semestre, horario y plazas para estudiantes de intercambio), publicada en la web del centro de destino. Los horarios y las plazas suelen conocerse tarde.
- Mínimo de ECTS de la estancia según las [normas SICUE](https://www.crue.org/sicue/): 24 ECTS en medio curso y 45 en curso completo.
- Caso real: el acuerdo académico firmado de Pablo (UGR → UPM, curso completo, anonimizado), con la pareja de Análisis Funcional que el coordinador rechazó y la modificación por el conflicto de horario.

**Contexto.** [Etapa 2 del user journey: elaboración del acuerdo académico](user-journeys.md#2-elaboración-del-acuerdo-académico), [etapa 3: firma del coordinador](user-journeys.md#3-firma-del-coordinador) y [etapa 4: modificación del acuerdo](user-journeys.md#4-modificación-del-acuerdo).
