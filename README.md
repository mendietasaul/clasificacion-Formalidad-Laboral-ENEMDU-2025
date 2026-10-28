# Clasificación Predictiva de la Formalidad Laboral en el Ecuador (ENEMDU 2025)
**Proyecto Aplicado — Maestría en Ciencia de Datos y Máquinas de Aprendizaje con mención en IA**  
**Universidad Internacional del Ecuador (UIDE)**

---

## 1. Descripción del Proyecto
Este proyecto desarrolla una solución integral de Ciencia de Datos y Aprendizaje Automático Supervisado (*Machine Learning*) para modelar, clasificar e identificar los factores estructurales y de talento humano que determinan la pertenencia de un trabajador al **sector formal (`1`)** o **informal (`0`)** de la economía ecuatoriana, utilizando los microdatos oficiales de la Encuesta Nacional de Empleo, Desempleo y Subempleo (**ENEMDU 2025**) del INEC.

* **Universo analítico:** 154.330 personas ocupadas de 15 años o más (PET y PEA ocupada).
* **Partición experimental:** Entrenamiento (80% = 123.464 registros) y Prueba (20% = 30.866 registros) con muestreo estratificado.
* **Transformación matricial:** `ColumnTransformer` integrando `StandardScaler` (variables continuas) y `OneHotEncoder(drop='first')` (variables categóricas), expandiendo las 10 variables originales a **51 características matemáticas**.

---

## 2. Arquitectura y Herramientas Utilizadas
* **Lenguaje de Programación:** Python 3 (Google Colab).
* **Ingeniería de Datos y Almacenamiento Relacional:** `pandas`, `numpy` y **SQLite3** (`enemdu_2025.db` — tabla maestra `empleo_formalidad`).
* **Visualización y Análisis Estadístico:** `matplotlib`, `seaborn`, `openpyxl`.
* **Machine Learning (`scikit-learn`):**
  1. *Regresión Logística* (Modelo base paramétrico lineal).
  2. *Random Forest Classifier* (Ensamble no lineal por *Bagging*).
  3. *Gradient Boosting Classifier* (Ensamble secuencial por *Boosting* — **Modelo Campeón**).

---

## 3. Resultados Principales (Conjunto de Prueba: n = 30.866)

| Algoritmo / Modelo | Exactitud Global | Precisión (Formal = 1) | Sensibilidad / *Recall* (Formal = 1) | *F1-Score* (Formal = 1) | *F1-Score* Ponderado | ROC-AUC |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **Regresión Logística** | 86,59% | **88,75%** | 86,16% | 87,44% | 86,61% | 0,9415 |
| **Random Forest** | 85,30% | 86,49% | 86,33% | 86,41% | 85,30% | 0,9280 |
| **Gradient Boosting (ganador)** | **87,00%** | 88,32% | **87,57%** | **87,94%** | **87,00%** | **0,9450** |

### Matrices de Confusión Comparativas
![Matrices de Confusión](Resultados%20Aprendizaje.png)

### Top 15 Importancia de Variables (Gradient Boosting)
![Importancia de Variables](Aporte%20al%20modelo%20por%20variable.png)

---

## 4. Estructura del Repositorio y Entregables
* `01_ETL_y_EDA_ENEMDU_2025.ipynb` y `02_Modelado_SQL_y_Clasificacion.ipynb`: Notebooks con el flujo de trabajo (ETL, EDA, SQLite y Machine Learning).
* `Tabulaciones_EDA_ENEMDU_2025_v2.xlsx`: Cuadros estadísticos bivariados y descriptivos.
* `Informe Proyecto Ingreso - Machine Learning.pdf`: Documento académico completo del estudio.
* **Dataset (`enemdu_2025.db` y `.csv`):** Bases de datos originales y depuradas listas para consulta.
* **Video Explicativo (Presentación):** **[Falta poner el enlace]**.

---

## 5. Ética, Privacidad y Uso Responsable de Datos
Los microdatos empleados corresponden a registros públicos anonimizados por el INEC bajo el amparo del secreto estadístico nacional. El flujo de trabajo excluye identificadores personales o de vivienda, mitiga sesgos demográficos mediante controles estructurales y se destina exclusivamente a fines académicos y de diseño de políticas públicas basadas en evidencia.

---
**Autor:** Saúl Fernando Mendieta Tenesaca  
**Año:** 2026
