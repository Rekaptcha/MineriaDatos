## MINERÍA DE DATOS ##  
Área de conocimiento ubicada entre la estadística "clásica" y la informática.   

Distintas definiciones:  
- Una forma nueva de obtener información comercial valiosa a través del análisis de los datos almacenados en la BBDD de la empresa. Descubre información comercial usando técnicas de análisis y creación de modelos.  
- Proceso de detectar información de grandes conjuntos de datos para deducir patrones y tendencias existentes en los mismos, que no se pueden detectar con las técnicas tradicionales porque las relaciones que mantienen son muy complejas o hay demasiados datos.  

En resumen, permite descubrir patrones o tendencias en un conjunto de datos muy grande, con el objetivo de utilizarlos para distintos propósitos (por ejemplo, patrones de venta, para saber cuándo es mejor tener las tiendas abiertas). El objetivo al final es generar conocimiento que se pueda aplicar a otros individuos, circunstancias o en unfuturo, por lo que es fundamental asegurarse de que las conclusiones que se extraigan a partir de los datos no se restrinjan únicamente al conjunto de datos disponibles (esto es, que sean generalizables).

## DIFERENCIAS ENTRE MINERÍA DE DATOS Y ESTADÍSTICA ##

**Minería de datos:**
- La minería de datos trabaja con datos heterogéneos y abundantes (muchas observaciones y/o varibles) así como muchas veces, trabaja con datos de mala calidad (decimos que un conjunto de datos es de mala calidad cuando presenta muchos datos atípicos y/o faltantes), mientras que la estadística trabaja con datos de cierta calidad.

- Pone más énfasis en la predicción que en la explicación. Interesa más predecir qué pasará a partir de los datos analizados que explicar por qué se producen esos resultados. Eso permite aplicar modelos más complejos y obtener resultados más precisos, perdiendo capacidad para explicar los resultados.  

- Se trabaja con muchos datos, y el grna tamaño de la muestra precisamente suele hacer imposible la aplicación de inferencia en la predicción por la potencia de los contrastes (si la potencia de un contraste de hipótesis es demasiado alta, como así ocurre con conjuntos de datos muy grandes), siempre se rechazarán las hipótesis nulas, lo que inutiliza este tipo de técnica.  

- Habitual realizar una **partición aleatoria** de los datos en dos muestras (**entrenamiento y prueba**), de tal forma que la **muestra de entrenamiento** permita sacar conclusiones sobre la estructura/naturaleza de los datos y la **muestra de prueba** permitea confirmar las conclusiones obtenidas. Porcentaje habitual de partición: 70-80% y 30-20%.  La partición de prueba permite generalizar los resultados: la info de esta submuestra NO se usa en la fase de generación de conocimiento, sino que se comprueba si las conclusiones que se han extraído a partir de la otra submuestra (la de entrenamiento) son aplicables a los datos de prueba, permitiendo así afirmar con cierta confianza que dichas conclusiones se pueden genrealizar (siempre que el conjunto de datos del que disponemos sea **representativo de la población** a la que se quieren extrapolar).    
  
  
## METODOLOGÍA FUNDAMENTAL para DM ##
  
 Existen dos estrategias diferentes que guían los procesos y actividades de la minería de datos:  
  - SEMMA (Sample-Explore-Modify-Model-Assess)  
  - CRISP-DM (Cross Industry Standard Process for Data Mining). Más compleja que la anterior porque tiene en cuenta la aplicación de los resultados al **entorno de negocio**. Es la metodología más usada, es la que utilizaremos.  
    
## METODOLOGÍA CRISP-DM ##  
    
Conformada por 6 fases:  
   1. **BUSINESS UNDERSTANDING** (comprensión del negocio). Fase inicial. Enfocada en comprender los objetivos de proyecto. Se plantean los problemas de negocio que se pretenden solucionar aplicando técnicas minería de datos.  
   
   2. **DATA UNDERSTANDING** (estudio y comprensión de los datos). Esta fase comienza con la colección de datos inicial y durante ella se realizan una serie de actividades que permiten familiarizarse con dichos datos, detectando relaciones, anomalías y tendencias.  
   
   3. **DATA PREPARATION** (análisis de los datos y selección de características). Se preparan los datos, se realizan todas las actividades que hacen falta para construir el conjunto final de datos, osea, se transforman los datos brutos iniciales en el conjunto de datos final que se utilizarán. Tareas que abarca: selección de registros y atributos, transformación y limpieza de datos. Facilita la modelización.
   
   4. **MODELING** (modelado). Se seleccionan y aplican la stécnicas de modelado pertinentes (cuantas más mejor) y se calibran sus parámetros.
   
   5. **EVALUATION** (evaluación). Se evalúan los modelos construidos y se revisan los pasos ejecutados, evaluando si se han cumplido los objetivos de negocio. Se determina si la calidad de los resultados es suficiente para pasar al último paso o se debe volver a realizar algún paso anterior.
   
   6. **DEPLOYMENT** (despliegue). En función de lo que sea necesario, esta fase puede consistir en generar un informe o realizar de forma periódica un proceso de análisis de datos de la organización.  
   
   Muchas de estas fases están interconectadas y en algunas ocasiones en una fase se detecta alguna carencia/error subsanable en una fase previa resultando necesario repetir la fase anterior. También se puede alterar el orden o no realizar alguna de ella.  
     
     
 ## CLASIFICACIÓN DE LAS TÉCNICAS DE MINERÍA DE DATOS ##  
 
