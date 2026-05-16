

## Evaluación Parcial 2 Nombre
## Sigla Nombre Asignatura Tiempo Asignado % Ponderación
BIY7121 Minería de Datos 3 semanas 35%
-   Situación evaluativa
## Ejecución
práctica
## X
Entrega de
encargo
## Prueba
escrita
## Presentación
-   Agente evaluativo
## X Heteroevaluación Coevaluación Autoevaluación



-    Tabla de Especificaciones
## Resultado
de
## Aprendizaje
Indicador de Logro (IL) Indicador de Evaluación (IE)
## Ponderación
Indicador de
## Evaluación
## Ponderación
## Indicador
## Logro
RA2  Analizar
los        datos
mediante   la
aplicación
de   modelos
estadísticos,
utilizando  el
lenguaje
## Python.
IL     2.1          Realiza     limpieza     y
transformación     de     los     datos,
utilizando            lenguaje            de
programación                       Python,
procesándolos de acuerdo con sus
características.
Realiza  un  completo  manejo  de  valores  atípicos  en  los
datos siguiendo las buenas prácticas de la industria.
## 15%
## 30%
Realiza la transformación de variables de acuerdo con la
implementación  de  modelos  matemáticos  siguiendo
buenas prácticas de la industria.
## 15%
IL 2.2  Aplica modelos matemáticos
sobre      los      datos,      utilizando
bibliotecas      especializadas      de
Python,  para  obtener  información
significativa del negocio.
Aplica modelos de aprendizaje supervisado en tareas de
regresión y clasificación de acuerdo con la naturaleza de
los datos y las necesidades de la organización.
## 20%
## 40%
Aplica modelos de aprendizaje no supervisado en tareas
de  segmentación  de  acuerdo  con  la  naturaleza  de  los
datos y las necesidades de la organización.
## 20%
IL   2.3   Interpreta   los   resultados
obtenidos    del    trabajo    con    los
datos,     de     acuerdo     con     las
necesidades  y  características  del
negocio.
Interpreta  los  resultados  obtenidos  del  trabajo  con  los
datos, de acuerdo con las necesidades y características
del negocio.
## 15%
## 30%
IL 2.4 Analiza las  características de
los datos y del negocio a través de
la           identificando           insight,
permitiendo    entregar    valor    y
apoyar la toma de decisiones.
Analiza  las  características  de  los  datos  y  del  negocio
identificando insights de alto impacto.
## 10%
Propone soluciones e ideas prácticas basándose en los
Insight para apoyar la Toma de Decisiones
## 5%
## Total

## 100%

Comentado [1]: Indicador de Evaluación (IE)
Identifica existencia de valores atípicos y valores perdidos,
proponiendo rutina de limpieza con mayor precisión en los
modelos y menor sesgo en el análisis.

-   Instrucciones para el/la estudiante
Esta es una evaluación que corresponde a una Prueba Parcial de Encargo sin presentación y tiene un 35% de ponderación sobre la not  a final de
la asignatura.
El tiempo para desarrollar esta evaluación es de 3 semanas y se realiza en parejas de trabajo fuera de la sala de clases.
La evaluación consiste en realizar un informe técnico en formato Jupyter Notebook que contenga las cuatro primeras fases de la metodología
CRISP-DM aplicada a los datos del clima en Australia.
## Instrucciones:
## ●R
ealizar un informe técnico que contenga las cuatro primeras fases de la metodología CRISP-DM:
●En la etapa de Business Understanding investigar del negocio, identificando objetivos clave y posibles KPI que podrían ser relevantes
para la compañía.
●En  la  etapa  de  Data  Understanding  analizar  los  diferentes  tipos  de  datos,  calculando  estadísticos,  métricas  relevantes  que  permitan
resumir la distribución de los datos.
●Reconocer características o columnas claves dentro de los datos para definir los objetivos generales del análisis.
●Identificar existencia de valores atípicos y valores perdidos, proponiendo rutinas de limpieza que se pueden abordar para generar mayor
precisión en los modelos  y menor sesgo en el análisis.
●Aplicar  matriz  de  correlación,  identificando  qué  correlaciones  tienen  las  características,  reconociendo  las  correlaciones  negativas  y
positivas, e interpretando qué valor generan en el proceso los valores obtenidos.
●En  la  fase  de  Data  Preparation  realizar  las  transformaciones  necesarias  a  los  datos  para  evitar  inconsistencias  y  problemas  en
la
g
eneralización del modelo como overfitting o underfitting.
●Preparar los datos con las técnicas revisadas en clases, con el objetivo que se puedan entrenar y testear en modelos tanto supervisados
como no supervisados.
●Implementar más de 3 modelos supervisados que incluya tareas de regresión y de clasificación definiendo un target objetivo.
●Implementar  más  de  3  modelos  no  supervisados  que  incluya  tareas  de  segmentación  infiriendo  patrones  de  comportamiento  en  los
datos.
●Analizar los resultados obtenidos, proponiendo insights relevantes que permitan apoyar la toma de decisiones.
## L
os estudiantes deben comprender aspectos generales del negocio y de los datos.
Considerar uso de bloques de códigos debidamente comentados y realizar análisis de la información en bloques Markdown.

