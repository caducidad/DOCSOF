# Decisiones · E3.4.4 Plataforma web para automatizar la generación de flujos de integración

Acuerdos específicos de este entregable, confirmados por el usuario. Formato: `D-NN (AAAA-MM-DD): decisión — motivo`.

- **D-01 (2026-09-20): Enfoque.** El protagonista del entregable es la aplicación desarrollada: una plataforma web que modifica automáticamente pipelines de CI/CD existentes para integrar en ellos el modelo de predicción. Todo lo demás se subordina a explicarla y justificarla.
- **D-02 (2026-09-20): Referencias a la UMA, solo las imprescindibles.** Se cita el origen del modelo (entregable de la UMA en la línea) y se remiten a él los criterios con los que el modelo predice. No se usa la descripción de memoria del desarrollador sobre qué datos utiliza el modelo.
- **D-03 (2026-09-20): Enfoque y alcance.** Apartado explícito, redactado en positivo (D-05 raíz), basado en `material/anotacion-enfoque.md`: qué se proponía (generación agnóstica de pipelines), por qué no era viable abarcar toda la diversidad tecnológica, qué camino se tomó (modelo que predice por commit si la build fallará: si se predice fallo, se ejecuta; si no, se puede omitir) y qué aporta (se mantiene el propósito de la CI optimizando recursos). Se vincula con T3.4.4: la aplicación es el conector entre el modelo y la herramienta de integración (GitHub Actions).
- **D-04 (2026-09-20): Plataformas.** Se presenta como demostrado sobre GitHub / GitHub Actions y como aplicable a otras plataformas Git por diseño, sin afirmarlo como probado.
- **D-05 (2026-09-20): Entrenamiento.** El modelo se entrena por repositorio, de forma acumulativa (con todo el histórico) y a demanda mediante la API.
- **D-06 (2026-09-20): Indicadores.** Se usan las fórmulas corregidas (incidencia I-03 raíz), explicando brevemente el cambio:
  - I3.4.1: reducción del tiempo de integración y despliegue gracias a omitir builds innecesarios.
  - I3.4.2: porcentaje de componentes cuyo pipeline se adapta automáticamente; en la demo, un único cambio en el pipeline cubre toda la matriz de servicios del repositorio.
- **D-07 (2026-09-20): Evidencia de funcionamiento.** La ejecución del pipeline modificado se presenta como probada en varios proyectos. La captura 12 (`BUILD_OPTIONAL` y build omitida) es la prueba central.
- **D-08 (2026-09-20): Material gráfico.** Capturas del flujo (01–05), del resultado de la ejecución (12) y de la API (13); diagramas de arquitectura y de flujo pendientes de aportar.
- **D-09 (2026-09-20): Seguridad.** El token del usuario aparece anonimizado y la clave de la API se gestiona como *secret* del repositorio; se menciona como buena práctica de la solución.
