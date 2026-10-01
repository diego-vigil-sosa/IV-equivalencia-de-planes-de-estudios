# Milestones

## M0. Modelo del problema para la cobertura de un destino

**Historia de usuario:** [HU2](https://github.com/diego-vigil-sosa/IV-equivalencia-de-planes-de-estudios/issues/3). **En GitHub:** [M0](https://github.com/diego-vigil-sosa/IV-equivalencia-de-planes-de-estudios/milestone/1).

### Producto

El modelo en código de los conceptos que necesita la HU2: entidades, objetos valor, excepciones y la interfaz de la operación que implementará el M1, sin lógica de negocio. El lenguaje se elige en este milestone, por consenso con quien lo desarrolle; por eso los nombres de fichero se dan sin extensión y son orientativos: la disposición final sigue las buenas prácticas del lenguaje elegido.

| Fichero | Contenido | Concepto |
|---|---|---|
| `src/equivalencias/guia_docente` | `GuiaDocente` (identificación, ECTS, carácter, competencias, contenidos) y `Caracter` (obligatoria u optativa; las básicas cuentan como obligatorias) | [Guía docente](conceptos.md#guía-docente) |
| `src/equivalencias/asignatura` | `AsignaturaOrigen` y `AsignaturaDestino`, cada una con su guía docente | [Asignatura de origen y de destino](conceptos.md#asignatura-de-origen-y-asignatura-de-destino) |
| `src/equivalencias/destino` | `Destino` (centro y titulación de otra universidad, con las asignaturas que oferta) y `Estancia` (medio curso o curso completo). Declara, sin implementarla, la operación que calcula la cobertura del destino para unas asignaturas que me faltan y una estancia | [Universidad de destino](conceptos.md#universidad-de-destino-candidata-y-elegida), [Estancia](conceptos.md#estancia) |
| `src/equivalencias/cobertura` | `Similitud` (valor entre 0 y 1, por dimensión y combinada) y `Cobertura` (asignaturas sin equivalente plausible y porcentaje de ECTS que sí lo tiene). Solo los tipos, sin cálculo | [Similitud y umbral](conceptos.md#similitud-y-umbral), [Cobertura de un destino](conceptos.md#cobertura-de-un-destino) |
| `src/equivalencias/errores` | Excepciones del dominio, dentro de la jerarquía estándar del lenguaje, para los valores que el dominio no admite (ver [Validación](#validación)) | — |
| `iv.yaml` | Claves `lenguaje` (el elegido) y `entidad` (el fichero de `Destino`) | — |

Las asignaturas que me faltan se representan como una colección de `AsignaturaOrigen`; no necesitan un tipo propio en este milestone.

`Destino` es la entidad del milestone: se identifica por universidad, centro y titulación, y su oferta cambia con el tiempo. `GuiaDocente`, `Caracter`, `Estancia`, `Similitud` y `Cobertura` son objetos valor: inmutables y definidos solo por su valor. Esta clasificación es una propuesta; quien desarrolle el milestone puede cambiarla si justifica la decisión en el issue correspondiente.

Quedan fuera del M0: correspondencias, planes, viabilidad (horarios y plazas) y precedentes. Se modelarán en el milestone de la historia que los necesite, igual que la similitud de un grupo de asignaturas, que solo aparece con las correspondencias. Tampoco hay gestor de tareas ni tests: llegan en el M1.

### Entrega

Un pull request a `main` desde una rama, con `[IV-26-27]` en el título y asociado al milestone M0 en GitHub. Antes del código se abren issues que planteen los problemas de la HU2 (no tareas), enlazados a ella y asignados al M0; cada commit referencia el issue que resuelve.

El pull request incluye el código de `src/equivalencias/`, el `iv.yaml` y, en el README, el lenguaje elegido con su justificación y la orden para comprobar que el código es sintácticamente correcto.

### Validación

La valida quien es propietario del repositorio al revisar el pull request, porque en el M0 todavía no hay tests:

- El código es sintácticamente correcto con la orden documentada en el README.
- `iv.yaml` es YAML válido y su clave `entidad` apunta a un fichero que existe.
- Cada entidad, objeto valor y atributo corresponde a un concepto de [Conceptos](conceptos.md) usado por la HU2, con el mismo nombre, y no hay ninguno sin concepto.
- Los objetos valor son inmutables y no admiten estados que el dominio no permite: ECTS no positivos, similitud fuera de [0, 1], un carácter o una estancia que no existen. Intentarlo lanza una excepción del dominio con un mensaje que indica el valor rechazado.
- Con el modelo se puede expresar el caso de Pablo (asignaturas que le faltan en la UGR y oferta de la UPM para un curso completo) sin añadir nada.
- El M1 puede implementar el cálculo de la cobertura sobre este modelo sin modelización adicional.

## M1. Cobertura de un destino

**Historia de usuario:** [HU2](https://github.com/diego-vigil-sosa/IV-equivalencia-de-planes-de-estudios/issues/3). **En GitHub:** [M1](https://github.com/diego-vigil-sosa/IV-equivalencia-de-planes-de-estudios/milestone/2).

### Producto

La lógica de negocio que calcula la cobertura de un destino a partir de las guías docentes, y sus tests.

| Fichero | Contenido |
|---|---|
| `src/equivalencias/similitud` | Similitud TF-IDF con coseno, por separado para competencias y contenidos, y similitud combinada w · sim(competencias) + (1 − w) · sim(contenidos), según la [lógica de negocio](../README.md#lógica-de-negocio) |
| `src/equivalencias/cobertura` | Cálculo de los equivalentes plausibles de cada asignatura que me falta y de la cobertura del destino, con θ y w como parámetros |
| `tests/` | Tests de la similitud y de la cobertura |
| `tests/datos/` | Competencias y contenidos de las guías docentes del caso de Pablo (UGR → UPM, anonimizado), en un formato estructurado. Extraer las guías de las páginas web queda fuera de este milestone |
| Fichero del gestor de tareas | Una tarea que ejecuta los tests |

### Entrega

Un pull request a `main` asociado al milestone M1 en GitHub, que cierra el issue de la HU2.

### Validación

La tarea de tests termina sin errores y los tests comprueban, como mínimo:

- **Similitud.** Dos guías idénticas tienen similitud 1; dos guías sin términos en común tienen similitud 0; el resultado no cambia al duplicar el texto de una guía (no depende de la longitud); un término que aparece en todas las guías no aumenta la similitud.
- **Reglas de cobertura.** Una optativa de origen siempre tiene equivalente plausible; una obligatoria lo tiene solo si alguna pareja alcanza θ; el porcentaje se calcula sobre ECTS de origen; un destino sin oferta da una cobertura del 0 %.
- **Caso de Pablo.** Todas las asignaturas de origen de su acuerdo firmado tienen un equivalente plausible en la UPM, y Análisis Funcional aparece como sin equivalente plausible. Es el primer caso de [validación](../README.md#validación): uno positivo y uno negativo. θ se fija sin usar el caso de Pablo, que se reserva para comprobarlo.
