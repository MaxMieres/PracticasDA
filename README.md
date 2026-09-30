# PracticasDA
Practicas analisis de datos 
# Análisis de Precios y Volúmenes de Frutas y Hortalizas — ODEPA Chile 2025
## Autor

Proyecto desarrollado por Maximiano Mieres como parte de su portafolio de transición hacia Data Analytics.

> **Estado del proyecto:** en desarrollo — Fase 1 (limpieza y normalización) completada, Fases 2-5 en curso. Este README se irá actualizando con los hallazgos reales a medida que avance el análisis.
## Fuente de datos

- **Origen:** [ODEPA — Boletines de precios](https://www.odepa.gob.cl/publicaciones/boletines), Ministerio de Agricultura de Chile
- **Periodo cubierto:** enero a diciembre de 2025
- **Cobertura:** principales mercados mayoristas del país
- **Formato original:** Excel (.xlsx), un archivo por mes y categoría

## Descripción

Este proyecto analiza los precios y volúmenes de comercialización de frutas y hortalizas en los principales mercados mayoristas de Chile durante 2025, a partir de los boletines públicos de precios de la Oficina de Estudios y Políticas Agrarias (ODEPA).

El dataset original consta de 24 archivos Excel (12 meses × 2 categorías: frutas y hortalizas), con aproximadamente 29.000 registros en total, que incluyen mercado, producto, variedad, calidad, volumen transado y precios (mínimo, máximo y promedio ponderado) reportados en distintas unidades de comercialización (caja, bandeja, kilo suelto, entre otras).

El objetivo es transformar estos datos crudos en información comparable y accionable: normalizar los precios a una unidad común (precio por kilogramo), y a partir de ahí identificar patrones de estacionalidad, variación entre mercados, y relación entre precio y volumen — el tipo de análisis que en un contexto real sirve de apoyo a decisiones de compra, venta o anticipación de oferta.



## Stack técnico

- **Python** — pandas (manipulación de datos)
- **Jupyter Notebook** (vía VS Code) — desarrollo exploratorio
- **Git / GitHub** — Entrega del proyecto

## Estructura del repositorio

```
proyecto_odepa/
├── data/
│   ├── raw/          # Archivos originales de ODEPA, sin modificar
│   └── processed/    # Datos ya limpios y normalizados, listos para análisis
├── notebooks/         # Notebooks de exploración, limpieza y análisis
└── README.md
```

**Principio de trabajo:** los archivos originales en `data/raw/` nunca se modifican directamente. Todo el procesamiento ocurre en memoria y se guarda como una versión nueva en `data/processed/`, preservando siempre la trazabilidad hacia la fuente original.

## Metodología y avance por fase

### Fase 1 — Limpieza y normalización ✅ *(completada)*

- Carga de archivos saltando filas de presentación no tabulares (encabezados de boletín)
- Detección y eliminación de filas no correspondientes a datos reales (notas al pie del boletín, del tipo "Fuente: ODEPA")
- Verificación de completitud y tipos de dato por columna
- Resolución del problema central del dataset: la columna de unidad de comercialización mezcla envase y peso en texto libre (ej. *"caja 18 kg"*, *"bandeja 10 kg"*, *"kilo"*), con más de 60 variantes distintas. Se extrajo el peso mediante expresiones regulares y se normalizaron los casos sin peso explícito (unidad ya expresada en kilo)
- Cálculo de un precio por kilogramo comparable entre productos, mercados y formatos de venta

### Fase 2 — Consolidación *(pendiente)*

- Automatización del proceso de limpieza de la Fase 1 sobre los 24 archivos (función + iteración)
- Unificación de los 12 meses de cada categoría en una única tabla por categoría (frutas / hortalizas), agregando una columna de periodo
- Validación cruzada de consistencia de columnas entre meses (nombres, formatos)

### Fase 3 — Análisis exploratorio *(pendiente)*

- Estadística descriptiva por producto, mercado y mes
- Detección y tratamiento de valores atípicos
- Primeras preguntas de negocio: ¿qué productos muestran mayor variación de precio? ¿qué mercados son sistemáticamente más caros o más baratos?

### Fase 4 — Análisis con foco *(pendiente)*

Selección de 2-3 preguntas de negocio para profundizar, entre ellas:

- **Estacionalidad de precios** — evolución mensual del precio por kilo, por producto
- **Variabilidad y diferencial entre mercados** — dispersión de precios para un mismo producto en el mismo periodo, según mercado
- **Relación precio-volumen** — si se observa la relación esperada entre mayor volumen transado y menor precio

### Fase 5 — Entregable final *(pendiente)*

- Notebook o dashboard final con visualizaciones
- Conclusiones y hallazgos documentados
- Este README actualizado con resultados reales (reemplazando este borrador de alcance)

## KPIs que el análisis busca responder

| KPI | Descripción |
|---|---|
| Precio promedio por kilo (producto × mes) | Detecta estacionalidad de precios |
| Variabilidad de precio (desviación estándar / rango) | Qué tan volátil es cada producto |
| Diferencial de precio entre mercados | Dónde conviene más comprar o vender un producto dado |
| Volumen total transado (producto × mes) | Identifica temporada alta/baja de oferta |
| Participación de cada mercado en el volumen total | Relevancia relativa de cada mercado |
| Relación precio-volumen | Valida (o refuta) la lógica de oferta y demanda en los datos reales |

*Nota: esta tabla lista los KPIs que el análisis explora. Los resultados y hallazgos concretos se documentarán aquí a medida que se completen las Fases 3 y 4.*

