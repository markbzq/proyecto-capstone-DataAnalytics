# Proyecto 1 — Exposición a IA para una ocupación sin puntaje

## 1. Problema
Una empresa que está contratando para un rol quiere saber si la IA ya está haciendo buena parte de ese trabajo, para diseñar el puesto en función de eso ahora en vez de un año después. Existe un puntaje de exposición publicado, pero solo cubre cerca de 900 ocupaciones con datos medidos, y los títulos de trabajo reales muchas veces no calzan con esa lista. El modelo es para darle un puntaje a un rol que no está en ella.

## 2. Cliente
Un equipo de RR.HH. o reclutamiento de una empresa mediana en EE.UU. que está escribiendo una descripción de puesto.

## 3. Datos

**Capa 1 — lo que ya se puede hacer (sin modelar, sin supuestos):**
Dos archivos públicos del Anthropic Economic Index: uno da un puntaje de exposición observado (0 a 1) para ~900 ocupaciones, el otro puntúa tareas de trabajo individuales. Ambos vienen de medir uso de IA en casi un millón de conversaciones reales, cruzadas con el catálogo de tareas del Department of Labor (18,428 tareas atadas a códigos de ocupación).

**Capa 2 — lo que se quiere hacer:**
Entrenar con las ocupaciones que sí tienen puntaje para predecir el puntaje de las que no, usando el texto de sus tareas. La variable de respuesta es `observed_exposure` (0 a 1), real para las filas de entrenamiento, ausente para las que se quieren predecir. Se separan ocupaciones que el modelo nunca ve y se reporta el error sobre esas. Una versión preliminar a nivel de tarea ya tiene **AUC 0.85 en validación cruzada de 5 particiones** — esto ya se corrió, es dato real.

**Capa 3 — todavía una meta:**
Si un reclutador de verdad cambia lo que escribe por ver el puntaje. No se puede probar esto en el semestre.

## 4. ¿Es difícil encontrar los datos?
No. Están todos disponibles, son gratis, y hay un paquete de R en CRAN (`aieconindex`) que los descarga directo. Las limitaciones reales no son de acceso sino de la medición: la exposición se mide por ocupación completa (todos los que están en una ocupación tienen el mismo número), y viene de conversaciones, así que el trabajo que ya se automatizó silenciosamente dentro de software nunca aparece. Esto se deja explícito en vez de dejar que el número parezca más de lo que es.

## 5. Qué sería éxito

**A lo que nos comprometemos:** un modelo que prediga el puntaje de exposición para ocupaciones con las que no se entrenó, reportado como error absoluto medio (MAE) sobre el conjunto separado, contra un baseline de solo predecir el promedio. Si no se le gana a ese baseline, se dice así.

**A lo que apuntamos:** una herramienta donde se pega una descripción de puesto y se devuelve un puntaje predicho, las ocupaciones con puntaje real más parecidas, y qué tareas son las que más pesan en el número.

## Nota sobre uso real / valor para el cliente
El puntaje solo es diagnóstico, no da una recomendación directa. Lo que lo hace útil para RR.HH. no es el número aislado sino que viene con las ocupaciones más parecidas y las tareas que más pesan — eso es lo que permite que un humano revise el razonamiento en vez de confiar a ciegas. Una capa de reglas simple sobre esas tareas (p. ej. "si las tareas que más pesan son repetitivas/administrativas, sugerir contratar pensando en menor volumen de ejecución manual") convertiría esto en algo más accionable, pero sigue sin poder medirse si un reclutador realmente actúa distinto — eso cae en la Capa 3.
