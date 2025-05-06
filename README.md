# 📊 Entrega 7: Redes Neuronales Artificiales (RNA)

---

# 🧠 Proyecto de Clasificación y Regresión con Redes Neuronales

---

## 🏫 Universidad del Valle de Guatemala - Campus Central  
**Facultad:** Ingeniería  
**Departamento:** Ciencias de la Computación  
**Curso:** Minería de Datos (CC3074) - Sección 10  
**Semestre:** I – 2025  
**Proyecto:** Proyecto #2  
**Entrega:** Entrega 7 – Redes Neuronales Artificiales  

---

## 👥 Integrantes del Grupo #1  
- **Pablo Daniel Barillas Moreno** - *Carné No. 22193*  
- **Mathew Cordero Aquino** - *Carné No. 22982*  

---

## 📌 Descripción del Proyecto  

En esta entrega se desarrollaron dos modelos de **Redes Neuronales Artificiales** con el objetivo de clasificar viviendas como **baratas**, **medias** o **caras**, y también se abordó el problema de regresión para predecir el valor real de venta (`SalePrice`) de las viviendas. Se utilizaron los conjuntos `train_set.csv` y `test_set.csv` definidos previamente.

---

## 🔎 Actividades Realizadas  

### Serie 1: Reutilización de Conjuntos  
- Se cargaron los archivos `train_set.csv` (937 observaciones) y `test_set.csv` (232 observaciones).
- Se validó que `SalePriceCat` estuviera correctamente categorizada y balanceada (aprox. 1/3 por clase).

### Serie 2: Selección de Variable Respuesta  
- Se seleccionó `SalePriceCat` como variable de salida para clasificación.
- Se confirmó que no existieran valores nulos y que las etiquetas fueran factores correctamente definidos.

### Serie 3: Entrenamiento de Modelos de RNA  
- **Modelo 1:** Red neuronal simple con `nnet`, 5 predictores y 3 neuronas ocultas.
- **Modelo 2:** Red neuronal con `neuralnet`, misma entrada pero con 1 capa oculta de 4 neuronas.
- Se aplicó centrado, escalado e imputación a los datos.
- Ambos modelos se entrenaron correctamente y mostraron convergencia sin errores.

### Serie 4: Predicción y Evaluación  
- Ambos modelos realizaron predicciones sobre el conjunto de prueba.
- Se generaron **matrices de confusión** para comparar sus desempeños.
- Resultados:
  - **Modelo 1 (`nnet`)**: Accuracy = 85.78%, Kappa = 0.7867
  - **Modelo 2 (`neuralnet`)**: Accuracy = 87.07%, Kappa = 0.806

### Serie 5: Evaluación de Modelos  
- Se analizaron métricas por clase: sensibilidad, especificidad, precisión y balanced accuracy.
- Se observó que la clase **media** fue la más difícil de predecir.
- Se generaron gráficas de matrices de confusión para comparar visualmente errores y aciertos.

### Serie 6: Comparación de Modelos  
- Se comparó efectividad, tiempo de entrenamiento y errores por clase.
- Ambos modelos fueron similares, pero `neuralnet` mostró **ligera ventaja en precisión general**.
- El modelo `nnet` fue más rápido en tiempo de ejecución.

### Serie 7: Análisis de Overfitting  
- No se detectó sobreajuste en ninguno de los dos modelos.
- Se observó consistencia entre métricas de validación cruzada y prueba.
- Las curvas de aprendizaje fueron estables y convergentes.

### Serie 8: Tuning de Parámetros  
- Se utilizó `caret::train` con validación cruzada 10-fold para tunear el modelo `nnet`.
- Mejores resultados con `size = 3` y `decay = 0.1`.
- No se observó sobreajuste posterior al tuning; el modelo se mantuvo robusto.

### Serie 9: Cambio a Regresión (SalePrice)  
- Se reemplazó la variable objetivo por `SalePrice` para abordar el problema como regresión.
- Se aplicó el mismo preprocesamiento.
- Se confirmó el rango de precios (`35,311` a `745,000`) y consistencia en el conjunto.

### Serie 10: Modelos de Regresión con Redes Neuronales

* Se entrenaron **dos modelos de regresión** con redes neuronales para predecir el precio `SalePrice`:

  * Modelo 1: Red simple con `neuralnet` (1 capa, 3 neuronas).
  * Modelo 2: Red profunda con `neuralnet` (2 capas: 4 y 2 neuronas).
* Ambos modelos utilizaron los mismos 5 predictores (`OverallQual`, `GrLivArea`, `GarageCars`, `TotalBsmtSF`, `YearBuilt`) con preprocesamiento previo.
* La evaluación se hizo con métricas de regresión como **RMSE**, **MAE**, y **R²**.

### Serie 11: Comparación entre los Modelos de Regresión

* Se compararon los modelos por desempeño en el conjunto de prueba:

  * Modelo 1: RMSE ≈ 36,000; R² ≈ 0.78
  * Modelo 2: RMSE ≈ 32,500; R² ≈ 0.83
* El **modelo 2 fue superior** en precisión sin evidencia clara de sobreajuste.

### Serie 12: Análisis de Sobreajuste en Regresión

* Se usaron **curvas de aprendizaje** para visualizar el error de entrenamiento vs prueba.
* En ambos modelos, las curvas convergieron sin grandes brechas, **descartando sobreajuste**.
* Se observó estabilidad en el error conforme aumentaban los datos de entrenamiento.

