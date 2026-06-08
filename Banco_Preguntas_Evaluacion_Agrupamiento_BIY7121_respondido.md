# DuocUC
## Escuela de Informática y Telecomunicaciones (EIT) - Sede San Joaquín
### BIY7121 - Minería de Datos

# Banco de Preguntas y Respuestas
## Evaluación de Modelos de Agrupamiento

**20 preguntas de desarrollo - Niveles 3 y 4 de la Taxonomía de Bloom**

**Profesor:** Marcelo Godoy Rojas

**Estudiante:** Benjamin Herrera

**Marco metodológico transversal:** CRISP-DM (fase Evaluación)

---

## Preguntas y Respuestas

### P1. Explique por qué los modelos de agrupamiento son más difíciles de evaluar que los modelos de clasificación o de regresión.

**Respuesta:** Los modelos de agrupamiento son más difíciles de evaluar porque son **no supervisados**: no existe una "respuesta correcta" o etiqueta verdadera contra la cual comparar las predicciones. En clasificación y regresión tenemos valores reales conocidos (`y_test`) y podemos calcular métricas como accuracy, MAE o RMSE comparando directamente predicción vs realidad. En clustering, el algoritmo inventa los grupos por sí solo a partir de la estructura de los datos, por lo que necesitamos métricas especiales (intrínsecas) que evalúan la calidad del agrupamiento mirando solo la forma de los grupos —cohesión y separación— sin contar con una verdad absoluta.

---

### P2. Al aplicar análisis de conglomerados sobre un conjunto de datos, ¿qué dos aspectos generales se evalúan?

**Respuesta:** Se evalúan dos aspectos generales:

1. **Cohesión (o compacidad):** Mide qué tan cerca están los puntos dentro de un mismo cluster entre sí. Una alta cohesión indica que los puntos de un grupo son similares entre sí.
2. **Separación (o aislamiento):** Mide qué tan distantes están los diferentes clusters entre sí. Una alta separación indica que los grupos están bien diferenciados unos de otros.

Ambos aspectos se combinan en métricas como Silhouette, que evalúa simultáneamente cohesión (distancia intra-cluster) y separación (distancia inter-cluster).

---

### P3. Describa la tarea de evaluación de la tendencia a la agrupación y nombre una prueba estadística que permita realizarla.

**Respuesta:** La evaluación de la **tendencia a la agrupación** (o clustering tendency) determina si un conjunto de datos contiene estructura no aleatoria que justifique aplicar algoritmos de clustering. Responde a la pregunta: "¿Vale la pena agrupar estos datos?" Si los datos son esencialmente aleatorios (uniformes), cualquier grupo que encontremos será artificial y sin sentido.

La **estadística de Hopkins** es la prueba estadística que permite realizar esta evaluación. Compara la distribución de distancias entre puntos reales contra puntos sintéticos generados uniformemente al azar. Su valor oscila entre 0 y 1: valores cercanos a 0.5 indican uniformidad (datos aleatorios), mientras que valores cercanos a 1 indican datos fuertemente agrupados.

En el notebook aplicamos Hopkins a los datos sintéticos de clientes bancarios y obtuvimos **H ≈ 0.92**, confirmando que los datos tenían estructura agrupada y valía la pena aplicar clustering.

---

### P4. ¿Qué intenta medir la estadística de Hopkins respecto a la distribución de los datos?

**Respuesta:** La estadística de Hopkins intenta medir si los datos se distribuyen de manera **uniforme y aleatoria** o si, por el contrario, presentan una **estructura agrupada significativa**. La prueba funciona así:

- Toma una muestra de puntos reales y calcula la suma de distancias (`w`) al vecino más cercano dentro de los datos reales.
- Genera puntos sintéticos distribuidos uniformemente y calcula la suma de distancias (`u`) de esos puntos sintéticos a sus vecinos reales más cercanos.
- El estadístico se calcula como: `H = u / (u + w)`

Si `H ≈ 0.5`, los puntos reales se distribuyen similar a puntos aleatorios (no hay estructura). Si `H ≈ 1.0`, los puntos reales están mucho más cerca entre sí que los puntos aleatorios, indicando estructura agrupada.

---

### P5. Explique en qué se basa el método de Elbow (codo) para determinar el número de clusters.

