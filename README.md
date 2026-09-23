# Análisis de equivalencia entre planes de estudio de universidades diferentes

## Problema

### Contexto

Soy un estudiante de Erasmus que ha tenido problemas con el proceso de elaboración del plan de estudios en la universidad de acogida.

### Descripción del proceso actual

Seleccionar, en la universidad de acogida, asignaturas equivalentes a las del plan de estudios de la universidad de origen es un proceso agotador. El estudiante tiene que:

1. Leer y analizar las guías docentes de todas las asignaturas que pueda elegir, así como las de su programa en la universidad de origen.
2. Seleccionar aquellas que desee y que considere equivalentes.

La equivalencia del plan elaborado por el estudiante solo se confirma tras el análisis y la decisión de la comisión de su titulación en la universidad de origen. Esta decisión se toma según criterios (resultados de aprendizaje) que son accesibles. En mi caso concreto, se aplican los reglamentos de la Facultad de Ciencias de la Universidad de Oporto (https://sigarra.up.pt/up/pt/legislacao_geral.ver_legislacao?p_nr=7172). En caso de que la facultad en cuestión no tenga criterios propios, o de que estos no sean públicos, se pueden usar los criterios oficiales del programa Erasmus+, si se trata de un intercambio de dicho programa (https://erasmus-plus.ec.europa.eu/resources-and-tools/mobility-and-learning-agreements/learning-agreements/studies-agreement-guidelines-ka131).

### Por qué es un problema

- El proceso es lento y puede tener que repetirse por falta de plazas en las asignaturas, conflictos de horarios, entre otras causas.
- Es un problema muy habitual entre los estudiantes de programas de intercambio, y supone una pérdida de tiempo y de oportunidades para que el estudiante pueda cursar las asignaturas que realmente desea.

### Datos disponibles

Las guías docentes de las asignaturas suelen ser públicas, al igual que otros criterios de equivalencia, como el número de créditos ECTS. Las guías están en formato textual en páginas web.

### Caso concreto

Antes de inscribirme en el programa *incoming* de la UGR, leí las guías docentes de una serie de asignaturas que me interesaban, que parecían tener equivalencia con las de mi programa, o ambas cosas. Fue un proceso largo y no conseguí tomar una decisión con confianza, porque en ese momento no conocía los reglamentos de reconocimiento de créditos de asignaturas cursadas fuera de mi universidad. Por ello, recurrí a un servicio de inteligencia artificial de pago (22,14 €) para que me ayudara a elaborar un plan. Con su ayuda, elaboré un plan que me satisfacía y que tenía aproximadamente un 70 % de equivalencia con el plan que habría cursado si hubiera hecho el semestre en Portugal.

En la universidad de origen hay 4 asignaturas obligatorias y 1 optativa. La comparación debe hacerse entre esas asignaturas y un grupo de asignaturas escogidas por el estudiante, de modo que se alcance un mínimo de créditos ECTS igual al de las asignaturas de la universidad de origen.

**Asignaturas de la ETSIIT que podía escoger por año del grado en el primer semestre**

| Curso | Asignaturas en el 1er semestre |
|---|---|
| 1º | 5 (todas troncales) |
| 2º | 5 (todas obligatorias) |
| 3º | 5 (comunes; las de especialidad son del 2º semestre) |
| 4º | 28: 15 obligatorias de especialidad (3 por mención) + 13 optativas de especialidad |
| **Total** | **43** |

**Atención: soy alumno de último año de la Licenciatura en Inteligencia Artificial y Ciencia de Datos (FCUP), por lo que mis opciones en la ETSIIT se limitan a las asignaturas de 3º y 4º del grado, es decir, 33 asignaturas en total. C(33, 5) = 237 336**

**Plan de estudios en la FCUP:**

| Código | Asignatura | Semestre | ECTS |
|---|---|---|---|
| CC3043 | Aprendizagem Computacional II | 1S | 6 |
| CC3006 | Interação Pessoa-Máquina | 1S | 6 |
| CC3042 | Introdução aos Sistemas Inteligentes e Autónomos | 1S | 6 |
| CC3044 | Laboratório de IA e CD | 1S | 6 |
| M3023 | Modelação e Otimização | 1S | 6 |

**Plan de estudios inicial en la ETSIIT (equivalencia estimada: ~70 %):**

| Código | Asignatura | Semestre | ECTS |
|---|---|---|---|
| 296114L | Bases de Datos Distribuidas | 1S | 6 |
| 296114F | Desarrollo Basado en Agentes | 1S | 6 |
| 296114N | Infraestructura Virtual | 1S | 6 |
| 296114K | Inteligencia de Negocio | 1S | 6 |
| 296114B | Visión por Computador | 1S | 6 |

#### Primer cambio: falta de plazas

Mi facultad aceptó el plan. Sin embargo, cuando la ETSIIT se puso en contacto conmigo para la matrícula, no quedaban plazas en dos de las asignaturas: Inteligencia de Negocio y Visión por Computador. Tuve que elegir dos asignaturas nuevas dentro de un grupo de opciones mucho más limitado, y el análisis de la IA indicó una caída drástica de la equivalencia, hasta aproximadamente un 40 %. Las asignaturas que escogí como sustitutas fueron:

| Código | Asignatura | Semestre | ECTS |
|---|---|---|---|
| 2961132 | Diseño y Desarrollo de Sistemas de Información | 1S | 6 |
| 296114A | Procesadores de Lenguajes | 1S | 6 |

La ETSIIT aceptó el cambio. No obstante, como no sabía cómo funcionaba el proceso de modificación del plan de estudios, solicité el cambio en la plataforma de mi facultad, pero nunca llegué a enviar personalmente el documento correspondiente a todas las partes implicadas (Relaciones Internacionales de la ETSIIT, Relaciones Internacionales de la FCUP y la directora de mi titulación en la FCUP). Y es que, efectivamente, es el propio estudiante quien tiene que hacer de puente entre todas ellas.

#### Segundo cambio: conflicto de horarios

Al llegar a la ETSIIT y publicarse los horarios, descubrí un conflicto de horarios causado por Bases de Datos Distribuidas, lo que me obligó a modificar mi plan de estudios de nuevo, esta vez con todavía menos opciones. Finalmente, escogí:

| Código | Asignatura | Semestre | ECTS |
|---|---|---|---|
| 2961135 | Ingeniería de Servidores | 1S | 6 |

El nuevo análisis de la IA indicó una equivalencia de aproximadamente un 25 %.

**Plan de estudios final en la ETSIIT (equivalencia estimada: ~25 %):**

| Código | Asignatura | Semestre | ECTS |
|---|---|---|---|
| 296114F | Desarrollo Basado en Agentes | 1S | 6 |
| 296114N | Infraestructura Virtual | 1S | 6 |
| 2961132 | Diseño y Desarrollo de Sistemas de Información | 1S | 6 |
| 296114A | Procesadores de Lenguajes | 1S | 6 |
| 2961135 | Ingeniería de Servidores | 1S | 6 |

Actualmente estoy a la espera de que mi facultad me comunique si las asignaturas que estoy cursando en la ETSIIT serán reconocidas o no.

#### Conclusión

La ineficiencia del proceso de selección de asignaturas no fue la única causa de este problema, pero sí es la única que está bajo el control del estudiante. Por lo tanto, es la única que puede resolverse mediante un proyecto de desarrollo de software.

## Lógica de negocio

Para resolver este problema sin usar API externas se pueden emplear algoritmos y etapas de comparación de texto libre implementadas por el developer como:

- Bag-of-words + TF-IDF + similitud del coseno
- Índice de Jaccard sobre conjuntos de términos o n-gramas (*shingling*)
- Preprocesamiento del texto
- Comparación por secciones

Para comprobar el éxito de la solución, puedo usar mi propio caso, preguntar a la directora de mi carrera si un determinado plan sería aceptado o usar el caso de otros alumnos, que no son pocos.

![Fotografía de la tarjeta de rol](tarjeta.jpeg)

## Documentación adicional

- [Configuración de git y GitHub](docs/configuracion.md)