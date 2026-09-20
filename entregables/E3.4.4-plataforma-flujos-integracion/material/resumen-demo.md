# Resumen de la demo de la aplicación · E3.4.4

Resumen detallado de la reunión del **21 de agosto de 2026** (1 h) en la que Jesús Bintaned (desarrollador) presentó la aplicación ("Integrator") a Juan Domínguez y Jorge Amarillo. Se ha eliminado lo irrelevante (saludos, logística de capturas, conversación ajena al entregable, opiniones sobre terceros) y se conserva todo lo técnico y funcional. La demo se apoyó en un vídeo grabado el 20 de agosto y, al final, en una ejecución en directo del pipeline modificado.

> Notas para el generador:
> - Donde este resumen dice "según el desarrollador", es una afirmación suya en la demo, no un dato verificado.
> - La línea L3.4 tomó un camino distinto al que describía la memoria (generación automática de pipelines a partir de metamodelos). Ver `anotacion-enfoque.md` y, cuando existan, las decisiones del entregable.
> - Hugging Face: no se menciona en el texto (`decisiones.md` raíz, D-06), aunque aparezca en capturas.

## 1. Qué hace la aplicación
- Pantalla "**Reparador de Pipelines de CI/CD**". Según el desarrollador, "reparar" no es la palabra exacta: la aplicación **inyecta una serie de acciones en un pipeline de CI/CD ya existente** para que pueda **omitir la fase de build cuando no es necesaria**.
- Se apoya en el **algoritmo de predicción desarrollado por la UMA** en la línea, que determina si un build es necesario.
- Casi todo pipeline de CI/CD incluye un build previo al despliegue (para verificar el código y construir los artefactos). En proyectos grandes (Angular, Java, TypeScript…) un build puede tardar de 5 a 10 minutos, y un ciclo completo de CI/CD puede llegar a 2 horas. Omitir builds innecesarios supone un **ahorro de tiempo relevante** si el pipeline se ejecuta varias veces por semana. En proyectos triviales (p. ej., HTML estático) no aporta valor.

## 2. Arquitectura
- **Frontend** muy sencillo, en línea con el requisito de la memoria de que la interfaz sea fácil de usar; con la apariencia corporativa común de las aplicaciones del proyecto (marca Sof.ia).
- La complejidad está en el **backend**: la integración con el algoritmo de la UMA y la infraestructura de microservicios creada para que funcione.
- **Backend de predicción ("CI Prediction API")**, construido por AYESA-DIGITAL (`capturas/13`):
  - La UMA, en su entregable, hizo una comparativa de seis modelos; **el backend lo construyó AYESA-DIGITAL** a partir del modelo seleccionado y del código de entrenamiento de la UMA.
  - Endpoints: `/health`, `/train` (lanza en segundo plano el pipeline completo de entrenamiento para un repositorio), `/predict` (predice el resultado del último build).
  - Autenticación obligatoria mediante cabecera `x-api-key`; sin ella devuelve 401.
  - Parámetros: `repository_url` y `branch` (por defecto `develop`).
- **Entrenamiento por repositorio**: el modelo se entrena para cada repositorio en el que se va a usar. `/train` descarga del repositorio la información que necesita y reentrena el modelo **con todo el histórico acumulado** (no desde cero), de modo que gana precisión con el uso. El reentrenamiento se lanza a demanda, no automáticamente con cada commit.
  - Según el desarrollador (de memoria, a contrastar con el entregable de la UMA), los datos incluyen el perfil de quien hace los commits, el histórico de pull requests y los resultados de ejecuciones anteriores del pipeline, entre otras estadísticas del repositorio.
- **Sin estado**: la aplicación no guarda nada en base de datos; se puede usar de forma secuencial, un repositorio tras otro.
- **Diagramas**: el desarrollador prepara diagramas de arquitectura (ya tiene algunos de flujo y de contexto) y Juan elaborará los diagramas de flujo a partir de las grabaciones.

## 3. Flujo de uso
### Paso 1 · Datos del repositorio (`capturas/01`)
- **URL del repositorio**. En la demo, GitHub; según el desarrollador, válido para cualquier repositorio Git (GitLab, Bitbucket…).
- **Token** con permisos de lectura y escritura sobre el repositorio (generado por el usuario en su plataforma). En las capturas debe aparecer anonimizado.
- **Rama** del repositorio que contiene el pipeline.
- **Ruta del pipeline** en el repositorio (en la demo, `.github/workflows/ci.yml`).
- Botón **Guardar**: la aplicación procesa el pipeline (tarda unos instantes).

### Paso 2 · Cambios en el código (`capturas/02`)
- Se muestra un **diff estilo GitHub** con los cambios propuestos en el pipeline:
  - Nuevo paso **"Check if build is required"**: llama a la API de predicción (con la clave como *secret* del repositorio, el repositorio y la rama actuales), extrae el campo `status` de la respuesta y lo publica como salida del paso.
  - Modificación del paso **"Build project"**: se añade la condición `steps.prediction.outputs.status == 'BUILD_REQUIRED'`. Si la predicción no es BUILD_REQUIRED, el build se omite.
- Según el desarrollador, es una evidencia clara de que el código inyectado no es trivial. En un pipeline más complejo se inyectaría de la misma forma.

### Paso 3 · Subir cambios (`capturas/03`)
- Diálogo **"Subir cambios"** con la **rama de destino** (en la demo, `feature/pipeline-improvement`).
- Al confirmar, los cambios se suben al repositorio, aparece una notificación de éxito y el formulario se limpia.

### Resultado en el repositorio (`capturas/04`, `05`)
- En GitHub aparece la **rama nueva**, un commit por delante de `develop`.
- El commit **"Add UMA prediction model to pipeline"** (usuario `integrator-sofia`) modifica 1 fichero (12 adiciones, 1 eliminación) y contiene exactamente el cambio mostrado en la aplicación. Desde ahí el usuario puede abrir una pull request.

## 4. Ejecución del pipeline modificado (`capturas/06`–`12`)
- La ejecución del pipeline ocurre en el repositorio del usuario, **fuera del alcance de la aplicación**, pero se mostró para evidenciar que el código inyectado funciona. Se hizo en otro repositorio (`devaid-libs`) con el pipeline ya modificado ("CI - Project Health", lanzado manualmente sobre `develop`).
- Estructura: un job `configuration` (checkout, caché, instalación de dependencias, detección de proyectos afectados) y una matriz `project-health` con un job por servicio (tests unitarios → "Check if build is required" → "Build project" → fin).
- Resultado clave (`capturas/12`, servicio `projects-service`): tras los tests (con su resumen de cobertura), el paso de predicción devolvió `prediction: 1`, `status: BUILD_OPTIONAL`, `failure_risk: 0.24762`, y **el paso "Build project" se omitió** (skip); el pipeline terminó correctamente.
- Algunos jobs de la matriz fallaron en sus tests unitarios, lo que es ajeno a la aplicación.

## 5. Enfoque del documento (propuesta del desarrollador)
- Incluir una o dos secciones de resultados explicando que el código se inyecta en un pipeline preexistente del repositorio del usuario y que ese código invoca el algoritmo de la UMA para decidir si se omite el build.
- Los criterios concretos que usa el algoritmo para decidir corresponden al entregable de la UMA y quedan fuera del alcance de este entregable; basta con referenciarlos.
- Alinear la justificación con la que haya hecho la UMA en su entregable y, en lo posible, ampliarla.
