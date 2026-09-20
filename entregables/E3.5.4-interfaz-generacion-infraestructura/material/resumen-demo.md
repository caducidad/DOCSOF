# Resumen de la demo de la aplicación · E3.5.4

Resumen detallado de la reunión del **1 de julio de 2026** (32 min) en la que Jesús Bintaned (desarrollador) presentó la aplicación a Juan Domínguez. Se ha eliminado lo irrelevante (saludos, interrupciones, conversación ajena al entregable) y se conserva todo lo técnico y funcional. Las capturas de `capturas/` se tomaron el 4 de agosto de 2026 a partir de la grabación de esta reunión.

> Notas para el generador:
> - El reentrenamiento de los modelos se documenta según `decisiones.md` (D-05), de forma genérica.
> - Donde este resumen dice "según el desarrollador", es una afirmación suya en la demo, no un dato verificado.

## 1. Punto de partida
- La aplicación se ha adaptado al enfoque del algoritmo desarrollado en la tarea anterior de la línea (E3.5.3). Ese trabajo partía de un microservicio Java desarrollado para experimentación, con cuatro tipos de endpoint que caracterizan la carga:
  - **r_ping**: peticiones muy ligeras de comprobación de estado (health check).
  - **r_cpu**: operaciones de cálculo intensivo en CPU.
  - **r_users**: peticiones de lectura contra base de datos.
  - **r_orders**: peticiones de escritura pesada (transaccionales) contra base de datos.
- Los modelos de esa tarea se reentrenaron con datos de aplicaciones desplegadas de AYESA-DIGITAL, seleccionando endpoints equivalentes a esas cuatro clases. La aplicación explota esos modelos reentrenados.

## 2. Arquitectura
- **Backend** desarrollado íntegramente en **Python**, que expone los modelos mediante una **API** (ver `capturas/02-api-backend.png`):
  - Modelos: `/train` (entrenar un modelo: lr, poly, rf, svr, mlp), `/train/status`, `/predict` (predice CPU y RAM, recomienda instancia AWS y devuelve el Terraform; entrada: r_ping, r_cpu, r_users, r_orders y modelo).
  - Parseo de logs: `/logs/parse` (parámetros: umbral de CPU en ms, por defecto 1000; ventana temporal, opcional).
  - Utilidades: `/health`, `/docs` (Swagger).
- **Frontend** con la apariencia común de las aplicaciones del proyecto; acceso mediante el sistema de autenticación común de la plataforma DevAId (de ahí el logo en el login), con la marca Sof.ia dentro de la aplicación.
- El backend **no se limita a llamar a los modelos**: aporta trabajo propio de **parseo y tratamiento de logs** para determinar qué endpoints del servicio corresponden a cada una de las cuatro clases (r_ping, r_cpu, r_users, r_orders) y calcular sus tasas de peticiones.
- **Catálogo de instancias AWS**: el backend contiene un diccionario de instancias (nombre, vCPU, RAM, coste), heredado del trabajo de la UMA, con el que selecciona la instancia y genera el código.
- **Despliegue**: la parte de modelos/backend está desplegada y funcionando en **Hugging Face**. **No se menciona en el entregable** (ver `decisiones.md`, D-10).
- **Reentrenamiento vía API**: se incluye para trabajo futuro; los modelos de IA deben reentrenarse periódicamente para ganar precisión, y el sistema ya está preparado para ello.
- El desarrollador sugiere incluir un **diagrama de arquitectura** de alto nivel; la pantalla de la API no aporta valor visual (la generó una IA para no mostrar una página en blanco).

## 3. Entrada: los logs
- La aplicación parte de **ficheros de log de servicios reales** (entornos de producción, preproducción o test), o de una aplicación en local que se vaya a subir a producción.
- Cada línea de log registra la llamada (método, endpoint) y el **tiempo de procesamiento en milisegundos**, que es lo relevante.
- La trazabilidad de endpoints es un requisito habitual de cualquier sistema que pasa a producción, independientemente del lenguaje, por lo que este tipo de log es muy común.
- La aplicación está construida sobre un **formato de log concreto**: el de las aplicaciones de AYESA-DIGITAL con las que se ha trabajado (la API lo identifica como log de NestJS), generado por una librería disponible para muchos lenguajes.
- **Extensibilidad**: si un proyecto usa otro formato de log, basta con adaptar el endpoint de parseo. **No hay que reentrenar los modelos ni reimplementar el núcleo de la aplicación**, que se mantiene inalterado.
- Según el desarrollador, se ha probado con muchos de los microservicios de AYESA-DIGITAL y ha funcionado con todos aquellos con los que se probó.

