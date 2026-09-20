# Anotación del usuario · Enfoque de la línea L3.4

Anotación de trabajo aportada por el usuario. **No es una decisión ni texto definitivo**: sirve como referencia para redactar cómo se presenta el camino tomado en la línea. Recuerda la regla D-05 (`decisiones.md` raíz): sin "desviación" ni sinónimos.

---

Se proponía un sistema de IA capaz de generar automáticamente pipelines de CI/CD de forma agnóstica al stack tecnológico. Sin embargo, abarcar toda la diversidad tecnológica resultaría inabarcable y quedaría obsoleto rápidamente.

En lugar de modelar los pipelines, se propone un modelo de machine learning agnóstico que, ante cada commit, predice si la build resultará en pass o fail sin necesidad de ejecutarla.

La lógica acordada entre los socios académicos e industriales es:
- Si se predice fail → merece la pena ejecutar la build (revela un error que hay que corregir).
- Si se predice pass → se puede ahorrar la ejecución (no aporta información nueva).

De este modo se mantiene el propósito esencial de la CI de detectar errores pronto, pero optimizando los recursos y reduciendo el gasto computacional.

---

Relación con la demo: la API devuelve `BUILD_REQUIRED` (se ejecuta la build) o `BUILD_OPTIONAL` (se puede omitir), junto con un `failure_risk`. En la ejecución mostrada (`capturas/12`) la respuesta fue `BUILD_OPTIONAL` con `failure_risk: 0.24762` y la build se omitió.
