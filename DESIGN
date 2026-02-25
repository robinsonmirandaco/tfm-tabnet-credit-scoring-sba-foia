# DESIGN.md

# Trabajo Fin de Máster: Diseño
## Aprendizaje profundo tabular interpretable para scoring crediticio PYME
### Evaluación experimental comparativa frente a Regresión Logística y XGBoost

Referencias bibliográficas: ver [REFERENCES.md](REFERENCES.md)

---

## 1. Introducción

### 1.1 Motivación

Las instituciones financieras requieren modelos de pre-scoring crediticio capaces de estimar la probabilidad de incumplimiento (default) con alta precisión predictiva, adecuada calibración probabilística y suficiente interpretabilidad para cumplir con requisitos regulatorios y operativos.

En el ámbito industrial, los modelos basados en *gradient boosting*, especialmente XGBoost, se han consolidado como estándar de facto debido a su elevado rendimiento en datos tabulares estructurados. Sin embargo, en los últimos años han surgido modelos de aprendizaje profundo específicamente diseñados para datos tabulares, como TabNet, que incorporan mecanismos de atención interpretables.

A pesar de estos avances, persiste incertidumbre sobre la viabilidad real del aprendizaje profundo tabular en entornos financieros regulados, debido a preocupaciones relacionadas con:

- Estabilidad del entrenamiento.
- Interpretabilidad de las decisiones.
- Calibración probabilística.
- Robustez frente a cambios en la distribución de datos.
- Aceptación industrial.

Este trabajo aborda esta brecha mediante una evaluación experimental rigurosa y reproducible.

---

### 1.2 Problema de investigación

No está claramente establecido si los modelos de aprendizaje profundo tabular interpretable pueden ofrecer un rendimiento predictivo competitivo frente a modelos tradicionales basados en árboles, manteniendo simultáneamente un nivel de interpretabilidad suficiente para su aplicación en decisiones crediticias reales.

---

### 1.3 Pregunta de investigación

¿Cuál es el desempeño relativo del modelo de aprendizaje profundo tabular interpretable TabNet en términos de rendimiento predictivo y calibración, en comparación con Regresión Logística y XGBoost, y en qué medida mantiene estabilidad y coherencia interpretativa bajo un protocolo experimental homogéneo aplicado al dataset SBA FOIA 7(a)?

---

## 2. Objetivos

### 2.1 Objetivo General

Evaluar, durante el periodo de elaboración del Trabajo Fin de Máster, mediante un diseño experimental comparativo y reproducible, si el modelo TabNet alcanza no inferioridad frente a XGBoost en términos de discriminación (ROC-AUC, margen Δ ≤ 0.02), manteniendo calibración comparable (Brier Score no significativamente mayor) y estabilidad inter-fold equivalente, bajo un esquema de validación cruzada estratificada 5×k aplicado al dataset SBA FOIA 7(a).

Además, analizar la robustez de los modelos ante un cambio de distribución asociado al periodo posterior a COVID-19, utilizando un enfoque de entrenamiento base pre-COVID y evaluación de estrés post-COVID.

---

### 2.2 Objetivos Específicos

1. Implementar y configurar tres modelos bajo un protocolo homogéneo:
   - Regresión Logística (baseline lineal).
   - XGBoost (modelo estándar industrial).
   - TabNet (modelo de aprendizaje profundo tabular interpretable).

2. Diseñar y ejecutar un pipeline experimental reproducible que garantice:
   - Mismo preprocesamiento.
   - Mismas particiones de datos.
   - Control explícito de semillas aleatorias.
   - Validación cruzada estratificada 5×k.

3. Optimizar los hiperparámetros de cada modelo mediante un esquema comparable de búsqueda, utilizando ROC-AUC como métrica objetivo primaria durante la validación.

4. Comparar el rendimiento discriminativo de los modelos utilizando:
   - ROC-AUC como métrica primaria.
   - PR-AUC como métrica complementaria.
   - KS statistic como métrica complementaria.
   - Intervalos de confianza al 95%.