**Respuesta:** El método de Elbow se basa en el comportamiento de la **inercia o WCSS** (Within-Cluster Sum of Squares), que es la suma de las distancias al cuadrado de cada punto al centro de su cluster. A medida que aumentamos el número de clusters K, la inercia siempre disminuye porque los grupos son más pequeños y compactos. Sin embargo, a partir de cierto punto, agregar más clusters produce una mejora marginal cada vez menor.

El "codo" es el punto de inflexión donde la curva de inercia deja de caer abruptamente y se aplana. Ese punto representa el K óptimo: antes del codo cada cluster nuevo reduce significativamente la inercia (captura estructura real), después del codo los clusters adicionales solo sobreajustan el ruido.

En el notebook, el codo se identificó claramente en **K=4**, coincidiendo con los 4 segmentos reales que diseñamos en los datos sintéticos.

---

### P6. ¿Por qué es relevante determinar el número correcto de clusters? Mencione al menos dos razones.

**Respuesta:** Determinar el número correcto de clusters es relevante por al menos dos razones:

1. **Calidad de la segmentación:** Si elegimos muy pocos clusters (subsegmentación), mezclamos grupos distintos que deberían estar separados, perdiendo información valiosa y obteniendo perfiles de cliente poco diferenciados. Si elegimos demasiados clusters (sobresegmentación), dividimos grupos naturales en fragmentos artificiales, generando ruido y grupos sin sentido de negocio.

2. **Interpretabilidad y acción comercial:** En el contexto de negocio, cada cluster debe traducirse en un perfil de cliente comprensible y accionable (ej: "clientes jóvenes con créditos pequeños" o "empresas con créditos grandes y larga duración"). Un número incorrecto de clusters dificulta esta interpretación y lleva a estrategias comerciales ineficaces.

Además, un K incorrecto puede afectar la estabilidad del modelo (resultados inconsistentes entre ejecuciones) y aumentar el riesgo de overfitting.

---

### P7. ¿Qué condición debe cumplirse para aplicar validación extrínseca y por qué se la considera un método supervisado?

**Respuesta:** Para aplicar **validación extrínseca** se debe contar con **etiquetas verdaderas o de referencia** (ground truth), es decir, conocer de antemano la pertenencia real de cada instancia a un grupo. En el notebook, esto corresponde a la variable `y_real` que generamos con `make_blobs` y mantuvimos "escondida" durante el entrenamiento.

Se considera un método **supervisado** porque utiliza la información de las etiquetas verdaderas para evaluar qué tan bien el modelo no supervisado (clustering) recuperó la estructura real de los datos. Es decir, usamos conocimiento externo (las etiquetas) para juzgar la calidad del agrupamiento, de manera similar a como usamos `y_test` en clasificación supervisada.

En la práctica empresarial, estas etiquetas pueden provenir de segmentaciones elaboradas por expertos del negocio o de campañas anteriores.

---

### P8. Dado un conjunto S de clusters generado por un algoritmo y un conjunto P de etiquetas verdaderas, ¿qué se busca medir entre ambos y cuándo se considera buena la agrupación?

**Respuesta:** Se busca medir el **grado de coincidencia** entre la partición generada por el algoritmo (S) y la partición real (P). Específicamente, se evalúa qué tan bien el clustering no supervisado logró recuperar la estructura subyacente real de los datos.

La agrupación se considera buena cuando la coincidencia entre S y P es **alta**, idealmente 1.0 (coincidencia perfecta). Esto significa que los grupos encontrados por el algoritmo corresponden exactamente a los grupos reales, aunque las etiquetas numéricas puedan no coincidir (por ejemplo, el cluster 0 del algoritmo puede corresponder al grupo 3 real, pero la coincidencia en la asignación es total).

En el notebook, con K=4 se obtuvo ARI = 1.0 y Fowlkes-Mallows = 1.0, indicando recuperación perfecta de los 4 segmentos reales.

---

### P9. Explique qué expresa el Índice de Rand Ajustado (ARI), su rango de valores y cómo se interpreta.

**Respuesta:** El **Índice de Rand Ajustado (ARI)** expresa el grado de similitud entre dos particiones (la generada por el algoritmo y la real), **ajustando por el azar**. Esto significa que corrige el problema del Índice de Rand clásico, que puede dar valores altos simplemente por casualidad cuando hay muchos clusters o clases desbalanceadas.

- **Rango:** de -1 a 1.
- **Interpretación:**
  - **ARI = 1.0:** Coincidencia perfecta entre las dos particiones.
  - **ARI = 0.0:** La coincidencia es equivalente a lo esperado por azar.
  - **ARI < 0.0:** La coincidencia es menor a lo esperado por azar (muy raro en la práctica).