Caso de Estudio
Australia es uno de los países con mayor extensión del mundo y el continente más seco y llano del planeta. Aproximadamente la mitad occidental de Australia
es una extensa meseta árida. El clima predominante es el desértico y semiárido (se estima que un 40% del territorio lo forman dunas de arena), si bien el norte
del país cuenta con un clima tropical. Las tierras más fértiles y el clima templado con cuatro estaciones se concentran en el sureste y suroeste. La principal
cordillera del país, la Gran Cordillera Divisoria (The Great Dividing Range), se extiende a lo largo de más de 3.500 km entre los estados de Queensland y Victoria.
El pico más alto es el Monte Kosciuszko con 2.228 metros. Los ríos más caudalosos nacen en la Gran Cordillera Divisoria y, en su gran mayoría, fluyen hacia el
este y desembocan en el océano Pacífico. Por su longitud y caudal destacan dos ríos: el Murray y el Darling. Australia se divide en seis estados (New South
Wales, Victoria, Queensland, South Australia, Western Australia y Tasmania) y dos territorios continentales (Northern Territory y Australian Capital Territory
(ACT)). La ciudad de Sídney, con sus 5,73 millones de habitantes, es la más poblada de Australia y es la capital del estado de Nueva Gales del Sur. Es a su vez
un  importante  centro  industrial  y  puerto  comercial  de  primera  magnitud.  La  ciudad  es  muy  extensa,  con  un  radio  aproximado  de  40  km,  incluyendo  los
suburbios. Otras ciudades importantes son Melbourne (5,19 millones), Brisbane (2,56 millones), Perth (2,38 millones) y Adelaide (1,41 millones). Casi el 90%
de la población se concentra en las zonas urbanas. De sus más de 25 millones de habitantes, un 65,5% se encuentra en edad de trabajar (de 15 a 64 años),
mientras que aquellos con más de 65 años y con menos de 15 años suponen el 15,7% y el 18,8% de la población respectivamente. La superficie del país es de
aproximadamente 7.741.220 km², quince veces superior a España, representando el 5% del total de la superficie terrestre emergida. Es el sexto país del mundo
en extensión. La distancia máxima del continente australiano de este a oeste es de 4.100 km y de norte a sur, de 3.200 km. La longitud costera es de 36.735
km. Su vasta extensión inevitablemente condiciona el tráfico de personas, mercancías y servicios. Australia es, además, el más llano de los continentes, con
una altitud media de menos de 300 metros, siendo The Great Dividing Range la única gran cordillera de importancia. Casi dos tercios del territorio carecen de
corrientes de agua hacia el mar. La principal cuenca fluvial es la del Murray-Darling con 1.061.469 km², que drena las vertientes sur occidentales de la Gran
Cordillera.  El  país  cuenta  con  una  gran  diversidad  climática  que  abarca  desde  el  clima  tropical  en  el  norte,  que  representa  el  39%  del  territorio,  al  clima
templado-continental en el sudeste y Tasmania. En las zonas del centro predomina el clima desértico. La zona más fértil es la franja costera entre Sídney y
Adelaida,  con  lluvias  moderadas  todo  el  año.  Australia  está  menos  sujeta  a  climas  extremos  que  otros  países  en  su  misma  latitud,  debido  a  los  efectos
moderadores  de  los  mares  y  océanos  circundantes  y  a  la  ausencia  de  grandes  montañas.  Las  estaciones  varían  con  la  latitud  pero  aproximadamente  son:
primavera (septiembre y octubre), verano (noviembre-marzo), otoño (abril y mayo) e invierno (junio-agosto). Las temperaturas medias oscilan entre los 27°C

