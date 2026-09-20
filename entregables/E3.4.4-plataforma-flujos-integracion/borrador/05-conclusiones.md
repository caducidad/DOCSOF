# 5. Conclusiones

La tarea T3.4.4 ha dado como resultado una plataforma web que conecta el modelo de predicción de la línea L3.4 con las herramientas de integración continua de los equipos de desarrollo. En tres pasos, y sin necesidad de modificar a mano el pipeline, un equipo puede incorporar a su flujo de CI/CD un modelo que decide en cada ejecución si es necesario ejecutar el *build*.

Las principales aportaciones de la tarea son:

- **La incorporación automática del modelo a pipelines existentes**, con cambios mínimos que conservan la estructura y las condiciones de cada pipeline.
- **Un servicio de predicción propio**, construido a partir del modelo de la línea, con entrenamiento por repositorio y acumulativo, que permite que las predicciones se ajusten a cada proyecto y mejoren con el uso.
- **La transparencia del proceso**: el usuario ve exactamente qué se modifica antes de aplicarlo y los cambios se integran mediante el flujo habitual de revisión del equipo.
- **La validación en ejecución real**: el pipeline adaptado consulta al modelo y omite el *build* cuando la predicción lo permite, sin intervención manual.

El enfoque adoptado en la línea, que consiste en predecir el resultado del *build* en lugar de modelar los pipelines, mantiene el propósito esencial de la integración continua de detectar los errores cuanto antes y, al mismo tiempo, optimiza los recursos y reduce el gasto computacional. Es, además, independiente del *stack* tecnológico de cada proyecto, lo que lo hace sostenible frente a la rápida evolución de las tecnologías.

La solución constituye una prueba de concepto funcional, validada sobre GitHub Actions, y aplicable por diseño a otras plataformas basadas en Git. Sus líneas de evolución naturales son la incorporación de otras plataformas de integración y el reentrenamiento periódico del modelo con los nuevos datos que generen los propios repositorios.