### Serie 13: Tuneo de Parámetros del Mejor Modelo

* Se ajustaron hiperparámetros (`hidden`, `threshold`, `stepmax`, `act.fct`) del modelo 2.
* La mejor configuración fue con:

  * Capas ocultas: 4 y 2 neuronas
  * Activación: `logistic`
  * Threshold: 0.01
* **El tuning mejoró levemente el RMSE y R²**, sin provocar sobreajuste.

### Serie 14: Comparación con Modelos de Entregas Anteriores (Regresión)

* Se comparó el mejor modelo RNA con:

  * Regresión Lineal: R² ≈ 0.89, RMSE ≈ 28,000
  * Random Forest: R² ≈ 0.98, RMSE ≈ 15,000
  * SVM: R² ≈ 0.87, RMSE ≈ 33,000
* RNA tuvo **buen desempeño**, pero fue **superado por Random Forest y Regresión Lineal** en eficiencia y precisión.

### Serie 15: Comparación de Modelos de Clasificación

* Comparando el modelo RNA (clasificación) con entregas anteriores:

  * **SVM radial** y **RNA** obtuvieron los mejores `Kappa` (> 0.80).
  * RNA fue **más costoso computacionalmente**.
  * RNA tuvo ventaja en sensibilidad para la clase “cara”, pero menor precisión en “media”.

### Serie 16: Comparación de Modelos para Predecir Precio

* En regresión pura, **Random Forest y Regresión Lineal** dominaron por su precisión y rapidez.
* RNA fue una buena alternativa, **aunque más costosa y menos estable**.
* A pesar de su flexibilidad, **no fue el modelo más efectivo** en este caso.

### Serie 17: Conclusiones Globales de Modelos Usados

| Tipo de Modelo | Algoritmo         | Accuracy/R² | Kappa/MAE | Ventaja principal           |
| -------------- | ----------------- | ----------- | --------- | --------------------------- |
| Clasificación  | SVM radial        | 87.07%      | 0.806     | Mejor balance entre clases  |
| Clasificación  | RNA (`nnet`)      | 85.78%      | 0.786     | Alto rendimiento en “cara”  |
| Regresión      | Regresión Lineal  | R² 0.89     | MAE \~25K | Simplicidad y buen ajuste   |
| Regresión      | RNA (`neuralnet`) | R² 0.83     | MAE \~28K | Flexible, sin sobreajuste   |
| Regresión      | Random Forest     | R² 0.98     | MAE \~12K | Máxima precisión, más lento |

> En términos generales:

* **SVM** fue el mejor modelo para **clasificación**.
* **Random Forest** fue el mejor modelo para **regresión**.
* **RNA** mostró un **buen rendimiento en ambas tareas**, aunque no fue el más eficiente.

### Serie 18: Informe de Consultoría Técnica

* Se elaboró un **Informe de Consultoría Técnica** para la empresa ficticia **InmoValor**, con el objetivo de **recomendar el mejor modelo predictivo** para estimar el precio de las viviendas en función de datos estructurales.

* El informe incluyó:

  ✅ **Resumen ejecutivo** con el objetivo del análisis y los principales hallazgos.
  ✅ **Comparación de modelos predictivos** (Regresión Lineal, SVM, Random Forest, RNA).
  ✅ **Justificación del modelo recomendado**, considerando precisión, interpretabilidad y escalabilidad.
  ✅ **Gráficos de rendimiento** y tablas comparativas de métricas como R², MAE y RMSE.
  ✅ **Recomendaciones estratégicas** sobre cómo aplicar el modelo en un sistema de apoyo a decisiones inmobiliarias.

* El modelo recomendado para la empresa fue **Random Forest**, por ser el que alcanzó el **mejor rendimiento en predicción** de `SalePrice`, con un R² cercano a 0.98 y errores mínimos.

* También se destacó el uso potencial de redes neuronales en escenarios con grandes volúmenes de datos o relaciones no lineales más complejas.

> 📌 **Conclusión:** El informe ofreció un enfoque claro, técnico y orientado a negocios, basado en los resultados obtenidos durante el proyecto, con el objetivo de apoyar decisiones comerciales más precisas.

---

## 📦 Limpieza y Transformación de Datos  

- Conversión de etiquetas a factores y codificación dummy (`class.ind`).
- Imputación con la mediana, centrado y escalado de variables predictoras.
- Verificación de estructura, dimensiones y balance de clases.
- Alineación de columnas entre `train` y `test`.
- Verificación y balanceo de clases (`SalePriceCat`).

---

## 🛠 Herramientas Utilizadas

* **Lenguaje:** R
* **Entorno:** RStudio
* **Librerías:** `caret`, `nnet`, `neuralnet`, `ggplot2`, `dplyr`, `Metrics`, `reshape2`
* **Datos:** Kaggle House Prices (`train.csv`, `test.csv`)
* **Control de versiones:** GitHub

---

## 📢 Hallazgos Destacados  

✔️ Ambos modelos clasifican correctamente más del **85%** de las viviendas.  
✔️ La clase **media** sigue siendo la más difícil de predecir, pero mejora con RNA.
✔️ El modelo de RNA clasificó correctamente más del 87% de los casos.
✔️ No se detectó **sobreajuste**, gracias a la validación cruzada y arquitectura simple.  
✔️ El modelo con `neuralnet` fue **ligeramente más preciso**, pero más lento.  
✔️ El pipeline queda listo para comparar regresión en el siguiente inciso.
