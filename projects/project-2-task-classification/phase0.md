# Proyecto 2 — Qué tareas de un trabajo ya se le delegan a la IA

## 1. Problema
Las empresas delegan partes de un trabajo, no el trabajo completo. Cuáles partes se decide adivinando.

## 2. Cliente
Un gerente de operaciones de una empresa mediana decidiendo qué delegar primero a la IA.

## 3. Datos

**Capa 1 — ya se puede hacer:** el catálogo tiene 18,428 tareas de trabajo, y el índice dice cuáles 3,514 de ellas muestran uso medido de IA y cuánto. Ya corrido: 81% de las tareas no muestra ningún uso medido, y 100 tareas cargan como la mitad de todo el uso.

**Capa 2 — ya corrido, dato real:** predecir del texto de una tarea si es una que la gente le delega a la IA. La variable de respuesta es 1 si la tarea aparece en el archivo de uso y 0 si no, en las 18,428 filas. **AUC 0.849 en validación cruzada de 5 particiones**, contra una tasa base de 19%, y calibrado: el 10% superior de las predicciones tiene ~66% positivos, el 10% inferior tiene menos de 1%. También ordena bien tareas escritas en lenguaje de empresa, no solo como las escribe el catálogo.

**Capa 3 — todavía una meta:** el dato mide adopción, no lo que la IA puede hacer. Clasificar tickets de soporte puntúa bajo porque ese trabajo corre dentro de software, no en una ventana de chat. Medir esa brecha significa correr una prueba propia, y no se ha cotizado el costo.

## 4. ¿Es difícil encontrar los datos?
No. Este es el que ya está hecho en vez de solo descrito.

## 5. Qué sería éxito

**A lo que nos comprometemos:** un AUC, una matriz de confusión y un gráfico de calibración sobre tareas separadas, más las palabras que más pesan en cada predicción, que por sí solas separan trabajo de escritorio de trabajo físico.

**A lo que apuntamos:** una herramienta que toma una lista de tareas escritas y las separa en qué delegar, en qué asistir, y qué dejar en manos humanas.

## Nota sobre proxy
El label (1/0 según aparece en el archivo de uso) es en sí un proxy de "la gente le delega esto a la IA" — mide adopción medida, no capacidad real. Ya está reconocido en la Capa 3.