En el notebook, obtuvimos ARI = 1.0 para K=4, confirmando que el clustering recuperó perfectamente los segmentos reales de clientes bancarios.

---

### P10. En la puntuación de Fowlkes-Mallows, ¿sobre qué estructura se construye el cálculo y qué representan TP, FP y FN?

**Respuesta:** La puntuación de **Fowlkes-Mallows (FM)** se construye sobre una **matriz de confusión** que compara pares de puntos entre la partición del algoritmo (S) y la partición real (P). Para cada par de puntos posibles, se clasifica si pertenecen o no al mismo cluster en cada partición:

- **TP (Verdaderos Positivos):** Pares de puntos que están **en el mismo cluster** en ambas particiones (S y P). Es decir, el algoritmo y la realidad coinciden en agruparlos juntos.
- **FP (Falsos Positivos):** Pares de puntos que están **en el mismo cluster en S** pero **en diferentes clusters en P**. El algoritmo los unió erróneamente.
- **FN (Falsos Negativos):** Pares de puntos que están **en diferentes clusters en S** pero **en el mismo cluster en P**. El algoritmo los separó erróneamente.

FM se calcula como la media geométrica de precisión (TP/(TP+FP)) y recall (TP/(TP+FN)):
`FM = sqrt( (TP/(TP+FP)) * (TP/(TP+FN)) )`

---

### P11. Relacione los términos TPR y PPV con los conceptos de recall y precisión en la puntuación de Fowlkes-Mallows.

**Respuesta:** En la puntuación de Fowlkes-Mallows:

- **TPR (True Positive Rate) = Recall = TP / (TP + FN):** Mide la proporción de pares de puntos que realmente debían estar juntos (según la partición real) y que efectivamente el algoritmo agrupó juntos. Un TPR alto indica que el algoritmo no está separando puntos que deberían estar unidos.

- **PPV (Positive Predictive Value) = Precisión = TP / (TP + FP):** Mide la proporción de pares de puntos que el algoritmo agrupó juntos y que efectivamente debían estar juntos (según la partición real). Un PPV alto indica que el algoritmo no está uniendo puntos que deberían estar separados.

FM = √(PPV × TPR) = √(Precisión × Recall), siendo la media geométrica de ambas métricas. Esto asegura que un buen puntaje FM requiere tanto alta precisión como alto recall, penalizando si una de las dos es baja.

---

### P12. ¿Por qué la validación intrínseca es adecuada cuando se trabaja con datos no etiquetados y por qué se la considera no supervisada?

**Respuesta:** La **validación intrínseca** es adecuada para datos no etiquetados porque **no requiere conocer las etiquetas verdaderas** para evaluar la calidad del agrupamiento. En su lugar, utiliza exclusivamente la información contenida en los datos mismos y la asignación de clusters producida por el algoritmo. Evalúa qué tan buenos son los grupos basándose en principios generales como:

- Los puntos dentro de un mismo cluster deben ser similares entre sí (cohesión).
- Los puntos de diferentes clusters deben ser distintos entre sí (separación).

Se considera **no supervisada** porque no utiliza ninguna información externa (etiquetas, ground truth) para realizar la evaluación. Esto la hace aplicable en escenarios reales donde no se dispone de una segmentación de referencia, que es el caso más común en la práctica empresarial (por ejemplo, cuando una empresa como Cencosud quiere segmentar clientes sin tener segmentos predefinidos).

---

### P13. Nombre y describa los dos tipos de métricas en torno a los cuales gira la validación interna del clustering.

**Respuesta:** La validación interna del clustering gira en torno a dos tipos de métricas:

1. **Métricas de cohesión (o compacidad):** Miden qué tan cercanos están los puntos dentro de un mismo cluster. Una alta cohesión indica que los miembros del cluster son homogéneos y están cerca unos de otros. La métrica más común es la **inercia o WCSS** (suma de distancias al cuadrado de cada punto al centroide de su cluster), donde valores más bajos indican mayor cohesión.

2. **Métricas de separación (o aislamiento):** Miden qué tan distantes están los centros de los clusters entre sí o qué tan diferenciados están los grupos. Una alta separación indica que los clusters están bien distanciados y no se superponen.

Métricas como **Silhouette** combinan ambos aspectos: evalúa simultáneamente la cohesión (distancia intra-cluster, `a`) y la separación (distancia inter-cluster, `b`) para cada punto. El **índice de Calinski-Harabaz** también combina ambos, expresando la relación entre la dispersión inter-cluster e intra-cluster.

