# 5. Conclusiones

La tarea T3.5.4 ha dado como resultado una aplicación que pone el sistema de generación automática de infraestructura de la línea L3.5 al alcance de cualquier usuario. A partir de los *logs* de un servicio, y en tres pasos, el usuario obtiene una estimación de su consumo de recursos, la instancia más económica capaz de soportarlo y el código Terraform para desplegarla, sin necesidad de conocimientos específicos de infraestructura.

Las principales aportaciones de la tarea son:

- **La caracterización automática del componente** a partir de sus *logs*, que traduce el comportamiento real del servicio a las cuatro clases de carga que utilizan los modelos y hace innecesario que el usuario clasifique su componente.
- **La integración de los modelos de predicción** de la tarea T3.5.3, reentrenados con datos de uso real de servicios de AYESA-DIGITAL, en un flujo de trabajo completo que termina en código desplegable.
- **La visibilidad de la capa de control**, que convierte las correcciones automáticas del sistema en avisos comprensibles para el usuario.
- **Una arquitectura extensible**, en la que la incorporación de nuevos formatos de *log*, proveedores o plantillas de infraestructura no requiere modificar el núcleo del sistema ni reentrenar los modelos.

La solución constituye una prueba de concepto funcional, en línea con el objetivo del proyecto de validar las tecnologías investigadas en un nivel TRL4, y ofrece una base sólida para su evolución. Las líneas de evolución identificadas son:

- **Escalado horizontal**: pasar de dimensionar una única instancia a determinar la arquitectura de clúster óptima (número de réplicas y tipo de instancia) que minimice el coste de operación, tal como se plantea en el entregable E3.5.3.
- **Nuevos proveedores y entornos**: incorporar catálogos y plantillas para otros proveedores cloud, infraestructura on-premise y plataformas de contenedores.
- **Nuevos formatos de *log***: añadir adaptadores para otros formatos de registro.
- **Reentrenamiento periódico**: actualizar los modelos con nuevos datos de uso para mejorar progresivamente su precisión, aprovechando las operaciones de entrenamiento ya disponibles en la API.
