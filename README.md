# Exfiltradaz – Dataset

Este repositorio contiene los datos generados por Exfiltradaz, incluyendo snapshots en formato estructurado y reportes derivados de estos datos.

Los datos se construyen a partir de la recolección y procesamiento automatizado de publicaciones en foros, marketplaces y sitios asociados al ecosistema de filtraciones.

## Cómo se organizan los datos

El flujo de datos en este repositorio es:

snapshot (JSON) → reporte (Markdown)

Los snapshots contienen los datos recolectados y normalizados por periodo
Los reportes organizan y presentan esos datos para su lectura

## Estructura del repositorio
```
.
├── snapshots/   # Datos por periodo (JSON)
├── reports/     # Reportes derivados (Markdown)
├── README.md
└── .gitignore
```
### snapshots/

Contiene los datasets por periodo en formato JSON.

Cada snapshot agrupa los incidentes observados en un rango de fechas e incluye registros normalizados con campos como:

* `date` → fecha del evento
* `country` → país asociado
* `sector` → clasificación del incidente
* `source` → origen (foro, sitio, etc.)
* `author` → actor o usuario observado
* `content` → texto relevante de la publicación
* `victim` → entidad afectada (cuando es identificable)
* `dedup_key` → identificador usado para detectar registros duplicados o relacionados. Permite agrupar incidentes similares y evitar contarlos múltiples veces, aunque no garantiza una deduplicación perfecta.

Estos archivos son la base del análisis y no están pensados para lectura directa.

### reports/

Contiene los reportes generados a partir de los snapshots.

Cada reporte corresponde a un periodo específico y organiza los datos en una forma legible, incluyendo:

* Resumen del periodo
* Comparación del snapshot anterior, presenta nuevos actores, países y foros cuando hay movimientos.
* Distribuciones (por país, sector, etc.)
* Visualizaciones
* Registro tabular de incidentes

Los reportes estructuran y presentan la información contenida en los snapshots.

### Alcance de los datos

Los registros corresponden a referencias de filtraciones observadas en:

* Foros
* Marketplaces de credenciales
* Sitios de ransomware
* Otros espacios públicos

Los cuales se publican en un canal especifico en Telegram. Por lo tanto un registro no implica necesariamente una filtración confirmada, sino la observación de una publicación asociada a una posible exposición de datos.

## Limitaciones
* No todas las filtraciones son detectadas
* Existe sesgo hacia fuentes públicas accesibles
* La clasificación por sector puede ser ambigua
* La identificación de víctimas es parcial
* Algunos registros pueden contener información incompleta

## Pipeline

El código utilizado para generar estos datos se encuentra en:

https://github.com/ZoqueLabs/leak-observatory

## Uso previsto

Este dataset puede utilizarse para analizar tendencias, investigación en seguridad digitalo exploración del ecosistema de filtraciones.

* Para un análisis programático, utilizar snapshots/.
* Para una lectura general, utilizar reports/.

Zoquelabs
