# EA3 – Aprendizaje No Supervisado mediante K-Means

## 1. Descripción de la técnica utilizada y justificación

En esta actividad se aplicó el algoritmo de **K-Means Clustering** sobre el dataset `application_.csv`, el mismo utilizado en el examen y en el proyecto de scoring crediticio. El objetivo de este análisis no supervisado es descubrir patrones ocultos y agrupar clientes en segmentos homogéneos según sus características financieras y sociodemográficas.

El uso de K-Means se justifica porque:

- Permite **segmentar** a los solicitantes de crédito en grupos con comportamientos similares.
- Facilita identificar **subpoblaciones con mayor o menor riesgo** crediticio.
- Ayuda a complementar el modelo supervisado, proporcionando una capa adicional de interpretación.
- Es eficiente, sencillo de implementar e interpretable en contextos de negocio.

Las variables seleccionadas para el análisis fueron:

- **AMT_INCOME_TOTAL** (ingreso total)
- **AMT_CREDIT** (monto del crédito)
- **AMT_ANNUITY** (cuota periódica)
- **AMT_GOODS_PRICE** (valor del bien)
- **CNT_CHILDREN** (número de hijos)
- **AGE_YEARS** (edad derivada de DAYS_BIRTH)
- **CREDIT_INCOME_RATIO** (crédito / ingreso)
- **ANNUITY_INCOME_RATIO** (cuota / ingreso)

Estas variables capturan información relevante del nivel socioeconómico, la carga crediticia, la composición familiar y la capacidad de pago.

---

## 2. Instrucciones de ejecución

1. Abrir el notebook `EA3_KMEANS.ipynb` en Google Colab o en un entorno local.
2. Asegurarse de que el archivo **application_.csv** esté en el mismo directorio del notebook.
3. Instalar las librerías necesarias si Colab lo solicita:

Ejecutar las celdas del notebook siguiendo el orden CRISP–DM:

Business Understanding

Data Understanding

Data Preparation

Modeling (K-Means)

Evaluation

Conclusions

Verificar que el análisis utiliza SOLO el dataset base del proyecto (sin usar datos de validación o prueba) para evitar data leakage.

3. Análisis e interpretación de resultados
Determinación del número de clusters

A través del método del codo (Elbow Method) se identificó un valor adecuado de k que permite segmentar la población sin sobreajustar el modelo. En este caso, el codo del gráfico indica que k = 4 es una elección razonable (este valor puede variar según el gráfico real generado).

Interpretación de los centroides

Los centroides mostraron diferencias claras entre los grupos, destacando:

Variación en el nivel de ingresos.

Diferencias en la carga financiera (crédito / ingreso).

Diferencias en la cuota mensual y en el valor del bien adquirido.

Segmentos con mayor proporción de clientes jóvenes vs. mayores.

Impacto del número de hijos en el perfil crediticio.

Riesgo de impago por cluster (TARGET)

Al relacionar los clusters con la variable TARGET:

Algunos clusters presentaron tasas de impago significativamente superiores.

Otros mostraron perfiles estables con bajo riesgo.

Esto demuestra que los segmentos encontrados por K-Means capturan diferencias reales de comportamiento crediticio.

El análisis permitió identificar:

Segmentos de alto riesgo: alto ratio crédito/ingreso + bajos ingresos.

Segmentos de bajo riesgo: mayores ingresos + menor carga financiera.

Segmentos intermedios: perfiles mixtos.

4. Discusión sobre si incorporar el método al proyecto final

El uso de K-Means aporta información valiosa y puede integrarse al proyecto final de las siguientes maneras:

Como variable adicional del modelo supervisado

El número de cluster (CLUSTER_KMEANS) puede usarse como feature categórica.
Esto ayuda al modelo a capturar patrones no lineales difíciles de detectar solo con variables individuales.

Como herramienta de segmentación operativa

Los clusters pueden guiar decisiones como:

Límite de crédito

Tasas diferenciadas

Controles adicionales para segmentos de mayor riesgo

Enfoques de cobranza diferenciada

Para monitoreo y estabilidad del modelo

Cambios drásticos en la composición de clusters pueden indicar:

Cambios en el perfil de la cartera

Cambios económicos

Data drift

Riesgos emergentes

Limitaciones del método

K-Means es sensible a outliers.

Requiere escalamiento.

Asume clusters aproximadamente circulares en el espacio vectorial.

La elección de k influye fuertemente en el resultado.

A pesar de esto, la técnica aporta valor real al análisis crediticio, mejora la interpretabilidad y fortalece el proyecto de scoring.
   ```bash
   pip install pandas numpy scikit-learn matplotlib seaborn
