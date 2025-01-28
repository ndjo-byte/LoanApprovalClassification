# De Soñar con Bicicletas a Construir un Modelo de Machine Learning + Fintech 🚴‍♂️🤖

Hace poco estuve curioseando sobre futuras bicicletas. Me fijé en lo que cada vez se ve más en productos así: opciones de financiación 💸, las cuales me parecían muy tentadoras. Aunque por ahora he resistido la tentación, me picó la curiosidad: cuando pinchas la opción de financiación y te evalúan para decidir si darte el préstamo o no, ¿qué estará pasando por detrás? 🤔 Seguro que es un modelo de aprendizaje automático.

Para investigar, pensé que sería interesante crear mi propio modelo. Encontré un dataset con información detallada sobre solicitudes de préstamo (disponible en mi GitHub).

## Análisis Exploratorio 🔍
Lo primero fue realizar un análisis exploratorio para entender los datos y asegurarme de que estaban limpios. Observé las distribuciones de cada variable y noté que la variable objetivo (loan_status) estaba desequilibrada, con un 85% de las instancias como rechazos ❌. Esto hacía necesario estratificar los datos al dividirlos en entrenamiento y prueba.
Durante este análisis univariante, también noté que las variables numéricas tenían escalas muy diferentes 📏, algo que requeriría estandarización para modelos lineales. Exploré las variables categóricas con pandas.value_counts() para comprender mejor sus distribuciones y preparar su codificación posterior.

En el análisis bivariante, evalué relaciones entre las variables predictoras y el objetivo. Descubrí que dos variables numéricas mostraban una relación más clara con el objetivo cuando se combinaban. Esto me llevó a crear una nueva variable: loan_amnt_times_percent_income, que resultó ser muy predictiva.
También analicé las variables categóricas con gráficos de barras 📊 y descubrí patrones interesantes, como la fuerte relación entre loan_grade y los resultados de los préstamos.

## Preparación de Datos 🛠️
Estandaricé las variables numéricas con un StandardScaler para garantizar que todas tuvieran la misma escala, algo crucial para modelos lineales. Después, separé los datos en conjuntos de entrenamiento y prueba, cuidando de evitar data leakage y de mantener la proporción del objetivo mediante estratificación.

## Modelos y Resultados 🤖
Comencé con un modelo de Logistic Regression utilizando solo tres variables:

loan_int_rate
loan_percent_income
loan_amnt_times_percent_income

### Este modelo logró un ROC AUC de 86%.
¿Qué es ROC AUC? Representa el área bajo la curva que relaciona la tasa de verdaderos positivos (recall) y la tasa de falsos positivos a diferentes umbrales de clasificación. Un 100% indica un modelo que siempre clasifica bien, mientras que un 50% sería como adivinar al azar 🎯. Es un indicador especialmente útil en problemas con clases desbalanceadas, como este caso.

Entusiasmado por los resultados, probé un modelo más avanzado basado en Gradient Boosting (XGBoost). Usando validación cruzada estratificada con 10 divisiones, logré un ROC AUC promedio de 89%. Finalmente, optimicé el modelo con una búsqueda aleatoria de hiperparámetros (RandomizedSearchCV) y conseguí un 90% ROC AUC, lo que considero excepcional con solo tres variables.

## Lecciones y Próximos Pasos 🚀
Una gran ventaja de estos modelos es su interpretabilidad. Esto es valioso para empresas fintech 🏦, ya que permite explicar a los clientes por qué su solicitud fue rechazada. Además, al requerir solo tres variables, este modelo simplifica enormemente el proceso de decisión.

En cuanto a próximos pasos, planeo incorporar más variables categóricas, lo que probablemente mejorará el rendimiento del modelo. Usaré técnicas como OneHotEncoding para representarlas de forma adecuada.

Por ahora, estoy muy satisfecho con los resultados obtenidos. ¡Espero que te haya resultado interesante este pequeño viaje de curiosidad y aprendizaje! 🌟


