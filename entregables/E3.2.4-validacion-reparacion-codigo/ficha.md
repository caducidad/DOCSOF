# Ficha · E3.2.4 Validación de la herramienta software para la reparación automática de código fuente

| Campo | Valor |
|---|---|
| Entregable | E3.2.4 Validación de la herramienta software para la reparación automática de código fuente |
| Tarea | T3.2.4 Validación de la plataforma desarrollada |
| Línea | L3.2. Investigación en IA para la refactorización automática de código |
| Paquete de trabajo | PT3 (ver incidencia I-04 sobre su nombre) |
| Responsable (memoria) | UMA (tarea: responsable UMA, participante PROXYA) — ver incidencia I-01 |
| Fecha (memoria) | M31–M36 |
| Cabecera para la plantilla | `PT3 - L3.2. Investigación en IA para la refactorización automática de código - T3.2.4 Validación de la plataforma desarrollada` |

## Descripción de la tarea (memoria, pág. 53–55)
Validación del servicio de refactorización automática en un entorno relevante web. La validación se hará sobre proyectos software existentes.

Relacionado con el objetivo **O3.2.5**: poner los algoritmos al servicio del equipo de desarrollo mediante una aplicación web que permita refactorizar proyectos (basados en **Maven**) para mejorar su calidad.

## Línea L3.2 (contexto)
- **Meses:** M1–M36 · **Líder:** UMA · **Colaboradores:** PROXYA, Grupo AZVI · **Subcontratista:** FIDETIA
- **Estado del arte en la memoria:** sección 2.2.9.
- **Descripción:** herramienta que encuentre y aplique automáticamente refactorizaciones para reparar *code smells* y antipatrones de diseño detectados por analizadores como SonarQube, basadas en IA, para mejorar la calidad interna del código. Exploración adicional en representación del conocimiento (ontologías).

**Objetivos:**
- O3.2.1: identificar los objetivos y criterios de calidad a abordar con la refactorización.
- O3.2.2: investigar algoritmos de IA para refactorización automática.
- O3.2.3: servicio de refactorización automática (secuencias de refactorizaciones que reduzcan los problemas detectados).
- O3.2.4 (en la memoria figura como "O3.3.4", ver I-02): refactorización de alto nivel para representación del conocimiento/ontologías.
- **O3.2.5: validación del servicio en un entorno relevante mediante aplicación web para proyectos Maven.** ← objetivo directo de este entregable

**Retos tecnológicos:** operaciones de refactorización basadas en reglas de asociación; metaheurísticas (evolutivos, recocido simulado, búsqueda local iterada) para hallar la secuencia óptima; nombrado automático de variables, métodos y clases; PLN y aprendizaje automático sobre comentarios e identificadores; IA generativa (GPT-3/GPT-4).

**Indicadores:**
- **I3.2.1:** número de problemas (antipatrones y *code smells*) resueltos. Objetivo: **+60 % a +100 %** respecto a herramientas existentes como JDeodorant.
- **I3.2.2:** semántica de los nombres generados, evaluada con encuestas a desarrolladores. Objetivo: **≥ 3 sobre 5**.

## Entregables relacionados de la línea (no son de este repo)
| Código | Título | Resp. | Fecha |
|---|---|---|---|
| E3.2.1 | Análisis industrial de la refactorización de código y nombrado automático | UMA | M1–M5 |
| E3.2.2 | Diseño y desarrollo de herramienta software para la reparación automática de código fuente | UMA | M6–M30 |
| E3.2.3 | Herramientas para reparación de códigos de representación de conocimiento | UMA | M6–M30 |

## Información pendiente de aportar por el usuario
- [ ] Descripción técnica de lo desarrollado (arquitectura, tecnologías, componentes).
- [ ] Capturas, diagramas u otro material gráfico.
- [ ] Resultados y mediciones reales para "Indicadores logrados".
- [ ] Documentación de los entregables previos de la línea (ver tabla de entregables relacionados).
- [ ] Proyectos software existentes usados en la validación y resultados obtenidos.
- [ ] Mediciones frente a JDeodorant (I3.2.1) y resultados de encuestas (I3.2.2).