5. Contrastar estadísticamente la hipótesis de no inferioridad de TabNet frente a XGBoost mediante:
   - Diferencia media de ROC-AUC.
   - Evaluación formal del margen Δ ≤ 0.02.
   - Aplicación de pruebas estadísticas apropiadas sobre los resultados inter-fold.

6. Evaluar la calibración probabilística de los modelos mediante:
   - Brier Score.
   - Curvas de confiabilidad.
   - Comparación estadística de diferencias en error probabilístico.

7. Analizar la estabilidad del rendimiento entre particiones mediante:
   - Desviación estándar inter-fold.
   - Intervalos de confianza.
   - Comparación de la dispersión entre modelos.

8. Evaluar la interpretabilidad global y local de los modelos mediante:
   - SHAP en XGBoost.
   - Coeficientes en Regresión Logística.
   - Máscaras de atención y atribuciones agregadas en TabNet.
   - Análisis de coherencia interpretativa respecto al dominio crediticio.

9. Analizar el compromiso entre discriminación, calibración e interpretabilidad para determinar la viabilidad práctica del enfoque de aprendizaje profundo en contextos de scoring crediticio regulado.

10. Evaluar robustez ante cambio de distribución (stress test COVID-19):
   - Entrenamiento y validación interna sobre el subconjunto pre-COVID (base).
   - Evaluación adicional sobre el subconjunto post-COVID (estrés), manteniendo el mismo pipeline y criterios de evaluación.
   - Comparación del deterioro relativo entre modelos en discriminación, calibración y métricas complementarias.

11. Derivar conclusiones fundamentadas sobre la viabilidad operativa de TabNet en comparación con modelos tradicionales, bajo criterios cuantitativos previamente definidos.

---

## 3. Hipótesis de investigación

El presente estudio adopta un enfoque confirmatorio bajo un marco de inferencia estadística con nivel de significación α = 0.05 e intervalos de confianza al 95%.

La comparación entre modelos se realizará mediante validación cruzada estratificada, evaluando el desempeño promedio obtenido en cada métrica sobre los distintos folds.

---

### 3.1 Hipótesis principal (Discriminación)

El desempeño discriminativo se evaluará mediante el Área Bajo la Curva ROC (ROC-AUC).

Sea:

- μ_TN = media del ROC-AUC de TabNet.
- μ_XGB = media del ROC-AUC de XGBoost.
- μ_RL = media del ROC-AUC de Regresión Logística.

Se plantea el siguiente contraste bilateral entre TabNet y XGBoost:

- H₀₁: μ_TN = μ_XGB  
- H₁₁: μ_TN ≠ μ_XGB  

De forma complementaria, se contrastará TabNet frente a Regresión Logística:

- H₀₁b: μ_TN = μ_RL  
- H₁₁b: μ_TN ≠ μ_RL  

El análisis se realizará sobre diferencias pareadas inter-fold del ROC-AUC.

---

### 3.2 Hipótesis secundaria (Desempeño probabilístico)

El desempeño probabilístico global se evaluará mediante el Brier Score.

Sea:

- μ_Brier_TN = media del Brier Score de TabNet.
- μ_Brier_XGB = media del Brier Score de XGBoost.
- μ_Brier_RL = media del Brier Score de Regresión Logística.

Dado que valores menores de Brier Score indican mejor desempeño probabilístico, se plantean los siguientes contrastes unilaterales.

Entre TabNet y XGBoost:

- H₀₂: μ_Brier_TN ≥ μ_Brier_XGB  
- H₁₂: μ_Brier_TN < μ_Brier_XGB  

Entre TabNet y Regresión Logística:

- H₀₂b: μ_Brier_TN ≥ μ_Brier_RL  
- H₁₂b: μ_Brier_TN < μ_Brier_RL  

---

### 3.3 Criterio de interpretación

Se considerará que TabNet constituye una alternativa competitiva en el contexto de scoring crediticio PYME si:

- Su desempeño discriminativo es estadísticamente comparable al de XGBoost.
- Presenta desempeño probabilístico equivalente o superior.
- Supera o iguala consistentemente a la Regresión Logística bajo el mismo protocolo experimental.

