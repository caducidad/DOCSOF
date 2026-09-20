# 4. Resultados obtenidos

## 4.1. Características de la interfaz

La interfaz desarrollada presenta las siguientes características:

| Característica | Descripción |
|---|---|
| Sencillez de uso | El proceso se completa en tres pasos guiados, con un indicador de progreso siempre visible. No requiere conocimientos de infraestructura, en línea con el requisito de la memoria de que la interfaz sea fácil de usar. |
| Caracterización automática | La tipología del componente se obtiene automáticamente de los *logs*, clasificando sus operaciones en cuatro clases de carga. |
| Control por parte del usuario | Los parámetros de análisis y los valores de carga son editables, lo que permite incorporar el conocimiento del usuario sobre su servicio. |
| Elección de modelo | Permite elegir entre cuatro modelos de predicción, con la red neuronal como modelo recomendado. |
| Resultado accionable | Proporciona la instancia recomendada, su coste y el código Terraform listo para desplegar. |
| Fiabilidad | La capa de control corrige entradas fuera de rango y predicciones imposibles, e informa al usuario mediante avisos explícitos. |
| Criterio económico | Recomienda la instancia más económica que satisface la carga sostenida, con un margen de seguridad. |
| Extensibilidad | Los puntos dependientes de formato o proveedor están aislados del núcleo del sistema. |
| Integración corporativa | Comparte apariencia y sistema de autenticación con el resto de aplicaciones del proyecto. |

*Tabla 5. Características de la interfaz.*

## 4.2. Indicadores logrados

La tabla siguiente relaciona cada indicador de la línea L3.5 con su definición operativa en el contexto de la solución desarrollada y con el resultado obtenido.

| Indicador (memoria) | Meta | Definición operativa | Resultado |
|---|---|---|---|
| I3.5.1. Reducción del tiempo invertido en tareas de despliegue | ≥ 40 % | Tiempo dedicado a dimensionar la infraestructura de un servicio y a redactar su código de infraestructura, frente al proceso manual | [PENDIENTE] |
| I3.5.2. Reducción del plazo en el que se despliegan nuevos componentes | ≥ 60 % | Plazo entre que un componente está listo y su infraestructura queda definida | [PENDIENTE] |
| I3.5.3. Porcentaje de infraestructuras generadas de forma automática | ≥ 30 % | Infraestructuras generadas automáticamente sobre el total de infraestructuras generadas por el sistema | [PENDIENTE] |

*Tabla 6. Indicadores de la línea L3.5.*

**I3.5.1. Reducción del tiempo invertido en tareas de despliegue.** La memoria define este indicador sobre el tiempo invertido en tareas de despliegue, y la descripción de la línea lo concreta en el tiempo y el esfuerzo necesarios para la creación y configuración de la infraestructura. Es en esas tareas donde actúa la aplicación: el dimensionamiento manual de un servicio requiere preparar y ejecutar pruebas de carga, monitorizar el consumo, interpretar los resultados con criterio experto y redactar el código de infraestructura. Con la aplicación, ese proceso se reduce a aportar los *logs* del servicio y revisar el resultado, en pocos minutos. [PENDIENTE: valor del indicador.]

**I3.5.2. Reducción del plazo en el que se despliegan nuevos componentes.** El plazo total de despliegue de un componente depende también de procesos organizativos ajenos a la infraestructura, como las aprobaciones o las ventanas de despliegue. El indicador se evalúa, por ello, sobre el tramo en el que actúa el sistema: desde que el componente está listo hasta que su infraestructura queda definida. En ese tramo, la aplicación sustituye una campaña de pruebas y análisis, que puede ocupar días, por una estimación inmediata. [PENDIENTE: valor del indicador.]

**I3.5.3. Porcentaje de infraestructuras generadas de forma automática.** La fórmula del indicador en la memoria relaciona el número de infraestructuras generadas de forma automática con el número total de infraestructuras generadas. La redacción del objetivo O3.5.3 se refiere, en cambio, a las soluciones de software de la empresa; el indicador se calcula según su fórmula. [PENDIENTE: valor del indicador.]
