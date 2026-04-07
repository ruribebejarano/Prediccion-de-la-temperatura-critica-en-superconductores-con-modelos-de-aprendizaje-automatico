# ⚡ Superconductor Tc Predictor: Machine Learning para Ciencia de Materiales

![Status](https://img.shields.io/badge/Status-Completed-success)
![Python](https://img.shields.io/badge/Python-3.0+-blue)
![Framework](https://img.shields.io/badge/Framework-Scikit--Learn%20%7C%20XGBoost-orange)

## Descripción del Proyecto
[cite_start]Este proyecto desarrolla un sistema predictivo de la **Temperatura Crítica ($T_c$)** de materiales superconductores basándose únicamente en su fórmula química. [cite_start]La capacidad de predecir $T_c$ es vital para acelerar el descubrimiento de materiales que operen a altas temperaturas, con aplicaciones revolucionarias en medicina (MRI), energía y física de partículas[cite: 295, 301].

## El Desafío de Ingeniería
[cite_start]Predecir $T_c$ es complejo debido a la alta asimetría de los datos (de 0.0002K a 185K) y la presencia de outliers extremos[cite: 322]. 

### Pipeline de Datos:
* **Dataset:** 21,263 muestras de la base de datos NIMS (Japón).
* [cite_start]**Feature Engineering:** Extracción de 81 características basadas en propiedades atómicas (masa, ionización, conductividad térmica, etc.)[cite: 297, 320].
* [cite_start]**Preprocesamiento:** Implementación de **Winsorización** para manejo robusto de outliers y reducción de dimensionalidad mediante umbrales de varianza y correlación ($>0.7$)[cite: 325, 331, 337].

## Modelos y Resultados
[cite_start]Se evaluaron 5 arquitecturas diferentes, optimizadas mediante `RandomizedSearchCV`[cite: 298, 335, 346, 351]:

| Modelo | $R^2$ (Test) | RMSE (Test) |
| :--- | :---: | :---: |
| **Stacking Regressor** (Ensamble Final) | **0.93** | **9.21 K** |
| Random Forest Regressor | 0.93 | 9.30 K |
| XGBoost Regressor | 0.93 | 9.31 K |
| Polynomial Ridge Regression | 0.87 | 14.21 K |
| Support Vector Regression (SVR) | 0.84 | 13.79 K |
[cite_start][cite: 369]

> [cite_start]**Insight Clave:** El modelo **Stacking** (combinando XGBoost, SVR y Random Forest) logró la mejor generalización al capturar diversos tipos de sesgos y varianzas de los modelos base[cite: 357, 391].

## Tecnologías Utilizadas
* **Lenguaje:** Python 3.0 [cite: 300]
* [cite_start]**Entorno:** Google Colab [cite: 300]
* [cite_start]**Librerías:** Pandas, Scikit-Learn (VarianceThreshold, StandardScaler, RidgeCV), XGBoost[cite: 300, 331, 346, 357].

## Cómo usar este repositorio
1. Clona el repo.
2. Instala dependencias: `pip install -r requirements.txt`.
3. Ejecuta el notebook `Superconductor_ML.ipynb`.

## Conclusiones
[cite_start]Los modelos de ensamble demostraron ser herramientas prometedoras para acelerar la identificación de nuevos materiales de alto $T_c$ en fase de diseño, ofreciendo una precisión significativamente mayor que las reglas empíricas tradicionales[cite: 390, 395].