---

### 3.4 Justificación metodológica del criterio de no inferioridad y los contrastes de igualdad

El objetivo principal del estudio incorpora un criterio operativo de viabilidad basado en no inferioridad, definido mediante un margen Δ = 0.02 en términos de ROC-AUC, con el fin de traducir la comparación entre modelos a una regla de decisión práctica y consistente con el uso aplicado de modelos de scoring. Este criterio se utiliza como umbral de relevancia empírica para interpretar la magnitud de las diferencias, evitando conclusiones basadas únicamente en significación estadística.

De forma complementaria, el estudio plantea contrastes bilaterales de igualdad para comparar TabNet frente a XGBoost y Regresión Logística, con el propósito de evaluar si existen diferencias estadísticamente detectables en cualquier dirección bajo el mismo protocolo experimental. Esta dualidad responde a dos necesidades metodológicas: (i) disponer de un criterio de decisión cuantitativo asociado a viabilidad práctica (margen Δ) y (ii) mantener un marco inferencial simétrico que permita detectar tanto mejoras como deterioros.

En consecuencia, los resultados se interpretarán de manera jerárquica: primero, verificando el cumplimiento del criterio de no inferioridad como condición de viabilidad, y segundo, utilizando los contrastes bilaterales y los intervalos de confianza al 95% para caracterizar la evidencia estadística, la dirección del efecto y la incertidumbre asociada a las diferencias observadas.

---

## 4. Definición operacional de viabilidad

Se considerará que el modelo de aprendizaje profundo tabular es viable si cumple simultáneamente las siguientes condiciones:

1. Su ROC-AUC medio no es inferior en más de Δ = 0.02 respecto a XGBoost.
2. Su Brier Score no muestra deterioro significativo respecto al modelo de referencia.
3. Proporciona explicaciones globales y locales coherentes con el dominio financiero.
4. Mantiene estabilidad en diferentes particiones de validación cruzada.
5. No presenta degradación significativa en PR-AUC en escenarios de desbalance de clases.
6. Mantiene robustez razonable ante el stress test post-COVID en comparación con el periodo base pre-COVID.

---

## 5. Tipo de trabajo

El presente TFM se enmarca en la modalidad Tipo 3: Comparativa de soluciones, al realizar un análisis experimental sistemático entre distintos enfoques de modelado aplicados a un mismo problema de clasificación binaria.

---

## 6. Dataset

### 6.1 Dataset seleccionado

#### FOIA: Programas 7(a)

Existen cuatro archivos para el programa de préstamos 7(a) que segmentan los datos por década.

Se incluye un diccionario de datos para facilitar la navegación y comprensión de los archivos.

Nota: Los datos de la FOIA para los programas 7(a) se actualizan trimestralmente. Por lo general, la información está disponible un mes después del cierre de cada trimestre.

---

### Datos y Recursos

| Nombre del Archivo | Formato |
|---|---|
| Diccionario de Datos 7a_504_FOIA (al 31/12/25) | .xlsx |
| FOIA - 504 (FY1991-FY2009) (al 31/12/25) | .csv |
| FOIA - 504 (FY2010-Presente) (al 31/12/25) | .csv |
| FOIA - 7(a) (FY1991-FY1999) (al 31/12/25) | .csv |
| FOIA - 7(a) (FY2000-FY2009) (al 31/12/25) | .csv |
| FOIA - 7(a) (FY2010-FY2019) (al 31/12/25) | .csv |
| FOIA - 7(a) (FY2020-Presente) (al 31/12/25) | .csv |

---

### Información Adicional

- Última actualización: 6 de febrero de 2026, 9:58 AM (UTC-05:00)
- Fecha de creación: 9 de marzo de 2021, 12:33 PM (UTC-05:00)

### 6.2 Características

- Datos tabulares estructurados.
- Variables financieras relacionadas con comportamiento crediticio.
- Problema de clasificación binaria (default vs no default).
- Dataset representativo de escenarios reales de scoring PYME en EE.UU.

### 6.3 Justificación

