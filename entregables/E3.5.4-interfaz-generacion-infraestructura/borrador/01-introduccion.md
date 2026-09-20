# 1. Introducción

## 1.1. Objeto del documento

El presente documento describe la interfaz de usuario desarrollada por AYESA-DIGITAL en la tarea T3.5.4 del proyecto SOFIA, cuyo propósito es permitir que cualquier usuario utilice el sistema de inteligencia artificial de la línea L3.5 para obtener, de forma automática, la infraestructura necesaria para desplegar un componente de software.

La aplicación resultante permite al usuario, a partir de los ficheros de registro (*logs*) de un servicio, obtener en tres pasos una estimación del consumo de CPU y memoria, la instancia de computación más económica capaz de soportar la carga y el código de infraestructura como código (IaC) listo para desplegarla.

## 1.2. Contexto: la línea L3.5

La línea L3.5 del proyecto persigue desarrollar un sistema de inteligencia artificial capaz de generar automáticamente la infraestructura necesaria para el despliegue de componentes de software, reduciendo el tiempo y el esfuerzo que requieren la creación y configuración de dicha infraestructura. Este proceso es hoy complejo y exige un conocimiento especializado en infraestructura y prácticas DevOps.

La línea se articula en cuatro tareas:

| Tarea | Título | Resultado |
|---|---|---|
| T3.5.1 | Análisis de tipologías de componentes de software y sus requerimientos de infraestructura | E3.5.1 |
| T3.5.2 | Investigación de las diferentes infraestructuras de despliegue | E3.5.2 |
| T3.5.3 | Desarrollo de un algoritmo de IA para la generación automática de infraestructura | E3.5.3 |
| T3.5.4 | Desarrollo de una interfaz de usuario para el sistema | E3.5.4 (este documento) |

*Tabla 1. Tareas de la línea L3.5.*

La tarea T3.5.4 cierra la línea: pone el algoritmo desarrollado en T3.5.3 al servicio de los usuarios mediante una interfaz que, según la memoria del proyecto, debe ser fácil de usar y permitir seleccionar la tipología de componente de software y la infraestructura de despliegue deseada.

## 1.3. Estructura del documento

- El apartado 2 presenta la solución propuesta: el enfoque adoptado, la arquitectura y los elementos principales del sistema.
- El apartado 3 describe el funcionamiento de la aplicación paso a paso.
- El apartado 4 recoge los resultados obtenidos: las características de la interfaz y los indicadores de la línea.
- El apartado 5 expone las conclusiones y las líneas de evolución.
- El apartado 6 recoge las referencias.
