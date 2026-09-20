# Material · E3.5.4

Material aportado por el usuario. **No se modifica.** Las capturas se tomaron el 2026-08-04 a partir de la grabación de la demo de la aplicación (reunión del 2026-07-01 con Jesús Bintaned); **el orden es relevante** y refleja la secuencia de la demo. La hora indicada es la de la captura, no la de la reunión.

| Fichero | Hora | Contenido |
|---|---|---|
| `capturas/01-login.png` | 14:13:01 | Pantalla de inicio de sesión (sistema de autenticación común de la plataforma DevAId; usuario/contraseña o Google). |
| `capturas/02-api-backend.png` | 14:13:51 | Portada de la API del backend: endpoints de modelos (`/train`, `/train/status`, `/predict`), parseo de logs (`/logs/parse`, parámetros `cpu_threshold_ms` y `window_seconds`) y utilidades (`/health`, `/docs`). Según el desarrollador, esta pantalla no aporta valor visual. |
| `capturas/03-subida-logs.png` | 14:14:34 | Paso 1 · Subida de logs: zona de carga de fichero `.log`, umbral de CPU (ms) y ventana temporal (ms). |
| `capturas/04-prediccion-valores-y-modelo.png` | 14:16:21 | Paso 2 · Predicción: tasas extraídas de los logs para r_ping, r_cpu, r_users, r_orders (periodo, ventana, nº de peticiones, umbral), valores editables (r_cpu = 50) y desplegable de modelo. |
| `capturas/05-subida-logs-analizar.png` | 14:18:05 | Paso 1 · Subida de logs con el botón "Analizar logs". |
| `capturas/06-prediccion-seleccion-modelo.png` | 14:19:12 | Paso 2 · Selección de modelo: Random Forest, Regresión Lineal, SVR, Red Neuronal. |
| `capturas/07-resultados-t3micro.png` | 14:20:38 | Paso 3 · Resultados con valores extraídos de los logs: CPU 1,69 %, RAM 427,69 MB; instancia recomendada t3.micro con coste (≈ 8,32 €/mes) y demanda; código Terraform generado. |
| `capturas/08-resultados-avisos-auditoria.png` | 14:22:31 | Paso 3 · Resultados con r_cpu = 50 (fuera de rango): avisos de la capa de control (entrada recortada a 25,2; CPU 106,69 % corregida a 100 %); instancia c5.2xlarge; Terraform. |

Resumen detallado de la demo: `resumen-demo.md`.
