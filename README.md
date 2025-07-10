<h1 style="margin-bottom: 0; font-weight: bold;">Proyecto: Predicción de depresión en estudiantes</h1>
<p style="margin: 0;"><em>Sebastián Lira y Sebastián Vásquez - Introducción a la Inteligencia Artificial</em></p> 
<em>Docente: Gabriel Cabas M.</em>


### Definición del problema
Este proyecto se enfocará en analizar la depresión en los estudiantes universitarios, esta es una condición de salud mental que afecta a gran parte de los estudiantes hoy en día, con un alto impacto en la salud y la calidad de vida. Situaciones como el estrés académico, la falta de apoyo emocional, mala situación económica y problemas familiares pueden afectar en el estado emocional de las personas y por consiguiente en el desarrollo de esta condición. El hecho de poder detectarla a tiempo puede ayudar a prevenir consecuencias como el bajo rendimiento académico, abandono de estudios, desmotivación o incluso autolesiones.

Por lo tanto, la idea del modelo es lograr predecir si un estudiante presenta síntomas de depresión analizando los datos recolectados, lo cuál será útil para las instituciones educativas desarrollar e implementar medidas preventivas o apoyo psicológico. Creemos que es una problemática bastante relevante, especialmente en la actualidad donde se está dando una mayor atención a la salud mental y los recursos son limitados, por lo que las herramientas pueden ser de gran ayuda.

### Plan de Acción

El dataset a explorar contiene datos sobre depresión en estudiantes, donde encontramos 27.901 filas y 18 columnas con distintas características sobre el estudiante. Estas features son: 
- **ID**
- **Gender:** Masculino o femenino
- **Age**: Entre 18 y 24 años
- **City:** Ciudad donde viven
- **Profession:** Estudiante (No hay profesiones)
- **Academic Pressure:** Escala de 0 a 5
- **Work Pressure:** Escala de 0 a 5
- **CGPA:** Promedio General Acumulativo, es una métrica que representa el promedio de todas las notas obtenidas por un estudiante a lo largo de su programa académico
- **Study Satisfaction:** Escala de 0 a 5
- **Job Satisfaction:** Escala de 0 a 5
- **Sleep Duration**: Horas que duermen los estudiantes
- **Dietary Habits:** Clasificados en unhealthy, moderate, healthy, others
- **Degree:** Nivel de estudios
- **Have you ever had suicidal thoughts?:** Respuestas de si y no
- **Work/Study Hours** : Horas de estudio o trabajo
- **Financial Stress:** Escala de 1 a 5
- **Family History of Mental Illness:** Historial familiar de enfermedad mental
- **Depression:** Variable binaria

Con este dataset buscamos seleccionar las features más importantes para entrenar un modelo con el fin de predecir si un estudiante tiene síntomas de depresión o no. 

Nuestra estrategia de evaluación consiste en primero realizar una exploración y análisis de los datos para identificar el comportamiento de estos, identificar las features categóricas y numéricas, buscar datos faltantes y visualizar los datos mediante gráficos. Luego de esto se analizará el reducir el número de muestras, features o reducción de dimensionalidad para lograr mejores resultados. 

Una vez con los datos preparados se seleccionarán los datos de entrenamiento y testeo, se entrenará el modelo utilizando Random Forest y se realizarán las predicciones. Estas serán evaluadas mediante métricas como accuracy, precision, recall, f1-score, entre otros. 

### Justificación del Modelo

Seleccionamos Random Forest ya que funciona bien en presencia de datos ruidosos o faltantes, lo que es común en encuestas o datos relacionados con salud mental. Por otro lado, es adecuado para bases de datos con mezclas de variables categóricas sin codificar y numéricas.
Como ventajas, al ser un método de ensamblado con una gran cantidad de árboles, reduce el riesgo de overfitting que se presenta en modelos de árbol únicos. También puede evaluar qué variables son más importantes para predecir la depresión, debido a que usa el índice de Gini el cúal mide la impureza.

Por otra parte, el dataset cuenta con ciertas limitaciones, al considerar sólo datos de estudiantes de la India no se podrán generalizar las predicciones para todos los países, ya que tener condiciones de vida diferentes que pueden afectar a la interpretación de los datos. Además, columnas como “Academic Pressure” o “Study Satisfaction” son autoevaluaciones subjetivas que pueden variar dependiendo de las personas.

### Metodología Aplicada

Al cargar la base de datos en el código, lo primero que realizamos fue una exploración de los datos, verificando y eliminando la presencia de valores nulos (de los cuales sólo encontramos 3), y graficando las features mediante boxplots y gráficos de barras para entender su comportamiento y encontrar los outliers.

Se realizó un feature selection donde eliminamos de la data las columnas que no consideramos relevantes para nuestro análisis. Estas son:

