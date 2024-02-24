Nombre: Joffre Quinteros

# Descripcion del proyecto

Supongamos que usted trabaja en el servicio de salud y recibe muestras que provienen de mujeres con cáncer de mama.
Los médicos han extraído características y las han anotado, su trabajo es crear un modelo que sea capaz de identificar si un paciente tiene o no cáncer.
Recordemos que un falso positivo no es tan preocupante como un falso negativo, ya que en el futuro se le hacen más pruebas a las pacientes y hay oportunidades de descubrir que
estábamos en un error.
Sin embargo, un falso negativo puede llevar a que el cáncer se desarrolle sin supervisión durante más tiempo del necesario y podría llevar a daños más graves o incluso la muerte de
la paciente.

# Reto
Teniendo en cuenta el contexto. Hay que desarrollar un modelo que funcione lo mejor posible.


# Descripcion del dataset
Las características se calculan a partir de una imagen digitalizada de una aspiración con aguja fina (PAAF) de una masa mamaria. Describen características de los núcleos celulares presentes en la imagen.
El plano de separación descrito anteriormente se obtuvo utilizando el árbol del método multisuperficie (MSM-T) [K. P. Bennett, "Construcción de árboles de decisión mediante programación lineal". Actas de la 4ª Sociedad de Inteligencia Artificial y Ciencias Cognitivas del Medio Oeste, págs. 97-101, 1992], un método de clasificación que utiliza programación lineal para construir un árbol de decisión. Las características relevantes se seleccionaron mediante una búsqueda exhaustiva en el espacio de 1 a 4 características y 1 a 3 planos de separación.
Dentro de los campos mas importantes tenemos los siguientes:

1) ID number
2) Diagnosis (M = malignant, B = benign)
3-32)

Ten real-valued features are computed for each cell nucleus:

	a) radius (mean of distances from center to points on the perimeter)
	b) texture (standard deviation of gray-scale values)
	c) perimeter
	d) area
	e) smoothness (local variation in radius lengths)
	f) compactness (perimeter^2 / area - 1.0)
	g) concavity (severity of concave portions of the contour)
	h) concave points (number of concave portions of the contour)
	i) symmetry 
	j) fractal dimension ("coastline approximation" - 1)

# Pasos a realizar en el ejercicio
1. Se procede a realizar la importación y evaluación de la información para determinar si hay valores nulos, vacios o incongruencias.
2. Se usan los distintos tipos de modelos para clasificación para ello se ejecutan los siguiente pasos:

	Dividir tus datos en características (X) y etiquetas (y), puedes seguir los siguientes pasos para construir y entrenar tu modelo:
	Dividir los datos en conjuntos de entrenamiento y prueba para evaluar el rendimiento del modelo.
	Importar la clase del modelo deseado
	Crear una instancia del clasificador
	Entrenar el modelo en el conjunto de entrenamiento.
	Evaluar el modelo en el conjunto de prueba.
	Ajustar los hiperparámetros del modelo si es necesario.
	Generar matrix de confusion para el conjunto de evaluación y entrenamiento.
3. Se determinan las conclusiones de que mejor funciona mejor y se tiene en cuenta la premisa de los valores falsos positivos que son importantes para el estudio ya que son vidas humanas afectadas que pueden llegar a tener complicaciones.


## Evaluación de los modelos

# SVM

SVM lineal es una variante de Support Vector Machine (SVM) que utiliza un kernel lineal para separar las clases en el espacio de características. En SVM lineal, la función de decisión es una función lineal de las características de entrada. Esto significa que intenta encontrar un hiperplano de separación lineal que maximice el margen entre las clases.
SVM lineal: Busca el hiperplano que mejor separa las dos clases de pacientes (con y sin cáncer).
¿Por que usarlo?

Eficiencia con datos de alta dimensionalidad: Los conjuntos de datos de detección de cáncer de mama a menudo tienen un gran número de características (por ejemplo, características extraídas de imágenes médicas o datos genómicos). SVM lineal es eficiente en espacios de alta dimensionalidad y puede manejar eficazmente conjuntos de datos con muchas características.

Buena generalización: SVM lineal tiende a generalizar bien a partir de conjuntos de datos de tamaño moderado a grande. Esto significa que puede funcionar bien en la detección de cáncer de mama en nuevos datos no vistos, lo que es crucial en aplicaciones médicas.

