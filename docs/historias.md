# Historias de usuario

Todas las historias son problemas de [Pablo](personas.md), que salen del [user journey](user-journeys.md#estudiante-sicue-de-curso-completo-ugr--upm), y usan la definición de *equivalencia* de [Conceptos](conceptos.md#equivalencia): se juzga por competencias y contenidos, no por el nombre de la asignatura.

Las [guías docentes](conceptos.md#guía-docente) son la fuente de datos común a todas. Son públicas y están en las webs de cada universidad, una por asignatura y curso académico, en texto y con una estructura muy similar. De ellas se usan las competencias, los contenidos, los ECTS y el carácter.

### HU1. Plan válido ([#2](https://github.com/diego-vigil-sosa/IV-equivalencia-de-planes-de-estudios/issues/2))

**Problema.** Pablo tardó entre 6 y 8 horas en combinar a mano las [asignaturas que le faltan](conceptos.md#asignaturas-que-me-faltan) con las de la UPM. Aun así, no sabe si su combinación es un [plan válido](conceptos.md#plan-válido-y-plan-completo), ni si hay otra con mayor [grado de equivalencia](conceptos.md#grado-de-equivalencia): el número de combinaciones posibles (ver [Escala del problema](../README.md#escala-del-problema)) hace imposible explorarlas todas. Cuando una obligatoria no tiene equivalente, tiene que dar él solo con la salida de [cursarla en origen](conceptos.md#asignatura-cursada-en-origen), como hizo con Análisis Funcional mediante evaluación única final.

**Datos.**

- Guías docentes de las asignaturas que le faltan y de las que oferta el destino elegido.
- Oferta del destino elegido para la estancia (semestre, horario y plazas para estudiantes de intercambio), publicada en la web del centro de destino. Los horarios y las plazas suelen conocerse tarde.
- Asignaturas que le faltan: las elige el estudiante a partir del plan de estudios de su titulación.
- [Mínimo de ECTS](conceptos.md#mínimo-de-ects) según la estancia, de las [normas SICUE](https://www.crue.org/sicue/).
- Caso real: el acuerdo académico firmado de Pablo (UGR → UPM, curso completo, anonimizado).

**Contexto.** [Etapa 2 del user journey: elaboración del acuerdo académico](user-journeys.md#2-elaboración-del-acuerdo-académico).

### HU2. Cobertura de cada destino ([#3](https://github.com/diego-vigil-sosa/IV-equivalencia-de-planes-de-estudios/issues/3))

**Problema.** Pablo eligió destino sin saber cuáles de las asignaturas que le faltan no tenían ningún [equivalente plausible](conceptos.md#equivalente-plausible) en él. Lo descubrió después de leer las guías y lo confirmó en la firma, cuando ya no podía cambiar de destino: Análisis Funcional no tenía equivalente en la UPM. El riesgo se concentra en la titulación con menos oferta en destino (Matemáticas, en una universidad elegida por su oferta de Informática). El problema se da con cada universidad candidata, antes de elegir, y con la elegida, después (ver [cobertura de un destino](conceptos.md#cobertura-de-un-destino)).

**Datos.**

- Guías docentes de las asignaturas que le faltan y de las que oferta cada destino en la estancia.
- Destinos candidatos: las plazas de la convocatoria SICUE de su centro, que publica el centro de origen.
- Caso real: en el acuerdo firmado de Pablo, todas las asignaturas de origen tienen equivalente en la UPM salvo Análisis Funcional.

**Contexto.** [Etapa 1 del user journey: elección de destino](user-journeys.md#1-elección-de-destino) y [etapa 2: elaboración del acuerdo académico](user-journeys.md#2-elaboración-del-acuerdo-académico).

### HU3. Parejas débiles antes de la firma ([#4](https://github.com/diego-vigil-sosa/IV-equivalencia-de-planes-de-estudios/issues/4))

**Problema.** Pablo no supo qué parejas de su acuerdo podía rechazar el coordinador hasta presentarlo. El coordinador de origen cuestionó Análisis Funcional porque «la guía no coincidía del todo con la de la UGR», y hicieron falta 2 versiones del acuerdo hasta la firma. Sin saber qué [pareja es débil](conceptos.md#pareja-débil) y por qué (qué dimensión falla, en qué coinciden las asignaturas y qué no cubre la de destino), no puede corregirla ni justificarla antes de la firma.

**Datos.**

- Competencias y contenidos de las guías docentes de cada pareja del acuerdo.
- Caso real: la pareja de Análisis Funcional que el coordinador de origen no aceptó en el acuerdo de Pablo.

**Contexto.** [Etapa 3 del user journey: firma del coordinador](user-journeys.md#3-firma-del-coordinador).

### HU4. Precedentes vigentes ([#5](https://github.com/diego-vigil-sosa/IV-equivalencia-de-planes-de-estudios/issues/5))

**Problema.** Pablo hizo el análisis solo: los coordinadores validan, pero no recomiendan. Repitió desde cero un trabajo que otros estudiantes del mismo centro y destino ya habían hecho y que el coordinador ya había aprobado, porque esos acuerdos no son públicos. Aunque los hubiera conseguido, no sabría cuáles siguen valiendo, porque las guías docentes cambian cada curso (ver [precedente vigente](conceptos.md#precedente-vigente)).

*Necesidad deducida:* el estudiante no la expresó en la entrevista.

**Datos.**

- Acuerdos académicos firmados de estudiantes anteriores con el mismo centro de origen y destino. No son públicos: los aportan el coordinador de origen o los propios estudiantes, como el de Pablo (anonimizado).
- Guías docentes del curso académico en que se firmó cada acuerdo y del curso actual.

**Contexto.** [Etapa 2 del user journey: elaboración del acuerdo académico](user-journeys.md#2-elaboración-del-acuerdo-académico).

### HU5. Sustitutas equivalentes ([#6](https://github.com/diego-vigil-sosa/IV-equivalencia-de-planes-de-estudios/issues/6))

**Problema.** La semana antes de empezar las clases, un conflicto de horario hizo que una asignatura del acuerdo de Pablo dejara de ser [viable](conceptos.md#asignatura-viable-y-no-viable). Tuvo que encontrar una [sustituta](conceptos.md#sustituta) dentro del plazo de modificación del acuerdo (el primer mes del semestre). En su caso fue rápido porque era de Informática, con muchas alternativas en la UPM; con una asignatura con pocas alternativas habría tenido que rehacer el análisis con prisa, sin saber siquiera si existe una sustituta.

**Datos.**

- Oferta del destino elegido (horarios y plazas para estudiantes de intercambio), publicada en la web del centro de destino poco antes del semestre.
- Guías docentes de las asignaturas de destino que siguen siendo viables.
- El acuerdo académico firmado que hay que modificar.
- Caso real: la modificación del acuerdo de Pablo por un conflicto de horario en el primer cuatrimestre.

**Contexto.** [Etapa 4 del user journey: modificación del acuerdo](user-journeys.md#4-modificación-del-acuerdo).
