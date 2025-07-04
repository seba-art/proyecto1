# **Proyecto: Predicción de depresión en estudiantes**


## **Definición del problema**
El proyecto que realizaremos se enfocará en analizar la depresión presente en los estudiantes puesto que es un problema de salud mental que hoy en día tiene un alto impacto en la educación y la calidad de vida. Situaciones como la falta de apoyo emocional, problemas familiares y el estrés académico pueden afectar en el estado emocional de las personas y por consiguiente en el desarrollo de esta condición. El hecho de poder detectarla a tiempo puede ayudar a prevenir consecuencias como el bajo rendimiento académico, abandono de estudios, desmotivación o incluso autolesiones.
Por lo tanto, la idea del modelo es lograr predecir si un estudiante presenta síntomas de depresión analizando los datos recolectados, lo cuál será útil para las instituciones educativas desarrollar e implementar medidas preventivas o apoyo psicológico. Creemos que es una problemática bastante relevante, especialmente en la actualidad donde se está dando una mayor atención a la salud mental y los recursos son limitados, por lo que las herramientas pueden ser de gran ayuda.

## **Plan de Acción**

El dataset a explorar contiene datos sobre depresión en estudiantes, donde encontramos 27.901 filas y 18 columnas con distintas características sobre el estudiante. Estas features son: 
- **ID**
- **Gender:** Masculino o femenino
- **Age**: entre 18 y 24 años
- **City:** Ciudad donde viven
- **Profession:** Estudiante (No hay profesiones)
- **Academic Pressure:** en escala de 0 a 5
- **Work Pressure:** en escala de 0 a 5
- **CGPA:** Promedio General Acumulativo, es una métrica que representa el promedio de todas las calificaciones obtenidas por un estudiante a lo largo de su programa académico
- **Study Satisfaction:** en escala de 0 a 5
- **Job Satisfaction:** en escala de 0 a 5
- **Sleep Duration**: Horas que duermen las personas.
- **Dietary Habits:** Clasificados en unhealthy, moderate, healthy, others
- **Degree:** Nivel de estudios
- **Have you ever had suicidal thoughts?:** Respuestas de si y no
- **Work/Study Hours** : Horas de estudio o trabajo
- **Financial Stress:** en escala de 1 a 5
- **Family History of Mental Illness:** Historial familiar
- **Depression:** en binario 

Con este dataset buscamos seleccionar las features más importantes para entrenar un modelo con el fin de predecir si un estudiante tiene depresión o no. Para entrenar los datos utilizaremos el modelo Random Forest, también evaluaremos utilizar otro modelo como KNN para realizar comparaciones entre los modelos y analizar cuál logra una mayor precisión.

## **Justificación del modelo**

Seleccionamos Random Forest ya que funciona bien en presencia de datos ruidosos o faltantes, lo que es común en encuestas o datos relacionados con salud mental. Por otro lado, es adecuado para bases de datos con mezclas de variables categóricas sin codificar y numéricas.
Como ventajas, al ser un método de ensamblado con una gran cantidad de árboles, reduce el riesgo de overfitting que se presenta en modelos de árbol únicos. También puede evaluar qué variables son más importantes para predecir la depresión, debido a que usa el índice de Gini y este mide la impureza.
De igual manera, este tiene ciertas limitaciones, el dataset al considerar sólo datos de la India no se podrá generalizar para todos los países ya que se puede tener condiciones de vida diferentes que pueden afectar a la predicción y la interpretación de los datos. También columnas como “Academic Pressure” o “Study Satisfaction” son autoevaluaciones subjetivas que pueden variar dependiendo de las personas.
