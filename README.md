# Proyecto Data Analytics — Fall 2026

Repo de contexto compartido para el equipo (5 integrantes) y para las IAs (Claude, ChatGPT, etc.) que cada uno use mientras avanza en el proyecto. La idea: en vez de que cada persona tenga su propio hilo de conversación con su IA sin visibilidad de lo que hicieron los demás, este repo es la fuente única de verdad — cualquier IA puede leerlo y partir de ahí.

## Estado actual (26 oct 2026)

El curso pide un gate en dos fases antes de comprometerse a un proyecto para el semestre:
- **Phase 0** — evaluar hasta 3 proyectos candidatos (problema, cliente, disponibilidad de datos, qué sería éxito).
- **Phase 1** — para UNO de esos candidatos, profundizar en qué se va a predecir, si el dato existe o hace falta un proxy, qué variables predictoras se usarían, y confirmar que no haya fuga de información (leakage).

El texto completo de la asignación está en [`docs/phase0-phase1-instructions.md`](docs/phase0-phase1-instructions.md).

Hasta ahora el equipo trabajó dos candidatos a fondo:

1. **Proyecto 1 — Predecir exposición a IA de ocupaciones sin puntaje.** Usando el Anthropic Economic Index (900 ocupaciones con puntaje real) + O*NET (características de todas las ocupaciones) para predecir el `observed_exposure` de roles que no están en esas 900. Ya tiene una versión preliminar a nivel de tarea con AUC 0.85 (5-fold CV). Ver [`projects/project-1-exposure-score/`](projects/project-1-exposure-score/).
2. **Proyecto 2 — Clasificar qué tareas de un trabajo ya se le delegan a la IA.** Clasificación binaria por tarea (18,428 tareas), ya corrida: AUC 0.849, calibrada. Ver [`projects/project-2-task-classification/`](projects/project-2-task-classification/).

**Nuevo (26 oct 2026):** surgió un tercer candidato, comparar modelos de IA entre sí en distintas tareas/métricas. Todavía sin detalle — ver [`projects/project-3-model-comparison/README.md`](projects/project-3-model-comparison/README.md), pendiente de que se agregue el contexto completo.

## Próximos pasos

- [ ] Decidir si el Proyecto 3 reemplaza a los Proyectos 1/2 como el proyecto final, o si se evalúan los tres en Phase 0 y se elige uno para Phase 1.
- [ ] Si se mantiene Proyecto 1 o 2: cerrar la sección de variables predictoras (explícitas / derivadas / proxy) y el chequeo de leakage para Phase 1.
- [ ] Correr el modelo real a nivel de ocupación (Proyecto 1) o terminar de documentar el gap de adopción vs. capacidad (Proyecto 2).
- [ ] Cada integrante: usar el prompt en [`team/ai-context-prompt.md`](team/ai-context-prompt.md) con su propia IA para volcar a este repo lo que tenga de sus propias conversaciones.
- [ ] Armar la respuesta única de Phase 0 para enviar al profesor con todo el equipo en copia.

## Cómo usar este repo (humanos e IA)

1. Clona el repo o descárgalo.
2. Si vas a pedirle a tu IA (Claude, ChatGPT, etc.) que te ayude a avanzar, dale el contenido de la carpeta `projects/` y `data/` como contexto antes de pedirle que escriba algo nuevo — así no se repite trabajo ni se contradice lo que ya está.
3. Si tienes información adicional de tus propias conversaciones (de las últimas semanas de clase), agrégala en el archivo del proyecto correspondiente dentro de `projects/`, o crea un archivo nuevo si es información que no cabe en la estructura actual. No borres lo que ya está — si algo contradice lo existente, deja una nota explicando el cambio en vez de simplemente sobrescribir.
4. Haz commit con un mensaje claro de qué agregaste y de qué conversación/fecha viene.

## Estructura

```
docs/        → el texto original de la asignación (Phase 0 y Phase 1)
projects/    → un folder por proyecto candidato
data/        → las fuentes de datos y links, compartidas entre proyectos
team/        → el prompt para que cada IA del equipo contribuya aquí
```
