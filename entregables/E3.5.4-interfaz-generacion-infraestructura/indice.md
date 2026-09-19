# Índice · E3.5.4 Interfaz de usuario para el sistema de generación automática de infraestructura

**Estado:** propuesta del generador (v1, 2026-09-19), en revisión (buzón `001`).

**Cabecera:**
- `E3.5.4 Interfaz de usuario para el sistema de generación automática de infraestructura`
- `PT3 - L3.5. Investigación IA para generación automática de infraestructura para el despliegue de soluciones software de forma agnóstica - T3.5.4 Desarrollo de una interfaz de usuario para el sistema`

## Índice propuesto

| Nº | Sección | Contenido previsto | Fuente | Fichero de borrador |
|---|---|---|---|---|
| 1 | **Introducción** | | | `01-introduccion.md` |
| 1.1 | Contexto: proyecto SOFIA y línea L3.5 | Objetivo de la línea, sistema de IA agnóstico de la infraestructura (on-premise, nube, contenedores). Diferencia con L3.4: allí la infraestructura de integración y despliegue continuo del desarrollo; aquí la infraestructura de puesta en producción. | Memoria §2.2.12.1, L3.5 (pág. 59) | |
| 1.2 | Objeto y alcance del entregable | Qué cubre T3.5.4 y qué no (el algoritmo es E3.5.3). Relación con E3.5.1, E3.5.2 y E3.5.3. | Memoria T3.5.4 (pág. 60) | |
| 1.3 | Estructura del documento | Breve guía de las secciones. | — | |
| 2 | **Solución propuesta** | | | `02-solucion-propuesta.md` |
| 2.1 | Requisitos de la interfaz | Facilidad de uso; selección de la tipología de componente y de la infraestructura de despliegue deseada; uso por un perfil no experto en infraestructura (la IA parte de la caracterización del componente). | Memoria T3.5.4; §2.2.12.2 | |
| 2.2 | Arquitectura general del sistema | Interfaz, servicio del algoritmo de IA (E3.5.3) y conexión con las herramientas de despliegue. Figura de arquitectura. | [PENDIENTE: usuario] | |
| 2.3 | Tecnologías empleadas | Frontend, backend, despliegue de la propia aplicación. | [PENDIENTE: usuario] | |
| 3 | **Diseño e implementación de la interfaz** | | | `03-diseno-implementacion.md` |
| 3.1 | Flujo de uso | Recorrido de principio a fin: caracterizar el componente → elegir infraestructura destino → generar → revisar → exportar o desplegar. | [PENDIENTE: usuario] | |
| 3.2 | Caracterización del componente software | Cómo se introduce la tipología y las características del componente; tipologías disponibles. | E3.5.1 [PENDIENTE: documento] | |
| 3.3 | Selección de la infraestructura de despliegue | Destinos soportados (on-premise, AWS, Kubernetes, contenedores u otros) y cómo se eligen. Recomendación automática, si la hay. | E3.5.2 [PENDIENTE: documento] | |
| 3.4 | Integración con el algoritmo de IA | Cómo invoca la interfaz al algoritmo de E3.5.3, qué le envía y qué recibe. | E3.5.3 [PENDIENTE: documento] | |
| 3.5 | Presentación, revisión y exportación de la infraestructura generada | Visualización de los artefactos generados (p. ej. ficheros IaC o manifiestos), edición/validación por el usuario y descarga. | [PENDIENTE: usuario] | |
| 3.6 | Integración con herramientas de despliegue existentes | Respuesta al segundo reto tecnológico de la línea. | Memoria L3.5, retos (pág. 60) | |
| 3.7 | Supervisión humana y trazabilidad | *Opcional, a confirmar.* Aspectos de IA fiable aplicados a la interfaz: el usuario revisa y aprueba antes de desplegar, registro de lo generado, explicación de la propuesta. Solo si lo implementado lo respalda. | Memoria OG1, §1 (guías de IA Fiable de la CE) | |
| 4 | **Resultados obtenidos** | | | `04-resultados.md` |
| 4.1 | Características de la interfaz | Funcionalidades finales, con capturas de pantalla. | [PENDIENTE: capturas] | |
| 4.2 | Indicadores logrados | Tabla con I3.5.1, I3.5.2 e I3.5.3: fórmula, valor objetivo, valor obtenido, método y muestra de medición. Relación con O3.5.1–O3.5.3. | Memoria L3.5 (págs. 59–60); valores [PENDIENTE: usuario] | |
| 5 | **Conclusiones** | Cumplimiento de la tarea, retos abordados, limitaciones y trabajo futuro. | — | `05-conclusiones.md` |
| 6 | **Referencias** | Memoria del proyecto, entregables E3.5.1–E3.5.3 y bibliografía citada. | — | `06-referencias.md` |

## Trazabilidad con la ficha

| Elemento de la ficha | Dónde se cubre |
|---|---|
| Descripción T3.5.4: facilidad de uso | 2.1, 4.1 |
| Descripción T3.5.4: selección de tipología de componente | 2.1, 3.2 |
| Descripción T3.5.4: selección de infraestructura de despliegue | 2.1, 3.3 |
| Descripción T3.5.4: uso del algoritmo de IA | 3.4 |
| Reto: algoritmo que entienda y genere la infraestructura | 3.4 (resumen; el detalle es de E3.5.3) |
| Reto: integración con herramientas de despliegue existentes | 3.6 |
| O3.5.1 / I3.5.1 (tiempo de despliegue, ≥ 40 %) | 4.2 |
| O3.5.2 / I3.5.2 (plazo de nuevos componentes, ≥ 60 %) | 4.2 |
| O3.5.3 / I3.5.3 (% infraestructuras automáticas, ≥ 30 %) | 4.2 |
| Carácter agnóstico de la infraestructura | 1.1, 3.3 |

## Notas
- La sección 3 es la sección propia del entregable que la plantilla deja abierta ("3. …"). Se mantienen los nombres de la plantilla en las demás, incluida "Características de la interfaz", que encaja con este entregable sin adaptación.
- Los indicadores de L3.5 ya tienen la fórmula de reducción correcta; no les afecta la incidencia I-03.
- La mayor parte del contenido técnico depende de información que aún no está en el repo (ver "Información pendiente" de la ficha).