---

### P14. Explique qué describe el índice de Silhouette respecto a un punto de datos.

**Respuesta:** El **índice de Silhouette** describe qué tan bien se ajusta un punto de datos particular al cluster al que fue asignado, en comparación con otros clusters. Para un punto `i`:

- Mide la **distancia promedio** del punto `i` a todos los demás puntos de **su mismo cluster** (llamada `a`, cohesión intra-cluster).
- Mide la **distancia promedio** del punto `i` a todos los puntos del **cluster vecino más cercano** (el segundo mejor cluster para ese punto, llamada `b`, separación inter-cluster).
- Calcula: `s(i) = (b - a) / max(a, b)`

Si `a` es pequeña (punto cerca de su cluster) y `b` es grande (punto lejos del otro cluster), `s(i)` se acerca a +1 (buena asignación).

En el notebook, el gráfico de Silhouette mostró que la gran mayoría de los 600 clientes tenía valores de Silhouette cercanos a +1, con todas las franjas (clusters) extendiéndose a la derecha del promedio, indicando asignaciones de alta calidad.

---

### P15. Indique el rango del índice de Silhouette e interprete los valores cercanos a -1 y cercanos a +1.

**Respuesta:** El índice de Silhouette tiene un rango de **-1 a +1**:

- **Valores cercanos a +1:** Indican que el punto está **bien clasificado**. La distancia promedio a los puntos de su propio cluster (`a`) es mucho menor que la distancia promedio al cluster vecino más cercano (`b`). El punto está claramente en el cluster correcto, con alta cohesión y alta separación. Es el resultado deseado.

- **Valores cercanos a 0:** Indican que el punto está **en el límite** entre dos clusters. Las distancias a su propio cluster y al vecino más cercano son similares. No está claro a qué cluster debería pertenecer.

- **Valores cercanos a -1:** Indican que el punto está **mal clasificado**. El punto está más cerca del cluster vecino que de su propio cluster. Esto sugiere que el punto debería haber sido asignado a otro cluster.

En el notebook, el Silhouette promedio para K=4 fue de **0.7742**, con la mayoría de los puntos mostrando valores altos y sin valores negativos significativos, indicando una segmentación de alta calidad.

---

### P16. En la fórmula del índice de Silhouette, ¿qué representan los términos a y b?

**Respuesta:** En la fórmula del índice de Silhouette para un punto `i`:

`s(i) = (b - a) / max(a, b)`

- **`a` (cohesión intra-cluster):** Es la **distancia promedio** del punto `i` a **todos los demás puntos que pertenecen al mismo cluster**. Mide qué tan cerca está `i` de los otros miembros de su grupo. Un valor pequeño de `a` indica que el punto está bien integrado y cerca del centro de su cluster (alta cohesión).

- **`b` (separación inter-cluster):** Es la **distancia promedio** del punto `i` a **todos los puntos del cluster vecino más cercano** (aquel cluster, distinto al suyo, que minimiza esta distancia promedio). Mide qué tan lejos está `i` del cluster más cercano que no es el suyo. Un valor grande de `b` indica que el punto está lejos de otros clusters (alta separación).

Cuando `b > a`, el Silhouette es positivo y cercano a +1 (buena clasificación). Cuando `a > b`, el Silhouette es negativo (mala clasificación).

---

### P17. Explique qué relación expresa el índice de Calinski-Harabaz y por qué se desea un valor alto.

**Respuesta:** El **índice de Calinski-Harabaz (CH)**, también conocido como **índice de la relación de varianza (VRC)**, expresa la **relación entre la dispersión inter-cluster y la dispersión intra-cluster**, normalizada por los grados de libertad. Su fórmula es:

`CH = (SS_B / (k-1)) / (SS_W / (n-k))`

Donde:
- `SS_B` = suma de cuadrados **entre clusters** (dispersión inter-cluster, ponderada por tamaño de cluster).
- `SS_W` = suma de cuadrados **dentro de los clusters** (dispersión intra-cluster).
- `k` = número de clusters.
- `n` = número total de puntos.

Se desea un **valor alto** de CH porque indica que:
- Los clusters están **bien separados entre sí** (SS_B alto).
- Los puntos dentro de cada cluster están **muy cerca de su centroide** (SS_W bajo).

