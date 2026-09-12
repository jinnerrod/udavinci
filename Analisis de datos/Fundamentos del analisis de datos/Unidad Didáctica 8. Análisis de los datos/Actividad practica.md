# Ciencia de los datos y análisis de datos

## Objetivo general

Comprender los factores que rodean a la ciencia de los datos, así como al análisis de estos.

## Desarrollo de la actividad

Con ayuda de internet responda a las siguientes cuestiones que a continuación se plasman, cita y referencia a través de APA 7º Ed.

---

### 1. ¿En cuántas etapas se compone el proceso de la Data Science? Sintetiza y describe cada una de sus funciones y procesos.

El proceso de Data Science suele estructurarse en **cinco etapas principales**, que abarcan desde la captura del dato bruto hasta la comunicación de los resultados obtenidos:

1. **Obtención y captura de los datos**: En esta fase se identifican las fuentes de información (bases de datos internas, APIs, web scraping, sensores, redes sociales, etc.) y se extraen los datos necesarios para el análisis. Incluye también los procesos ETL (Extract, Transform, Load), la lectura e importación de datos y la integración desde múltiples orígenes.

2. **Limpieza y preparación de los datos**: También conocida como *data wrangling*, consiste en depurar los valores erróneos, corregir inconsistencias, tratar los valores ausentes (NA/NAN), eliminar duplicados, estandarizar formatos y consolidar la información. El objetivo es obtener datos de alta calidad que sirvan de base fiable para el análisis posterior.

3. **Análisis y modelado de los datos**: Se aplican técnicas de estadística descriptiva (media, mediana, varianza, cuartiles), inferencia estadística (contrastes de hipótesis, intervalos de confianza) y modelos predictivos (regresión lineal y múltiple, árboles de decisión, aprendizaje automático). El objetivo es descubrir patrones, relaciones y tendencias que aporten valor.

4. **Visualización de resultados**: Los hallazgos se representan mediante gráficos (barras, histogramas, diagramas de caja, sectores, nubes de puntos) y herramientas de Business Intelligence como Tableau, Spotfire o CARTO, que facilitan la interpretación y comunicación de los resultados a los responsables de la toma de decisiones.

5. **Comunicación y toma de decisiones**: La última etapa consiste en traducir los hallazgos en informes, cuadros de mando o recomendaciones accionables que permitan a la organización tomar decisiones informadas, ya sean reactivas (Business Intelligence) o proactivas (Business Analytics).

Adicionalmente, el ciclo puede repetirse iterativamente a medida que se incorporan nuevos datos o se refinan los modelos, dando lugar a un proceso continuo de mejora.

---

### 2. ¿Cómo se lleva a cabo el análisis de redes sociales en R? Muestra un ejemplo de ello.

El análisis de redes sociales en R se realiza principalmente mediante el paquete **igraph**, que permite crear, manipular y analizar grafos que representan las relaciones entre actores (nodos) y sus vínculos (aristas).

**Proceso general:**

1. **Instalación del paquete**: Se instala `igraph` desde el repositorio CRAN, ya que no viene por defecto en R.
2. **Construcción del grafo**: Se puede crear a partir de una matriz de adyacencia o de una lista de aristas, usando funciones como `graph.adjacency()` o `graph_from_data_frame()`.
3. **Visualización**: Se emplea `plot()` junto con distintos algoritmos de disposición (`layout.circle`, `layout.fruchterman.reingold`, etc.).
4. **Cálculo de métricas**: Se obtienen indicadores como el coeficiente de agrupamiento (`transitivity()`), el camino mínimo medio (`average.path.length()`), el grado de un nodo (`degree()`) y la distribución del grado (`degree.distribution()`).
5. **Detección de comunidades**: Se aplican algoritmos como Girvan-Newman o métodos modulares para identificar subgrupos dentro de la red.

**Ejemplo práctico:**

```r
# 1. Crear la matriz de adyacencia
matriz <- matrix(c(0,0,0,0,1,0,0,0,0,0,
                   0,0,0,0,0,1,0,0,0,0,
                   0,0,0,0,0,0,0,0,1,0,
                   0,0,0,0,0,0,1,0,0,1,
                   1,0,0,0,0,1,0,0,1,1,
                   0,1,0,0,1,0,1,0,0,1,
                   0,0,0,1,0,1,0,0,0,1,
                   0,0,0,0,0,0,0,0,0,1,
                   0,0,1,0,1,0,0,0,0,0,
                   0,0,0,1,1,1,1,1,0,0),
                 nrow=10, ncol=10)

# 2. Crear el grafo no dirigido a partir de la matriz
library(igraph)
grafo <- graph.adjacency(matriz, mode="undirected")

# 3. Visualizar el grafo
plot(grafo)
plot(grafo, layout=layout.circle)

# 4. Calcular métricas
transitivity(grafo, type="global")        # Coeficiente de agrupamiento global
average.path.length(grafo, directed=FALSE) # Camino mínimo medio
degree(grafo, 10)                          # Grado del nodo 10
degree.distribution(grafo)                 # Distribución del grado