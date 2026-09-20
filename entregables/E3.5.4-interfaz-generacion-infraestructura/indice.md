# Índice · E3.5.4 Interfaz de usuario para el sistema de generación automática de infraestructura

**Estado:** primer borrador redactado (2026-09-20), pendiente de revisión.

1. Introducción — `borrador/01-introduccion.md`
   1.1. Objeto del documento · 1.2. Contexto: la línea L3.5 · 1.3. Estructura del documento
2. Solución propuesta — `borrador/02-solucion-propuesta.md`
   2.1. Enfoque y alcance · 2.2. Visión general · 2.3. Arquitectura · 2.4. Caracterización de la carga a partir de los *logs* · 2.5. Modelos de predicción · 2.6. Capa de control · 2.7. Extensibilidad
3. Funcionamiento de la aplicación — `borrador/03-funcionamiento.md`
   3.1. Acceso · 3.2. Paso 1: subida de *logs* · 3.3. Paso 2: predicción de infraestructura · 3.4. Paso 3: resultados de la predicción · 3.5. Avisos de la capa de control
4. Resultados obtenidos — `borrador/04-resultados.md`
   4.1. Características de la interfaz · 4.2. Indicadores logrados
5. Conclusiones — `borrador/05-conclusiones.md`
6. Referencias — `borrador/06-referencias.md`

Cabecera: `borrador/00-cabecera.md`.

## Pendientes para el usuario
- Diagrama de flujo del proceso (2.2) y diagrama de arquitectura con puntos de extensión (2.3).
- Confirmar si la interfaz marca la red neuronal como recomendada o por defecto (2.5).
- Valores de los indicadores I3.5.1, I3.5.2 e I3.5.3 (4.2).
