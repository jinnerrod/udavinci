# Introducción
Según Dorian Pyle “el objetivo fundamental del pre-procesamiento de datos es manipular y transformar los datos en bruto de modo que el contenido de la información envuelto en el conjunto de datos pueda ser expuesto o accesible con mayor facilidad”. Por otro lado, el procesamiento de datos sería “la acumulación y manipulación de elementos de datos para producir información significativa”.

En esta Unidad veremos cómo se obtienen y limpian datos, los modelos de regresión, la inferencia estadística y las pruebas de hipótesis.

# Objetivos

- Entender la diferencia entre pre-procesamiento y procesamiento de datos.
- Conocer los modelos de regresión.
- Aprender a obtener y limpiar datos.

# Mapa Conceptual
![Mapa conceptual](https://cdn.educalms.com/byUyRkFmJTJGUENYViUyQjYwaHNLQ0tROGJOZyUzRCUzRA==-1660647017.jpg?Expires=1788987941&Signature=Owsg2AyDyARXaZeBN9GdifyvjqJY-yk-5dG2X5Ju7ykSXslWGxnjvWSqhsOQtV6XzgruumggqRZ~gaILwwDlPWNBi3MnYKvnompJjgx900JVAiPJ4sQZom06rseYqYgdn4oUOOOnmquXwxhDXeshiqPWEDT2CjZkShSw~8ZTjhdKk4SuXPdw6vOsFKwoU7sPBEUlsfaUqYb4X~vNRmozDU2bhM6xvpytCzkFlfLUVQ5Oi8i04X5-IcN9VGYVAFCusMq8tQQpVoukNZkFelrFNot5uJlhM~UMOaeBniTSqCIZQrT8-OJtXdPJLzbOuR~nC8OadGX0NdCG1vv9dlZhJA__&Key-Pair-Id=K2XVTQ1784SQT0)

# 1. Obtención y limpieza de los datos (ETL)
El proceso ETL permite el tratamiento de la información desde los distintos orígenes de datos (CRM, ERP, Redes Sociales, etc.) para poder alimentar el DataWarehouse con información de calidad.

Sus siglas ETL, del inglés Extract-Transform-Load, vienen a dar significado al proceso que organiza el flujo de los datos entre diferentes sistemas en una organización, aportando los métodos y herramientas necesarias para mover los datos desde múltiples fuentes a un almacén de datos, reformatearlos, limpiarlos y cargarlos en otra base de datos, data mart o datawarehouse. ETL forma parte de lo que llamamos Data Management o “Gestión de los datos”, y lo podemos englobar dentro del proceso de captación de datos llevado a cabo por Data Science.

Recordamos a continuación brevemente cada una de las etapas del proceso ETL, de manera que transformemos los datos para adaptarlos a nuestro modelo de análisis.

**- Extracción:** Se obtienen los datos de las fuentes de origen y se cargan en el repositorio en tablas intermedias que contienen los datos sin la estructura final del modelo. El principal objetivo de la extracción es extraer tan sólo aquellos datos de los sistemas transaccionales que son necesarios y prepararlos para el resto de los subprocesos de ETL. Para ello se deben determinar las mejores fuentes de información, las de mejor calidad, por lo que se deben analizar las fuentes disponibles y escoger aquellas que sean mejores.
**- Transformación:** En esta etapa se pretende adecuar la información, Se suele duplicar tablas que contienen la información correcta y la creación de nuevos campos o nuevas tablas con datos agregados y/o calculados. El objetivo no es otro que evitar duplicidades innecesaria e impedir la generación de islas de daos inconexas, por lo que este proceso incluye cambios de formato, sustitución de códigos, valores derivados y agregados.
**- Carga de datos:** Una vez reorganizada la información, la cargamos en las tablas definitivas de nuestro(s) repositorio(s) de datos: datawarehouse y/o datamart. Nuevamente se duplican las tablas que contienen la información correcta y posteriormente se crean los nuevos campos necesarios para contener toda la información.

<video width="100%" controls>
  <source src="videos/datawirehouse-data-mart.mp4" type="video/mp4">
</video>


Se debe tener en cuenta que en los procesos ETL no sólo se utilizan cuando aparecen nuevas aplicaciones que se han de integrar a las rutinas de la organización, sino que también es frecuente emplearlas para la integración con sistemas heredados. Estos sistemas heredaros son aplicaciones antiguas que existen en la organización y muchas veces se deben integrar con nuevas normas aplicativas. La principal dificultad que puede presentarse en este tipo de situaciones es que la tecnología utilizada en estas aplicaciones antiguas complica la integración con los nuevos programas.

## 1.1. Limpieza de los datos
Algunos autores prefieren dividir ETL en un proceso de 5 etapas en lugar de 3 como hemos visto hasta el momento. Estas cinco etapas serían:

- Extracción
- Limpieza
- Transformación
- Carga
- Actualización

Como vemos, se introduce una fase de limpieza tras la de extracción y previa a la transformación, y una última etapa de actualización. Quizás la etapa de limpieza esta inherente hasta al momento con el proceso de extracción, pero creemos que se le debe dar una mención especial por la importancia y relevancia que tiene de cara a la creación de un almacén de datos libre de inconsistencias y funcional.

Con limpieza, nos referimos a todos aquellos procesos que eliminan registros que no se incorporarán a nuestro almacén de datos.

Es aconsejable que estos registros se guarden en tablas que se explotarán, como copia de seguridad, por si es necesaria una marcha atrás en el proceso. Hablamos por tanto de registros sin información válida, campos nulos o incorrectos, datos aislados, etc.

Por tanto, en la etapa de limpieza tras recuperar los datos en bruto, debemos comprobar su calidad, eliminar los duplicados y cuando es posible, corregir los valores erróneos y completar los valores vacíos. El objetivo es conseguir datos limpios y de alta calidad que serán manipulados en la etapa siguiente del proceso, por lo que deberemos:

**- Depurar los valores:** Consiste en localizar e identificar los elementos individuales de información en las fuentes de datos y los aísla en los ficheros destino. Por ejemplo: separar el nombre completo, en nombre + primer apellido + segundo apellido
**- Corregir:** Corregimos los valores individuales de los atributos usando algoritmos de corrección y fuentes de datos externas. Por ejemplo: comprobar que la letra de un DNI se corresponde con el número que identifica, o que un código postal se corresponde con la dirección.
**- Estandarizar:** Se aplican ahora rutinas de conversión para transformar valores en formatos definidos y consistentes, aplicando procedimientos de estandarización y definidos por las reglas del negocio.
**- Relacionar:** Se buscan y relacionan los valores de los registros, corrigiéndolos y estandarizándolos, basándose en reglas de negocio para eliminar duplicados.
**- Consolidar:** Se analiza e identifican relaciones entre registros relacionados y los junta en una sola representación.

La limpieza debe realizarse a ser posible, en cada fuente de datos de origen. La mayoría de herramientas ETL tienen funcionalidades de limpieza de datos, aunque existen herramientas especializadas.

## 1.2. Características de las herramientas ETL
Las herramientas ETL ahorran tiempo y dinero en el proceso de desarrollo y actualización de un datawarehouse, ya que reducen la cantidad de sistemas de conversión personalizados a desarrollar, para migrar o concentrar la información.

Un desarrollo reciente en el software ETL es la aplicación de procesamiento en paralelo, esto ha permitido desarrollar una serie de métodos para mejorar el rendimiento general de los procesos ETL cuando se trata de grandes volúmenes de datos. Hay 3 tipos principales de paralelismos que se pueden implementar en las aplicaciones ETL:

**- Paralelismo de datos:** consiste en dividir un único archivo secuencial en pequeños archivos de datos para proporcionar acceso paralelo.
**- Paralelismo de segmentación (pipeline):** se base en permitir el funcionamiento simultáneo de varios componentes en el mismo flujo de datos.
**- Paralelismo de componente:** este tipo de procesamiento consiste en el funcionamiento simultáneo de múltiples procesos en diferentes flujos de datos para el mismo puesto de trabajo.

Según Gartner, las características que debe tener una herramienta ETL son:

**- Conectividad /capacidades de adaptación:** se refiere a la habilidad para conectar con un amplio rango de tipos de estructuras de datos entre los que podrían incluirse: bases de datos relacionales y no relacionales, variedad de formatos de ficheros, XML, aplicaciones ERP, CRM o SCM, formatos de mensajes estándar (EDI, SWIFT o JL7), colas de mensajes, emails, websites, repositorios de contenidos o herramientas de ofimática.
**- Capacidades de entrega de datos:** supone la habilidad para proporcionar datos a otras aplicaciones, procesos o bases de datos en varias formas, con capacidades para programación de procesos batch, en tiempo real o mediante lanzamiento de eventos.
**- Capacidades de transformación de datos:** habilidad para la transformación de los datos, desde transformaciones básicas (conversión de tipos, manipulación de cadenas o cálculos simples) o transformaciones intermedias (agregaciones, sumarizaciones, lookups) hasta transformaciones complejas, como análisis de texto en formato libre o texto enriquecido.
**- Capacidades de Metadatos y Modelado de Datos:** recuperación de los modelos de datos desde los orígenes de datos o aplicaciones, creación y mantenimiento de modelos de datos, mapeo de modelo físico o lógico, repositorio de metadatos abierto, sincronización de los cambios en los metadatos en los distintos componentes de la herramienta, documentación, etc.
**- Capacidades de diseño y entorno de desarrollo:** representación gráfico de los objetos del repositorio, modelo de datos y flujos de datos, soporte para test y, capacidades para trabajo en equipo, gestión de workflows de los procesos de desarrollo, etc.
**- Capacidades de gestión de datos**
*- Adaptación a las diferentes plataformas hardware y sistemas operativos existentes.*
**- Operaciones y capacidades de administración:** habilidades para gestión, monitorización y control de los procesos de integración de datos, como gestión de errores, recolección de estadísticas de ejecución, controles de seguridad, etc.
**- Arquitectura e integración:** grado de compactación, consistencia e interoperabilidad de los diferentes componentes que forman la herramienta de integración de datos
**- Capacidades SOA**

# 2. Inferencia estadística
La estadística descriptiva y la teoría de la probabilidad van a ser los pilares del procedimiento de inferencia estadística, con los que se va a estudiar el comportamiento global de un fenómeno. La probabilidad y los modelos de distribución junto con las técnicas descriptivas, constituyen la base de una nueva forma de interpretar la información suministrada por una parcela de la realidad que interesa investigar.

La inferencia estadística es por tanto, el proceso de obtener conclusiones sobre una población a partir del análisis de una muestra. En la medida en que la muestra sea representativa de la población, los resultados podrán generalizarse.

La bondad de estas deducciones se mide en términos probabilísticos, es decir, toda inferencia se acompaña de su probabilidad de acierto.

Por tanto, uno de los principales objetivos de la inferencia estadística es estimar un determinado parámetro desconocido de la población bajo estudio. Esta estimación puede ser de carácter puntual, si únicamente se proporciona un valor para dicho parámetro, o confidencial, si lo que se calcula es un rango de valores entre los que figura el valor real del parámetro dado un cierto nivel de confianza. Otras veces, lo que se pretende es comprobar alguna hipótesis inicial sobre la población objeto de estudio a través de la información extraída de una muestra, para lo que se emplea el contraste de hipótesis, de lo que hablaremos en puntos posteriores del tema.

![Esqueme de métodos inferenciales](https://cdn.educalms.com/RzFOV21VaXcySUUxV2NBVCUyQnJwNkJ3JTNEJTNE-1660647015.png?Expires=1789251481&Signature=PCL9tR~7E97-anfqTfzONkQxrZ0u~k7iQbapzGzy3LIDeuicImhHRNabQHjnEt4GplIVucovvTwPSB8sGg4a-qJfeKw7ih3Prxeyw8zU~wsyCjNT2rB1vIdn7uNd5-kPyk5yPvwXHqyId7gqIh6Oa0yN2VF9SuZUAIiFE0Ttwthx6hXO6PLyOapE--aLRh3OOK8adUm3nLUbOsIAUOwKMzGt~XB8EjHqlgDturaroOYZ0npQaApqulq829MW8JOrjlt82ZRiwERI1zoALpHiJ2XxrnjCowJd3IT4C6CrdZ9v4Bss5iRa77udgOxVecgQQxenj0Pbg8tfC6Dmc-ZF8A__&Key-Pair-Id=K2XVTQ1784SQT0)

En el proceso de inferencia se pretende, como hemos visto, estimar el valor de un parámetro a partir del valor de una variable estadística.

Esta estimación puede ser puntual o bien por intervalo. La mejor estimación puntual de un parámetro es simplemente el valor de la variable estadística correspondiente, pero es poco informativa, porque la probabilidad de no dar con el valor correcto es muy elevada, es por eso que se acostumbra a dar una estimación por intervalo, en el que se espera encontrar el valor del parámetro con una elevada probabilidad. Esta estimación recibe el nombre de estimación mediante intervalos de confianza.

La estimación por intervalos de confianza consiste en determinar un posible rango de valores o intervalo (a;b), en el que, con una determinada probabilidad, sus límites contendrán el valor del parámetro poblacional que buscamos. Para cada muestra obtendremos un intervalo distinto que, para el X% de ellas, contendrá el verdadero valor del parámetro. A este intervalo se le denomina intervalo de confianza. A la probabilidad de que hayamos acertado al decir que el intervalo contiene el parámetro se le denomina nivel de confianza. Hablamos de nivel de significación a la probabilidad de errar en esta afirmación, es decir la significación será 1 – nivel de confianza, ya que el nivel de confianza corresponde a la probabilidad de que el intervalo contenga el valor verdadero del parámetro.

De lo visto anteriormente podemos deducir que, toda inferencia se acompaña de su probabilidad de acierto, lo que llamamos bondad de ajuste.

Así con las técnicas de inferencia estadística nuestro objetivo va a ser: extraer conclusiones y generalizaciones sobre la población basándonos en la información suministrada por la muestra. Se supone que la propiedad que se desea estudiar en la población puede describirse en términos de una variable aleatoria X que tendrá una función de distribución F.


## 2.1. Inferencia estadística en R

La resolución de problemas de inferencia con R, puede llevarse a cabo de forma sencilla calculando el estimador que corresponda mediante funciones que proporcionan en muchos casos la solución al problema de una forma más directa.

La función **t.test()** es la encargada de los procedimientos de inferencia sobre la media en poblaciones normales. Mediante esta función:

- Podemos construir intervalos de confianza para una media y para la diferencia de medias entre dos poblaciones.
- Podemos llevar a cabo contrastes de hipótesis, tanto unilaterales como bilaterales, sobre una media o sobre la diferencia de medias entre dos poblaciones.
- En el caso particular de la comparación de dos poblaciones, permite elegir entre considerar las varianzas poblacionales iguales o distintas.

Esta función se basa en la distribución t de Student, que surge del problema de estimar la media de una población normalmente distribuida cuando el tamaño de la muestra es pequeño, y se desconoce la varianza.

---

Imaginemos que tenemos dos grupos de pacientes, uno al que se le da un nuevo medicamento y otro en el que se toma un placebo, queremos estimar si el tiempo medio de recuperación de los pacientes que toman el nuevo medicamento es menor que los que toman el placebo. Para ello disponemos de los datos siguientes para una muestra de 10 pacientes en cada caso, donde se recoge el tiempo (en días) que se tardó en la recuperación.

Pacientes con medicamento: 15, 10, 13, 7, 9, 8, 21, 9, 14, 8

Pacientes con placebo: 15, 14, 12, 8, 14, 7, 16, 10, 15, 12

Desconocidas las varianzas, podemos aplicar la función t.test() sobre los valores para realizar el análisis de los datos correspondiente:

![Función t.test()](https://cdn.educalms.com/bTU3MTVVMWJkWFQyTjhqRGs5QTNJUSUzRCUzRA==-1660647015.png?Expires=1789251771&Signature=rqJtV7Tyrkgy4-BSwlai4EF92Myxo5lSnL8m~R3Lmm0qxOuFgup~jvTa~L4pE8PFG6JKb33QQ~~9iouEVnEESK0VxERoB9U-qVKZCIFF1772pSSc30NEizMdFpd0nwYqbOGKRl6FbUD6MJkz0bbix1V0tVdxeBHUqOuHmNOGh1-JwXDI-8ERz0tGoyPGWnXOfSbjMegVvPiDYNr7e8-gfW6WCBI3POXVR3KR5GpJC7zrPlblil7a1UF1HysPHSg3hgm5WE3anhsQJVNobToxzf3zbjUXpFkYjZUA1CL1isSDs5y3H0dWLzIPUId30eKeMjMA1q9~dmeAo~fLh~JKIA__&Key-Pair-Id=K2XVTQ1784SQT0)

*Función t.test()*

Podemos decir de los resultados obtenidos, que al ser p-value > 0.05 no podemos refutar que tienen la misma media, es decir el fármaco no presenta ninguna mejora. Para entender mejor estos conceptos veamos en detalle la función t.test() y los resultados que arroja su ejecución.

---

##### Función t.test()

Las pruebas sobre la media nos pueden resultar útiles para en base a unos resultados sobre una muestra referentes a las medias queremos realizar una extrapolación a toda la población o bien si tenemos dos muestras diferentes y queremos saber si ambas pertenecen a la misma población.

Así la función t.test() produce test de hipótesis e intervalos de confianza basados en la distribución t, siendo su sintaxis:

`t.test(x, y = NULL, alternative = c("two.sided", "less", "greater"), mu = 0, paired = FALSE, var.equal = FALSE, conf.level = 0.95)`

Donde:

- **x, y**: son vectores numéricos que contienen los datos. En el caso de que omitamos "y" se realiza un test t para una muestra
- **alternative**: es una cadena de caracteres que especifica la hipótesis alternativa: "two.sided" = bilateral, "greater" = mayor o "less" = menor.
- **mu**: es un valor numérico que especifica el valor para la hipótesis nula (media o diferencia de medias). El valor por defecto es 0.
- **paired**: valor lógico que indica si se quiere realizar un test t-apareado (por defecto se calcula el test t para muestras independientes)
- **var.equal**: variable lógica que se utiliza sólo en el caso del test para muestras independientes. Si es TRUE se calcula la varianza pesada para estimar la varianza, si es FALSE (valor por defecto) se utiliza la sugerencia de Welsch para los grados de libertad utilizados.
- **conf.level**: nivel de confianza del intervalo estimado para la media, adecuado a la hipótesis alternativa especificada (por defecto 95%).

Por tanto, la función t.test() se basa en una prueba de hipótesis (explicaremos en puntos posteriores del tema qué son), y como en cualquier contraste de hipótesis tendremos dos alternativas complementarias para las que se especificarán distintos valores de un parámetro poblacional y a la vista de los datos optaremos por una de ellas:

---

**Hipótesis nula**: a la que nos referimos como H0

**Hipótesis alternativa**: a la que nos referimos como HA o H1

A la hipótesis nula siempre se le concede el beneficio de la duda, y se intenta encontrar en la muestra evidencias en contra de ella. Así, al terminar el contraste habremos de optar por aceptar H0 o rechazarla. Cuando rechazamos la hipótesis nula admitimos implícitamente como cierta H1, sin embargo, en el caso de que aceptemos H0 seguimos sin saber cuál de las dos opciones, si la hipótesis nula o la alternativa, es cierta, por lo tanto el objetivo habitual que se perseguirá a la hora de hacer cualquier contraste de hipótesis será el de descartar la H0.

Para aceptar o rechazar la hipótesis nula, nos basaremos en el valor que se haya establecido de significatividad, es decir si el valor de p-valor, que se define como la probabilidad de error que asumiríamos en caso de rechazar la hipótesis nula con los datos de que disponemos, es menor al valor de significatividad rechazamos H0, y lo aceptamos en caso contrario. El valor de significatividad que se asume en la mayoría de los estudios estadísticos es 0.05, aunque también puede tomar el valor 0.01 o 0.10 dependiendo del riesgo que se quiera asumir a equivocarse.

---

Si volvemos sobre nuestro ejemplo:

```
Two Sample t-test

data:  med and plac
t = -0.53311, df = 18, p-value = 0.3002
alternative hypothesis: true difference in means is less than 0
95 percent confidence interval:
      -Inf 2.027436
sample estimates:
mean of x mean of y 
     11.4      12.3 
```

Obtenemos un valor de 0.3 para p-value, por lo que al ser p-value > 0.05 no podemos refutar la hipótesis nula, cuyo valor estaba definido de la siguiente forma:

H0: ambas muestras tienen la misma media (tanto pacientes que toman medicamentos como los que toman el placebo tardan el mismo tiempo medio en recuperarse)

H1: la diferencia entre las medias de las muestras es menor de 0, es decir la media de recuperación para los pacientes con medicación es mayor que la de los pacientes con placebo.

Al no poder refutar la hipótesis nula, (los pacientes no tardan el mismo tiempo medio en recuperarse en ambas muestras) y ser la hipótesis alternativa que el tiempo medio de recuperación en los pacientes con medicación es mayor que los pacientes con placebo, podemos predecir que la toma del medicamento no supone una mejora en el tiempo de recuperación.

# 3. Modelos de regresión

En términos generales, el análisis de regresión trata de la dependencia de una variable, la *variable dependiente*, en una o más *variables predictorias* o independientes, con el objeto de estimar o predecir la media o valor promedio de la primera con base a valores conocidos o fijados de las segundas.

Dicho de otro modo, los modelos de regresión tratan de estimar o predecir el valor de una variable dependiente en función de valores conocidos de variables predictivas. Sin embargo, aun cuando los modelos de regresión traten de predecir los valores de una variable dependiente en términos de una o más variables independientes, de ninguna forma se establece una relación formal de causa-efecto; solo se trata de una relación matemática empírica.

Existen muchos tipos de modelos de regresión como el lineal, el cuadrático, el polinomial, exponencial, logarítmico, etc; el más simple es el de regresión lineal, este modelo, trata de explicar mediante una relación funcional de tipo lineal, los cambios en la media de la variable dependiente debido a los cambios en las variables predictorias.

---

Todos los modelos de regresión que existen, funcionan de un modo similar, se calcula un conjunto de valores que le asignan un peso a cada variable explicativa. Los valores calculados se obtienen de la información que se tiene de las variables independientes. Sin embargo, los métodos para calcular estos valores pueden ser distintos de un modelo a otro.

Para hacer un uso efectivo de los modelos de regresión, es necesario identificar el modelo que mejor se adapta a nuestro problema en particular, ya que utilizar un modelo erróneo dará lugar a que las estimaciones hechas no sean de utilidad.

Dentro de la ciencia de datos, quizás el modelo de regresión más importante y más usado es el modelo de regresión lineal. La base de este método es la idea de que es posible ajustar una línea a un conjunto de puntos de datos que representa el efecto que tiene una variable *independiente* en una variable *dependiente*.

Se pueden encontrar varios tipos de regresión:

- Regresión lineal simple: y = A + Bx
- Regresión múltiple (varias variables): y = A + Bx1 + Cx2 + … + Mxn
- Regresión logarítmica: y = A + BLn(x)
- Regresión Exponencial: y = ABx
- Regresión cuadrática: y = A + Bx + Cx²


## 3.1. Regresión en R

La función en R que nos permite obtener modelos de regresión lineal simple es **lm**, aunque también se puede utilizar esta función para el análisis de la varianza y el análisis de la covarianza.

Supongamos que queremos calcular si existe alguna relación entre el volumen de ventas y el gasto en publicidad, para ello usamos los datos de los últimos 6 años de la empresa.

| Volumen de Ventas (miles €) | Gastos en publicidad (miles €) |
| :--- | :--- |
| 100 | 16 |
| 150 | 32 |
| 200 | 48 |
| 220 | 56 |
| 300 | 64 |
| 320 | 80 |

---

Si ejecutamos el siguiente script de R:

![Script de R](https://cdn.educalms.com/a3dmSW5pSlJvRkh4dGpZZFpNenM2ZyUzRCUzRA==-1660647015.png?Expires=1789252131&Signature=U9Ae71uy1~iIoBujSrzWCkghCH8CtdT50l5Klpx8J9DCgp~GitvkUIF5SBXSgXyni2Z-xrpPuXVwLAr7rYiW8nbapo6p96YERL~Z21lZXE1MgjXn~C~qpMkR4QsU-YwjkJN53XZAVCPtEwaC1T9tSP41lfdwR3kqtS~PNxMkrKrAEsNp732cSvXwD48LxL6XJGZ-ovSveONXIHv8iRGiT6gkQ2DCHieQrLrQOsq~d5eH1IC0IisF5Q9p5sObCRlANScDRmBi6LL9uAmCVrUbltoFJ0-PzkTNFfy5rCOcKAjvFaA2p2ugzXvPQ0XYYd79amwINVaExUMOd2wof~piMg__&Key-Pair-Id=K2XVTQ1784SQT0)

*Script de R*

Obtenemos el resultado que se muestra a continuación:

![Resultado](https://cdn.educalms.com/cjQyQWZkU281SFdMeFlEZDhUJTJGN2dnJTNEJTNE-1660647015.png?Expires=1789252131&Signature=XIhWs2h~4TwtQ3yC~HHv2SfpyV1OcCBqZ09wAwFeY2A2zdqzbYqZHFD1k-lvwO3V3r1WLh4-aCcuyMUKH1QybpgSTFTDil~6h0YZJ-yZiGywWlSYaZHC-ZV54j~bRZibtAsl-k135r5uc0DZjHEIoqe98eofG2Chxbe6y~66roRg7y0aMK6gBiTV-K7P6gZdOGYh6kAk8GscKlAOS3JNh1YPjLmMAbJ1oY3ZwZpFF~ZL7cOsKYkjb8-T1mFPFNOaEENBFUN0kG~wxIld6flmwqzjZPRKAyxdUZsa0y3Akc35OpBldzYl~fKmZCrxkQ1uH1XHsQd6vw7-T0WaGrqD5w__&Key-Pair-Id=K2XVTQ1784SQT0)

*Resultado*

Hay que tener en cuenta el orden en el que se escriben las variables, siendo Intercept la ordenada en el origen de la recta de regresión. Del ejemplo anterior deducimos que la recta de regresión es:

Y(x) = (-7.3621) + (0.2637)x

Vamos a dibujar la recta de regresión del ejemplo:

![Ejemplo](https://cdn.educalms.com/bzFKTFE2a2c3djVoOHBudkxZVGdXUSUzRCUzRA==-1660647016.png?Expires=1789252131&Signature=PiAw3AMwOrsGI7L0M5O--m0bTVH8~xozg5MLnD0e8sZsZWs8FjjruCAPyAgNC0hYzM4PUmzOOusD5uZAGOCI-lM9kXKK9v0BSedg94L4VSBdxpyX5bsNq7iXIplvwMJw3u58SLawsZhRxAjsLei4N~JCUTtyXDx-k4mFNa0vmBEoE-AdaFgLP7J~7e6VOuLUh8wGdyY7r2rLn5Z0WI~zVvb2TvZe~6w9M~B-2ttmEtTmJbNR40GVsgq7SIB~nBRRBjOV9glhiCRRUmIEPgFGOh-Aun~gND10KR4vvMd74vCqzc2FfgJwtyTkbPOZTTh8VUQ1P~VfqrFJfW-4VME36Q__&Key-Pair-Id=K2XVTQ1784SQT0)

*Ejemplo*

Obtenemos la siguiente representación

![Recta de regresión](https://cdn.educalms.com/eFdGJTJCUUVzZ3VCa3RsZXo4T29DbkZ3JTNEJTNE-1660647016.png?Expires=1789252131&Signature=zqhJayBcxkvMPPpd1SrOFsuFW3PEZZnDtgGyeu~A6gp1yMwVKfamtjr0thbCSD-~4FnBMtGZcsTfr3ORgvREm6gdDutN2veGH~3P6vFM7Gkstw2HmNPtWl-ARlcr9dMnGdcc5C1AHADpd-Mj7exYCk5nWrnqiLfVeS6dXp-2WahIg4~7HZ7LSzqmbwCjO0t1n647rNvytRLuszwq~03EdtmSXvgg55aZZp9JbYuin4OwBbKZLPPzuANra5n0brjVeCv~9YOSpBntYXPW6-MRILNdu5UlXZ1GxV-uG2rg4veldwV~pbC9~3D1WhvpyZHP0FRUCYRr8yQwiiuoIjU~dg__&Key-Pair-Id=K2XVTQ1784SQT0)

*Recta de regresión*

A partir de este punto podemos ajustar el modelo para poder usarlo posteriormente para predecir datos, para ello usamos la función **predict** que nos permite obtener todas las posibles predicciones para la variable x según la posición en la que se encuentren sus datos

Si ejecutamos predict(r1):

```
> predict(r1)
       1        2        3        4        5        6 
19.00788 32.19286 45.37784 50.65183 71.74780 77.02179 
```

---

Por último para tener un resumen de las características más importantes de un modelo de regresión utilizaremos la función **summary**, como se muestra a continuación

![Summary](https://cdn.educalms.com/c0MzYmhiOGlKTWdydUF0SXZRbDIlMkZnJTNEJTNE-1660647016.png?Expires=1789252131&Signature=gE3qciltapsJozzPiFEKSIOqFL2vDWvWaFgxnRAvyL0IqQt7fEITzDZL5OQV-wrUGbNEnAd6vB~6DXED4ZiPMWdpftsr3~lDZr2mPhrhLvMWbQR8vMjz7AZK4bre2PoCYWSBo9rgHc2kdp-bzHmdi6fRt83fU53cN5fx4ISuU-KGsH1XpB7ZNiE8wRyG9iQO-Kbqy0TZMALfu-hyjEie3ffiuexlII-rKdXi6LWHIsgTI2vYcEjfE7rzuP0HlHvDX1WqbzXIbAWs2YPTH8zaYnOq5IaYb~EJRmiJRCHZvoTKivIR-JZ2Z2vBxn-UJQMk0iWChRTrEY-rUxsWAbYUdg__&Key-Pair-Id=K2XVTQ1784SQT0)

*Summary*

Donde **Residuals** es un resumen de los residuos obtenidos por el modelo. **Coefficients** es una tabla con los valores de las estimaciones (**Estimate**), sus errores estándar, el valor del estadístico y **p-valor** para las pruebas de hipótesis de los estimadores. **Residual Standard error** es el valor del error estándar del residuo. **Multiple R-squared** es el valor del coeficiente de determinación. **Adjusted R-squared** es el valor ajustado del coeficiente de determinación. Como vemos del ejemplo anterior el coeficiente de determinación es cercano a 1 por lo que las predicciones a partir del modelo casi NO tendrían error.

# 4. Pruebas de hipótesis

Muchos de los problemas con los que nos vamos a encontrar en la ciencia de datos, requieren que se tome una decisión entre aceptar o rechazar una proposición sobre algún parámetro. Esta proposición recibe el nombre de **hipótesis.**

Este es uno de los aspectos más útiles de la inferencia estadística, puesto que muchos tipos de problemas de toma de decisiones, pruebas o experimentos pueden formularse como problemas de prueba de hipótesis.

Una hipótesis estadística es una proposición o supuesto sobre los parámetros de una o más poblaciones. Como vimos en el punto de inferencia estadística para cualquier estudio basado en prueba de hipótesis debemos establecer dos hipótesis:

- **H0**: Hipótesis nula que es la que se pretende rechazar o invalidar. Así por ejemplo, si deseamos decidir si un procedimiento es mejor que otro, formularemos la hipótesis de que no hay diferencia entre ellos. Por tanto la hipótesis nula es la que se somete a comprobación, y es la que se acepta o rechaza, como la conclusión final del contraste.

- **H1**: Hipótesis alternativa es igualmente una afirmación acerca de la población de origen. Será la hipótesis que se acepta en caso de que se rechace H0 y viceversa.

Por tanto el contraste de hipótesis es un mecanismo mediante el que se rechaza la hipótesis nula cuando existan diferencias significativas entre los valores muestrales y los valores teóricos, y se acepte en caso contrario. Pueden ser de dos tipos:

---

- **Bilateral**: Cuando en la hipótesis alternativa aparece ≠
- **Unilateral** (derecho o izquierdo): Cuando en la hipótesis alternativa aparece el signo > (unilateral derecho), o el signo < (unilateral izquierdo)

##### Tipos de errores en el contraste de hipótesis, estadístico de contraste y región de rechazo

Cuando extraemos una conclusión tras un contraste de hipótesis puede darse el caso de que sea o no cierta, pues desconocemos la verdadera situación. Es decir puede que rechacemos una hipótesis cuando debería haberse dado por cierta o bien que aceptemos una hipótesis que debería haber sido rechazada, esto es lo que conocemos como errores de tipo I y tipo II respectivamente.

La probabilidad de cometer un Error de tipo I es lo que se conoce como nivel de significación Ɑ, mientras que la probabilidad de error de tipo II es igual a β.

El nivel de significación es el más importante, ya que nos informa de la probabilidad que tenemos de estar equivocados si aceptamos la hipótesis alternativa.

---

Como se habrá podido deducir, los errores de tipo I y tipo II no se pueden cometer simultáneamente, ya que uno se da si H0 era correcta y el otro en el caso de que fuera incorrecta.

El estadístico de contraste lo entendemos como un valor estandarizado que se calcula a partir de los datos de la muestra durante una prueba de hipótesis, y se utilizan para determinar si puede o no rechazarse la hipótesis nula. El estadístico de contraste compara los datos con lo que se espera según la hipótesis nula, para qué tipo de prueba de hipótesis tendremos un estadístico de prueba, y usar uno u otro tipo dependerá del tipo de datos que tengamos y de la estimación que queremos plantear. Por otro lado la región de rechazo es el conjunto de valores tales que si la prueba estadística cae dentro de este rango, decidimos rechazar la hipótesis nula.

## 4.1. Test de hipótesis en R

Algunas de las pruebas de hipótesis que podemos llevar a cabo en R, en función de la muestra y los estadísticos de prueba o contraste son:

##### Contraste de normalidad

Consiste en asegurar que una variable se ajusta a la distribución normal. Este contraste se realiza entonces para comprobar si se verifica la hipótesis de normalidad necesaria para que el resultado de algunos análisis sea fiable.

Para comprobar la hipótesis nula de que la muestra ha sido extraída de una población con distribución de probabilidad normal se puede realizar un estudio gráfico y/o analítico.

##### Prueba de Kolmogorov-Smirnov

Este test se utiliza para contrastar si un conjunto de datos se ajustan o no a una distribución normal. Tiene la peculiaridad de que es recomendable su uso para muestras con más de 50 observaciones, y el estadístico de prueba que utiliza es la máxima diferencia.

Por tanto, utilizaremos este contraste para comprobar si dos conjuntos de datos siguen la misma distribución, o bien para ver si un determinado conjunto de datos se ajusta a una distribución determinada. Las muestras no tienen por qué ser del mismo tamaño.

---

Para aplicar el test de Kolmogorov-Smirnov hay que tener en cuenta que es necesario conocer la media y la desviación estándar de los datos. En R utilizamos la función ks.test().

*Vamos a generar 50 datos de una distribución normal y 70 de una distribución uniforme, para comprobar si el test nos advierte de que las distribuciones de origen no son las mismas.*

![Prueba de Kolmogorov-Smirnov](https://cdn.educalms.com/Z2FYJTJGbFFWMCUyRldsZFlrSm9rZ1VKJTJCdyUzRCUzRA==-1660647016.png?Expires=1789252338&Signature=Alb6wgvDylF2~DTUTmGzw9eBX67MV263cwvWB5MyzGs4ll1iYmtMlcp0qMlOEgWVWpeVJFjDRAX5KuURu7t3YBpcqvIDMw49rBfSUAcYAnfjgWkJPqcqr4wx5-7gWqB-CaZEcJFr7QdPbVpp1CRXkCPGBLqZECi2RtITLEydFoKz9xiCqEIahK6hj-duTYFCu0UIWC0ZHhQf1R~fWQvegojyK6UrWNiTvhQgNfjGgcYs6PdXvzYIt4epoG5DqOdSASxGs6~W5Po7NKLqN55nozrHa-qXUqI~RAhqZqQCFAs4qD0ZYfJzRLZMm94zoMJyqHj4SpFSI0eUWtkHdy0J-Q__&Key-Pair-Id=K2XVTQ1784SQT0)

*Prueba de Kolmogorov-Smirnov*

Como **p-value** es prácticamente 0, rechazamos la hipótesis de que los datos vienen de la misma distribución.

##### Prueba de Shapiro-Wilk

El test de Shapiro-Wilk permite contrastar la normalidad cuando la muestra con la que contamos es de un tamaño máximo de 50.

Sobre el ejemplo del punto anterior podemos ejecutar la función shapiro.test() sobre los valores de x para comprobar si los datos provienen de una distribución normal.

![Prueba de Shapiro-Wilk](https://cdn.educalms.com/a3RMekY5VW9YJTJGNHB3RExsbWZReERBJTNEJTNE-1660647016.png?Expires=1789252338&Signature=ypTzdcdI4SP2Ntmx09B557lKvQUI5DHmYr99B9aS6CI35kb-fZmfVg3nUgQTWUwvjm6DqKqP4KyLL1Gd8T7YzHyU51J5Vb1CM5Juu6559e20ok24qwU0YrRWQzqzdAoKZTUsnN2j5r0491x5NOCV7vwxkBZDCY7q5vGb6lM~G1uDiFpSxfatumY~GQ-~C9Yc0dFLhWznArGfwFuoUbOfJyjOpswfUtMPRfubGQemJeA90gVdge5p1oxnF2UzQJfMaAanUjnlLDcjVBoX37sVOTkS6V23sCeQVVp9R-6Zwm7dN5LcxqvgXGwEd1tJKGq7u1JujdM-lRBroqwlbOfDLw__&Key-Pair-Id=K2XVTQ1784SQT0)

*Prueba de Shapiro-Wilk*

En este caso para p-value obtenemos un valor cercano a 1 por lo que no rechazamos la hipótesis nula de que los datos provienen de una distribución normal, dándola como válida.

---

##### Contraste de medias

Son los contrastes de hipótesis o prueba de significación que hemos estado viendo a lo largo de todo el punto. Tendremos datos como µ que es la media de la población, σ la desviación típica de la población, s la desviación típica de la muestra, n es el tamaño de la muestra, X la media de la muestra y Z el estadístico.

##### T de Student

Como vimos en la introducción de la inferencia estadística la función t de Student se utiliza para comprobar la igualdad de las medias de dos muestras. También para comprobar si la media de una muestra es igual a una media teórica determinada. Los datos tienen que tener distribución normal para poder aplicarse la función t.test().

*A modo de ejemplo vamos a generar dos muestras aleatorias, y mediante la función t.test() comprobamos la igualdad entre sus medias*

![T de Student](https://cdn.educalms.com/VFNHVFVKQ29HMCUyQmpaNTUxVVElMkZnTEElM0QlM0Q=-1660647016.png?Expires=1789252338&Signature=BKGr3wA6qK3aMR4cj5bqW5Z8X~pzaCXBrt67A0BUbF112wXHP78qzYvNPjdmeR1SIlHHOzJM2qVV7apUG4cysZ81nOc5Ca~FWUtKKD-xkm6usz386DZVW~T~1hayGqIH7zKHVgm~2SqJQOCZBtDwvD8~I9WfKPqbOcE0hPMMyNu2z-tVKfS1HAFK2EWe4JDvZnljHqcQROD8-AXdJGTrhpg-TxXdXNT7PouQ5w1J1orGABRCt0AW26xpTXX-KxQNK30bJbUxp9Nh3j~nc61AECxsHfqMFrzoG4pmgKj0Y3tSvYDZEVTeH2U0x9HMQh1XwGEZEQvCQSDp8sI~CtYmpw__&Key-Pair-Id=K2XVTQ1784SQT0)

*T de Student*

Si observamos el valor de p-value > 0.05 por lo que con un nivel de confianza de 95% no podemos rechazar la hipótesis nula de igualdad de medias y es muy probable que las medias sean iguales para ambos conjuntos de datos, de hecho, si nos fijamos en los valores que nos devuelve la función para la media son muy similares, siendo la media para la variable x = -0.087 y para la variable y = -0.197. Vamos a comprobar ahora qué ocurre si creamos dos variables aleatorias en las que definimos dos medias diferentes.

---

![Creación de dos variables aleatorias](https://cdn.educalms.com/NWxXS3h0VzZLJTJGYlBOUmhyMlY3dWp3JTNEJTNE-1660647016.png?Expires=1789252338&Signature=UXSopmiERfLI6mWizXIjFn5OKlQp2zbumbZqrT6PhqFHWGO0Ru8KYY0-ha8I7y2b3O8qZpU2ul0BHaTPtfhhUjv1e093MbPacRThAaLZgSFinkTBTDKr49kbn-O479cY2G7hNU6~N~7za3RiYMZH7jsRBeBy4RAz5dPV2P6emGslBm6CEoui06S42vntJBwyxreI2GswCzjfEWgHVM034MHNS33vP9XDH0~MxU6p7UVX76OJJd6FQM5Xw2PkZ38NT8fZmfrF4v~xtS5eJRIDYkjvx~FIMvQgjjkj-E44iBkldy~iIwQurvwJpuczJZ90gzrkhelv6EKG4KvnHn8jQg__&Key-Pair-Id=K2XVTQ1784SQT0)

*Creación de dos variables aleatorias*

En este caso creamos una variable de números aleatorios "x" con media = 10 y otra "y" con media = 12.5, cuando aplicamos la función t.test() obtenemos un p-value < 0.05 por lo que podemos afirmar que las muestras difieren en su media.

Podemos representar los resultados anteriores mediante un gráfico de cajas para entender mejor los resultados obtenidos. Las medias se representan mediante un punto rojo.

![Resultados](https://cdn.educalms.com/S09mSWolMkZtb3g2T0ZuUDBPY3BKREVRJTNEJTNE-1660647016.png?Expires=1789252338&Signature=GAYogGQUgYkekYLThlqL-LUMfzajANlw3NbdSMPpRnotBTNoeX2frNdRUR8o23fs9In5tm9AuazIJtF8H6NNPcAb2cjt7FogPXyl8sWQxLFPVjEYSWQdcg3N9udi6rHz1gLucaWEs7bywIw093wvOdpkldrcu9jzOW0ujPwluWZfROUwM1uj-LzP0PVFDdp-UvxcL9Bxx6vjxry9mqmFqqcFP16sC-mOjJLlv6qfEX5jS6Uq5nJgfSQSXnJm1KXj3oHd4NMmeaz8jCgIWfSKD~9FhcqjQdaR1WyJLy1gh9y2FWHt0zN8a2L2dcoQqWBwpr10Xjtpf485tBCw9tXrEQ__&Key-Pair-Id=K2XVTQ1784SQT0)

*Resultados*

![Gráfico de cajas](https://cdn.educalms.com/WElJU0xqJTJGalRpNiUyQkhIOThic3dmV1ElM0QlM0Q=-1660647016.png?Expires=1789252338&Signature=qRbgEL~wK~sSGtStxUIOKvc-EyZhLhceuEGLZX5vVGHBmNMNI~xBIwAXpFdlCcVmYQlIFrAHI8EWSRIB2HqVn6SnGjMoqOJc07lFXPw9GKxCdMQBfM9dgHFTVdjJxGxVC7b~htG7SG-LpYI-MpZIDPF8bZ8JR3PRcuzdMB-2BJY6~Y6ZcMJzBWtMMtPfLYh~0OTR1M6~apjvPB~KIFsMXZV1nulo66vImYZtsViY0Bah3nr-NI4GVIQeOOIIIc0vcMcS0x3c5ARHFz3ueVkWmqNrnAbbnnHOL~oibx3C6ISg1-0E922NBcaBKhJRairdy83mghXSOGziwCD8Fkx9-g__&Key-Pair-Id=K2XVTQ1784SQT0)

*Gráfico de cajas*

![Gráfico de cajas](https://cdn.educalms.com/d3JQZXllNFoyblBLbnpidFJDbnJkQSUzRCUzRA==-1660647016.png?Expires=1789252338&Signature=nbnwJGdDUCSWFA84s9pTCxybqGfe7AZMlnh1dTEERXVqAT2hxjAW1PcptFNQu~sY6yoLAOddtoeaLw~1gSntfvML707WZxpYhoJsTbz~jo5OCop~PlZRh~XyAa9Rr16cYHl1tkwFi9X5S9FlEPZhcuTDc7uN17p1TnwEOiuBgKWAK9L4qvqtHHfhZ5mI71nYUjKo8M0JWCbic8GiqOgqbIPu303WxexsC8klSX8ZOjVnUSW7pJxCi9vPyq2f56RW0f2wPxbmiBix8P7tRMhgcV2r3whfJUKW1n0qhYCHMhy~r67TTsKiaktCexFgv11YksdP4cNn3Nj0xHaftNBPVg__&Key-Pair-Id=K2XVTQ1784SQT0)

*Gráfico de cajas*

![Aplicación de t.test() a un solo conjunto de datos](https://cdn.educalms.com/QVdibWl3d3J3Q2ZaMWV5Tmk1OTFJQSUzRCUzRA==-1660647016.png?Expires=1789252338&Signature=UkN63USVnpKQaJw5fvoBOxwQB6cB7OKvArrOPu67bWUMzVDyxKEUpJ8QJY2ix22Ti1M7pRmUNozObV95yC0R1RlOrKZ9W2KfqRk9s65RzaXT5pp09MB-aCZ3rv21dXvcyA5MZqIEduyIhhuGB~shGErWgwEDFGs1ampgtxijGzKh0b1TpiCSWP9nODaObqfYZsTZEwlRBjEFk1fLEEL~ObqETg86GQ9YLt2hvv2k5xBDkR1vsecgJFm5B6WoAScLiE8TeFWVSi5z2zv6-dWaFBaaB8eI-Q1DE9hxZsbfYCBZTVFIMsQMj8BTK3Hwh8nY4txGI3TGcJav6ABfvOvVXQ__&Key-Pair-Id=K2XVTQ1784SQT0)

*Aplicación de t.test() a un solo conjunto de datos*

En este caso observamos que p-value > 0.05 por lo que rechazamos la hipótesis nula de que la media de altura de la población masculina en España es 1.70, como vemos la media de altura que nos sale es 1.73.

---

Hemos visto ejemplos muy sencillos de uso de la función t.test(), pero como podemos observar esta función tiene un gran potencial para hacer estimaciones de poblaciones comparando datos muestrales.

##### F de Snedecor

La homocedasticidad o igualdad de varianzas de diferentes muestras, es un supuesto que aparece tanto en la estadística paramétrica como en la regresión lineal. Estas pruebas nos permiten comprobar la igualdad entre varianzas, permitiendo el contraste de la igualdad de varianzas de dos poblaciones normales, y mediante su análisis poder detectar la existencia o inexistencia de diferencias significativas entre nuestras muestras. Es esencial en todos aquellos casos en los que el objetivo es investigar la relevancia de un factor en el desarrollo y naturaleza de una característica.

De entre las funciones disponibles en R para la comparación de varianzas debemos tener en cuenta si vamos a comparar dos o más muestras, normales o no. Así usaremos var.test() cuando la comparación sea entre dos muestras, fligner.test() cuando comparemos más de dos muestras no normales o bartlett.test() y leveneTest() para comparar más de dos muestras normales.

---

Veamos un ejemplo de uso, supongamos dos variables aleatorias con diferente media y en las que queremos comparar si tienen igual varianza.

![Comparación de varianza de dos variables aleatorias](https://cdn.educalms.com/Nk8xRGRqdG9mNTVlN3FtaG80cmlWdyUzRCUzRA==-1660647016.png?Expires=1789252338&Signature=XLlvpf88vMTfou3Yf2Ko98ji~Pcaff5pFXv3yXpqIDxi0~2QGotDv-g~MDGuU5m~bRFQpTViYckkr7lCW1tgkRiH4aqrapPQvYDmXTfelmhcKMJQ4ewL~gaLDHz70rTbHq7dR6u6OIAS6j9ttFZfNf7JjLnUkUGbmU0htxRWgR9lEcdDhOPsnuPjY7KgT~kHhRe40~9pCdQGmHft3gZivVuNT4~MfTjKPHqELHv8ye30k1i2IRXPFvWM19KN5wu1w97Q5lWQxVKtQfbHwTjy7pCoDWfbnsfaNWqztQWZnAnQ4g3ZKOJ2ShDXRv6zVNdzyt8LbVTGrhwJlxbIijr-Vw__&Key-Pair-Id=K2XVTQ1784SQT0)

*Comparación de varianza de dos variables aleatorias*

Observamos que el valor de p-value es cercano a 1 por lo que no podemos rechazar la hipótesis de que sean distintas y por tanto podrían ser iguales. Veamos otro ejemplo en el que las varianzas son diferentes, y observamos los resultados que obtenemos.

![Varianzas diferentes](https://cdn.educalms.com/M2k0OG0yRFZRMyUyRlhONmZmS0NBNFlBJTNEJTNE-1660647016.png?Expires=1789252338&Signature=Pdb6JIsIJaB1y4EmpWEx~3B-gbAWglLTFEPSYDIkc5n0yZgvlw7SJG74i5-xJZ8gjboCC7Rh9FnAp-V5Noam04nnc2yh~yQdM6k1rfKSBnq8ePfSOgfujpZD9cEOTL0EZyuC3TZLBh4beqmZolTseCzCynmBBbuCYQy5ZSLrF3H~mHHXj6J36T4Y3GwnSWp~YPGwainHdUXjfcG0QJiugCSdlSB31nQBJU2aKWXOoCls6qvtKw~DM7a81E9O2f7JHPc4a8CzJuEpJbT98yM5j2S~x-Vjz0-N3OG8cJSzBpLS9vpYRtZQlzNlmPEPXC3ti9vn~g9GL9tMQdlfeKNBdg__&Key-Pair-Id=K2XVTQ1784SQT0)

*Varianzas diferentes*

A raíz de los resultados podemos comprobar que p-value es prácticamente 0, por lo que podemos afirmar que las varianzas son diferentes, es decir rechazamos la hipótesis de que los conjuntos de datos x e y provienen de distribuciones con la misma varianza.

##### Test chi cuadrado de Pearson

En este caso estamos ante una prueba de hipótesis que compara la distribución observada de los datos con una distribución esperada de los datos. Es considerada una prueba no paramétrica que mide, como hemos visto, la discrepancia entre una distribución observada y otra teórica (bondad de ajuste), indicando en qué medida las diferencias existentes entre ambas, de haberlas, se deben al azar en el contraste de hipótesis. También se utiliza para probar la independencia entre variables mediante la presentación de los datos en tablas de contingencia.

---

*Supongamos por ejemplo que tenemos una clasificación de un grupo de personas según su opinión sobre una película documental y su nivel de estudios, y queremos contrastar la hipótesis de independencia del nivel de estudios con la opinión sobre el documental.*

| RECUENTO | | OPINIÓN | | | Total |
| :--- | :--- | :--- | :--- | :--- | :--- |
| | | Malo | Regular | bueno | |
| Nivel de Estudios | Bajo | 1 | 10 | 30 | 41 |
| | Medio | 40 | 80 | 60 | 180 |
| | alto | 25 | 12 | 0 | 37 |
| Total | | 66 | 102 | 90 | 258 |

---

![Ejecución de prueba Chi-cuadrado en consola de R](https://cdn.educalms.com/MkcwdktFdlhvNHglMkJNOVdhNDJmaFlnJTNEJTNE-1660647016.png?Expires=1789252338&Signature=FOcj3HXb87ipe3CKbS5F~5RmpYZTBkpuJZgYT9k7CGVXGpG7tGnA4QKihngwhfGyvTcG9oM69JCTU12nPxa1w8W7dbUqW6cFxSzZmn-8RJq4VNV0AssOBDoFAKtZOIiR2rubNNik8Sm65lHaoIXAbW1vZxc2ef0TvRJlGzHeSrNqVpPX2X2C0m~2Rh9QAAnHlIevMobIwjt0vxtpWJCEGATrlUZZYdC6yiOuqVYoa4kSlcDi4M15sHvcSdc63VZ0ucXhZYYJQifXW4gLE4dFRUdrz0Wte9XLw-zBFfkj3zgOCtKBSfo1CGPh5rMtEGkw~1KaAw9mNYKhtlMVy9-vcA__&Key-Pair-Id=K2XVTQ1784SQT0)

*Ejecución de prueba Chi-cuadrado en consola de R*

Suponiendo que la H0 establezca que las variables estudios y opinión son independientes, a raíz de los resultados arrojados por la prueba, obtenemos que

p-value < 0.05 por lo que rechazamos la H0 y por tanto la independencia de los datos

Además la ejecución de la prueba chi-cuadrado arroja más información sobre los datos, como las frecuencias esperadas así como los componentes del chi-cuadrado, para calcularlos podemos proceder como sigue:

![Cálculo de más datos](https://cdn.educalms.com/YVhBbkV0ekFYJTJGM2NMNk8wSHBZRkRnJTNEJTNE-1660647017.png?Expires=1789252338&Signature=TGr7QScdm8e6yDPvKSmM-W2jmOdNhpnkaEqhOjqDcVFjdnoUpLWCY5z3gjS9ODg3ojps6EEgziS-n2GEN3Sd4rXTf2KQ7txhtBkI2CzuQwmu0aAlX9kD2DHZfvEZKteyScMowZEous7j11NHipJqWm-8kBUUmXmAD4PCRV1WjZu0OEkfHOrnEXCn0FKs88h7ULa3pKyr4Ge67ZJX7EohV~8bv7ddQ0m1UhNtKv9gGzoFN-937g6l~7tJ8Jrj4k5wS3BEEea6lHTIvl6kEYjfFhO3U4LWVomU~S3rT9iaZJ1m~8uIFNkQDtKHs5kK2~LUlJG6fgTZnyBEPAge4DZmjA__&Key-Pair-Id=K2XVTQ1784SQT0)

*Cálculo de más datos*

# Recuerda

- El **proceso ETL** permite el tratamiento de la información desde los distintos orígenes de datos (CRM, ERP, Redes Sociales, etc.) para poder alimentar el DataWarehouse con información de calidad.
  - **Extracción**: Se obtienen los datos de las fuentes de origen y se cargan en el repositorio en tablas intermedias que contienen los datos sin la estructura final del modelo.
  - **Transformación**: En esta etapa se pretende adecuar la información. Se suele duplicar tablas que contienen la información correcta y la creación de nuevos campos o nuevas tablas con datos agregados y/o calculados.
  - **Carga de datos**: Una vez reorganizada la información, la cargamos en las tablas definitivas de nuestro(s) repositorio(s) de datos: datawarehouse y/o datamart.

- En la **etapa de limpieza**, tras recuperar los datos en bruto, debemos comprobar su calidad, eliminar los duplicados y cuando es posible, corregir los valores erróneos y completar los valores vacíos. El objetivo es conseguir datos limpios y de alta calidad que serán manipulados en la etapa siguiente del proceso, por lo que deberemos:
  - Depurar los valores
  - Corregir
  - Estandarizar
  - Relacionar
  - Consolidar

- Las herramientas ETL ahorran tiempo y dinero en el proceso de desarrollo y actualización de un datawarehouse, ya que reducen la cantidad de sistemas de conversión personalizados a desarrollar, para migrar o concentrar la información.

- Según Gartner, las **características** que debe tener una herramienta ETL son:
  - Conectividad / capacidades de adaptación
  - Capacidades de entrega de datos
  - Capacidades de transformación de datos
  - Capacidades de Metadatos y Modelado de Datos
  - Capacidades de diseño y entorno de desarrollo
  - Capacidades de gestión de datos
  - Adaptación a las diferentes plataformas hardware y sistemas operativos existentes
  - Operaciones y capacidades de administración
  - Arquitectura e integración
  - Capacidades SOA

- La **inferencia estadística** es el proceso de obtener conclusiones sobre una población a partir del análisis de una muestra. En la medida en que la muestra sea representativa de la población, los resultados podrán generalizarse.

- Uno de los **principales objetivos** de la inferencia estadística es estimar un determinado parámetro desconocido de la población bajo estudio.

- La **resolución de problemas** de inferencia con R, puede llevarse a cabo de forma sencilla calculando el estimador que corresponda mediante funciones que proporcionan en muchos casos la solución al problema de una forma más directa.

- Los **modelos de regresión** tratan de estimar o predecir el valor de una variable dependiente en función de valores conocidos de variables predictivas. Sin embargo, aun cuando los modelos de regresión traten de predecir los valores de una variable dependiente en términos de una o más variables independientes, de ninguna forma se establece una relación formal de causa-efecto; solo se trata de una relación matemática empírica.

- La **función en R** que nos permite obtener modelos de regresión lineal simple es **lm**, aunque también se puede utilizar esta función para el análisis de la varianza y el análisis de la covarianza.

- Una **hipótesis estadística** es una proposición o supuesto sobre los parámetros de una o más poblaciones.

- Para cualquier estudio basado en prueba de hipótesis debemos establecer dos hipótesis:
  - **H0**: Hipótesis nula que es la que se pretende rechazar o invalidar.
  - **H1**: Hipótesis alternativa es igualmente una afirmación acerca de la población de origen. Será la hipótesis que se acepta en caso de que se rechace H0 y viceversa.
