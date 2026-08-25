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
* **Machine Learning (Fase 3):** Algoritmo FP-Growth (Optimización de memoria para matrices esparsas corporativas) para extracción de Reglas de Asociación B2B, con ingesta automatizada de de vuelta hacia BigQuery.

## 🧠 Modelos Matemáticos Implementados
1. **Weighted Hashing Semántico:** Transfiormación probabilística de datos genéricos a categorías automotrices respetando la ley de Pareto del mercado (35% Frenos, 25% Suspensión, etc.).
2. **Modelo de Croston:** Cálculo avanzado de demanda intermitente (ADI) para fijar Puntos de Reorden (ROP) y Stocks de Seguridad (SS) realistas en entornos B2B.
3. **Corss-Selling Risk Logic:** Motores SQL auto-gestionados para detectar "Efecto Dominó" (pérdida de ingresos por falta de componentes en un kit de reparación).
4. **Digital Twin (Simulación de Eventos Discretos):** Motor en Python que viaja en el tiempo para recrear el Kardex histórico, descontando ventas diarias y simulando tiempos de tránsito (Lead Time marítimo) para calcular con exactitud el GMROI y el capital inmovilizado real mes a mes.
5. **FP-Growth (Market Basket Analysis Avanzado):** Superando las limitaciones computacionales de Apriori ($0(2^n)$), este modelo procesa matrices binarias masivas para descubrir reglas ocultas de compra cruzada B2B, entregando predicciones de Up-Selling basadas en métricas de Confianza y Lift.

## 🗂️ Estructura del Data Lake
* `/01_raw`: Datos transaccionales crudos y desnormalizados.
* `/02_processesd`: Capa Silver. Limpieza B2B, vectorización temporal y preservación de "Cestas de Compra".
* `03_gold_star_schema`: Capa Gold. Modelo de Estrella inyectado en BigQuery (`Dim_Bodega`, `Dim_Producto`, `Fact_Ventas`).

## Emulación de Streaming (Live POS)
Para demostrar la capacidad de reacción de los tableros, el proyecto incluye un emulador de punto de venta (POS) en Python. Este script funciona bajo la capa gratuita de GCP usando **Micro-Batching** (LoadJobConfig con WRITE_APPEND) para inyectar transacciones en tiempo real a BigQuery. Cuenta con compuertas lógicas que respetan el horario comercial (8 AM - 6 PM) y reglas de descuento automático por volumen. 

## 📊 Tableros de Control (Looker Studio)
* **Dashboard C-Suite:** Resumen Financiero (YoY, YTD, TTM), control de márgenes dinámicos B2B, volumen (UPT) y Ticket Promedio (AOV).
* **Dashboard Operativo:** Visualización de capital en riesgo y hojas de compra automatizadas impulsadas por el cruce de ROP y Market Basket Analysis.
* **Torre de Control en Tiempo Real:** Diagnóstico comercial de "hoy". Monitorea la velocidad de quema de efectivo (Burn Rate), los días de Superviviencia de Stock por categoría y el Margen B2B en vivo, usando una vista snapshot (últimos 30 días) contra el catálogo físico actual.
* **Motor de Recomendación de Ventas (IA):** Interfaz táctica para asesores comerciales que dicta el "Next Best Offer" (Siguiente Mejor Oferta). Basado en las probabilidades generadas por FP-Growth, permite buscar repuestos en tiempo real y sugiere kits de complemento para maximizar el ticket promedio por llamada.

---
*Desarrollado por Juan Fernando Mosquera A. para Dataground | Construyendo arquitecturas que deciden.*
