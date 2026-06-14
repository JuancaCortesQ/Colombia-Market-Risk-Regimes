# Detección de Regímenes de Riesgo Financiero: Caso Colombiano
# Colombia Market Risk Regimes

Este proyecto implementa un modelo de Machine Learning (**Random Forest Classifier**) para identificar y predecir tres regímenes de riesgo financiero (Estabilidad, Estrés Moderado y Crisis) en el mercado colombiano, utilizando variables macroeconómicas y de mercados globales.

## 📊 Origen de los Datos
Debido a la ausencia de un dataset unificado, la información fue recopilada de manera independiente a través de múltiples fuentes oficiales, principalmente del **Banco de la República de Colombia (Banrep)**, consolidando métricas mensuales de tasas, inflación, tipo de cambio y variables globales de volatilidad.

## 🛠️ Metodología Aplicada
* **Definición de Regímenes:** Clasificación basada en percentiles estructurales de volatilidad histórica.
* **Control de Sesgos:** División de datos de manera temporal (`shuffle=False`) para respetar la naturaleza de las series de tiempo financieras y evitar *Look-Ahead Bias*.
* **Estandarización Rigurosa:** Procesamiento con `StandardScaler` aplicado estrictamente post-split para mitigar problemas de *Data Leakage*.
* **Balanceo de Clases:** Uso de pesos balanceados en el algoritmo para manejar la baja frecuencia de eventos de crisis extrema.

