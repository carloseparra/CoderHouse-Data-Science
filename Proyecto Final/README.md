![Portada](./media/header.png)
# Proyecto Final de Data Science
## "Entrenamiento y optimización de modelos de machine learning para la predicción del abandono de clientes en una empresa de telecomunicaciones"<br><br> 

# Introducción 
El proyecto que aquí desarrollamos tiene como finalidad el entrenamiento y optimización de modelos de Machine Learning para la predicción del abandono de clientes en una empresa de telecomunicaciones, este análisis se centra en el comportamiento de los clientes de telecomunicaciones que tienen más probabilidades de abandonar la plataforma. La idea es descubrir el comportamiento de los clientes a través del análisis exploratorio de datos (EDA) y luego utilizar algunas de las técnicas de análisis predictivo para determinar los clientes que tienen más o menos probabilidades de abandonar.
<br><br>

# Índice
* Contexto y Audiencia
* Hipótesis/ Preguntas de Interés
* Análisis Exploratorio de datos
* Algoritmos de clasificación
* Ingeniería de atributos
* Entrenamiento y Testeo
* Optimización
* Insights
* Conclusiones
<br><br>
# Contexto y Audiencia

Contexto
Este análisis se centra en el comportamiento de los clientes de una empresa de telecomunicaciones para determinar que suscriptores tienen más probabilidades de abandonar la plataforma. 
La idea es descubrir el comportamiento de los clientes a través del análisis exploratorio de datos (EDA) y luego utilizar algunas de las técnicas de análisis predictivo para determinar los clientes que tienen más probabilidades de abandonar.
Audiencia
Esta investigación estadirigida a los responsables de la toma de decisiones del área comercial de la empresa de Telecomunicaciones, en virtud de la perdida de suscriptores activos en los últimos meses.
<br><br>
# Preguntas de Interés
Determinar si la cantidad y el tipo de servicios contratados influye en la retención del cliente.
Determinar cómo se correlacionan las distintas variables del estudio con la duración de los contratos y la retención.
Determinar si el aumento en los cargos incide en la tasa de abandono
Predecir a través de un modelo si el cliente va a abandonar el servicio o no y cuáles son las variables que más influyen en la predicción.
¿Cuáles son los indicadores clave de la rotación de clientes?
Demostrar que el aumento de los servicios contratados incide en la permanencia de los clientes
¿Qué estrategias de retención se pueden implementar en función de los resultados para disminuir la pérdida de clientes potenciales?
<br><br>
# Análisis Exploratorio de datos
Nombre del dataset: "Dataset-Telco-Customer-Churn.csv
Este dataset incluye un total de 7,043 registros y 21 columnas

> Las columnas contenidas son las siguientes:
*	customerID : >  ID del cliente
*	gender : si el cliente es hombre o mujer.
*	SeniorCitizen : si el cliente es una persona mayor o no (1, 0)
*	Partner : Si el cliente tiene socio o no (Sí, No)
*	Dependents : si el cliente tiene dependientes o no (Sí, No)
*	tenure : permanencia: Número de meses que el cliente ha permanecido en la empresa
*	PhoneService : si el cliente tiene un servicio telefónico o no (Sí, No)
*	MultipleLines : si el cliente tiene múltiples líneas o no (Sí, No, Sin servicio telefónico)
*	InternetService : proveedor de servicios de Internet del cliente (DSL, fibra óptica, No)
*	OnlineSecurity : si el cliente tiene seguridad en línea o no (Sí, No, Sin servicio de Internet)
*	OnlineBackup : si el cliente tiene copia de seguridad en línea o no (Sí, No, Sin servicio de Internet)
*	DeviceProtection : Si el cliente tiene protección de dispositivo o no (Sí, No, Sin servicio de Internet)
*	TechSupport : si el cliente tiene soporte técnico o no (Sí, No, Sin servicio de Internet)
*	StreamingTV : si el cliente tiene transmisión de TV o no (Sí, No, Sin servicio de Internet)
*	StreamingMovies : si el cliente tiene películas en streaming o no (Sí, No, Sin servicio de Internet)
*	Contract : el plazo del contrato del cliente (mes a mes, un año, dos años)
*	PaperlessBilling : si el cliente tiene o no facturación electrónica (Sí, No)
*	PaymentMethod : el método de pago del cliente (cheque electrónico, cheque enviado por correo, transferencia bancaria (automática), tarjeta de crédito (automática))
*	MonthlyCharges : la cantidad cargada al cliente mensualmente
*	TotalCharges : El monto total cobrado al cliente
*	Churn : si el cliente abandonó o no (Sí o No)


A través de un gráfico de tarta, de represento la tasa de abandono, ya que solo hay 2 clases y se representa más claramente la magnitud de cada uno, evidenciando que casi 1/4 de los clientes ha abandonado de contrato en el periodo.
De verificó que el dataset esta desbalanceado
EL género (que en su mayoría son mujeres) no influye en la tasa de abandono
Se represento la permanencia a través de un KDE Plot y pudimos observar que la mayoría de los clientes que abandonaron estuvieron en la empresa menos de 20 meses y que a medida que aumenta la permanencia la probabilidad de abandonar disminuye.

