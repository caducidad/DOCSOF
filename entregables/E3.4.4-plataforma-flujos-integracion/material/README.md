# Material · E3.4.4

Material aportado por el usuario. **No se modifica.** Las capturas se tomaron el 2026-08-21 durante la reunión de demo de la aplicación con Jesús Bintaned; **el orden es relevante** y refleja la secuencia de la demo. La hora indicada es la de la captura.

- Capturas 01–05: vídeo de demo de la aplicación grabado el 2026-08-20 (usuaria: Cristina), sobre el repositorio `devaid-llm-service`.
- Capturas 06–12: ejecución en directo del pipeline modificado en otro repositorio (`devaid-libs`), para mostrar el código inyectado en funcionamiento.
- Captura 13: API del backend de predicción.

| Fichero | Hora | Contenido |
|---|---|---|
| `capturas/01-formulario-repositorio.png` | 12:09:30 | Pantalla "Reparador de Pipelines de CI/CD": URL del repositorio, token de GitHub (anonimizado), rama y ruta del pipeline (`.github/workflows/ci.yml`); botón Guardar. |
| `capturas/02-cambios-en-el-codigo.png` | 12:11:31 | Pantalla "Cambios en el código": diff estilo GitHub del `ci.yml` con el paso añadido "Check if build is required" (llamada a la API de predicción) y la condición añadida al paso "Build project" (`status == 'BUILD_REQUIRED'`). |
| `capturas/03-subir-cambios-rama-destino.png` | 12:29:26 | Diálogo "Subir cambios": rama de destino `feature/pipeline-improvement`. |
| `capturas/04-github-rama-creada.png` | 12:30:40 | GitHub: rama `feature/pipeline-improvement` recién creada (1 commit por delante de `develop`). |
| `capturas/05-github-comparativa-commit.png` | 12:31:08 | GitHub: comparativa de la rama; commit "Add UMA prediction model to pipeline" del usuario `integrator-sofia`, 1 fichero, 12 adiciones y 1 eliminación; mismo diff que muestra la aplicación. |
| `capturas/06-ejecucion-configuration-dependencias.png` | 12:35:00 | Ejecución: job `configuration`, instalación de dependencias (avisos de npm). |
| `capturas/07-ejecucion-configuration-inicio.png` | 12:35:23 | Ejecución "CI - Project Health #381": job `configuration`, inicio de instalación de dependencias. |
| `capturas/08-ejecucion-configuration-pasos.png` | 12:36:53 | Pasos del job `configuration` (checkout, caché, dependencias, proyectos afectados). |
| `capturas/09-ejecucion-resumen-workflow.png` | 12:37:13 | Resumen del workflow `ci.yml` lanzado manualmente sobre `develop`: job `configuration` y matriz `project-health` a la espera. |
| `capturas/10-ejecucion-analysis-service-cache.png` | 12:46:48 | Job `project-health (analysis-service)`: restauración de caché; pendientes "Check if build is required" y "Build project". |
| `capturas/11-ejecucion-analysis-service-tests.png` | 12:46:59 | Mismo job: ejecución de tests unitarios. |
| `capturas/12-ejecucion-prediccion-build-optional.png` | 12:52:56 | **Captura clave.** Job `project-health (projects-service)`: tests OK (cobertura), paso "Check if build is required" con respuesta de la API (`prediction: 1`, `status: BUILD_OPTIONAL`, `failure_risk: 0.24762`) y paso "Build project" **omitido** (skip). |
| `capturas/13-api-backend-prediccion.png` | 12:54:28 | Portada de "CI Prediction API": endpoints `/health`, `/train` (entrenamiento completo en segundo plano), `/predict` (predicción del último build); cabecera `x-api-key` obligatoria; parámetros `repository_url` y `branch`. |

Resumen detallado de la demo: `resumen-demo.md`.

Anotación del usuario sobre el enfoque de la línea: `anotacion-enfoque.md`.

Nota: algunas capturas muestran Hugging Face; no se menciona en el texto (`decisiones.md` raíz, D-06).
