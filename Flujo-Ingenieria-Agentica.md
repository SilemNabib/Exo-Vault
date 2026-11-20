# Ingeniería agéntica — resumen del live de Hola Mundo

Fuente: https://www.youtube.com/watch?v=FlBHb5wTtTU ("Agentes desde cero: del vibe coding al desarrollo profesional", 2h33m).
Basado en la transcripción automática en español, sin frames. Los nombres de modelos y herramientas pueden estar mal transcritos (p. ej. "Fable 7", "Sonet 5"): verifícalos antes de citarlos.
Minutos entre paréntesis = posición en el video.

## Tesis

Ingeniería de software con agentes sigue siendo ingeniería de software. El agente escribe el código. Tú defines, diseñas, verificas y revisas, y sigues siendo el responsable (31:00, 40:53, 2:30:46). Parte más lento y se acelera después. Si "vibe-codeas", parte rápido y se frena (1:04).

## Ciclo de 5 fases (57:06)

definir → preparar → construir → revisar → aprender

| Fase | Qué hace | Minuto |
|---|---|---|
| **Definir** | Parte del problema, no de la solución. Usa un modelo bueno razonando, no el de mejores benchmarks. Frena al modelo con "no hablemos de tecnología todavía". Dedica de 30 min a 2 h. | 26:44, 1:08 |
| | Revisión cruzada: otro agente, o el mismo con contexto limpio, deja preguntas abiertas en `qa.md`. No modifica el plan, solo sirve de checklist. | 28:44, 1:13 |
| | Historias de usuario pequeñas con criterios de aceptación verificables. Quita o fusiona historias para simplificar. La especificación va solo dentro de cada historia. | 33:48, 1:15 |
| | Stack: tú decides y el agente lista, y tú corriges. Después `stack.md` con versiones consultadas por Context7. | 1:19–1:26 |
| **Preparar** | Fase de **arquitectura**, que dice que Spec Kit y OpenSpec se saltan. No es solo estructura de carpetas, sino patrones y dónde va cada responsabilidad. | 6:08, 1:27 |
| | `AGENTS.md` y `CLAUDE.md` cortos (~100 líneas) con comandos, convenciones y un ejemplo canónico de cada patrón. Incluyen referencia a las historias. | 47:00, 1:47 |
| | Verificación automática: tests, linter, tipos, CI, logs. El linter y los tipos solo validan forma, no lógica. | 48:01 |
| **Construir** | Una historia a la vez. Explorar y planificar, aprobar el plan, implementar y verificar. | 49:02 |
| | **Walking skeleton** antes de cualquier historia: dependencias, "hola mundo" end-to-end, un comando para levantar todo y el linter. | 1:52 |
| | **Refactor temprano**, porque el agente copia lo que ve, bueno o malo. | 51:03 |
| | Git worktrees y paralelizar solo cuando ya hay buenos patrones que copiar. | 52:03 |
| **Revisar** | Tú lees el diff y pruebas a mano. Además un agente revisor de solo lectura, y un subagente de seguridad basado en OWASP Top 10. | 53:05 |
| | PRs pequeños (el tamaño es preferencia tuya) y un QA o un dev externo. | 55:06 |
| **Aprender** | Cada ciclo debe dejar algo: una regla nueva en `AGENTS.md` o una skill nacida de un problema recurrente. | 56:06, 2:25 |

**Por qué insiste:** el costo de un error crece en cada fase y mantener es lo más caro (13:11–21:00). Los tests solo dicen que el agente terminó, no que esté bien (7:00).

## Críticas que hace

**Spec Driven Development (SDD):**
- Burocracia para cambios pequeños.
- Revisar specs cansa más que revisar código.
- Falsa sensación de control, porque el LLM no es determinista.
- Spec y código se desincronizan y consumen más contexto.
- Es una cascada disfrazada.

Lo que sí rescata es la especificación, pero dentro de cada historia.

**Historias de usuario solas:** quedan vacías o vagas, no cubren requisitos no funcionales ni deuda técnica. Por eso las combina con la especificación por historia y con una arquitectura definida.

## Ejemplo que muestra (to-do app)

- **Stack:** Hono, Postgres, Drizzle, React, TanStack Query, React Hook Form, Zod, Tailwind, Vitest.
- **Backend:** rutas por composición de middlewares (validar → autorizar → ejecutar → responder).
- **Frontend:** Atomic Design.
- **Esquemas Zod:** compartidos entre front y back.

Es su gusto personal y lo repite varias veces: "la arquitectura es preferencia, lo peor es no tener ninguna".

## Consejos sueltos

- Para gastar menos tokens, dale ejemplos de archivos en `AGENTS.md` para que no tenga que leer todo el código (36:48).
- Si el agente pregunta demasiado, crea skills (1:20).
- Usa un modelo distinto para revisar.

## Cómo armar mi propio flujo

**Principios (conservar):**
1. Partir del problema y discutirlo sin hablar de tecnología.
2. Segunda opinión con contexto limpio, solo como lista de preguntas.
3. Historias pequeñas con criterios verificables, una a la vez.
4. Arquitectura explícita antes de construir.
5. Walking skeleton y refactor temprano.
6. Revisión humana obligatoria, más agente revisor de solo lectura.
7. Cerrar cada ciclo con una regla nueva en `AGENTS.md` o `CLAUDE.md`.

**Preferencias del autor (adaptar a mi stack):** Hono, Atomic Design, Drizzle, Tailwind, PRs pequeños, terminal.

## Pendiente por decidir

- [ ] Mi stack habitual y su arquitectura de referencia (¿Clean Architecture, hexagonal u otra?).
- [ ] Mi "definición de listo" (tests, linter, tipos y revisión).
- [ ] Qué skills o subagentes crear, solo cuando un problema se repita (ideas: `spec-historia`, `revisor`, `seguridad-owasp`).
- [ ] Plantilla de `CLAUDE.md` con las fases y carpeta `docs/` con `spec`, `stories` y `stack`.

Transcripción completa (puede borrarse al reiniciar): `C:\Users\silem\AppData\Local\Temp\watch-n_m7y0s6\subs\t.txt`
