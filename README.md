# gold-recovery-prediction
Regression model predicting gold recovery rates in an industrial flotation process, using a custom weighted sMAPE metric and validation against a dummy baseline.
## English

### Problem
Zyfra, an industrial process optimization company, needs a model to predict the amount of gold recovered from ore during a flotation and purification process, in order to optimize production and eliminate unprofitable parameters. The model must predict recovery at two stages: the rougher (initial) process and the final process.

### Approach
- Verified the provided recovery formula by recalculating it manually and comparing it against the dataset's own value, confirming near-zero error (MAE = 9.3e-15).
- Identified that the test set is missing all `output`/`calculation` columns, since these depend on lab measurements not yet available at prediction time — and structured feature selection accordingly to avoid data leakage.
- Cleaned missing values via median imputation (computed only from training data) and removed anomalous rows with zero or near-zero total substance concentration, indicative of process shutdowns.
- Built a custom evaluation metric: sMAPE, weighted 25% on the rougher stage and 75% on the final stage, matching the project's business requirement.
- Trained and tuned a Random Forest, validating the final model against a dummy baseline to confirm it adds real predictive value beyond a naive average-based guess.

### Results
- **Test sMAPE: 4.75 (rougher), 8.30 (final), 7.42 (weighted overall)** — outperforming the dummy baseline (7.58).
- Identified and documented a structural limitation: the final-stage prediction is inherently harder, since the most informative variables about each processing stage are only known *after* that stage occurs — a data availability constraint no amount of hyperparameter tuning can overcome.

### Stack
Python | pandas | scikit-learn | NumPy | Jupyter Notebook

---

## Español

### Problema
Zyfra, una empresa de optimización de procesos industriales, necesita un modelo para predecir la cantidad de oro recuperado del mineral durante un proceso de flotación y purificación, con el fin de optimizar la producción y eliminar parámetros no rentables. El modelo debe predecir la recuperación en dos etapas: el proceso rougher (inicial) y el proceso final.

### Enfoque
- Se verificó la fórmula de recuperación proporcionada recalculándola manualmente y comparándola contra el valor propio del dataset, confirmando un error casi nulo (EAM = 9.3e-15).
- Se identificó que al conjunto de prueba le faltan todas las columnas `output`/`calculation`, ya que dependen de mediciones de laboratorio no disponibles al momento de la predicción — y se estructuró la selección de features en consecuencia para evitar fuga de datos.
- Se limpiaron valores ausentes mediante imputación por mediana (calculada solo con datos de entrenamiento) y se eliminaron filas anómalas con concentración total de sustancias en cero o casi cero, indicativas de paros de proceso.
- Se construyó una métrica de evaluación personalizada: sMAPE, ponderado 25% en la etapa rougher y 75% en la etapa final, conforme al requerimiento de negocio del proyecto.
- Se entrenó y ajustó un bosque aleatorio, validando el modelo final contra un modelo dummy de referencia para confirmar que aporta valor predictivo real más allá de una estimación ingenua basada en el promedio.

### Resultados
- **sMAPE de prueba: 4.75 (rougher), 8.30 (final), 7.42 (ponderado general)** — superando al modelo dummy de referencia (7.58).
- Se identificó y documentó una limitación estructural: la predicción de la etapa final es inherentemente más difícil, ya que las variables más informativas de cada etapa de proceso solo se conocen *después* de que esa etapa ocurre — una restricción de disponibilidad de datos que ningún ajuste de hiperparámetros puede superar.

### Stack
Python | pandas | scikit-learn | NumPy | Jupyter Notebook

---

**Santiago Quintanilla** — Mechatronics Engineer | Data Science Student @ TripleTen
LinkedIn: https://www.linkedin.com/in/santiago-quintanilla-zurita
GitHub: https://github.com/borre3205
