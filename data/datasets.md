# Datasets del proyecto — links directos

Compartido entre Proyecto 1 y Proyecto 2 (ambos usan la misma base: Anthropic Economic Index + O*NET).

## 1. La etiqueta: Anthropic Economic Index

Fuente oficial (CC-BY 4.0): https://huggingface.co/datasets/Anthropic/EconomicIndex

### Tablas de impacto laboral `[VERIFICADO]`
- `job_exposure.csv` — 37 KB, 900 ocupaciones, columnas `occ_code`, `title`, `observed_exposure`
  https://huggingface.co/datasets/Anthropic/EconomicIndex/resolve/main/labor_market_impacts/job_exposure.csv
- `task_penetration.csv` — 1.89 MB, tarea por tarea, columnas `task`, `penetration`
  https://huggingface.co/datasets/Anthropic/EconomicIndex/resolve/main/labor_market_impacts/task_penetration.csv

### Release de febrero 2025, espejo en GitHub `[BAJADO]`
- https://raw.githubusercontent.com/gianluigilopardo/AnthropicEconomicIndex/main/onet_task_mappings.csv — 461 KB / 3,514 filas
- https://raw.githubusercontent.com/gianluigilopardo/AnthropicEconomicIndex/main/onet_task_statements.csv — 3.6 MB / 19,530 filas
- https://raw.githubusercontent.com/gianluigilopardo/AnthropicEconomicIndex/main/automation_vs_augmentation.csv — 197 bytes / 6 filas
- https://raw.githubusercontent.com/gianluigilopardo/AnthropicEconomicIndex/main/SOC_Structure.csv — 77 KB
- https://raw.githubusercontent.com/gianluigilopardo/AnthropicEconomicIndex/main/wage_data.csv — 128 KB
- https://raw.githubusercontent.com/gianluigilopardo/AnthropicEconomicIndex/main/bls_employment_may_2023.csv — 1.1 KB

## 2. El vocabulario: O*NET 31.0 `[EXISTE]`

Departamento de Trabajo de EE.UU., CC-BY 4.0. Versión actual 31.0, sitio actualizado 25/08/2026.
- https://www.onetcenter.org/database.html
- https://www.onetcenter.org/dl_files/database/db_31_0_excel.zip

Archivos que sirven de features: `task_statements`, `task_ratings`, `work_activities`, `work_context`, `essential_skills`, `abilities`, `software_skills`.
API: https://services.onetcenter.org/

## 3. El paquete de R `[VERIFICADO]`

`aieconindex` v0.2.0, CRAN, 02/08/2026. Baja los 6 releases del índice, sin API key, con caché local.
- https://cran.r-project.org/package=aieconindex
- https://github.com/charlescoverdale/aieconindex

```r
install.packages("aieconindex")
library(aieconindex)
aei_releases()
df  <- aei_index("2026-06-26", source = "claude_ai")
pen <- aei_labor_market("task_penetration")
```

## 4. Contexto y validación

### AIOE, exposición a IA por ocupación `[BAJADO]`
Paper revisado por pares (Felten, Raj y Seamans, Strategic Management Journal 2021). 774 ocupaciones por SOC, 250 industrias por NAICS, 3,271 geografías por FIPS.
- https://github.com/AIOE-Data/AIOE
- https://raw.githubusercontent.com/AIOE-Data/AIOE/main/AIOE_DataAppendix.xlsx

### BTOS, adopción de IA por empresas `[EXISTE]`
Census Bureau. ~1.2 millones de empresas, cada 2 semanas desde sept 2023. Por sector NAICS, estado, los 25 metros más grandes y tamaño de empresa.
- https://www.census.gov/hfp/btos/data
- https://www.census.gov/data/experimental-data-products/business-trends-and-outlook-survey.html
- https://github.com/EIG-Research/ai-btos (código de limpieza en Stata, útil para entender el formato)
