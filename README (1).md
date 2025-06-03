

# Proyecto Final - Programación 2025-1

Este proyecto consiste en el desarrollo de un sistema de análisis y modelado predictivo aplicado a datos de salud relacionados con indicadores de diabetes. Se siguen todas las fases de un pipeline de ciencia de datos, desde la adquisición del dataset hasta la comparación y evaluación de modelos de clasificación.

---

## 📁 Estructura del repositorio

```
.
├── 01 - exploración.ipynb
├── 02 - preprocesado.ipynb
├── 03 - modelo 1.ipynb
├── 04 - modelo 2.ipynb
├── 05 - comparación.ipynb
├── 06 - dataset_original.csv
├── 06 - dataset_valores_nulos.csv
├── 07 - informe.pdf
└── README.md
```

---

## 🧾 Dataset

El dataset fue obtenido desde la plataforma [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/891/cdc%2Bdiabetes%2Bhealth%2Bindicators), específicamente el conjunto de datos:

**CDC Diabetes Health Indicators Dataset** (ID: 891)

Para cargar y preparar el dataset se utilizó el siguiente código:

```python
from ucimlrepo import fetch_ucirepo 
import pandas as pd

# Fetch dataset 
cdc_diabetes_health_indicators = fetch_ucirepo(id=891) 

# Unir features y target
X = cdc_diabetes_health_indicators.data.features 
y = cdc_diabetes_health_indicators.data.targets 
df = pd.concat([X, y], axis=1)

# Guardar como CSV
df.to_csv("06 - dataset_original.csv", index=False)
```

Posteriormente se simularon valores nulos (~5%) para cumplir los requisitos del trabajo.

---

## ⚙️ Proceso realizado

1. **Exploración de datos**: análisis descriptivo, visualización de distribuciones, correlaciones y detección de outliers.
2. **Preprocesamiento**: imputación de valores nulos, normalización y codificación.
3. **Modelado**:
   - Modelo 1: Random Forest con `class_weight='balanced'`, optimizado para `recall`.
   - Modelo 2: LinearSVC también balanceado y optimizado para `recall`.
4. **Evaluación**: precisión, recall, F1-score, matriz de confusión, curvas de aprendizaje.
5. **Comparación de modelos**: incluyendo análisis de concordancia mediante Cohen’s Kappa (`0.8462`).

---

## 🧠 Conclusiones

Ambos modelos lograron una alta sensibilidad en la detección de casos positivos de diabetes (~75% de recall), siendo adecuados para contextos donde minimizar los falsos negativos es prioritario. La concordancia entre ambos modelos fue alta, lo que respalda la confiabilidad de sus predicciones.

---

## 👤 Autor

María J. Arias-Alejandro Mejía
Trabajo final de la asignatura **Programación 2025-1**
