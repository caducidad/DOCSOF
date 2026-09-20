# DOCSOF · Documentación de entregables del proyecto SOFIA

## Contexto
SOFIA: Investigación en un ecosistema de aplicaciones para la mejora de la productividad en la industria de desarrollo SOFtware mediante el uso intensivo de IA Fiable en todo su ciclo de vida (programa Transmisiones 2023). Consorcio de 8 empresas (Proxya → AYESA-DIGITAL, GHENOVA, TSK, AZVI, SEGULA, COTESA, INIXA, UNDANET), 2 organismos de investigación (U. Salamanca, U. Málaga) y 3 centros subcontratados (ITCL, FIDETIA, Tecnalia). Este repo cubre solo los entregables de AYESA-DIGITAL pendientes.

Empresa autora de los entregables: **AYESA-DIGITAL** (en la memoria aparece como PROXYA). Ver `decisiones.md`.

## Roles
En este repo trabajan dos sesiones de Claude con roles distintos. Al empezar, el usuario te dirá cuál eres.
- **Generador** → lee `roles/generador.md`
- **Revisor** → lee `roles/revisor.md`

## Antes de cada tarea (ambos roles)
1. `git pull`
2. Lee `decisiones.md` (raíz) y el `decisiones.md` del entregable en curso.
3. Lee la `ficha.md` del entregable.
4. Revisa `entregables/<entregable>/buzon/` y atiende los mensajes pendientes dirigidos a ti.

## Estructura
- `decisiones.md`: acuerdos de todo el proyecto e incidencias detectadas en la memoria.
- `roles/`: instrucciones y aprendizaje acumulado de cada rol.
- `referencias/`: memoria (PDF y texto en `memoria.md`) y plantilla. **No se modifica.**
- `entregables/<código-nombre>/`
  - `ficha.md`: lo que dice la memoria sobre el entregable. Solo la modifica el usuario.
  - `indice.md`: índice propuesto/acordado.
  - `decisiones.md`: acuerdos específicos del entregable.
  - `borrador/`: una sección por fichero (`01-introduccion.md`, `02-solucion-propuesta.md`, …).
  - `buzon/`: mensajes entre generador y revisor.

## Entregables
- `E3.2.4-validacion-reparacion-codigo`: E3.2.4 Validación de la herramienta software para la reparación automática de código fuente
- `E3.4.4-plataforma-flujos-integracion`: E3.4.4 Plataforma web para automatizar la generación de flujos de integración
- `E3.5.4-interfaz-generacion-infraestructura`: E3.5.4 Interfaz de usuario para el sistema de generación automática de infraestructura
- `E3.6.5-app-web-accesibilidad-ui`: E3.6.5 Aplicación web para la adaptación/corrección de código de interfaz de usuario

## Qué actualiza cada uno
| Situación | Fichero | Quién |
|---|---|---|
| Acuerdo que afecta a todo el proyecto (nombres, terminología, estilo) | `decisiones.md` (raíz) | Quien lo proponga, **solo tras confirmación del usuario** |
| Acuerdo de un solo entregable | `entregables/<e>/decisiones.md` | Quien lo proponga, tras confirmación del usuario |
| Aprendizaje sobre cómo trabajar como generador | `roles/generador.md` | Generador |
| Criterio nuevo o error recurrente detectado | `roles/revisor.md` (checklist) | Revisor |
| Cambio de índice | `entregables/<e>/indice.md` | Solo generador |
| Contenido del documento | `entregables/<e>/borrador/` | Solo generador (el revisor no edita, comenta por el buzón) |
| Comunicación | `entregables/<e>/buzon/` | Ambos |
| `ficha.md`, `CLAUDE.md`, `referencias/` | — | Solo el usuario |

## Protocolo del buzón
- Un fichero por mensaje: `NNN-remitente-asunto.md` (numeración correlativa de 3 dígitos por entregable). Ej.: `001-generador-indice.md`.
- Cabecera obligatoria:
  ```
  ---
  de: generador | revisor
  para: revisor | generador
  entregable: Ex.y.z
  tipo: revisar | responder | informar
  ficheros: [rutas afectadas]
  responde_a: NNN (si aplica)
  estado: pendiente | respondido
  fecha: AAAA-MM-DD
  ---
  ```
- Al atender un mensaje, cambia su `estado` a `respondido` y, si procede, crea el mensaje de respuesta.
- Discrepancias: una sola ronda de discusión. Si no hay acuerdo, se escala al usuario con ambas posturas resumidas.

## Convenciones
- **Respuestas breves (ambos roles).** Al usuario: qué has hecho, qué queda pendiente y qué necesitas de él, sin preámbulos ni repeticiones. Los mensajes del buzón, igual de concisos. La brevedad no se aplica al contenido de los entregables, que tendrá la extensión que requiera.
- Idioma: español. Formato de trabajo: Markdown. La conversión a Word con la plantilla se hará al final.
- No inventes datos: resultados, métricas, capturas o detalles técnicos que no estén en las referencias o no los haya aportado el usuario se marcan como `[PENDIENTE: descripción de lo que falta]`.
- Commits pequeños con prefijo de rol: `[generador] E2.3.1 propuesta de índice`, `[revisor] E2.3.1 observaciones índice`. Haz `git push` al terminar cada tarea.