Se puede destacar que a medida que la factura es mayor existes menos suscriptores
No existe una variación significativa del comportamiento de pagos de acuerdo con el género, solo que los pagos automáticos son mayores a los que no son automáticos y el menos utilizado es el cheque.
<br><br>
# Algoritmos de clasificación
Por las características del dataset se debería adaptar más un modelo clasificación más que uno de regresión, pero observando los valores de accuracy en el de regresión lineal es mayor llegando a 90%, y en los de clasificación máximo a un 80%.
Durante la fase inicial se utilizaron algoritmos de clasificación como Regresión Logística, KNeighbors,  al dataset original obteniendo métricas que no son las esperadas en un modelo eficiente, por ello se procede a aplicar otras técnicas, ya que se obtuvieron las siguientes conclusiones

* Tamaño del conjunto de Entrenamiento: **5634**
* Tamaño del conjunto de Prueba: **1409**
* Con el Algoritmo KNeighbors es mayor el accuracy, el recall y el f1-score.
* Con el Algoritmo KNeighbors se obtiene una precision de 0.93.
* EL KNeighbors da la puntuación F1 más alta, por lo que es el mejor modelo.
* El sexo no tiene impacto en la rotación.
* Las personas que tienen un contrato de mes a mes tienden a abandonar más que las personas que tienen contratos a largo plazo.
* A medida que aumenta la permanencia, la probabilidad de abandono disminuye.
* A medida que aumentan los cargos mensuales, aumenta la probabilidad de abandono.

Hasta el momento, la mejor métrica de Accuracy se obtuvo con un ajuste manual en el arbol de decisión a max_depth=2, pasando de un accuracy para árbol de decisión original sin ningún ajuste de: 0.7341862117981521 y luego de los ajustes manuales llegando con el Cross-Validation a: 0.7894222222222222.
<br><br>
# Ingeniería de atributos
Luego de todos los algoritmos y técnicas aplicadas encontramos que los resultados obtenidos en función al accuracy no son aceptables, procederemos a cambiar el enfoque y centrarnos específicamente en mejorar las métricas en función del resultado deseado que es predecir más eficientemente la tasa de abandono, que basado en los datos seria predecir la variable Churn con resultado = 1, mejorando el recall, para ello haremos uso de otros algoritmos más ajustados en función de los hiperparametros y aplicando oversampling entre otras cosas.
Para esto se tuvo que hacer un nuevo preprocesamiento aplicando get dummies para crear variales adicionales y estudiarlas mas fácilmente, se comprobaron outliers nuevamente y se reentrenaron de nuevo los modelos, obteniendo nuevamente resultados no concluyentes.
<br><br>

# Entrenamiento y Testeo
Como las métricas obtenidas hasta ahora no responden a nuestro problemas se decide entrenar los algoritmos aplicando  adicionalmente validación cruzada, grid search y un método árboles adicionales (sklearn.ensemble.ExtraTreesClassifier) para mejorar los resultados, resaltar los features más importantes para enfocarnos ahora es subir el recall, lo que permitió tener valores aceptables.
<br><br>

# Insights
El dataset contiene información sobre 7,043 clientes de una compañía de telecomunicaciones, con 21 variables diferentes.
La tasa de abandono de clientes (churn_rate) en el dataset es del 26.5%, lo que sugiere que la compañía de telecomunicaciones puede estar teniendo problemas para retener a sus clientes.
La mayoría de los clientes (68.5%) son usuarios de servicios de telefonía, mientras que el resto son usuarios de servicios de Internet y servicios de televisión.
Los clientes que tienen servicios de Internet de alta velocidad son más propensos a abandonar la compañía que los clientes que tienen servicios de Internet de baja velocidad.
Los clientes que tienen contratos mensuales son mucho más propensos a abandonar la compañía que los clientes que tienen contratos a largo plazo.
Los clientes que tienen cargos mensuales más altos y que han estado en la compañía por más tiempo tienden a tener cargos totales más altos.
Las variables MonthlyCharges y TotalChargesestán altamente correlacionadas, lo que sugiere que la compañía podría estar cobrando precios más altos a los clientes que han estado en la compañía por más tiempo.
La mayoría de los clientes que abandonaron la compañía lo hicieron durante los primeros dos años, lo que sugiere que la compañía podría beneficiarse al retener a los clientes por más tiempo y mejorar la experiencia del cliente durante los primeros años de su contrato
Se sugiere para mejorar la retención de sus clientes ofrecer contratos a largo plazo y mejorando la experiencia del cliente en los primeros años de su contrato. 
También podrían considerar la posibilidad de ajustar sus precios para retener a los clientes de mayor valor
<br><br>

# Conclusiones
Luego de todos los algoritmos y técnicas aplicadas encontramos que los resultados obtenidos en función al accuracy no son aceptables, procederemos a cambiar el enfoque y centrarnos específicamente en mejorar las métricas en función del resultado deseado que es predecir mas eficientemente la tasa de abandono, que basado en los datos seria predecir la variable Churn con resultado = 1, mejorando el recall, para ello haremos uso de otros algoritmos más ajustados en función de los hiperparametros.
Al observar que los datos están desabalanceados se aplica oversampling para corregir esto y establecer las variables más importantes, para a partir de allí, reentrenar los modelos y elegir el mejor predictor.
Luego de este enfoque (Mejorar el Recall), podemos determinar que el mejor modelo es el RandomForest Classifier, con un Recallde 95% para la predicción acertada de los pueden abandonar y un resultado de 84% para los que no.

<br><br>
<br><br>

## Realizado por:<br>Carlos Enrique Parra Vílchez<br>
<div style="text-align: right"> Santiago, Chile - Agosto de 2023</div>




