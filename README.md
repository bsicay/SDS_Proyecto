
# **Detección de Fraudes Secuenciales en Transacciones**

Este proyecto tiene como objetivo mejorar la detección de fraudes en transacciones de tarjeta de crédito, enfocándose particularmente en identificar **patrones secuenciales de fraude**. Los fraudes secuenciales son aquellos donde un mismo cliente o tarjeta realiza múltiples transacciones fraudulentas en cortos periodos de tiempo, siguiendo patrones específicos de comportamiento.

Para ello, se desarrollaron **métricas de evaluación personalizadas** y se aplicaron técnicas avanzadas de ingeniería de características, optimizando la detección mediante el uso de modelos de Machine Learning basados en **LightGBM**.

---

## **Estructura del Proyecto**

- **`exploracion_transformacion.ipynb`**
  
  - Análisis exploratorio de datos (**EDA**).
  - Creación de nuevas variables orientadas a detectar fraudes secuenciales:
    - Variables temporales (gaps de tiempo, ventanas móviles).
    - Variables geográficas (distancias entre transacciones).
    - Contadores de frecuencia de transacción.
    - Agrupación de fraudes en clústeres temporales.
  - Definición de la variable objetivo auxiliar: `is_sequential_fraud_pattern`.

- **`model.ipynb`**

  - Preparación de datos para modelado (train/test split, codificación de variables categóricas).
  - Entrenamiento de un **modelo base** utilizando LightGBM con métricas tradicionales (`AUC-ROC`, `F1-score`).
  - Definición y aplicación de **tres métricas de evaluación personalizadas**:
    - Penalización de falsos positivos (`fp_penalty`).
    - Penalización basada en ratio de falsos positivos (`fp_ratio_penalty`).
    - Balanced F1-score ponderado (`balanced_f1`).
  - Comparación de resultados entre el modelo base y los modelos personalizados utilizando:
    - Reportes de clasificación.
    - Curvas ROC-AUC.
    - Matrices de confusión.
    - Comparativas de Precision, Recall y F1-Score.

---

## **Requisitos**

- Python 3.8+
- Pandas
- NumPy
- LightGBM
- scikit-learn
- Seaborn
- Matplotlib
- Geopy




## **Resultados Principales**

-   **ROC AUC** cercano a 1.0 en todos los modelos.
    
-   **Precision** y **Recall** superiores al 99.8% para la detección de fraudes secuenciales.
    
-   **Reducción de falsos positivos** al utilizar métricas de evaluación personalizadas.


## **Conclusión**

El proyecto demuestra que mediante una correcta ingeniería de variables y el uso de funciones de evaluación personalizadas, es posible mejorar sustancialmente la detección de fraudes secuenciales sin comprometer el recall, manteniendo la cantidad de falsos positivos en niveles mínimos.