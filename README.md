# Proyecto_Final: Predicción de COVID-19 en México
## Descripción
Se utiliza el aprendizaje automatizado para predecir la clasificación final de pacientes de COVID-19 en función de ciertos atributos y síntomas.

## Conjunto de datos

El modelo se ha entrenado con información referente a casos COVID-19 en México. Los [datos] epidemiológicos fueron recopilados durante la pandemia y el conjunto contiene información detallada sobre  atributos como edad, género, comorbilidades, síntomas y resultados de pruebas.

[datos]: https://datos.gob.mx/busca/dataset/informacion-referente-a-casos-covid-19-en-mexico 

## Flujo de trabajo
- **Recolección de datos** : Los datos referente a casos COVID-19 en méxico se obtuvieron de [datos] abiertos de la Secretaria de Salud.
- **Exploración de datos** : El conjunto está formado por 1186694 registros pertenecientes a pandemia.
- **Preparación de datos** : Se realizó una limpieza y transformación de los datos para el modelado.
- **Entrenamiento del modelo**: Se seleccionó y entrenó un algoritmo adecuado de de aprendizaje automático con los datos previamente preparados.
- **Evaluación del Modelo**: La precisión se evaluó con metricas de precisión.
- **Implementación del Modelo**
Los elementos de entrada del modelo incluyen información específica sobre los individuos, abarcando aspectos como la edad, el género, así como detalles pertinentes sobre cualquier comorbilidad existente. Además, se incorporan los síntomas presentes, proporcionando una visión completa de la condición de la persona en cuestión. 

La interfaz de predicción presenta los siguientes datos de entrada:

| Dato     | Entrada       | <!-- -->      | <!-- -->      | <!-- -->      | <!-- -->      |
|:-------------:|:---------------:|:-------------:| :-------------:| :-------------:| :-------------:|
| Sexo   | 0 $\rightarrow$ Masculino     | 1 $\rightarrow$ Femenino  |  |  |
| Tipo de paciente   | 0 $\rightarrow$ Ambulatorio     | 1 $\rightarrow$ Hospitalizado  |
| Intubado    | 0 $\rightarrow$ Si     | 1 $\rightarrow$ No  |   97 $\rightarrow$ No aplica |  98 $\rightarrow$ Se ignora | 99 $\rightarrow$ No especificado |
| Neumonía   | 0 $\rightarrow$ Si     | 1 $\rightarrow$ No  |   97 $\rightarrow$ No aplica |  98 $\rightarrow$ Se ignora | 99 $\rightarrow$ No especificado |
| Edad   | Entre 0 y 120 años     | 
| Embarazo  | 1 $\rightarrow$ Si     | 2 $\rightarrow$ No  |   97 $\rightarrow$ No aplica |  98 $\rightarrow$ Se ignora | 99 $\rightarrow$ No especificado |
| Diabetes  | 1 $\rightarrow$ Si     | 2 $\rightarrow$ No  |   98 $\rightarrow$ Se ignora |
| EPOC  | 1 $\rightarrow$ Si     | 2 $\rightarrow$ No  |   98 $\rightarrow$ Se ignora |
| Asma  | 1 $\rightarrow$ Si     | 2 $\rightarrow$ No  |   98 $\rightarrow$ Se ignora |
| Inmunosupresión  | 1 $\rightarrow$ Si     | 2 $\rightarrow$ No  |   98 $\rightarrow$ Se ignora |
| Hipertensión  | 1 $\rightarrow$ Si     | 2 $\rightarrow$ No  |   98 $\rightarrow$ Se ignora |
| Otra Comorbilidad  | 1 $\rightarrow$ Si     | 2 $\rightarrow$ No  |   98 $\rightarrow$ Se ignora |
| Enfermedad cardiovascular  | 1 $\rightarrow$ Si     | 2 $\rightarrow$ No  |   98 $\rightarrow$ Se ignora |
| Obesidad  | 1 $\rightarrow$ Si     | 2 $\rightarrow$ No  |   98 $\rightarrow$ Se ignora |
| Enfermedad Renal Crónica  | 1 $\rightarrow$ Si     | 2 $\rightarrow$ No  |   98 $\rightarrow$ Se ignora |
| Tabaquismo  | 1 $\rightarrow$ Si     | 2 $\rightarrow$ No  |   98 $\rightarrow$ Se ignora |
| Contacto con otro caso  | 1 $\rightarrow$ Si     | 2 $\rightarrow$ No  |  99 $\rightarrow$ No especificado |
| Toma de muestra de laboratorio  | 1 $\rightarrow$ Si     | 2 $\rightarrow$ No  |   98 $\rightarrow$ Se ignora |
| Resultado de laboratorio  | 1 $\rightarrow$ Si     | 2 $\rightarrow$ No  |   97 $\rightarrow$ No aplica |  98 $\rightarrow$ Se ignora | 99 $\rightarrow$ No especificado |
| Toma de muestra de antígeno  | 1 $\rightarrow$ Si     | 2 $\rightarrow$ No  | 98 $\rightarrow$ Se ignora | 
| Resultado de antígeno  | 1 $\rightarrow$ Si     | 2 $\rightarrow$ No  |   97 $\rightarrow$ No aplica |  98 $\rightarrow$ Se ignora | 99 $\rightarrow$ No especificado |
|UCI  | 1 $\rightarrow$ Si     | 2 $\rightarrow$ No  |   97 $\rightarrow$ No aplica |  98 $\rightarrow$ Se ignora | 99 $\rightarrow$ No especificado |
| Días de Hospitalización  |Número de días      | 
| Días con Síntomas   |Número de días   | 

## Resultados

El modelo proporcionará la clasificación final del paciente, la cual podrá categorizarse en una de las siguientes opciones:

:one: **Caso confirmado de COVID-19 por asociación clínica epidemiológica**: Confirmado por asociación aplica cuando el caso informó ser contacto de un positivo a COVID-19 y al caso no se le tomó muestra o la muestra resultó no válida. 

:two: **Caso confirmado de SARS-COV-2** : Se asigna a aquellos pacientes cuya muestra de laboratorio o prueba antigénica resultó positiva a SARS-CoV-2, sin importar si el caso tienen asociación clínica epidemiológica.

:three: **Caso sospechoso**: Se refiere a situaciones en las que no se ha obtenido una muestra adecuada para realizar pruebas de COVID-19 o se le tomó muestra de laboratorio y está pendiente de resultado. El caso no tienen asociación clínico epidemiológica, ni dictaminación a COVID-19.

:four: **Caso negativo**: Esta categoría se asigna en casos donde se le tomó muestra de laboratorio y ésta resultó negativa a SARS-COV-2 o positiva a cualquier otro virus respiratorio (Influenza, VSR, Bocavirus, otros) sin importar que este caso tenga asociación clínico epidemiológica o dictaminación a COVID-19.
