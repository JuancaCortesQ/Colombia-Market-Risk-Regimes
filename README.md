# Detección de Regímenes de Riesgo Financiero en Mercados Emergentes: Caso Colombiano

Este repositorio contiene el desarrollo de un marco analítico predictivo basado en Machine Learning (**Random Forest Classifier**) diseñado para la identificación y clasificación estructural de regímenes de riesgo financiero (Estabilidad, Estrés Moderado y Crisis) en el contexto macroeconómico colombiano. 

El modelo evalúa la interacción de dinámicas locales frente a choques e indicadores de volatilidad global.

## 📊 Arquitectura y Consolidación de Datos
Ante la ausencia de un dataset centralizado para el mercado local, se construyó una base de datos propia mediante la recopilación y alineación temporal de series de tiempo de fuentes oficiales y plataformas analíticas globales:
* **Banco de la República de Colombia (Banrep):** Indicadores macroeconómicos domésticos, política monetaria, inflación y agregados financieros locales.
* **Investing.com:** Variables de mercados globales, precios de commodities (como el petróleo), índices internacionales y métricas de volatilidad externa (VIX).

* **Endogenización de Regímenes:** Configuración de las variables objetivo mediante umbriles basados en percentiles estructurales (33% y 66%) de la volatilidad histórica del mercado.
* **Preservación del Orden Cronológico:** División de conjuntos de entrenamiento y prueba (`train_test_split`) de forma estrictamente secuencial utilizando `shuffle=False`. Esto elimina por completo el *Look-Ahead Bias* inherente a los datos financieros.
* **Prevención de Fuga de Datos (*Data Leakage*):** Implementación del algoritmo de estandarización (`StandardScaler`) aplicado exclusivamente *post-split*. El estimador aprende los parámetros estadísticos únicamente del conjunto de entrenamiento, garantizando que la información futura no contamine el proceso de aprendizaje.
* **Optimización ante Desbalanceo de Clases:** Configuración de penalizaciones dinámicas mediante `class_weight='balanced'` para contrarrestar la baja frecuencia estadística de los eventos de crisis extrema, mejorando la sensibilidad (*recall*) del modelo en escenarios críticos.

## 📈 Resultados y Relevancia Analítica
El modelo base demuestra una alta especificidad y un **Precision del 83%** en la detección del régimen de crisis alta (Clase 2). Esto posiciona al algoritmo como una herramienta robusta y de carácter conservador, ideal para su integración en sistemas de alerta temprana o procesos de gestión de riesgos y asignación de activos en portafolios locales.