- **ID**: Irrelevante para las predicciones
- **Profession**: La gran mayoría (99%) son estudiantes
- **Job Satisfaction**: Irrelevante al seleccionar solo estudiantes
- **Work Pressure**: Irrelevante al seleccionar solo estudiantes
- **Degree**: Irrelevante para el análisis de depresión
- **City**: Al ser solo ciudades de la India lo consideramos irrelevante para las predicciones.

Luego del feature selection, solo quedaron las que consideramos importantes a la hora de predecir si un estudiante tiene depresión. Dentro de estas features se encontraban algunas de tipo categórico, por lo que se transformaron a tipo numérico para poder utilizarlas en el modelo Random Forest. Estás features son:

- **Gender**: Se transformó a binario, 0 = femenino y 1 = masculino
- **Have you ever had suicidal thoughts?**: Se transformó a binario, 0 = no y 1 = si
- **Family History of Mental Illness**: Se transformó a binario, 0 = no y 1 = si
- **Sleep Duration**: Se transformó de string a float. Ej: “Less than 5 hours” = 4.5
- **Dietary Habits**: Se transformó de string a float. Ej: "Unhealthy" = 0
- **Age**: Se seleccionó un rango de edad de los 18 hasta los 35, ya que los registros por sobre los 35 años son mínimos

Además, se eliminaron los outliers aplicando técnicas como el rango intercuartil.

Una vez con los datos preparados, pasamos a la fase de entrenamiento del modelo. Primero creamos las variables X = data sin la columna depresión, Y = columna depresión. Con esto separamos los datos en entrenamiento y testeo usando un test_size del 30%.

Posteriormente se entrenó el modelo Random Forest estableciendo parámetros como n_estimators = 50 y max_depth = 10. Con el modelo entrenado obtuvimos resultados mediante diferentes métodos: classification_report, confusion_matrix, feature_importances, roc_curve y plot_tree.

### Resultados Obtenidos

Mediante el classification_report obtuvimos los primeros resultados en forma de las métricas del modelo. Estas son: precisión, recall, f1-score y acurracy.

Para los estudiantes sin depresión (clase 0) se obtuvieron los siguiente resultados:
- **Precisión**: Un 82% de los datos fueron predichos correctamente por el modelo.
- **Recall**: Identificó al 76% de los estudiantes que efectivamente no presentaban depresión.
- **F1-score**: Con un 79% representa un equilibrio entre precisión y recall, lo que indica un rendimiento aceptable en esta clase.

Para los estudiantes con depresión (clase 1) se obtuvieron los siguientes resultados:
- **Precisión**: Un 84% de los datos acertó el modelo.
- **Recall**: logró detectar correctamente al 89% de los estudiantes que presentan depresión.
- **F1-score**: al igual que con la clase 0, muestra un buen  muestra un buen equilibrio y rendimiento con un 86%.

Del análisis de la matriz de confusión, se puede concluir: 

- Para la clase con depresión,  el 88% de los estudiantes con depresión fueron correctamente identificados (Verdaderos Positivos)  y el 12%  fueron clasificados erróneamente como “sin depresión” (Falsos Negativos) . Esto podría ser un problema en un contexto real, ya que se predice que un estudiante tiene depresión cuando en realidad no la padece.

- Para la clase sin depresión, 76% de los estudiantes sin depresión fueron correctamente clasificados (Verdaderos Negativos)   y el 24% fueron clasificados erróneamente como si tuvieran depresión (Falsos Positivos). Esto podría llegar a generar malas interpretaciones o preocupación innecesaria.

Luego de esos resultados también obtuvimos un gráfico que muestra que feature tiene mayor importancia a la hora de realizar la predicción. Las tres variables con mayor influencia fueron:  “Have you ever had suicidal thoughts ?”,  “Academic Preassure” y “Financial Stress”. Estas variables reflejan factores críticos que influyen significativamente en la presencia de depresión entre estudiantes.

Además, se generó la curva ROC, con un valor AUC igual a 0.90, lo que indica que el modelo tiene un excelente rendimiento para distinguir entre estudiantes con y sin depresión. Por lo tanto, el modelo es altamente confiable y puede ser utilizado como herramienta para apoyar procesos de detección temprana de depresión.

Finalmente graficamos varios árboles aleatorios para poder visualizar cómo se estaban realizando las subdivisiones. Al analizarlos, pudimos observar consistentemente que la variable más utilizada era “Have you ever had suicidal thoughts ?”, lo cuál tiene coherencia con el análisis de la importancia de features, ya que esta característica es la más influyente en la predicción.Con respecto a la precisión general del modelo (Acurracy), el modelo logró un 84%. Este es un buen resultado, sobre todo al tratarse de un problema de salud mental, puesto que malas predicciones conllevan a diagnósticos peligrosos.

### Conclusiones
