# Guía de Lectura: Predicción de Lluvia en Australia

## Resumen Ejecutivo

Este proyecto usa **Machine Learning** (aprendizaje automático) para predecir si lloverá mañana en Australia. Es como ensenarle a un niño a reconocer patrones del clima - cuando ve muchas nubes y alta humedad, aprende que eso usualmente significa lluvia.

---

## ¿Qué significa cada sección?

### Fase 1: Entendimiento del Negocio

**¿Por qué importa predecir la lluvia?**
- Las minas australianas pierden millones si no anticipan tormentas
- Los agricultores necesitan saber si regar o no sus cultivos
- El 65% de Australia no tiene ríos, entonces cada gota cuenta

**¿Qué es un KPI?**
Son "metas" que nos dice qué tan bien funciona nuestro modelo:
- **Recall ≥ 0.70**: Si va a llover, queremos detectarlo el 70% de las veces
- **Precisión ≥ 0.60**: No queremos decir "lloverá" cuando no lloverá

---

### Fase 2: Entendimiento de los Datos

**¿Qué son "datos"?**
Son como una hoja de cálculo con columnas (variables) y filas (registros). Cada fila es un día de información del clima.

**¿Qué son los "missing values" (valores faltantes)?**
Son datos que no tenemos. Por ejemplo, si no se midió la humedad en certainas días, aparece como "NaN" (vacío). Nuestro dataset tiene muchos de estos - hasta 48% en algunas columnas.

**¿Qué son los "outliers" (valores atípicos)?**
Son valores extremos que no son representativos. Por ejemplo, si llovió 371mm en un día (cuando lo normal es 0-2mm), eso es un outlier.

**¿Qué es la correlación?**
Es una medida de qué tan relacionadas están dos cosas:
- Correlación positiva (+1): cuando una aumenta, la otra también
- Correlación negativa (-1): cuando una aumenta, la otra disminuye
- Correlación cerca de 0: no tienen relación

**Ejemplo:** Humedad alta correlaciona con lluvia (+0.46). Presión baja también (-0.39).

---

### Fase 3: Preparación de los Datos

Antes de dar los datos a la computadora, los "limpiamos":
1. Eliminamos columnas con muchos datos faltantes (>40%)
2. Llenamos los datos faltantes con un valor "típico" (mediana)
3. Convertimos texto a números (Sí/No → 1/0)
4. Separamos: 80% para entrenar, 20% para probar

---

### Fase 4: Modelado

#### Modelos de Clasificación (predicen "Sí/No")

| Modelo | ¿Qué hace? | Como si fuera... |
|--------|------------|------------------|
| **Naive Bayes** | Calcula probabilidades | Un médico que pregunta síntomas y da diagnóstico |
| **Regresión Logística** | Encuentra una regla simple | Una fórmula matemática tipo "si X > 50, entonces llueve" |
| **Árbol de Decisión** | Preguntas secuenciales | Un juego de "20 preguntas" |
| **Random Forest** | Muchos árboles juntos | Un equipo de expertos votando |
| **K-Nearest Neighbors** | Busca vecinos similares | "Dime con quién andas y te diré quién eres" |

#### Métricas de evaluación

- **Accuracy**: De todas las predicciones, cuántas fueron correctas
- **Precision**: De las veces que dijimos "lloverá", cuántas realmente llovió
- **Recall**: De las veces que realmente llovió, cuántas predijimos
- **F1-Score**: Promedio entre precision y recall
- **AUC-ROC**: Qué tan bien separa las dos clases (como un examen)

#### Modelos de Regresión (predicen números)

Para predecir cuántos milímetros lloverá (RISK_MM):
- Regresión Lineal: línea recta que mejor se ajusta
- Ridge/Lasso: variaciones que evitan errores
- Random Forest: promedio de muchos árboles

#### Modelos No Supervisados (Clustering)

Estos no saben la respuesta correcta - descubren grupos solos:
- **K-Means**: Divide en k grupos
- **Agglomerative**: Agrupa lentamente
- **DBSCAN**: Encuentra grupos de densidad

---

## Resultados Clave

### Lo que aprendimos:
1. **Humedad a las 3pm** es el mejor predictor de lluvia mañana
2. **Presión atmosférica baja** significa más probabilidad de lluvia
3. Si llovió hoy, es más probable que llueva mañana
4. **Random Forest** es el mejor modelo (84% accuracy)

### Propuestas para el negocio:
1. Sistema de alertas cuando humedad > 70%
2. Integrar datos de presión en modelos de producción
3. Protocolo de preparación minera cuando hay lluvia predicted

---

## Glosario Simple

| Término | Significado Simple |
|---------|-------------------|
| Dataset | Archivo con datos (como Excel) |
| Feature/Variable | Una columna en los datos |
| Modelo | Fórmula que hace predicciones |
| Entrenar | Enseñar al modelo con datos |
| Test/Prueba | Verificar que el modelo funciona |
| Overfitting | Cuando el modelo memoriza en lugar de aprender |
| Underfitting | Cuando el modelo es muy simple |

---

*Este documento acompaña al notebook prueba2.ipynb para facilitar la comprensión a lectores no técnicos.*