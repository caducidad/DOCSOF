# 4. Resultados obtenidos

## 4.1. Características de la interfaz

La plataforma desarrollada presenta las siguientes características:

| Característica | Descripción |
|---|---|
| Sencillez de uso | El proceso se completa en tres pasos y solo requiere cuatro datos: repositorio, token, rama y ruta del pipeline. |
| Transparencia | Antes de aplicar ningún cambio, muestra exactamente qué se va a modificar, en el formato de comparación de código habitual para los desarrolladores. |
| Cambios mínimos y conservadores | Solo añade el paso de predicción y la condición del *build*; conserva el resto del pipeline y sus condiciones existentes. |
| Integración en el flujo de trabajo del equipo | Sube los cambios a una rama elegida por el usuario, de modo que se integran mediante el proceso habitual de revisión. |
| Sin almacenamiento de datos | No guarda información de los repositorios ni de los usuarios; cada operación es independiente. |
| Seguridad | Utiliza el token del usuario para acceder al repositorio y referencia la clave de la API como *secret*, sin escribirla en el pipeline. |
| Modelo adaptado a cada proyecto | El modelo se entrena por repositorio, de forma acumulativa, y gana precisión con el uso. |
| Integración corporativa | Comparte apariencia con el resto de aplicaciones del proyecto. |

*Tabla 4. Características de la plataforma.*

## 4.2. Indicadores logrados

Las fórmulas de los indicadores de la línea L3.4 que recoge la memoria tienen invertidos numerador y denominador: tal como están escritas, no expresan una reducción porcentual ni un porcentaje de componentes. Para calcular los indicadores se utilizan las fórmulas en su forma correcta, coherente con la de los indicadores de otras líneas del proyecto:

| Indicador (memoria) | Meta | Fórmula aplicada | Resultado |
|---|---|---|---|
| I3.4.1. Reducción del tiempo invertido en integración y despliegue | ≥ 60 % | [(Tiempo anterior − Tiempo posterior) / Tiempo anterior] × 100 | [PENDIENTE] |
| I3.4.2. Porcentaje de componentes con pipelines generados de forma automática | ≥ 60 % | (Componentes con pipeline adaptado automáticamente / Total de componentes objetivo) × 100 | [PENDIENTE] |

*Tabla 5. Indicadores de la línea L3.4.*

**I3.4.1. Reducción del tiempo invertido en integración y despliegue.** La solución reduce este tiempo por dos vías:

- **Adaptación del pipeline.** Incorporar manualmente a un pipeline la consulta a un modelo y la lógica condicional del *build* requiere conocer la sintaxis de la herramienta de integración, redactar y probar los cambios. La plataforma genera y sube esos cambios en unos instantes.
- **Ejecución del pipeline.** Cada vez que el modelo predice que el *build* resultará correcto, este se omite. En proyectos de gran tamaño (por ejemplo, Angular, Java o TypeScript), un *build* puede prolongarse de 5 a 10 minutos y un ciclo completo de CI/CD puede superar la hora. Si el pipeline se ejecuta varias veces por semana, el ahorro acumulado es significativo.

[PENDIENTE: valor del indicador.]

**I3.4.2. Porcentaje de componentes con pipelines generados de forma automática.** Como se describe en el apartado 2.1, la línea ha orientado la automatización a adaptar los pipelines existentes para incorporarles el modelo de predicción. El indicador se evalúa, por tanto, sobre los componentes cuyo pipeline se adapta automáticamente. Como se muestra en el apartado 3.5, un único cambio en la definición común del pipeline incorpora el modelo a todos los servicios de un repositorio, más de veinte en el caso analizado. [PENDIENTE: valor del indicador.]
