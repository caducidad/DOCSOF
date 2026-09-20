# Decisiones · E3.5.4 Interfaz de usuario para el sistema de generación automática de infraestructura

Acuerdos específicos de este entregable, confirmados por el usuario. Formato: `D-NN (AAAA-MM-DD): decisión — motivo`.

- **D-01 (2026-09-20): Enfoque.** El protagonista del entregable es la aplicación desarrollada (interfaz + backend). Todo lo demás se subordina a explicarla y justificarla.
- **D-02 (2026-09-20): Referencias al E3.5.3, solo las imprescindibles.** Este es el E3.5.4: se cita el E3.5.3 únicamente cuando sea necesario para entender o justificar la aplicación (origen de los modelos, acotación del alcance, modelo recomendado, capa de control). No se repite su contenido.
- **D-03 (2026-09-20): Desviación y alcance.** Apartado explícito que recorra:
  1. Qué pedía la memoria: sistema agnóstico (on-premise, AWS, Kubernetes…) a partir de la caracterización del componente.
  2. Qué acotó la línea en la fase de algoritmo: despliegue en instancia única (E3.5.3, §6.4).
  3. Qué hace la aplicación: a partir de logs de uso real genera la recomendación de instancia AWS y el código Terraform.
  4. Por qué sigue siendo válido: OG2 de la memoria (pruebas de concepto a TRL4); arquitectura extensible con puntos de extensión identificados (adaptador de logs, catálogo de instancias, plantilla IaC); escalado horizontal, orquestación de microservicios y multi-cloud como trabajo futuro.
- **D-04 (2026-09-20): Tipología de componente.** Se materializa como la clasificación automática de los endpoints del servicio en cuatro clases de carga (r_ping, r_cpu, r_users, r_orders) a partir de sus logs, sin requerir conocimiento experto del usuario.
- **D-05 (2026-09-20): Reentrenamiento.** Se afirma de forma genérica que los modelos se reentrenaron con logs de uso real de servicios de AYESA-DIGITAL. Sin cifras ni detalle adicional: con eso queda suficientemente justificado.
- **D-06 (2026-09-20): Modelo recomendado.** Se presenta la red neuronal (MLP) como modelo recomendado (seleccionado como principal en el E3.5.3) y Random Forest, Regresión Lineal y SVR como alternativas disponibles en la interfaz.
- **D-07 (2026-09-20): Indicadores.** Tabla de re-mapeo (indicador de la memoria / definición operativa / medición / resultado / justificación):
  - I3.5.1: tiempo invertido en tareas de despliegue = dimensionamiento de la infraestructura + redacción del código IaC.
  - I3.5.2: plazo acotado al tramo "componente listo → infraestructura definida".
  - I3.5.3: según la fórmula del indicador (sobre el total de infraestructuras generadas), señalando que no coincide con la redacción de O3.5.3 ("soluciones de software de la empresa").
- **D-08 (2026-09-20): Capa de control/auditoría.** Se presenta como evidencia del resultado esperado "reducción de errores y problemas en el despliegue". Se ilustra con el caso de la demo (r_cpu = 50 fuera de rango, recortado a 25,2; predicción de CPU de 106,69 % corregida a 100 %). No se mezcla con las cifras del E3.5.3.
- **D-09 (2026-09-20): Material gráfico.** Capturas en el orden del flujo (login → subida de logs → predicción → resultados → avisos), pantalla de la API y diagrama de arquitectura con los puntos de extensión.