Robustez frente a sobreajuste: SVM lineal es menos propenso al sobreajuste en comparación con algunos otros modelos más complejos. Esto es importante en la detección de cáncer de mama, donde es fundamental evitar la clasificación incorrecta de casos positivos y negativos.

Resultados del ejercicio
Exactitud del modelo: 0.956140350877193
El modelo detectó 4 como benignos y eran malignos esto es particularmente importante ya que 4 personas estan en riesgo.

Random Forest Classifier
Random Forest Classifier es un algoritmo de aprendizaje automático que se utiliza comúnmente tanto para tareas de clasificación como de regresión. Es una técnica de conjunto (ensemble) que utiliza múltiples árboles de decisión durante el entrenamiento y produce una predicción basada en la mayoría de votos o promedio de las predicciones individuales de los árboles.

¿Por que usarlo?
Manejo de datos complejos: Los conjuntos de datos utilizados en la detección de cáncer de mama pueden contener una gran cantidad de características (por ejemplo, características extraídas de imágenes médicas o datos genómicos). Random Forest tiene la capacidad de manejar eficientemente conjuntos de datos grandes y complejos con muchas características sin requerir una reducción de dimensionalidad previa.

Precisión: Random Forest es conocido por su alta precisión en la clasificación, incluso en conjuntos de datos desequilibrados y con ruido. Esto es crucial en la detección de cáncer de mama, donde la precisión en la identificación de casos positivos y negativos es de suma importancia.

Robustez frente al sobreajuste: Aunque Random Forest es un modelo complejo, tiende a ser menos propenso al sobreajuste que otros modelos más complejos como las redes neuronales profundas. Esto es especialmente importante en aplicaciones médicas donde se deben evitar los falsos positivos y negativos.

Resultados del ejercicio
Exactitud del modelo: 0.9649122807017544
El modelo detectó 3 como benignos y eran malignos esto es particularmente importante ya que 3 personas estan en riesgo de 114 elementos evaluados.


# KNN

K-Nearest Neighbors (KNN) es un algoritmo de aprendizaje supervisado utilizado para problemas de clasificación y regresión. Funciona asignando una etiqueta a un punto de datos basándose en la mayoría de las etiquetas de sus vecinos más cercanos en el espacio de características. En otras palabras, clasifica un punto de datos basándose en la clase predominante entre sus k vecinos más cercanos.

¿Por qué usar KNN para la detección de cáncer de mama?

Simplicidad: KNN es un algoritmo simple y fácil de entender. Su principio subyacente es intuitivo y directo: un punto es clasificado por la mayoría de sus vecinos más cercanos.

No paramétrico: KNN es un algoritmo no paramétrico, lo que significa que no hace suposiciones explícitas sobre la distribución de los datos. Esto lo hace adecuado para problemas donde la distribución de los datos no es conocida de antemano.

Flexibilidad: KNN puede manejar de manera efectiva conjuntos de datos con características no lineales o complejas. Esto es importante en la detección de cáncer de mama, ya que puede haber relaciones no lineales entre las características y la presencia de la enfermedad.

Interpretabilidad: Aunque KNN no proporciona un modelo explícito como algunos otros algoritmos, su proceso de clasificación basado en vecinos cercanos permite una fácil interpretación. Puedes identificar visualmente los vecinos más cercanos de un punto de datos y comprender mejor por qué se tomó una decisión de clasificación particular.

Resultados del ejercicio
Exactitud del modelo: 0.9561
El modelo detectó 5 como benignos y eran malignos esto es particularmente importante ya que 5 personas estan en riesgo de 114 elementos evaluados.

# XGBOOST
XGBoost (Extreme Gradient Boosting) es una implementación eficiente y escalable de árboles de decisión potenciados por gradient boosting. Es ampliamente utilizado en competiciones de ciencia de datos y aplicaciones del mundo real debido a su velocidad, precisión y capacidad para manejar una variedad de tipos de datos.

¿Por qué usar XGBoost para la detección de cáncer de mama?

Alta precisión: XGBoost es conocido por su precisión sobresaliente en una variedad de conjuntos de datos, incluidos aquellos con características complejas y no lineales. En la detección de cáncer de mama, donde la precisión es crucial, XGBoost puede producir modelos altamente precisos.

