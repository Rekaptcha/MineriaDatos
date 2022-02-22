###MODELO REGRESIÓN LINEAL##
Objetivo del del modelo de regresión: predecir una variable y (vv. dependiente u objetivo) a partir de un conjunto m de varaibles xi (vv. independientes o input) a través de la ecuación: **y = f(x1, x2, ... xm) + €**
Siendo € el **error cometido** o **parte de la varaible dependiente NO explicada a partir de las variables independientes**  

En **regresión lineal** la ecuación se reduce a: **y = B0 + B1X1 + B2X2 + ... BmXm + €**  
donde f() es cualquier función matemática, y es una variable cuantitativa, B0 representa el valor que toma la VD cuando todas las VI toman el valor 0 y los parámetros restantes repreesntan cuánto aumenta o disminuye la VD por cada incremento unitario de las VI correspondientes.  

Se puede por tanto predecir el valor de y para un determinado elemento conocidos los valores que toman las variables input o VI: ^y = B0 + B1x1 + B2x2 + ... + BmXm 

Pero para poder llevar a cabo la predicción es necesario conocer el valor de los parámetros, por lo que deben ser estimados a partir de los datos disponibles. Buscaremos para qué valor de los parámetros se minimiza el **error cuadrático** cometido por el modelo, que viene dado por: SSE = Sumatorio (yi - ^yi)2    
//Calculamos el error al cuadrado en lugar del error simple para que el error sea positivo. Así sabemos que el error perfecto es 0, y cuanto más se aleja de 0, peor, si no lo elevásemos al cuadrado, unas veces el error sería positivo y otras negativo. Otra opción es usar el valor absoluto en lugar de elevarlo al cuadrado, pero si usamos el valor absoluto obtendremos una función no derivable.   
El **estimador de mínimos cuadrados** aquel que minimiza la suma de cuadrados de los errores viene dado por... ver función en apuntes.  

El modelo de regresión lineal clásico se sustenta en una serie de **hipótesis** necesarias para la aplicación de contrsates de hipótesis. Hasta ahora no se ha impuesto ninguna porque los estimadores anteriores, mínimos cuadráticos, son **siempre válidos**. Aunque no se le imponga ninguna hipótesis, es importante destacar **aspectos prácticos** que influyen en la creación de ests modelos:  
- Por la forma en que se obitenen los estimadores de los parámetros, ni la VD ni las VI pueden contener **datos ausentes**, o no será posible realizar las pertinentes operaciones aritméticas.  
- Tampoco deben existir **datos atípicos** en las VI, pueden desvirtuar los resultados. Un sólo dato atípico puede modificar la recta de regresión los uficiente como para producir un incremento importante en el tamaño de los errores de predicción en las observaciones no atípicas.  
- No se pueden incluir en el modelo dos VI muy correlacionadas, no es posible invertir la matriz X'X  
- El nº de parámetros incluidos en el modelo debe ser **muy inferior** al nº de observaciones para evitar problemas en la estimación y de sobreajuste. Para obtener modelos confiables, las conclusiones que se extraigan del conjunto de datos se deben basar en info de un nº suficiente de categorías, de ahí que sea recomendable que el rato nº de observaciones por parámetro sea elevado.  
- Las VI categóricas no se pueden incluir en el modelo directamente ya que no contienen info numérica y no permiten obtener estimaciones. Tienen un tratamiento especial para incluirse en el modelo.  

## INCLUSIÓN DE VV CATEGÓRICAS E IMPLICACIONES SOBRE LA INTERPRETACIÓN DE LOS PARÁMETROS DEL MODELO ## 
La inclusión de vv categóricas en el modelo NO es tan directa como la de varaibles de intervalo (para estas es suficiente con añadr una columna en la matriz X que contenga los valores numéricos que toman las observaciones).   
Las categorías suelen venir dadas por valores alfanuméricos, no se puede incluir dicha info en la matriz X. Se deben construir tantas **variables auxiliares binarias** (dummy) como categorías tenga la VI categórica que toma el valor 1 (si la observación correspondiente toma ese valor) y 0 en otro caso. Estas vv al ser numéricas pueden incluirse como columnas en la matriz X.  

Dadas todas las variables dummys menos una, es posible conocer la restante (las variables dummys son linealmente dependientes), así, no se puede invertir la matriz X'X y por tanto, no se pueden estimar los parámetros. EN este caso se fija el parámetro en una de las categorías como ' y se elimina de la matriz X la columna correspondiente, de tal forma que, al incluir una vv input categórica, se incluyen en el modelo **tantos parámetros como niveles menos 1 tenga dicha vv**.  
Así, el parámetro constante B0 se corresponde con el valor de la VD que toma una observación de dicha categoría pero que toma el valor 0 para las demás VI continuas. Los parámetros restantes asociados a dicha vv miden el **aumento/disminución** de la VD entre los individuos de la categoría en cuestión y la de referencia.  