Podemos clasificar las técnicas de minería de datos en:  
- **Técnicas supervisadas**. Existe una variable, llamada **variable objetivo o respuesta** que se desea predecir de forma precisa a partir de la información que proporcionan el resto de variables. A veces se llaman **técnicas predictivas**. <<< Este módulo
  *ejemplos*: regresión lineal y logística, KNN, árboles de clasificación y regresión, random forest, gradient boosting...
- **Técnicas No supervisadas**. No existe ninguna variable respuesta, el objetivo es estudiar las relaciones existentes entre las variables y las observaciones del conjunto de datos.  
  *ejemplos*: análisis de componentes principales, escalamiento multidimensional, análisis de clúster.
  
## CLASIFICACIÓN DE LAS TÉCNICAS SUPERVISADAS ##  
Las técnicas supervisadas se clasifican en función de la tipología de la variable que se desea predecir, distinguiendo entre tipos de variables:    

- **Cuantitativas**. Variables asociadas a cantidades numéricas (salario, altura..). Tanto si toman sólo valores enteros como si abarcan todos los valores reales.  

- **Cualitativas, nominales o categóricas**. Variables que toman un número finito de valores (género, signo del zodíaco, país). A veces se codifican con números (1 hombres y 2 mujeres), no implicaque se deban tratar como variables cuantitativas (cuidado porque algunos software lo hacen así).  

- **Dicotómicas o binarias**. Variables cualitativas que toman sólo dos valores.

- **Fecha/Hora**. Variables que representan una fecha y/o hora. El formato es una secuencia alfanumérica, para poder aprovehcar su potencial en la fase de modelización, hay que obtener otras variables de ellas (ejemplos de variables que se pueden extraer de una fecha/hora: edad a partir de la fecha de nacimiento, día de semana a partir de fecha de compra, franja del día..).  
  
  Existen otros tipos de variables con los que trabajar en el contexto de MD: vídeos, imágenes, textos completos..  
  
  Las variables también se pueden clasificar según el rol que van a desempeñar:  
  - **Identificativas**.  Sirven para identificar observaciones (poco o nada útiles desde el punto de vista analítico), debe tomar un valor diferente para cada una de las observaciones del conjunto de datos. Ejemplo: nombre, DNI, código cliente.
  - **Objetivo**.  Variable que se pretende predecir (sólo aplicable a técnicas supervisadas). Cuando la variable objetivo es cuantitativa, se suele hablar de técnicas de regresión, si es cualitativa, de técnicas de clasificación.
  - **Input o de entrada**.  Variables básicas que se usan para generar conocimiento.
  - **Rechazadas**. Variables eliminadas antes de la fase de modelización. Se suele explotar todo el potencial de las variables pero algunas no se pueden usar y se deben rechazar (ejemplo, variable a la que le faltan más de la mitad de ls datos, no es recomendable tratarla). Al trabajar con **técnicas supervisadas** es importante asegurarse de que no se considera como input ninguna variable que se derive de la objetivo ni ninguna de las que no se vaya a disponer cuando se alcance la fase de implementación.  
  
 ## EVALUACIÓN DE LOS MODELOS DE PREDICCIÓN ##  
 La evaluación de los modelos es una fase imprescindible. Definimos como **error de predicción** la diferencia entre el valor real que toma la variable objetivo y el valor predicho por el modelo. Un modelo esperfecto cuando asigna un valor de predicción = valor real, lo que da lugar a error 0.  
 
Los modelos supervisados (de predicción) tienen como objetivo predecir una variable, costosa o imposible de obtener, llamada input. Al final el objetivo es predecir los valores de la variable objetivo en aquellas observaciones en las que desconocemos su valor. En la fase de evaluación se debe analizar lo similares que son las predicciones a los valores reales.  
Cuatro posibles combinaciones entre sesgo y varianza:  
- **Bajo sesgo y baja varianza**. Situación ideal, muy poco error y el error no varía de forma significativa.
- **Bajo sesgo y alta varianza**. En media el modelo funciona bien, pero hay observaciones para las que el error de predicción es muy bajo y otras en las que es alto. Genera incertidumbre al aplicarse porque no se puede saber si la observacióna predecir será de las que se predice con poco error o las que el error no predice correctamente.  
- **Alto sesgo y baja varianza**. Si el sesgo no es demasiado alto, se suele preferir al caso anterior, el error es más grande en media pero cosntante para todas las observaciones.
- **Alto sesgo y alta varianza**. Peor escenario, modelo no es capaz de predecir bien ninguna observación.  

Es importante cuantificar tanto el sesgo como la varianza de los modelos en la fase de evaluación. ¿Cómo realizamos esta cuantificación si sólo contamos con un conjunto de datos? Gracias a los **métodos de remuestreo** (entre los que está la partición entrenamiento-prueba).   

Ejemplo: tenemos un conjunto de obseraciones para las que se conoce el valor de las variables X e Y.