Manejo de datos desequilibrados: Los conjuntos de datos de detección de cáncer de mama pueden ser desequilibrados, es decir, puede haber una cantidad significativamente mayor de muestras negativas (no cancerosas) que positivas (cancerosas). XGBoost tiene técnicas incorporadas para manejar conjuntos de datos desequilibrados y puede producir modelos robustos incluso en estas situaciones.

Regresión y clasificación: XGBoost es versátil y puede utilizarse tanto para problemas de clasificación como de regresión. Esto significa que puede adaptarse a diferentes tipos de conjuntos de datos utilizados en la detección de cáncer de mama, incluidos aquellos que requieren predicciones de diagnóstico y pronóstico.

Regularización integrada: XGBoost tiene opciones integradas para regularización, como la penalización de L1 y L2 en los pesos de los árboles, lo que ayuda a prevenir el sobreajuste y mejora la capacidad de generalización del modelo.

Resultados del ejercicio
Exactitud del modelo: 0.964
El modelo detectó 3 como benignos y eran malignos esto es particularmente importante ya que 3 personas estan en riesgo de 114 elementos evaluados.

# Redes Neuronales artificiales (perceptron)
Redes neuronales perceptrón: Un modelo simple con una capa de neuronas que puede ser suficiente para conjuntos de datos pequeños.
Un perceptrón es una de las formas más simples de una red neuronal artificial, que consiste en una sola capa de neuronas que realizan una operación de suma ponderada seguida de una función de activación. Fue propuesto por Frank Rosenblatt en 1957 y puede utilizarse para problemas de clasificación binaria.
¿Por qué usar un perceptrón para la detección de cáncer de mama?

Simplicidad: Los perceptrones son modelos simples y fáciles de entender. Su estructura y operación son intuitivas, lo que puede ser útil en aplicaciones médicas donde se requiere una comprensión clara del modelo de clasificación utilizado.

Rapidez de entrenamiento: Debido a su estructura simple, los perceptrones pueden entrenarse rápidamente en comparación con modelos más complejos como las redes neuronales profundas. Esto puede ser beneficioso en situaciones donde se necesitan resultados rápidos o donde el tiempo de entrenamiento es un factor crítico.

Interpretación de características: Los pesos asociados a las características en un perceptrón pueden proporcionar información sobre la importancia relativa de cada característica en la clasificación. Esto puede ayudar a los médicos a comprender qué características son más relevantes para la detección de cáncer de mama.

Resultados del ejercicio
Exactitud del modelo: 0.938
El modelo detectó 7 como benignos y eran malignos esto es particularmente importante ya que 7 personas estan en riesgo de 114 elementos evaluados.


# Conclusiones finales

En conclusión, al analizar los diferentes modelos de clasificación utilizados para la detección de cáncer de mama, podemos destacar lo siguiente:

SVM Lineal: Ofrece una alta eficiencia con datos de alta dimensionalidad y una buena capacidad de generalización. Sin embargo, en este caso, detectó 4 casos benignos como malignos, lo que podría tener implicaciones graves para la salud de los pacientes.

Random Forest Classifier: Destaca por su manejo eficiente de datos complejos y su alta precisión en la clasificación. Aunque identificó 3 casos benignos como malignos, su rendimiento general fue superior, con una exactitud del modelo del 96.49%.

KNN: Aunque es un algoritmo simple y fácil de entender, su rendimiento fue ligeramente inferior al detectar 5 casos benignos como malignos.

XGBoost: Demostró una alta precisión y una capacidad efectiva para manejar conjuntos de datos desequilibrados. Identificó 3 casos benignos como malignos, lo que podría tener implicaciones graves para la salud de los pacientes.

Redes Neuronales Perceptrón: Aunque es un modelo simple y rápido de entrenar, su precisión fue ligeramente inferior a la de otros modelos, identificando 7 casos benignos como malignos.

En general, los modelos de Random Forest Classifier y XGBoost mostraron el mejor rendimiento en términos de precisión y capacidad para manejar conjuntos de datos desequilibrados. Sin embargo, es crucial tener en cuenta los casos de falsos positivos, ya que podrían llevar a tratamientos innecesarios y ansiedad para los pacientes. Por lo tanto, es fundamental realizar una evaluación exhaustiva de cada modelo y considerar cuidadosamente sus implicaciones clínicas antes de implementarlos en entornos médicos reales.
