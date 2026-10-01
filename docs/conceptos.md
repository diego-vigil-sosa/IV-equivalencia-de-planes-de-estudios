# Conceptos

Este documento define los términos del dominio que usan el README, las historias de usuario y los milestones. Es la **única fuente** de estas definiciones: si otro documento necesita una de estas reglas, enlaza aquí en lugar de repetirla.

Las definiciones describen el problema, no la solución. Cómo el sistema calcula, guarda o muestra cada concepto se explica en la [lógica de negocio](../README.md#lógica-de-negocio).

## Marco normativo

Las definiciones de equivalencia se apoyan en tres fuentes:

- **[Real Decreto 822/2021](https://www.boe.es/buscar/act.php?id=BOE-A-2021-15781), art. 10.** Regula el reconocimiento de créditos entre títulos universitarios oficiales y encarga a cada universidad aprobar su propia normativa. Estas normativas usan la misma fórmula: la adecuación entre las competencias y conocimientos asociados a las asignaturas cursadas y los previstos en el plan de estudios.
- **[Normas del programa SICUE (CRUE)](https://www.crue.org/sicue/).** Fijan el acuerdo académico, su plazo de modificación y el mínimo de ECTS, y exigen que el intercambio se adecúe al perfil curricular del estudiante.
- **[Reglamento de reconocimiento de créditos en movilidad nacional de la ETSIIT](https://etsiit.ugr.es/sites/centros/etsiit/public/inline-files/Reglamento_Reconocimiento_Nacional_ETSIIT_2021_0.pdf), Anexo I.**
  - **I.2.1:** admite correspondencias entre una o varias asignaturas de destino y una o varias asignaturas de origen.
  - **I.2.3–I.2.4:** permite reconocer créditos cursados en destino como optatividad genérica, sin exigir que se correspondan con una optativa concreta del plan de origen.

## Entidades

### Guía docente

Documento público que describe una asignatura en un curso académico concreto. De cada guía se extraen:

- **Identificación:** universidad, centro, titulación, nombre, curso, semestre y curso académico de la guía.
- **ECTS.**
- **Carácter:** básica (troncal), obligatoria u optativa. En este proyecto, las básicas y las obligatorias se tratan igual: ambas deben cubrirse para que un plan sea [completo](#plan-válido-y-plan-completo). En adelante, «obligatoria» incluye las básicas.
- **Competencias:** la sección de competencias. Si la guía las expresa como resultados de aprendizaje, se usan estos.
- **Contenidos:** el temario teórico y práctico.

Las secciones de metodología, evaluación y bibliografía no se usan. Describen cómo se enseña y se evalúa, no qué se aprende, y la normativa compara competencias y conocimientos.

Las guías se publican de nuevo cada curso académico y pueden cambiar (ver [precedente vigente](#precedente-vigente)).

### Asignatura de origen y asignatura de destino

Una **asignatura de origen** pertenece al plan de estudios de la titulación del estudiante en su universidad. Su información es la de su guía docente.

Una **asignatura de destino** pertenece a la universidad de destino y se oferta en el semestre o semestres de la estancia. Además de su guía docente, tiene datos de oferta: semestre, horario y plazas para estudiantes de intercambio. Estos datos determinan si es [viable](#asignatura-viable-y-no-viable) y suelen conocerse tarde.

### Estancia

Periodo de intercambio: **medio curso** (un semestre) o **curso completo**. Determina el [mínimo de ECTS](#mínimo-de-ects) y qué asignaturas de destino pueden elegirse.

### Asignaturas que me faltan

Subconjunto de las asignaturas de origen aún no superadas que el estudiante quiere cursar durante la estancia y que, por tanto, quiere sustituir por asignaturas de destino. No son necesariamente todas las pendientes: el estudiante decide cuáles incluye (por ejemplo, puede dejar fuera el Trabajo Fin de Grado).

Pueden incluir optativas. Una optativa de origen se puede cubrir con cualquier asignatura de destino con ECTS suficientes (ver [correspondencia](#correspondencia)).

En un plan, cada asignatura que me falta acaba como [cubierta](#asignatura-cubierta) o como [cursada en origen](#asignatura-cursada-en-origen).

### Asignatura cursada en origen

Asignatura que me falta que el plan no cubre y que el estudiante cursará en su universidad de origen, fuera del acuerdo académico (por ejemplo, con evaluación única final, o en un semestre en que no esté de intercambio).

- No aparece en el acuerdo académico.
- **No cuenta** para el mínimo de ECTS, que solo se refiere a lo que se cursa en destino.
- Sí cuenta en el [grado de equivalencia](#grado-de-equivalencia): forma parte del total y, al no estar cubierta, lo reduce.
- Si es obligatoria, el plan no es [completo](#plan-válido-y-plan-completo), aunque puede ser válido.

### Universidad de destino candidata y elegida

Las plazas SICUE se ofertan mediante convenios bilaterales entre centros, así que un destino es, en realidad, un centro y una titulación de otra universidad.

- **Candidata:** destino con convenio con el centro de origen para la titulación del estudiante, que el estudiante está considerando antes de solicitar plaza. Sobre una candidata solo se calcula la [cobertura del destino](#cobertura-de-un-destino), para comparar destinos.
- **Elegida:** destino en el que el estudiante tiene plaza adjudicada. Es el único destino sobre el que se construyen [planes](#plan).

Un estudiante puede tener muchas candidatas y, como máximo, una elegida.

### Acuerdo académico

Documento oficial que recoge las asignaturas de origen y de destino del intercambio. Lo firman el estudiante y los coordinadores SICUE de ambos centros. Una vez firmado es vinculante: lo que el estudiante curse en destino se reconoce automáticamente en origen, y solo puede modificarse durante el primer mes desde el inicio del semestre ([normas SICUE](https://www.crue.org/sicue/)).

Relación con el plan: un **plan** es una propuesta del contenido de un acuerdo. Sus correspondencias son las filas del acuerdo; las asignaturas cursadas en origen no aparecen en él. El proyecto genera y justifica planes, pero no firma ni sustituye al coordinador de origen: es su firma la que decide si las asignaturas son equivalentes.

Las correspondencias de los acuerdos ya firmados son [precedentes](#precedente) para los estudiantes posteriores.

## Reglas de equivalencia

### Similitud y umbral

La **similitud** es una medida entre 0 y 1 de cuánto se parecen las competencias y los contenidos de dos asignaturas (o de dos grupos de asignaturas). Puede referirse a cada una de las dos dimensiones por separado o a ambas en conjunto.

El **umbral** es el valor mínimo de similitud a partir del cual se considera que hay adecuación entre asignaturas.

Cómo se calculan ambas cosas se explica en la [lógica de negocio](../README.md#lógica-de-negocio).

### Equivalencia

Relación entre asignaturas de origen y de destino que permite reconocer unas por otras. Se juzga por la **adecuación de sus competencias y contenidos**, según el [marco normativo](#marco-normativo), y no por el nombre, el código ni el curso: dos asignaturas con el mismo nombre pueden no ser equivalentes, y dos con nombres distintos pueden serlo.

En este proyecto, un grupo de asignaturas de origen es equivalente a un grupo de asignaturas de destino cuando su similitud alcanza el umbral o cuando un coordinador ya lo aceptó con las mismas guías ([precedente vigente](#precedente-vigente)). La equivalencia se concreta en [correspondencias](#correspondencia). La última palabra la tiene el coordinador de origen al firmar el acuerdo.

### Correspondencia

Relación entre un grupo no vacío de asignaturas de origen y un grupo no vacío de asignaturas de destino. Admite cuatro formas: una a una, una a varias, varias a una y varias a varias (Reglamento de la ETSIIT, Anexo I.2.1).

Una correspondencia es válida si cumple:

1. **Similitud:** la similitud entre los dos grupos alcanza el umbral. No se exige en dos casos:
   - *El grupo de origen solo contiene optativas.* Los créditos de destino pueden reconocerse como optatividad genérica (Reglamento de la ETSIIT, Anexo I.2.3–I.2.4), así que no hace falta adecuación con una optativa concreta.
   - *La correspondencia coincide con un [precedente vigente](#precedente-vigente).* La similitud solo estima el juicio del coordinador; el precedente es ese juicio, emitido sobre las mismas guías.
2. **ECTS:** la suma de ECTS del grupo de destino es igual o mayor que la del grupo de origen.
3. **Viabilidad:** todas sus asignaturas de destino son [viables](#asignatura-viable-y-no-viable).

Además, dentro de un plan, **cada asignatura, de origen o de destino, forma parte como máximo de una correspondencia**.

### Asignatura cubierta

Asignatura de origen que pertenece al grupo de origen de una correspondencia del plan. La cobertura es total o no existe: no hay coberturas parciales. Si los ECTS de destino no llegan, no hay correspondencia y la asignatura no está cubierta.

### Equivalente plausible

Una asignatura de destino es **equivalente plausible** de una asignatura de origen si se cumple alguna de estas condiciones:

- la similitud de esa pareja alcanza el umbral;
- la asignatura de origen es optativa (en ese caso, cualquier asignatura de destino lo es);
- ambas forman parte de un mismo precedente vigente.

Es una condición sobre la pareja aislada: no tiene en cuenta ECTS, viabilidad ni el resto del plan. Tener un equivalente plausible no garantiza que la asignatura quede cubierta, porque puede no tener ECTS suficientes o estar ya usada en otra correspondencia.

### Pareja débil

Equivalente plausible con riesgo de que el coordinador no la acepte. Toda pareja débil es plausible; lo que la distingue es que cumple al menos una de estas condiciones:

- **Su similitud supera el umbral por poco.** La similitud es una estimación del juicio del coordinador, y cerca del umbral es donde más se equivoca. El margen que se considera «poco» se fija en la [validación](../README.md#validación).
- **Una de las dos dimensiones, por separado, no alcanza el umbral** (por ejemplo, contenidos parecidos pero competencias distintas). La normativa exige adecuación en competencias *y* en conocimientos, así que parecerse solo en una no basta.

Solo se aplica a parejas cuya plausibilidad depende de la similitud: no puede ser débil una pareja con asignatura de origen optativa ni una que forme parte de un precedente vigente.

El **porqué** de una pareja débil es lo que el estudiante necesita para decidir si la propone y cómo justificarla ante el coordinador: qué dimensión falla y por cuánto, en qué coinciden ambas asignaturas y qué tiene la de origen que la de destino no cubre.

## Planes

### Plan

Propuesta de acuerdo académico para una universidad de destino elegida y una estancia. Contiene:

- un conjunto de [correspondencias](#correspondencia);
- un conjunto de [asignaturas cursadas en origen](#asignatura-cursada-en-origen).

Cada asignatura que me falta aparece exactamente una vez: cubierta por una correspondencia o como cursada en origen. Toda asignatura de destino del plan pertenece a una correspondencia.

### Plan válido y plan completo

Un plan es **válido** si:

1. todas sus correspondencias son válidas (incluida la viabilidad, que abarca la compatibilidad de horarios);
2. la suma de ECTS de sus asignaturas de destino alcanza el [mínimo de ECTS](#mínimo-de-ects).

Un plan válido puede presentarse al coordinador, aunque deje asignaturas para cursar en origen.

Un plan es **completo** si es válido y además cubre **todas las asignaturas obligatorias** de las asignaturas que me faltan, es decir, si no obliga a cursar ninguna obligatoria en origen. Las optativas pueden quedar sin cubrir.

Por ejemplo, si una obligatoria no tiene equivalente y el estudiante la cursa en origen con evaluación única final (la salida de Pablo con Análisis Funcional), el plan es válido, pero no completo.

### Grado de equivalencia

Porcentaje de ECTS de origen cubiertos:

> grado de equivalencia = ECTS de las asignaturas cubiertas / ECTS de las asignaturas que me faltan × 100

Se cuentan los ECTS de origen, no los de destino: cursar en destino más créditos de los necesarios no lo aumenta. Por ejemplo, si me faltan 5 asignaturas de 6 ECTS y el plan cubre 4, el grado es del 80 %.

Un plan válido con grado del 100 % es siempre completo. Un plan completo puede tener un grado menor si deja optativas sin cubrir.

### Mínimo de ECTS

Créditos mínimos que el estudiante debe cursar en destino según las [normas SICUE](https://www.crue.org/sicue/):

| Estancia | Mínimo |
|---|---|
| Medio curso | 24 ECTS |
| Curso completo | 45 ECTS |

Se cuentan los ECTS de las asignaturas de destino del plan. Las asignaturas cursadas en origen no cuentan.

### Cobertura de un destino

Para una universidad de destino (candidata o elegida) y unas asignaturas que me faltan, la cobertura indica:

- qué asignaturas que me faltan **no tienen ningún equivalente plausible** entre las asignaturas que ese destino oferta en la estancia;
- qué porcentaje de los ECTS que me faltan sí lo tiene.

Es una estimación optimista del grado alcanzable: no comprueba ECTS, plazas, horarios ni que dos asignaturas de origen compitan por el mismo equivalente. Sirve para descartar destinos antes de solicitar plaza, sin construir planes.

## Modificación y precedentes

### Asignatura viable y no viable

Una asignatura de destino es **viable** en un plan si el estudiante puede cursarla efectivamente. Deja de serlo por:

- **No se oferta:** no se imparte en el curso académico o semestre de la estancia, o no está abierta a estudiantes de intercambio.
- **Sin plazas:** no quedan plazas para estudiantes SICUE.
- **Conflicto de horario:** coincide en horario con otra asignatura de destino del plan.

Las dos primeras causas dependen solo de la asignatura; la tercera depende del plan, así que una asignatura puede ser viable en un plan y no en otro. La viabilidad cambia con el tiempo (se agotan plazas, se publican horarios), por eso un plan válido puede dejar de serlo.

### Sustituta

Cuando una asignatura de destino de un plan deja de ser viable, una **sustituta** es una asignatura de destino viable, o un grupo de ellas, que ocupa su lugar en la misma correspondencia de forma que:

1. la correspondencia sigue siendo válida;
2. el plan resultante sigue siendo válido;
3. el plan cubre exactamente las mismas asignaturas de origen, y por tanto mantiene el **mismo grado de equivalencia**.

El resto del plan no cambia, para que la modificación del acuerdo sea mínima. Si no hay sustituta, hay que replantear el plan, y el nuevo plan puede tener un grado menor; eso ya no es una sustitución.

### Precedente

Correspondencia que figura en un acuerdo académico **firmado** por un estudiante anterior con el mismo centro y titulación de origen y el mismo destino. Recoge la decisión del coordinador de origen sobre esas asignaturas, tomada con las guías docentes del curso académico en que se firmó.

Un precedente no obliga al coordinador actual, pero es la mejor evidencia disponible de que esas asignaturas son adecuadas: es una decisión real, no una estimación.

### Precedente vigente

Un precedente es **vigente** si la decisión que recoge sigue refiriéndose a las mismas asignaturas. Deja de serlo cuando:

- cambian las competencias o los contenidos de alguna de sus guías docentes respecto a la versión con que se firmó (los cambios en metodología, evaluación o bibliografía no le afectan);
- alguna de sus asignaturas se extingue de su plan de estudios.

Que una asignatura de destino no se oferte en la estancia actual no afecta a la vigencia, sino a la [viabilidad](#asignatura-viable-y-no-viable).

Un precedente que no es vigente se conserva como referencia, pero no exime de la condición de similitud.