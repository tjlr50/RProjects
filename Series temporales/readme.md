# Proyecto series temporales
## Primera Parte:
Analisis de serie temporal de fabricación de un producto electrónico.
Importar el dataset Datos.xlsx
df = read_excel("Datos.xlsx")
head(df)

Con la observación anterior es posible notar como los tipos de datos ya no son numericos, ahora son de
serie temporal y se encuentran más estructurados (Años y meses). Procederemos a un analisis a partir de la
visualización de la serie temporal.
2
plot.ts(ts.n1)
Time
V1
2005 2010 2015
50 100 150 200 250
Suavizado: Holt Winters. Esta técnica de suavizado utiliza un conjunto de estimaciones recursivas a partir
de la serie histórica. Estas estimaciones utilizan una constante de nivel, una constante de tendencia, y una
constante estacional multiplicativa. Como veremos esta tecnica ofrece un ajuste estacional (s=12 en el caso
de datos mensuales).


Analisis inicial: Inicialmente podemos observar algunos patrones que no deberiamos apresurarnos a determinar estacionalidad, ademas, la tendencia puede ser confusa porque incialmente parece ser creciente con
unos picos notablemente altos, pero desde el 2010 los picos dejan de ser tan notables y la tendencia parece
cambiar de dirección (decreciente), aunque finalmente, a partir del 2015 parece elevarse un poco.
Al describir series de tiempo, utilizamos palabras como “tendencia” y “estacionalidad”, que deben definirse
con más cuidado. Basado en los estudios y materiales de clase podemos decir lo siguiente:
Tendencia Existe una tendencia cuando hay un aumento o disminución a largo plazo en los datos. No tiene
por qué ser lineal. A veces nos referiremos a una tendencia como “cambio de dirección”, cuando puede pasar
de una tendencia creciente a una tendencia decreciente.
Estacional Un patrón estacional ocurre cuando una serie de tiempo se ve afectada por factores estacionales
como la época del año o el día de la semana. (frecuencia fija)
4
Cíclico Un ciclo se produce cuando la observación de los datos suben y bajan sin una frecuencia fija. Estas
fluctuaciones suelen deberse a condiciones económicas o relacionadas con el “ciclo económico”. La duración
de estas fluctuaciones suele ser al menos 2 años.
A partir de la descomposición de la serie temporal se pude obtener mayor claridad sobre la tendencia,
estacional y el factor de aleatoriedad que puede presentar la fabricación del producto.

n1.ts.desc = decompose(ts.n1)
plot(n1.ts.desc, xlab='Año')

n1.ts.desc = decompose(ts.n1)
plot(n1.ts.desc, xlab='Año')

### Conclusión Los métodos de predicciones que se utilizaron anteriormente pueden ser interesantes, sin
embargo pueden ser muy simples para largas estimaciones de tiempo.
Al graficar el pronóstico, se puede observar que el método de la media (linea roja) no ayuda mucho debido a
que nuestra serie tiene tendencia, ni el caso de naive ya que de igual forma solo desplaza una línea sobre la
última observación. Finalmente, el método que mejor pronostica para este caso es el
