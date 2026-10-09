# Milestones

Los dos milestones avanzan en la misma historia de usuario, la [HU1](historias-de-usuario.md#hu1-elección-de-destino-3). Los dos son internos.

## M0. Módulo base de la HU1

**Historia de usuario:** [HU1](https://github.com/diego-vigil-sosa/IV-equivalencia-de-planes-de-estudios/issues/3). **En GitHub:** [M0](https://github.com/diego-vigil-sosa/IV-equivalencia-de-planes-de-estudios/milestone/1).

### Producto

Un módulo de código en la rama principal del repositorio, en una carpeta dedicada al código. En él ya se encuentran, en código, las cosas con que trabaja la HU1: las asignaturas, con los datos de sus guías docentes; la universidad de origen, con el plan de estudios de la titulación del estudiante, del que salen las asignaturas que le faltan; y las universidades candidatas, con su oferta. En el M1, la lógica que determina qué asignaturas no tienen equivalente en cada candidata, y los tests de dicha lógica, importan este módulo y se basan en él.

### Validez

El M0 está bien si yo, que conozco el problema, reviso el código teniendo solo la HU1 como referencia y confirmo dos cosas: todo lo que utiliza la HU1 está en el código, y nada de lo que está en el código proviene de fuera de la HU1.

## M1. Módulo de equivalencia con tests

**Historia de usuario:** [HU1](https://github.com/diego-vigil-sosa/IV-equivalencia-de-planes-de-estudios/issues/3). **En GitHub:** [M1](https://github.com/diego-vigil-sosa/IV-equivalencia-de-planes-de-estudios/milestone/2).

### Producto

Un segundo módulo, ubicado en el mismo lugar que el del M0, que lo importa y contiene la lógica que compara guías docentes para determinar qué asignaturas no tienen equivalente en cada universidad candidata. Incluye los tests de esa lógica, en una carpeta específica para tests. Quien continúe el proyecto a partir de aquí, ya sea para avanzar en la HU2 o para llegar al estudiante, importa este módulo y utiliza la respuesta que ya ofrece a la HU1.

### Validez

La validez se comprueba automáticamente: el producto es válido si los tests pasan, y los tests usan el caso real de la HU1 como primer caso de [validación](../README.md#validación):

- positivo: las asignaturas de Pablo que tenían equivalente en la UPM no se quedan sin él;
- negativo: Análisis Funcional se queda sin equivalente en la UPM.