- Relevancia en investigación académica.
- Idoneidad para modelos tabulares.
- Adecuado para evaluación de interpretabilidad.
- Representativo de escenarios reales de scoring.

---

## 7. Modelos a evaluar

### 7.1 Baseline estadístico
- Regresión Logística.

### 7.2 Modelo estándar industrial
- XGBoost.

### 7.3 Modelo deep learning tabular
- TabNet.

### 7.4 Justificación comparativa

Permiten comparar tres paradigmas de modelado:

- Modelo lineal interpretable.
- Ensemble basado en árboles.
- Arquitectura profunda con atención interpretable.

---

## 8. Diseño experimental

### 8.1 Esquema general

El diseño contempla dos evaluaciones complementarias:

1. Evaluación base (pre-COVID): comparación principal mediante validación cruzada estratificada 5×k.
2. Evaluación de estrés (post-COVID): evaluación adicional para analizar robustez ante cambio de distribución.

### 8.2 División de datos

- Validación cruzada estratificada (k = 5) en el subconjunto pre-COVID (base).
- Control de semillas aleatorias.
- Reproducibilidad completa del pipeline.

### 8.3 Optimización

- Búsqueda en rejilla (Grid Search) o método equivalente.
- Optimización basada en ROC-AUC.

### 8.4 Métrica primaria

- ROC-AUC.

### 8.5 Métricas secundarias

- PR-AUC.
- F1-score.
- KS statistic.
- Matriz de confusión.

### 8.6 Calibración

- Brier Score.
- Curvas de confiabilidad (Reliability curves).

### 8.7 Interpretabilidad

- SHAP values para XGBoost.
- Feature masks y mecanismos de atención para TabNet.
- Comparación de importancia global.
- Análisis local de casos representativos.
- Evaluación de estabilidad de explicaciones.

### 8.8 Control metodológico

- Misma partición para todos los modelos.
- Misma estrategia de validación.
- Mismo preprocesamiento.
- Comparación bajo condiciones experimentales homogéneas.

---

## 9. Pipeline experimental

1. Carga y limpieza del dataset.
2. Análisis exploratorio de datos.
3. Tratamiento de valores faltantes.
4. Preprocesamiento y transformación.
5. Segmentación del dataset en subconjuntos pre-COVID (base) y post-COVID (estrés).
6. División mediante validación cruzada sobre el subconjunto base.
7. Optimización y entrenamiento.
8. Evaluación de métricas.
9. Evaluación de calibración.
10. Generación de explicaciones.
11. Análisis comparativo.
12. Discusión del trade-off rendimiento–interpretabilidad.
13. Evaluación adicional de desempeño sobre el subconjunto de estrés post-COVID.

---

## 10. Alcance del trabajo

### Incluye

- Comparación experimental rigurosa.
- Evaluación de rendimiento predictivo.
- Análisis de calibración.
- Evaluación de interpretabilidad.
- Pipeline reproducible.

### No incluye

- Implementación en producción.
- Desarrollo de nuevos algoritmos.
- Validación con datos propietarios.
- Análisis legal exhaustivo.
- Sistemas fintech completos.

---

## 11. Contribución esperada

- Evaluación empírica reproducible del aprendizaje profundo tabular en scoring crediticio.
- Definición operacional de viabilidad en entornos financieros.
- Análisis del compromiso entre rendimiento e interpretabilidad.
- Evidencia cuantitativa sobre la competitividad de TabNet frente a XGBoost.
- Marco metodológico replicable para estudios comparativos futuros.

---

## 12. Criterios de éxito del estudio

El estudio se considerará exitoso si:

1. Se implementa un pipeline completamente reproducible.
2. Se obtiene una comparación rigurosa bajo condiciones homogéneas.
3. Se presentan resultados estadísticamente sólidos.
4. Se analiza de forma crítica la interpretabilidad.
5. Se derivan conclusiones coherentes con los objetivos e hipótesis.
6. Se establece una posición clara sobre la viabilidad del enfoque profundo.
7. Se documenta el comportamiento de los modelos bajo el stress test post-COVID.
