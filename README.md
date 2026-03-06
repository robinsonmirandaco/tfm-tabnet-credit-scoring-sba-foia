# TFM: Aprendizaje profundo tabular interpretable para scoring crediticio PYME  
## Evaluación experimental comparativa frente a Regresión Logística y XGBoost

## Autor: Robinson José Miranda Pérez

Este repositorio contiene el código, los datos de trabajo y los resultados asociados al **Trabajo Fin de Máster (TFM)** del **Máster Universitario en Inteligencia Artificial** de la **Universidad Internacional de La Rioja (UNIR)**.

El estudio analiza el uso de **modelos de aprendizaje profundo tabular** en tareas de **scoring crediticio para pequeñas y medianas empresas (PYMES)**, comparando su rendimiento con métodos clásicos ampliamente utilizados en la práctica.

Los modelos evaluados en el estudio son:

- Regresión Logística
- XGBoost
- TabNet

---

# Estructura del repositorio

## Estructura del repositorio

```
RMP_TFM_Scoring_Crediticio_Pyme.ipynb   # Notebook principal que contiene el flujo completo del estudio experimental

data/
  raw/                              # Conjunto de datos originales utilizados en el análisis

outputs/
  figures/                          # Figuras generadas para la memoria del TFM
  tables/                           # Tablas con los resultados experimentales
  predictions/                      # Predicciones generadas por los modelos evaluados
```

  
---

# Documentación

- **Diseño experimental:** ver `DESIGN.md`  
- **Referencias bibliográficas:** ver `REFERENCES.md`

---

# Reproducibilidad

El notebook incluido en el repositorio contiene el flujo completo de análisis:

1. preparación de datos  
2. entrenamiento de modelos  
3. evaluación experimental  
4. generación de tablas y figuras

---

# Licencia

Este proyecto se distribuye bajo licencia **Apache License 2.0**.  
Ver archivo `LICENSE`.
