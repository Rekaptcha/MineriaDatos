## DEPURACIÓN DE DATOS ##
Proceso mediante el cual se adecúa el conjunto de datos para la fase de modelización posterior, se ''limpia'' el conjunto de datos original (se quitan observaciones incoherentes, se ajustan las variables a las especificaciones del modelo, etc).  (Fase de DATA PREPARATION de CRISP-DM).  

Principales fases de la depuración de datos:  
**-Comprobación de la correcta tipología y rol de las variables.** Se verifica que la asignación de los distintos tipos y roles que toman las variables es correcta (importante, según la asignación que tengan, se aplicarán unas técnicas estadísticas u otras).  
  
**-Análisis exploratorio de los datos y correción de errores detectados.** En minería de datos se trabaja frecuentemente con datos de mala calidad. Antes de trabajar con los datos se deben intentar corregir los errores que contengan, realizando un análisis exploratorio previo que determine qué errores existen entre los datos.   

**-Detección de datos atípicos.** Los datos numéricamente distantes del resto pueden perturbar los resultados del os modelos, por ello se debe estudair y tratar la presencia de éstos.  

**-Tratamiento de datos faltantes.** Son un problema frecuente en los procesos de minería de datos debido a la falta de supervisión habitual en la recogida de datos. En las fases previas a la depuración se generan además datos ausentes adicionales, deben tratarse los datos faltantes porque reducen la información disponible.  

**-Análisis de las relaciones entre variables.** Una vez estén limpios los datos, es recomendable analizar la relación que existe entre las variables input y la objetivo para determinar la **utilidad predictiva** de las vv. input.  
 
 
Para realizar la primera fase de la depuración de datos se debe tener conocimiento suficiente del significado de las variables y el objetivo final qeu se persigue. Al establecer los tipos de variables (tras importar los datos) hay que saber que la mayoría de software (también R) consideran numérica cualquier variable codificada únicamente con números (cuidado con las variables cualitativas, binarias..).   

## APUNTES DE R ##  
Las variables cualitativas se denominan **factores**, las cuantitativas: **numéricas**.
Comprobar la tipologáia de las variables: **str(dataFrame)**   Indica el tipo de cada variable del conjunto de datos  

Cambiar el tipo de una variable cosniderada de forma incorrecta: **as.factor(variable)** o bien **as.numeric(variable)**  
 
**Si el nº de valores distintos que toman las variables cuantitativas es pequeño (<10) es preferible considerarlas como cualitativas, al no existir muchos valores distintos, los modelos posteriores pueden no funcionar bien**. Para verificar el nº de valores distintos que puede tomar una variable:   
  **sapply(Filter(is.numeric, dataFrame), function(x) length(unique(x)))**  

Si tiene pocos valores diferentes, es mejor transformarla a factor **as.factor(variable)**

## ANÁLISIS EXPLORATORIO DE LOS DATOS Y CORRECCIÓN DE ERRORES DETECTADOS (FASE 2 DEPURACIÓN DE DATOS) ##
Para poder detectar los problemas presentes en los datos, es necesario realizar un análisis exploratorio de ellos, a través de gráficos y tablas. Para ello, es útil:  
**summary(dataFrame)** ofrece un resumen de todas las variables presentes en el conjunto de datos. Variables numéricas: informa del valor mínimo, máximo, media, mediana, 1º y 3º cuartil. Variables de tipo factor: muestra los 6 niveles mayoritarios junto con sus frecuencias. En ambos casos se muestra el nº de datos ausentes.  

**psych:describe(Filter(is.numeric, dataFrame))** ofrece + medidas de las variables numéricas (desviación estándar e índice de simetría).  

**questionr::freq(varCuali)** muestra la tabla de frecuencias de la variable cualitativa  

**hist(varCuant)** muestra histograma de la variable cuantitativa  

**barplot(table(varCuali)) muestra el diagrama de barras de la variable cualitativa  

Con estas funciones es posible hacerse una idea muy clara de cómo son las variables del conjunto y sus problemas. ¿En qué nos tenemos que fijar? Importante:  

**-Límites de las variables cuantitativas.** Verificar que toman valores lógicos (máximo y mínimo se encuentran dentro del os límites marcados por la variable (por ejemplo, porcentaje esté entre 0 y 100, medidas antopométricas sólo tomen valores positivios..)).  

**-Niveles de las variables cualitativas.** Verificar que los niveles tienen sentido, teniendo en cuenta el significado de las variables.  

**-Número de datos faltantes.** Si una variable tiene más de la mitad de los datos faltantes, se recomienda rechazarla al inicio del proceso (carece de suficiente información). 

**-Datos faltantes codificados.** A veces, en lugar de ''dejar huecos'' para representar datos faltantes, se usa algún tipo de codificación (ejemplo: variables cualitativas: ?, NSNC / variables cuantitativas: -1, 999). Importante detectarlo para analizar correctamente la presencia de ausentes del punto anterior.  

**-Frecuencia de las categorías de las variables cualitativas.** Los modelos predictivos se basan en detectar patrones en las variables input que permitan aproximar el valor de la vv. objetivo, imprecindible que todos los niveles de las variables cualitativas estén **bien representados** (si no, se podrían detectar patrones NO extraplorables al estar basados en muy pocas observaciones). **Hay que verificar qeu la frecuencia de todas las vv. cualitativas sea superior al 2-5% (el % exacto depende del nº de observaciones)**  

