# 1. Introducción

## 1.1. Objeto del documento

El presente documento describe la plataforma web desarrollada por AYESA-DIGITAL en la tarea T3.4.4 del proyecto SOFIA. La plataforma conecta el modelo de inteligencia artificial de la línea L3.4 con las herramientas de integración continua que utilizan los equipos de desarrollo.

A partir de los datos de un repositorio de código, la plataforma modifica automáticamente su pipeline de integración y despliegue continuos (CI/CD) para incorporar el modelo de predicción. Una vez modificado, el pipeline consulta al modelo en cada ejecución y omite la fase de compilación y empaquetado (*build*) cuando no es necesaria, lo que reduce el tiempo de ejecución y el consumo de recursos.

## 1.2. Contexto: la línea L3.4

La línea L3.4 del proyecto persigue aplicar la inteligencia artificial a los flujos de integración y despliegue continuos de las factorías de software, con el fin de reducir el tiempo que se invierte en crearlos y configurarlos y de automatizar su definición.

La línea se articula en cuatro tareas:

| Tarea | Título | Resultado |
|---|---|---|
| T3.4.1 | Generación de un dataset con información de operaciones de integración y despliegue por tipología de artefacto haciendo uso de minería de repositorios | E3.4.1 |
| T3.4.2 | Definición de metamodelos de operaciones de integración | E3.4.2 |
| T3.4.3 | Generación de un modelo de machine learning para un motor de recomendación de operaciones de integración y despliegue de artefactos software | E3.4.3 |
| T3.4.4 | Desarrollo de conectores del metamodelo con las herramientas de integración seleccionadas | E3.4.4 (este documento) |

*Tabla 1. Tareas de la línea L3.4.*

La tarea T3.4.4 cierra la línea: su objetivo es que las operaciones que propone el modelo de machine learning se apliquen efectivamente en las herramientas de integración y despliegue. Da respuesta, además, al objetivo O3.4.3 de la línea: disponer de una plataforma web que habilite el uso de los resultados obtenidos.

## 1.3. Estructura del documento

- El apartado 2 presenta la solución propuesta: el enfoque adoptado, la arquitectura, el modelo de predicción y el código que se incorpora al pipeline.
- El apartado 3 describe el funcionamiento de la plataforma paso a paso y su resultado en un pipeline real.
- El apartado 4 recoge los resultados obtenidos: las características de la plataforma y los indicadores de la línea.
- El apartado 5 expone las conclusiones.
- El apartado 6 recoge las referencias.