en  la  zona  norte  y  los  13°C  en  las  zonas  más  al  sur,  alcanzando  las  máximas  en  la  zona  centro  (38°C).  Por  tanto,  las  principales  características  climáticas
australianas son inviernos suaves y veranos cálidos, así como abundante sol y poca humedad. Las precipitaciones son muy escasas en el interior y aumentan
en las zonas costeras, de modo que las zonas mejor regadas son los litorales norte, este, sudeste y sudoeste. En el norte del país hay dos estaciones, seca en
invierno  y  húmeda  en  verano  con  la  irrupción  de  lluvias  monzónicas.  Australia  es,  después  de  la  Antártida,  el  continente  más  seco.  Aun  así,  y  debido  a  su
diversidad climática, se dan todo tipo de fenómenos naturales extremos como sequías, inundaciones, ciclones tropicales, vendavales, incendios forestales (en
lo que se conoce como bush o monte en Australia) y, ocasionalmente, tornados. En cuanto a recursos naturales y minería, Australia es uno de los principales
productores y 3 exportadores de minerales y productos energéticos a nivel mundial. El sector minero representa alrededor del 10% del PIB con un valor de
148.000 millones de AUD. En 2018-19 presentó una tasa de crecimiento del 6%. El valor de las exportaciones totales de productos mineros y energéticos se
espera que alcance los 299.000 millones AUD en el periodo 2019-20. Las exportaciones de mineral de hierro alcanzaron durante 2018-19 los 100.000 millones
de AUD. Australia está entre los cinco principales países exportadores del mundo de bauxita, alúmina, mineral de hierro, zinc, carbón y de gas natural licuado
## (GNL).
Texto extraído del sitio https://www.icex.es/ ministerio de industria comercio y turismo de España.
Se dispone de un set de datos de observaciones meteorológicas diarias de múltiples ubicaciones en Australia, obtenidas de la Oficina de Meteorología de la
Commonwealth de Australia y procesadas para crear este conjunto de datos de muestra, los datos se han procesado para proporcionar una variable objetivo
RainTomorrow(si hay lluvia al día siguiente - No / Sí) y una variable de riesgo RISK_MM(cuánta lluvia registrada en milímetros), esta información se ha dejado
disponible para que usted la explore y busque información que sea relevante para demostrar su aprendizaje de Minería de datos.
## E
l dataset posee los siguientes campos:
## Columna Descripción
Fecha Fecha de la observación
Ubicacion Ubicación de la estación meteorológica
MinTemp Temperatura mínima en grados Celsius
MaxTemp Temperatura máxima en grados Celsius
Lluvia Cantidad de lluvia registrada ese día en mm.
Evaporacion Evaporación (mm) en 24 horas

