# Proyecto 1 — Phase 1: Data Availability

## Qué se está prediciendo
`observed_exposure` — el puntaje continuo de 0 a 1 — para ocupaciones que quedan fuera de las 900 que ya tiene Anthropic.

## ¿El dato lo incluye explícitamente?
Sí, pero solo para entrenamiento. `job_exposure.csv` da el valor real para 900 ocupaciones. Para las ocupaciones que realmente se quieren puntuar, el valor no existe — eso es el problema en sí, no un hueco que se tape con un proxy. Es extrapolación supervisada estándar: se entrena donde la etiqueta existe y se predice donde no. No hace falta pivotar — el target es real y explícito donde se necesita para entrenar.

## Variables predictoras

**Explícitas, sin transformación:** los archivos de rating a nivel de ocupación de O*NET 31.0 — `work_activities`, `work_context`, `abilities`, `essential_skills`, `software_skills` — más `wage_data` y `bls_employment_may_2023`. Importan porque O*NET califica así a todas las ocupaciones de su base, no solo a las 900 que puntuó Anthropic, y por eso están disponibles justo para las filas que se quieren predecir.

**Derivadas por transformación:** el texto de `task_statements` de O*NET por ocupación, convertido en embeddings (o TF-IDF) y agregado a nivel de ocupación. El texto crudo no es usable directo, así que es una variable calculada, no explícita.

**Proxy:** ninguno necesario. Deliberadamente NO se usa `task_penetration` (uso medido a nivel de tarea) agregado a nivel de ocupación como predictor, aunque es tentador — el puntaje de exposición de Anthropic probablemente ya se construye agregando algo parecido a esa misma señal a nivel de tarea, así que usarlo como predictor arriesga re-derivar el target en vez de predecirlo de forma independiente.

## ¿Son observables al momento de la decisión?
Sí. Todo lo que se usa — contenido de las tareas, actividades, contexto de trabajo, destrezas, salario, empleo — describe la ocupación en sí y se conoce antes de que alguien escriba o evalúe una descripción de puesto. Nada depende de resultados que solo existen después de una decisión de contratación o automatización, así que no hay riesgo de fuga (leakage).

## Normalización
Las variables de O*NET llegan en escalas distintas entre sí (ratings tipo Likert, salario en dólares, empleo en cantidad de personas). Antes de entrenar se estandarizan o se llevan a 0–1; si se usa un modelo basado en árboles (random forest, XGBoost, LightGBM) esto deja de ser necesario, porque esos modelos dividen por orden, no por magnitud. El target (`observed_exposure`) no se normaliza para "combinarlo" con las features — se queda tal cual, 0 a 1, porque es lo que el modelo intenta adivinar, no una pista más.

Punto aparte de la normalización: hay que emparejar `occ_code` (Anthropic) con el código SOC de O*NET usando `SOC_Structure.csv` como puente, para saber qué fila de features de O*NET corresponde a qué ocupación.
