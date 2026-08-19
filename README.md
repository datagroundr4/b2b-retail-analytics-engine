# ⚙️ DataGround Analytics Engine: B2B/B2C Auto Parts Retail
**Enterprise Data Architecture & Supply Chain Intelligence**

## Visión General del Proyecto
Este proyecto es una simulación de grado corporativo (End-to-End) diseñada para importadores y distribuidores B2B/B2C del sector de repuestos automotrices. Transforma datos transaccionales crudos en inteligencia prescriptiva de cadena de suministro (Supply Chain)

El sistema detecta patrones de compra cruzada (Market Basket) para prevenir quiebras de stock y modela la demanda intermitente usando algoritmos avanzados para optimizar el capital inmovilizado en bodegas.

## 🏗️ Arquitectura de Datos (Data Stack)
* **Data Lake / Storage:** Google Drive (Cloud Storage)
* **ETL & Data Wrangling:** Python (Pandas, Numpy) / Google Colab
* **Data Warehouse:** Google BigQuery (Esquema de Estrella / Star Schema)
* **Capa Semántica y BI:** Looker Studio (SQL Views)
* **Machine Learning (Fase 3):** Algoritmo Apriori (Association Rules)

## 🧠 Modelos Matemáticos Implementados
1. **Weighted Hashing Semántico:** Transfiormación probabilística de datos genéricos a categorías automotrices respetando la ley de Pareto del mercado (35% Frenos, 25% Suspensión, etc.).
2. **Modelo de Croston:** Cálculo avanzado de demanda intermitente (ADI) para fijar Puntos de Reorden (ROP) y Stocks de Seguridad (SS) realistas en entornos B2B.
3. **Corss-Selling Risk Logic:** Motores SQL auto-gestionados para detectar "Efecto Dominó" (pérdida de ingresos por falta de componentes en un kit de reparación).

## 🗂️ Estructura del Data Lake
* `/01_raw`: Datos transaccionales crudos y desnormalizados.
* `/02_processesd`: Capa Silver. Limpieza B2B, vectorización temporal y preservación de "Cestas de Compra".
* `03_gold_star_schema`: Capa Gold. Modelo de Estrella inyectado en BigQuery (`Dim_Bodega`, `Dim_Producto`, `Fact_Ventas`).

## 📊 Tableros de Control (Looker Studio)
* **Dashboard C-Suite:** Resumen Financiero (YoY, YTD, TTM), control de márgenes dinámicos B2B, volumen (UPT) y Ticket Promedio (AOV).
* **Dashboard Operativo:** Visualización de capital en riesgo y hojas de compra automatizadas impulsadas por el cruce de ROP y Market Basket Analysis.

---
*Desarrollado por Juan Fernando Mosquera A. para Dataground | Construyendo arquitecturas que deciden.*