## 4. Flujo de uso (tres pasos)
El objetivo de la aplicación es **estimar qué infraestructura necesita un servicio para desplegarlo en cloud**. La interfaz se ha diseñado deliberadamente sencilla, porque la tarea exige que sea fácil de usar.

### Paso 1 · Subida de logs (`capturas/03`, `05`)
- Zona para arrastrar o seleccionar el fichero `.log`.
- **Umbral de CPU (ms)**: a partir de qué tiempo de procesamiento una operación se considera de cálculo intensivo (clase r_cpu). Por defecto 1000 ms; totalmente personalizable (p. ej., 100 ms o 5000 ms según la aplicación).
- **Ventana temporal (ms)**: permite analizar solo el tramo reciente del log (último día, semana, mes). Si se deja vacía, se procesa el fichero completo. Utilidad: un servicio puede llevar meses desplegado en test, pero solo interesan los datos de las pruebas recientes. En un desarrollo local no tiene sentido.
- Botón **"Analizar logs"**: sube y procesa el fichero; el procesamiento es rápido.

### Paso 2 · Predicción de infraestructura (`capturas/04`, `06`)
- Se muestran las **tasas extraídas** (peticiones/s) para r_ping, r_cpu, r_users y r_orders, junto con el periodo analizado, la ventana, el número de peticiones y el umbral usado.
  - Ejemplo de la demo: 29/4/2026–22/6/2026, 54 días, 178 peticiones, umbral 1000 ms. r_ping = 0 porque ese servicio no tiene endpoint de health check en los logs. Valores muy bajos porque el microservicio apenas tiene tráfico.
- Los valores son **editables**: el usuario puede corregirlos o ajustarlos (p. ej., poner r_ping = 5 si sabe que hay 5 comprobaciones por segundo que el log no ha recogido, o subir r_cpu para dimensionar con más margen).
- **Selección de modelo**: Random Forest, Regresión Lineal, SVR o Red Neuronal. En la demo se ofrecen los cuatro sin marcar ninguno como recomendado (ver `decisiones.md`, D-06).
- Botón **"Ejecutar predicción"**.

### Paso 3 · Resultados (`capturas/07`, `08`)
- **Predicción de uso**: CPU (%) y RAM (MB). La RAM se deduce principalmente de las operaciones de escritura.
- **Instancia AWS recomendada**: la **más económica que satisface la carga sostenida**, con sus características, el coste (€/hora y €/mes) y la demanda estimada (incluye un margen o *buffer*).
  - Ejemplo con los valores extraídos de los logs: CPU 1,69 %, RAM 427,69 MB → **t3.micro** (2 vCPU, baseline 10 %, 1 GB RAM), 0,0114 €/h ≈ 8,32 €/mes; demanda 0,08 vCPU y 0,50 GB. La instancia no queda ajustada al límite: tiene holgura respecto a la demanda.
- **Código Terraform** de la infraestructura sugerida, listo para desplegar en AWS. Es deliberadamente sencillo y sirve como base para que el equipo lo personalice.
- Botón **"Terminar"**.

## 5. Capa de control: avisos y correcciones (`capturas/08`)
- Si el usuario introduce valores personalizados incoherentes, la aplicación **avisa y corrige**:
  - **Entrada** fuera del rango de entrenamiento: en la demo, r_cpu = 50 excede el rango y se **recorta a 25,2** (máximo de entrenamiento) para evitar extrapolaciones.
  - **Salida** físicamente imposible: predicción de CPU de **106,69 %** corregida a **100 %**.
  - Resultado en ese caso: instancia **c5.2xlarge** (8 vCPU, 16 GB), 0,384 €/h ≈ 280,32 €/mes.
- Esta lógica de control procede del trabajo de la UMA; la aplicación la integra y **la hace visible al usuario** mediante avisos, para que entienda qué se ha ajustado y por qué.
- Motivo: los valores extraídos de los logs son coherentes, pero la personalización manual puede introducir datos sin sentido; el sistema protege frente a ello.

## 6. Valoración del propio equipo
- La aplicación es muy sencilla, lo que se considera coherente con el requisito de la tarea (interfaz fácil de usar).
- En una presentación similar (otra herramienta del proyecto), ante el comentario de que era "muy básica", se argumentó que es precisamente la base necesaria para seguir evolucionando, y que a partir de ella la evolución es sencilla.
- Material gráfico sugerido: capturas del flujo, de un caso con valores personalizados y de un caso con avisos; diagrama de arquitectura.
