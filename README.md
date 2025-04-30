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

---

## 📦 Limpieza y Transformación de Datos  

- Conversión de etiquetas a factores y codificación dummy (`class.ind`).
- Imputación con la mediana, centrado y escalado de variables predictoras.
- Verificación de estructura, dimensiones y balance de clases.
- Alineación de columnas entre `train` y `test`.

---

## 🛠 Herramientas Utilizadas  

- **Lenguaje:** R  
- **Entorno:** RStudio  
- **Librerías:** `caret`, `dplyr`, `ggplot2`, `nnet`, `neuralnet`  
- **Datos:** Kaggle House Prices (`train.csv`)  
- **Control de versiones:** GitHub  

---

## 📢 Hallazgos Destacados  

✔️ Ambos modelos clasifican correctamente más del **85%** de las viviendas.  
✔️ La clase **media** sigue siendo la más difícil de predecir, pero mejora con RNA.  
✔️ No se detectó **sobreajuste**, gracias a la validación cruzada y arquitectura simple.  
✔️ El modelo con `neuralnet` fue **ligeramente más preciso**, pero más lento.  
✔️ El pipeline queda listo para comparar regresión en el siguiente inciso.