Una vez detectados los errores, hay que solucionarlos. Según el contexto de aplicación y el conjunto de datos, pueden existir otros aspectos a analizar.  

## SOLUCIÓN DE LOS PROBLEMAS ENCONTRAODS EN R ##  
**-Límites de las variables cuantitativas & Niveles de las variables cualitativas** -> sustituir los valores problemáticos por valores ausentes. Es igual de informativa la falta de respuesta que un valor erróneo, y existen técnicas específicas para tratar la presencia de datos faltantes, es práctico convertir errores a datos ausentes y después tratarlos.   
Valores de varaibles cuantitativas fuera de rango: **varCuant<-replace(varCuant, which((varCuant < limInf)|
                                                                      (varCuant>limSup)), NA)  
 Categorías de variables cualitativas erróneas:  
**varCuali<-recode.na(varCuali, "valorErroneo")   

**-Nº de datos faltantes.** Si existe alguna variable con demasiados datos ausentes, debemos rechazarla.  
variable<-NULL  

**-Datos faltantes codificados.** Para datos faltantes codificados (-1, 999, NCNS...) la mejor solución es declararlos como tales:   
Variables cuantitativas: **varCuant<-replace(varCuant, which(varCuant==valorCodificado), NA)  
Variables cualitativas: **varCuali<-recode.na(varCuali, "valorCodificado")**  

**-Frecuencia de las categorías de las variables cualitativas.** Si existen categorías infrarrepresentadas de vv.cualitativas, la solución es unir las categorías con poca representatividad entre ellas o con otras, hasta asegurar que todos los niveles tienen una frecuencia suficiente. Es recomendable realizarlo teniendo en cuenta el **parecido semántico** del los niveles.  
**varCual-car::recode(varCual, "'oldValue1'='NewValue1';
                               'oldValue2'='NewValue2'")  
                               
##DETECCIÓN DE DATOS ATÍPICOS##  
**Dato atípico**: observación numéricamente distante del resto de datos. No confundir con un dato grande, que toma un valoralto pero en línea con el resto de valores, ni con un dato erróneo, que toma un valor imposible. Para ser considerado como tal, debe representar una proporción pequeña del conjunto de datos (siempre <2-5%).
Problema datos atípicos: tienen una gran influencia en los modelos de predicción si no son robustos (un modelo es robusto cuando se ve poco afectado por la presencia de datos atípicos). Los modelos robustos son menos frecuentes por lo que es habitual necesitar tratar los datos atípicos. Ejemplo: los modelos predictivos persiguen estimar el valor que toma una observación en la variable objetivo, si no se cuenta con info de las variables input, una opción es usar la media. Dos conjuntos de datos: (1, 2, 3, 4 y 5) y (1, 2, 3, 4 y 50). En el primero la media es 2,5, en el segundo, 12. Se comete un error de predicción muy grande para todas las observaciones debido a la presencia del dato atípico 50.  
Una solución para el ejemplo sería usar una alternativa a la media, por ejemplo, la mediana, que se trata de una medida robusta. En ambos casos tomaría el valor 3. 

Aunque los datos erróneos y atípicos no sean lo mismo, la forma de tratarlos sí es la misma, consiste en ponerlos ocomo datos ausentes.  

Método más habitual para detectar los outliers (datos atípicos) es usar la info representada en los **diagramas de caja**. Se consideran **atípicas** aquellas **observaciones que se alejan más de 3 veces el rango intercuartílico entre el 1º y el 3º cuartil. Otras opciones: desviación estándar o desviación absoluta mediana, pero este método tiene la ventaja que su aplicaicón **no depende de la simetría de las variables ni del valor que toman otros estadísticos**. Para determinar conseguridad que un dato es atípico se debe verificar que cumple la condición <2-5% del total.  

**Tratamiento de datos atípicos en R**: utilizamos **outliers()**, determina la proporción de observaciones de datos atípicos, muestra info adicional y permite decidir si mantener dichas observaciones o convertir los valores a ausentes.


##TRATAMIENTO DE DATOS FALTANTES##
###TRATAMIENTO DE DATOS FALTANTES:  1.ELIMINACIÓN###
###TRATAMIENTO DE DATOS FALTANTES:  2.IMPUTACIÓN###
###TRATAMIENTO DE DATOS FALTANTES:  3.RECATEGORIZACIÓN###

##ANÁLISIS DE LAS RELACIONES ENTRE VARIABLES##  
Claves para crear un buen modelo predictivo: calidad de los datos (mejorados con lo hecho hasta ahora) y las variables input usadas para predecir. En minería de datos se trabaja con un gran nº de varaibles. Por eso a veces hace falta realizar una **preselección** de las que serán útiles en la fase de modelización (y evitar trabajar con demasiadas vv. en esa fase).   

¿Cómo saber qué variables serán útiles en la predicción? Hay que estudiar si las variables input contienen info sobre la varaible objetivo (esto es, si están relacionadas). Se recomienda realizar un **análisis gráfico bivariable** que permita detectar dichas relaciones.  

**Relación entre variables**: dos variables están relacionadas si al conocer el valor de una de ellas para cierta observación se pueden sacar conclusiones sobre el valor de la otra en dicha observación.  

Ejemplos de variables habitualmente relacionadas: altura y peso.  

Una primera aproximación a la evaluación de las relaciones consiste en realizar una exploración gráfica bivariante  de los datos. Algunos gráficos útiles para determinar visualmente la presencia de relación entre variables (dependen de la librería **ggplot2**):  