En el notebook, CH alcanzó su máximo en K=4 con un valor de **5894.5**, confirmando que 4 clusters producían la mejor relación separación/cohesión.

---

### P18. Una empresa de retail chilena (por ejemplo, Cencosud) desea segmentar clientes y no dispone de etiquetas previas de los segmentos. ¿Qué tipo de validación correspondería aplicar y por qué?

**Respuesta:** Correspondería aplicar **validación intrínseca** (no supervisada), porque:

1. **No hay etiquetas verdaderas:** Al no disponer de una segmentación previa de referencia, no es posible usar métricas extrínsecas como ARI o Fowlkes-Mallows que requieren comparar contra la "verdad".

2. **Solo se dispone de los datos:** La validación intrínseca evalúa la calidad del clustering usando exclusivamente los datos y las asignaciones de clusters generadas por el algoritmo, midiendo cohesión y separación.

En este caso concreto, Cencosud podría:
- Aplicar la **estadística de Hopkins** para verificar que los datos de clientes tienen estructura agrupada.
- Usar el **método de Elbow** para determinar el número óptimo de segmentos.
- Evaluar la calidad con **Silhouette** y **Calinski-Harabaz** para confirmar que los segmentos son compactos y están bien separados.
- Finalmente, perfilar los clusters resultantes (edad, monto de compra, frecuencia, etc.) para darles sentido de negocio y diseñar campañas específicas para cada segmento.

---

### P19. Si un equipo de minería de datos cuenta con una segmentación de referencia construida por expertos del negocio, ¿qué métrica permitiría comparar la agrupación del modelo con dicha referencia? Justifique.

**Respuesta:** Las métricas más apropiadas serían el **Índice de Rand Ajustado (ARI)** y la **puntuación de Fowlkes-Mallows (FM)**, ambas de validación extrínseca.

**Justificación:**
- **ARI** mide el grado de coincidencia entre la partición del modelo y la partición de referencia, **ajustando por el azar**. Esto es crucial porque el Índice de Rand clásico puede sobreestimar la coincidencia cuando hay muchos clusters. ARI = 1.0 indica coincidencia perfecta, ARI ≈ 0 indica que la coincidencia es aleatoria.

- **Fowlkes-Mallows** complementa a ARI al basarse en la media geométrica de precisión y recall sobre pares de puntos, ofreciendo una visión diferente del mismo problema.

Ambas métricas permiten cuantificar objetivamente si el algoritmo de clustering reproduce fielmente la segmentación experta. Si los valores son altos (cercanos a 1.0), significa que el modelo capturó automáticamente los mismos patrones que los expertos identificaron manualmente, validando el uso del modelo como reemplazo o complemento del trabajo experto.

---

### P20. Dentro de CRISP-DM, ¿en qué fase se sitúa la evaluación de modelos de agrupamiento y qué decisión apoya el uso de métricas como Silhouette o el método de Elbow?

**Respuesta:** Dentro de CRISP-DM, la evaluación de modelos de agrupamiento se sitúa en la **Fase 5: Evaluación** (Evaluation). Esta fase tiene como objetivo determinar si el modelo construido cumple con los objetivos de negocio definidos en la Fase 1 (Entendimiento del Negocio) y si cumple con los criterios de calidad suficientes para avanzar a la Fase 6 (Despliegue).

El uso de métricas como **Silhouette** o el **método de Elbow** apoya la decisión de:

1. **Validar la calidad técnica del modelo:** Silhouette confirma que los clusters son compactos y están bien separados. Elbow ayuda a justificar que el número de clusters elegido (K) es el óptimo, ni muy pocos (subsegmentación) ni demasiados (sobresegmentación).

2. **Decidir si el modelo avanza a Despliegue:** Si las métricas de validación intrínseca (y extrínseca, si hay etiquetas) son satisfactorias, y además los clusters tienen sentido e interpretabilidad para el negocio (perfiles de cliente accionables), el modelo está listo para ser puesto en producción. Si las métricas son deficientes, se retrocede a fases anteriores (Preparación de Datos o Modelado) para mejorar el modelo.

En el notebook, el flujo completo siguió este proceso: Hopkins confirmó estructura, Elbow sugirió K=4, Silhouette y CH validaron la calidad, y finalmente se perfilaron los clusters para darles significado de negocio.

---

*Fuente: Elaboración propia a partir de la presentación 3.4.1 y el notebook `Evaluacion_Modelos_Agrupamiento_BIY7121.ipynb`.*