Sol Número de horas de sol brillante en el día
DirRafaga Dirección de la ráfaga de viento más fuerte en 24 horas.
VelRafaga Velocidad (km/hr) de la ráfaga de viento más fuerte en 24 horas.
Dir9am Dirección del viento a las 9am
Dir3pm Dirección del viento a las 3pm
Vel9am Velocidad (km/hr) del viento a las 9am
Vel3pm Velocidad (km/hr) del viento a las 3pm
Hum9am Porcentaje de humedad a las 9am
Hum3pm Porcentaje de humedad a las 3pm
Pres9am Presión atmosférica (hpa) a nivel del mar a las 9am
Pre3pm Presión atmosférica (hpa) a nivel del mar a las 3pm
## Nub9am
Fracción del cielo cubierto por nubes a las 9am. Se mide en "octavos", de
manera que un valor 0 indica cielo totalmente despejado y 8, cielo totalmente
cubierto.
## Nub3pm
Fracción del cielo cubierto por nubes a las 3pm. Se mide en "octavos", de
manera que un valor 0 indica cielo totalmente despejado y 8, cielo totalmente
cubierto.
Temp9am Temperatura en grados Celsius a las 9am
Temp3pm Temperatura en grados Celsius a las 3pm
LluviaHoy
Variable indicadora que toma el valor 1 si la precipitación es en mm. en las
últimas 24 hrs. excede 1 mm. y 0 si no.
RISK_MM La cantidad de lluvia. Una especie de medida del "riesgo".
LluviaMan Variable indicadora que toma el valor 1 si al día siguiente llovió y 0 si no.



-    Pauta de Evaluación

## Categoría
## %
logro
Descripción niveles de logro
Muy buen
desempeño
## 100%
Demuestra un desempeño destacado, evidenciando el logro de todos los aspectos evaluados en el
indicador.
Buen desempeño
80% Demuestra un alto desempeño del indicador, presentando pequeñas omisiones, dificultades y/o errores.
## Desempeño
aceptable
## 60%
Demuestra un desempeño competente, evidenciando el logro de los elementos básicos del indicador, pero
con omisiones, dificultades o errores.
## Desempeño
incipiente
## 30%
Presenta  importantes  omisiones,  dificultades  o  errores  en  el  desempeño,  que  no  permiten  evidenciar  los
elementos básicos del logro del indicador, por lo que no puede ser considerado competente.
Desempeño no
logrado
0% Presenta ausencia o incorrecto desempeño.

Indicador de Evaluación
Categorías de Respuesta
## Ponderació
n Indicador
de
## Evaluación
Muy buen
desempeño
## 100%
## Buen
desempeño
## 80%
## Desempeño
aceptable
## 60%
## Desempeño
incipiente
## 30%
## Desempeño
no logrado
## 0%
Realiza    un    completo    manejo    de    valores
atípicos  en  los  datos  siguiendo  las  buenas
prácticas de la industria.
## Implementa
estrategias
avanzadas,
como
detección de
outliers con
métodos
estadísticos o
modelos, y
aplica técnicas
específicas
según las
Realiza un
manejo
básico de
valores
atípicos en
## Python,
utilizando
métodos
convencional
es como el
rango
intercuartílico
Tiene un
manejo
limitado de
valores
atípicos en
Python, con
aplicaciones
básicas y sin
considerar
completamen
te las
características
Reconoce la
existencia de
valores
atípicos en los
datos, pero no
es capaz de
realizar
manejo en los
datos para su
tratamiento.
No demuestra
competencia
en el manejo
de valores
atípicos en
## Python. La
estrategia de
manejo es
insuficiente o
inexistente.
## 15%



