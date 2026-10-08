# Milestones

Los dos milestones avanzan en la misma historia de usuario, la [HU1](historias-de-usuario.md#hu1-elección-de-destino-3).

## M0. Código comprobado sintácticamente

**Historia de usuario:** [HU1](https://github.com/diego-vigil-sosa/IV-equivalencia-de-planes-de-estudios/issues/3). **En GitHub:** [M0](https://github.com/diego-vigil-sosa/IV-equivalencia-de-planes-de-estudios/milestone/1).

### Producto

Código fuente que representa el problema de la HU1, sin lógica de negocio, y un fichero `iv.yaml` con las claves `lenguaje` (el lenguaje elegido) y `entidad` (un fichero del código). El lenguaje se elige en este milestone.

### Entrega

Un pull request a `main` desde una rama, con `[IV-26-27]` en el título y asociado al milestone M0 en GitHub. Antes del código se abren issues que planteen los problemas de la HU1 (no tareas), enlazados a ella y asignados al M0; cada commit referencia el issue que resuelve.

El README indica el lenguaje elegido, con su justificación, y la orden que comprueba la sintaxis del código.

### Validación

- La orden del README comprueba la sintaxis del código sin errores.
- `iv.yaml` es YAML válido y su clave `entidad` apunta a un fichero que existe.
- Al revisar el pull request, cada elemento del código procede de un issue del M0.
- Con el código se puede representar el caso real de la HU1 (las asignaturas que le faltaban a Pablo en la UGR y la oferta de la UPM) sin añadir nada.

## M1. Código con tests

**Historia de usuario:** [HU1](https://github.com/diego-vigil-sosa/IV-equivalencia-de-planes-de-estudios/issues/3). **En GitHub:** [M1](https://github.com/diego-vigil-sosa/IV-equivalencia-de-planes-de-estudios/milestone/2).

### Producto

El código del M0 con la lógica de negocio que resuelve la HU1 y tests que se ejecutan con un gestor de tareas.

### Entrega

Un pull request a `main` asociado al milestone M1 en GitHub, que cierra el issue de la HU1. Los issues del M1 plantean los problemas de la HU1 que quedan por resolver; cada commit referencia el issue que resuelve.

### Validación

- La tarea de tests del gestor de tareas termina sin errores.
- Los tests comprueban qué asignaturas de origen se quedan sin equivalente en un destino y usan el caso real de la HU1 como primer caso de [validación](../README.md#validación): uno positivo (las asignaturas con equivalente en la UPM) y uno negativo (Análisis Funcional).
