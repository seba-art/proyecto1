<h1 style="margin-bottom: 0; font-weight: bold;">Proyecto: Predicción de depresión en estudiantes</h1>
<p style="margin-top: 0;">Introducción a la inteligencia artificial - Sebastián Lira y Sebastián Vásquez</p>

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

Con este dataset buscamos seleccionar las features más importantes para entrenar un modelo con el fin de predecir si un estudiante tiene síntomas de depresión o no. Para entrenar los datos utilizaremos el modelo Random Forest, también evaluaremos utilizar otro modelo como KNN para realizar comparaciones entre los modelos y analizar cuál logra una mayor precisión.

Nuestra estrategia de evaluación consiste en primero realizar una exploración y análisis de los datos para identificar el comportamiento de estos, identificar las features categóricas y numéricas, buscar datos faltantes y visualizar los datos mediante gráficos. Luego de esto se analizará el reducir el número de muestras, features o reducción de dimensionalidad para lograr mejores resultados. Una vez con los datos preparados se seleccionarán los datos de entrenamiento y testeo, se entrenará el modelo y se realizarán las predicciones. Estas serán evaluadas mediante métricas como accuracy, precision, recall, f1-score, entre otros. 

### Justificación del Modelo

Seleccionamos Random Forest ya que funciona bien en presencia de datos ruidosos o faltantes, lo que es común en encuestas o datos relacionados con salud mental. Por otro lado, es adecuado para bases de datos con mezclas de variables categóricas sin codificar y numéricas.
Como ventajas, al ser un método de ensamblado con una gran cantidad de árboles, reduce el riesgo de overfitting que se presenta en modelos de árbol únicos. También puede evaluar qué variables son más importantes para predecir la depresión, debido a que usa el índice de Gini el cúal mide la impureza.

Por otra parte, el dataset cuenta con ciertas limitaciones, al considerar sólo datos de estudiantes de la India no se podrán generalizar las predicciones para todos los países, ya que tener condiciones de vida diferentes que pueden afectar a la interpretación de los datos. Además, columnas como “Academic Pressure” o “Study Satisfaction” son autoevaluaciones subjetivas que pueden variar dependiendo de las personas.
