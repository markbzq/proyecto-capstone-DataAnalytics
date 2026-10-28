# Colab + GitHub — flujo de trabajo del equipo

## Dónde trabajar

Trabajen siempre en el mismo notebook compartido de Google Drive. Compartan ese enlace dentro del equipo. Abrir Capstone.ipynb desde GitHub en Colab crea otra vista de trabajo; no reemplaza el enlace compartido de Drive.

Drive conserva el notebook de trabajo. GitHub conserva checkpoints guardados deliberadamente. No hay sincronización automática.

## Guardar checkpoints

Una persona del equipo guarda cada checkpoint:

1. Espera a que los cambios estén guardados en Drive.
2. Abre **File → Save a copy in GitHub**.
3. Selecciona **markbzq/proyecto-capstone-DataAnalytics**.
4. Selecciona una rama de trabajo existente donde tengas permiso de escritura y la ruta **Capstone.ipynb**. La rama **main** está protegida y no permite este guardado directo.
5. Escribe un mensaje que explique el cambio y guarda.
6. Abre un pull request hacia **main**. Se requiere al menos una revisión aprobatoria de un integrante con permisos de escritura antes de fusionar.
7. Comprueba que el archivo en **main** se actualizó después de la fusión.

Si Colab falla al guardar, usa **File → Download → Download .ipynb**. En GitHub abre **Add file → Upload files**, carga **Capstone.ipynb**, elige una rama nueva y crea un pull request.

## Claude y ChatGPT: solo sugerencias

No hace falta dar permisos de escritura a las IAs. Adjunta el notebook actual y los documentos relevantes del proyecto. Si tu IA no acepta .ipynb, pega las celdas y resultados relevantes. Si usa un conector de GitHub, actualiza su contexto antes de comenzar. Un enlace por sí solo no garantiza que pueda leer el contenido.

Prompt para copiar:

> Estamos trabajando en https://github.com/markbzq/proyecto-capstone-DataAnalytics. Usa los archivos que adjunto como contexto. Estamos en modo de sugerencias: no edites archivos, no hagas commits y no abras pull requests. Primero indica qué archivos y versión pudiste leer. Si no puedes acceder al contenido, pídeme las celdas o archivos necesarios. Para cada sugerencia, identifica la sección o celda, explica el motivo y proporciona el código propuesto por separado. No inventes datos, métricas ni resultados. Distingue resultados observados de hipótesis y ejemplos. Mi tarea de hoy es: [describir tarea].

Una persona revisa y aplica las sugerencias aceptadas en Colab, ejecuta las celdas afectadas y guarda un checkpoint. Las conversaciones privadas de cada integrante no se comparten automáticamente con las otras IAs.

Cada integrante tiene su propia sesión de ejecución en Colab: variables, archivos temporales y paquetes instalados no se comparten automáticamente. Incluyan celdas para instalar dependencias y cargar los datos.

Guía oficial de Google: https://github.com/googlecolab/colabtools/blob/main/notebooks/colab-github-demo.ipynb