características
de los datos.
o
visualización
de boxplots.
específicas de
los datos
Realiza   la   transformación   de   variables   de
acuerdo  con  la  implementación  de  modelos
matemáticos siguiendo buenas prácticas de la
industria.
## Implementa
transformacio
nes al 100%
de las
variables que
lo requieran,
de manera
precisa y
ajustada a las
buenas
prácticas de la
industria.
## Implementa
transformaci
ones al 80%
de las
variables que
lo requieran,
de manera
precisa y
ajustada.
## Implementa
transformaci
ones al 60%
de las
variables que
lo requieran,
de manera
precisa y
ajustada.
## Implementa
transformaci
ones sólo al
30% de las
variables que
lo requieran,
sin
considerar
buenas
prácticas de
la industria.
## No
implementa
transformacio
nes de las
variables.
## 15%
Aplica modelos de aprendizaje supervisado en
tareas  de  regresión  y  clasificación  de  acuerdo
con la naturaleza de los datos y las necesidades
de la organización.
## Construye
correctamente
más de 3
modelos
supervisados
para obtener
información
relevante sobre
los datos en
apoyo al
negocio.
## Construye
correctamente
entre 2 y 3
modelos
supervisados
para obtener
información
relevante sobre
los datos en
apoyo al
negocio.
## Construye
correctamente
solo 2 modelos
supervisados
para obtener
información
relevante sobre
los datos en
apoyo al
negocio.
## Construye
correctamente
solo un modelo
supervisado para
obtener
información
relevante sobre
los datos en
apoyo al
negocio.
No construye
ningún modelo
matemático
supervisado
aplicados a los
datos.
## 20%
Aplica modelos de aprendizaje no supervisado
en tareas de segmentación de acuerdo con la
naturaleza de los datos y las necesidades de la
organización.
## Aplica
correctamente
más de 3 modelos
no supervisados
obteniendo
información
relevante sobre
los datos.
Aplica 3 modelos
no supervisados
con algunos
errores,
obteniendo
información
relevante sobre
los datos.
Aplica solo 2
modelos no
supervisados
obteniendo
información
relevante sobre
los datos.
Aplica solo un
modelo no
supervisado
obteniendo
información
relevante sobre
los datos.
No construye
ningún modelo
matemático no
supervisado
aplicados a los
datos.
## 20%




Interpreta los resultados obtenidos del trabajo
con los datos, de acuerdo con las necesidades
y características del negocio.
Realiza una
interpretación
profunda de los
resultados,
identificando
conexiones
estratégicas clave
con las
necesidades y
características del
negocio.
Realiza una
interpretación
efectiva de los
resultados,
destacando
conexiones
relevantes con
las necesidades
y características
del negocio.
Realiza una
interpretación
básica de los
resultados, con
conexiones
limitadas con las
necesidades del
negocio.
Realiza una
interpretación
básica de los
resultados, pero
no logra
establecer
conexiones con
las necesidades
del negocio.
No demuestra
competencia en
la interpretación
relevante de los
resultados. Las
conexiones con
las necesidades
del negocio son
insuficientes o
inexistentes.
## 15%
Analiza  las  características  de  los  datos  y  del
negocio identificando insights de alto impacto.
Realiza un
análisis profundo
de las
características de
los datos y del
negocio,
identificando
insights de alto
impacto.
Realiza un
análisis
competente de
las
características
de los datos y
del negocio,
identificando
algunos insights
de forma
consistente.
Realiza un
análisis
completo de las
características
de los datos
pero no
identifica
insights
relevantes para
la organización.
Realiza un
análisis escaso
de las
características
de los datos, no
logrando
identificar
insight
relevantes para
la organización
No demuestra
competencia en
el análisis
significativo de
las características
de los datos y del
negocio. La
identificación de
insights es
insuficiente o
inexistente.
## 10%
Propone     soluciones     e     ideas     prácticas
basándose en los Insight para apoyar la Toma
de Decisiones
Propone al
menos tres
soluciones
estratégicas y
acciones
prácticas basadas
en insights.
Todas las
acciones
propuestas son
altamente
efectivas y
estratégicas,
contribuyendo
significativament
e a la toma de
decisiones.
Propone al
menos dos
soluciones
efectivas y
acciones
aplicables
basadas en
insights. Todas
las acciones
propuestas son
efectivas y
aplicables a la
realidad del
negocio,
apoyando la
toma de
decisiones.
Propone al
menos una
solución
competente y
acciones
concretas
basadas en
insights. Todas
las acciones
propuestas son
concretas y
contribuyen de
manera
competente a la
toma de
decisiones.
Propone al
menos una
solución básica y
acciones
limitadas
basadas en
insights. Puede
haber áreas
donde la
aplicación de las
propuestas sea
limitada en su
impacto.
No demuestra
competencia en
la propuesta de
soluciones
prácticas basadas
en insights. Las
propuestas son
insuficientes o
inexistentes,
limitando su
contribución a la
toma de
decisiones.
## 5%


## 100%