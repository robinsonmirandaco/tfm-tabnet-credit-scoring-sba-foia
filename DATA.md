# DATA.md

# Datos: SBA FOIA 7(a)

Este repositorio no redistribuye los datos originales de SBA FOIA.  
Para reproducir los experimentos, descarga los ficheros oficiales desde la SBA y colócalos en la estructura indicada.

## Fuente oficial

Dataset: U.S. Small Business Administration (SBA) – FOIA 7(a)  
Página: https://data.sba.gov

Nota: Los datos FOIA se actualizan de forma periódica.

## Archivos esperados

Se asume que dispones de los ficheros (o equivalentes) descritos en el diseño del TFM:

- Diccionario de Datos 7a_504_FOIA (al 31/12/25).xlsx
- FOIA - 7(a) (FY1991-FY1999) (al 31/12/25).csv
- FOIA - 7(a) (FY2000-FY2009) (al 31/12/25).csv
- FOIA - 7(a) (FY2010-FY2019) (al 31/12/25).csv
- FOIA - 7(a) (FY2020-Presente) (al 31/12/25).csv

## Estructura de carpetas

Coloca los CSV/XLSX descargados en:

- data/raw/

Ejemplo:

- data/raw/FOIA_7a_FY2010_FY2019.csv
- data/raw/FOIA_7a_FY2020_present.csv
- data/raw/7a_504_FOIA_data_dictionary.xlsx

## Reproducibilidad y versionado de datos

Para asegurar trazabilidad:

1. No modifiques manualmente los CSV originales.
2. Genera datos procesados mediante scripts/notebooks y guarda el resultado en:
   - data/processed/
3. Registra (en un log o en un archivo de metadatos) la fecha de descarga y el hash de los ficheros originales.

## Aviso legal y de uso

- Los datos proceden de una fuente pública (FOIA).
- Este repositorio contiene únicamente código y documentación para investigación.
- No se proporciona asesoramiento financiero ni debe utilizarse para decisiones reales de crédito.

## Problemas frecuentes

- Cambios de esquema entre versiones: si SBA modifica nombres/columnas, ajusta el mapeo en el preprocesado.
- CSV grandes: evita abrirlos directamente en GitHub; usa scripts de carga y muestreo.
