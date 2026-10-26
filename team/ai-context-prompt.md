# Prompt para que cada IA del equipo contribuya a este repo

Instrucciones para Mark → para pasarle a cada compañero de equipo (sobre todo al que tiene más historial de conversación sobre el proyecto).

## Cómo usarlo

1. Clona o descarga este repo.
2. Abre tu IA (Claude, ChatGPT, lo que uses) en la misma conversación donde han estado iterando el proyecto las últimas semanas.
3. Pégale el prompt de abajo.
4. Lo que te devuelva, agrégalo al archivo correspondiente dentro de `projects/` (o crea uno nuevo si no calza en la estructura actual). Si tu IA puede escribir archivos y hacer commits directamente (por ejemplo Claude Code, o Claude con acceso a este repo), pídele que lo haga ella misma siguiendo el mismo prompt.
5. No borres lo que ya está. Si algo de tu historial contradice lo que ya hay en el repo, que tu IA lo marque como una nota aparte ("esto contradice X, revisar con el equipo") en vez de sobrescribir en silencio.

## El prompt (cópialo tal cual)

```
Tengo un proyecto de equipo para un curso de data analytics (Yeshiva University,
semestre Fall 2026). El curso pide un gate de dos fases antes de comprometerse a un
proyecto: Phase 0 (evaluar candidatos: problema, cliente, datos, qué sería éxito) y
Phase 1 (para UNO de los candidatos: qué se predice, si el dato existe o hace falta
proxy, qué variables predictoras, y que no haya fuga de información).

He estado iterando este proyecto contigo en nuestras conversaciones de las últimas
semanas. Necesito que revises TODO nuestro historial de esta conversación (o de las
conversaciones relacionadas con este proyecto) y me saques, en texto claro y
organizado:

1. Cualquier candidato de proyecto que hayamos discutido que NO esté ya documentado
   (dime si alguno coincide con "Proyecto 1 — exposición a IA por ocupación",
   "Proyecto 2 — qué tareas se delegan a IA", o si es algo nuevo).
2. Para cada candidato nuevo o adicional: problema, cliente, datos disponibles, qué
   tan difícil es conseguirlos, y qué sería éxito (siguiendo exactamente esas 5
   preguntas de Phase 0).
3. Si llegamos a profundizar en Phase 1 para alguno: qué se predice, si el dato lo
   incluye explícito o hace falta proxy, qué variables predictoras (marcando cuáles
   son explícitas, cuáles derivadas por transformación, y cuáles proxy), y si son
   observables al momento de la decisión (chequeo de leakage).
4. Cualquier dataset, link, o fuente de datos que hayamos mencionado y que no esté
   ya en una lista de fuentes del equipo.
5. Cualquier número o resultado que ya corrimos de verdad (AUC, error, lo que sea) —
   márcalo como REAL, y cualquier número que fue solo ilustrativo o de ejemplo —
   márcalo como EJEMPLO. No mezcles los dos sin etiquetar.

Dame la respuesta en markdown, organizada por sección, lista para pegar en un
archivo del repo del equipo. Si algo de esto contradice lo que el equipo ya tiene
documentado en otro lado, dilo explícitamente en vez de simplemente reemplazarlo.
```

## Resumen y próximos pasos (para que tu IA también lo tenga de contexto)

Ver `README.md` en la raíz del repo — tiene el estado actual y la lista de próximos pasos pendientes del equipo.
