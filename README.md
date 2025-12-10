# 🛢️ Oil Well Profit Optimization

Proyecto para identificar la mejor región donde abrir 200 nuevos pozos petrolíferos utilizando datos geológicos sintéticos y modelos de regresión lineal. Se analizan beneficios esperados y riesgos mediante bootstrapping.

---

## 📘 Descripción del proyecto
La empresa petrolera **OilyGiant** desea seleccionar la región óptima para desarrollar **200 nuevos pozos**. Para ello se utilizan datos geológicos de tres regiones, con información sobre las características del terreno y el volumen de reservas de cada posible punto de perforación.

El objetivo es:
1. Predecir el volumen de reservas de cada pozo con **Regresión Lineal**.  
2. Seleccionar los **200 pozos con mayor volumen estimado** en cada región.  
3. Calcular el beneficio proyectado por región.  
4. Utilizar **bootstrapping** para estimar riesgo y variabilidad de ganancias.  
5. Elegir la mejor región cumpliendo:  
   - Beneficio promedio más alto  
   - Riesgo de pérdida **< 2.5%**

---

## 🗂 Dataset
Archivos:  
- `/datasets/geo_data_0.csv`  
- `/datasets/geo_data_1.csv`  
- `/datasets/geo_data_2.csv`

**Características:**
- `id` — identificador del pozo  
- `f0`, `f1`, `f2` — características geológicas  
- `product` — volumen de reservas (en miles de barriles)

---

## 🛠️ Proceso del proyecto

### 1. Preparación de datos
- Carga de datasets  
- División 75/25 en train/validation  
- Escalado y preparación de variables  

---

### 2. Entrenamiento del modelo
- **Regresión Lineal** entrenada por separado para cada región  
- Predicción sobre el conjunto de validación  
- Métricas evaluadas:  
  - Volumen medio predicho  
  - RMSE  
- Resultados analizados para las tres regiones

---

### 3. Cálculo preliminar de ganancias
- Se desarrollarán **200 pozos** por región  
- Presupuesto: **100 millones USD**  
- Ingreso por unidad: **4500 USD**  
- Punto de equilibrio: **111.1 unidades (miles de barriles)**  
- Se comparó este valor con las reservas medias de cada región  

---

### 4. Selección de pozos y cálculo de beneficio
- Predicción del volumen total para los **200 pozos con mayores reservas estimadas**  
- Cálculo del beneficio esperado por región utilizando:  
  `ganancia = (reservas · 4500) – 100.000.000`

---

### 5. Bootstrapping (1000 iteraciones)
Para cada región se estimó:
- Beneficio promedio  
- Intervalo de confianza al 95%  
- Riesgo de pérdida (<0 USD)

---

## 🏆 Resultados y conclusiones

### ✔ Riesgo (todas las regiones)
- **Todas las regiones presentan un riesgo de pérdida < 2.5%**, por lo que son aceptables.

### ✔ Ganancias promedio
- **Región 1** → Mayor beneficio promedio  
- **Región 2** → Menor beneficio promedio  

### ✔ Riesgo comparado
- **Región 1** → Mayor riesgo dentro de lo aceptable (<2.5%)  
- **Región 0** → Riesgo más bajo  

### 🎯 **Región recomendada**
**La Región 1**, debido a:
- El **beneficio promedio más alto**  
- Riesgo dentro del límite permitido  
- Resultados consistentes con la selección previa basada en predicciones sin bootstrapping  

---

## 🧰 Tecnologías utilizadas
- Python  
- pandas  
- numpy  
- scikit-learn  
- matplotlib / seaborn  
