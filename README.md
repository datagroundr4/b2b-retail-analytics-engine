# 🚀 Dataground DaaP Suite: Advanced Automotive Inventory & Network Intelligence (v4.0 Final)

![Data Architecture](https://img.shields.io/badge/Architecture-BigQuery%20%7C%20Python%20%7C%20Looker%20Studio-blue?style=flat&logo=googlecloud&logoColor=white)
![Core Engine](https://img.shields.io/badge/Core-FP--Growth%20%2B%20NetworkX%20%7C%20GVY-green?style=flat)
![Data Source](https://img.shields.io/badge/Data-Kaggle%20Synth%20%7C%20Ecuador%20Retail-orange?style=flat)
![Status](https://img.shields.io/badge/Status-Production%20Ready-brightgreen?style=flat)

> **Turning complex automotive aftermarket transactions into an autonomous inventory governance and C-Suite decision engine.**
> **Multi-layer data architecture: FP-Growth association mining · NetworkX topological graphs · Looker Studio interactive Treemaps · Autonomous RPA replenishment**

---

## 🎯 Business Problem & Domain Context

Managing inventory in high-complexity B2B retail environments (such as automotive spare parts and multi-line distribution) exposes companies to a silent capital drain: **Inventory Blindness**.

Using a robust foundational dataset sourced from Kaggle and transformed to simulate realistic B2B transactions from **2026 onwards** (tailored to the Ecuadorian market context), we analyze thousands of SKUs across high-rotation categories. Traditional ERP systems fail here because they treat products as isolated entities, leading to:
- **The Reactive Reorder Trap:** Relying on simple moving averages (`ROP`) that break entire cross-selling baskets when secondary items go out of stock.
- **Capital Immobilization:** Millions of dollars trapped in dead stock because legacy tools cannot evaluate the systemic network value of a product.
- **Executive Friction:** Unreadable data tables that provide zero visibility into network bottlenecks or cascading supply chain failures.

**This analytical suite answers four critical C-Suite questions:**
1. Which product clusters act as revenue anchors and drive systemic cross-selling traction?
2. How can we calculate a joint Reorder Point (`ROP_Par`) to protect critical multi-item sales combos?
3. Where are the active up-selling leaks caused by stockouts on secondary companion items?
4. How do we automate purchase orders (`PO-LIVE`) via RPA before inventory thresholds are breached?

---

## 📊 Dataset & Data Sources

| Attribute | Detail |
|-----------|--------|
| Source Foundation | Kaggle Automotive Retail Datasets (Engineered & Synthetic Simulation) |
| Temporal Coverage | 2026 — Present (Real-time simulated streaming frames) |
| Granularity | Transaction-level grain (`Transaccion_ID` + `SKU`) |
| Key Fields | SKU, Nombre_Repuesto, Categoria, Subcategoria, Stock_Fisico, Punto_Reorden_ROP, Costo_Nacionalizado_USD, Transaccion_ID, InvoiceDate, Ingreso_Total_USD |

**Data Preparation & Engineering:**
- **Initial Inventory & Seed Capital:** Baseline inventory values and day-zero capital metrics derived directly from historical transaction baselines.
- **Temporal Alignment:** Streaming simulation scripts (`Notebook 05`) anchored to the latest database timestamps, generating realistic transaction lags (4 to 34 minutes) without timeline distortion.
- **Taxonomy Enrichment:** Automated text-based derivation of product subcategories (`Frenos y Componentes`, `Suspensión y Dirección`, etc.) to power multi-level hierarchical drill-downs.

---

## 🏗️ Data Architecture & Pipeline

The pipeline operates on a cloud-native, serverless stack optimized for high-speed computation and low operational overhead (`OpEx`):

```text
[ 01. GOOGLE COLAB: ML Core & Simulation ]
 ├── 01. Data Wrangling & Automotive Enrichment
 ├── 02. Kardex Engine & Verhulst Growth Curves
 ├── 03. Market Basket Analysis (FP-Growth Mining)
 ├── 04. NetworkX Graph Topology & GVY Calculation
 └── 05. Real-Time POS Emulator (KNN & RPA)
                    │
                    ▼
[ 02. GOOGLE BIGQUERY: Data Warehouse ]
 ├── Base Tables (Dim_Producto_Nativa, Fact_Ventas_Nativa)
 ├── vw_inventario_vivo (Real-Time Stock & Status)
 ├── vw_canasta_reorden (Pairwise Co-occurrence & Joint ROP)
 ├── vw_motor_ia_enriquecido (Transition Rules & Lift)
 └── vw_recomendacion_avanzada_csuite (Network Cluster & Subcategories)
                    │
                    ▼
[ 03. LOOKER STUDIO: C-Suite Visual Analytics ]
 ├── Pages 1-3: Financial Benchmarks & B2B Margins
 ├── Page 4: Advanced Recommendation Engine (Treemap & GVY)
 └── Page 5: Master Inventory Governance (Multi-filter & Traffic Lights)
```
---

## 🧠 Proprietary Mathematics: Graph Value Yield (GVY)

Traditional inventory metrics look at volume or profit margins in complete isolation. To bridge statistical association with real corporate cash flow, Dataground developed **GVY (Graph Value Yield)**:

$$\text{GVY} = \text{Confidence} \times \text{Lift} \times \text{Unit Margin (USD)}$$

* **Confidence:** The historical probability that purchasing the "conductor" product triggers the purchase of the companion item.
* **Lift:** Measures how much stronger the association is compared to random market chance, filtering out false positives.
* **Unit Margin:** Anchors the probability directly to the **gross profit in dollars** generated by the destination SKU.

*Strategic Impact:* GVY prioritizes inventory placement not by what sells the highest volume individually, but by **what protects and drives the highest systemic liquidity across the corporate network.**

---

## 💡 Business Insights & Discoveries (Dashboard Findings)

Operating the suite across our data simulation uncovers critical behavioral insights that legacy ERPs completely miss:

1. **The "Anchor-Satellite" Dynamic ($K_9$ Core):**  
   Analysis revealed that high-margin assembly parts (such as specialized *Air Pumps* or *Alternator Kits*) act as network anchors. Even when their individual sales velocity is moderate, their absence breaks over 45% of secondary maintenance baskets, triggering a severe cascading loss in gross profit.
2. **Quarantine of Dead Stock vs. Active Canastas:**  
   Using the Treemap drill-down, management can instantly spot that over 30% of immobilized capital sits in non-connected SKUs, whereas capital tied up in the core network yields a positive velocity return up to 3.5x higher.
3. **Autonomous RPA Mitigation:**  
   By coupling seasonal KNN transaction frames with real-time stock audits, the system successfully intercepts stockouts before they occur, automatically generating purchase orders (`PO-LIVE`) for items approaching their joint reorder point (`ROP_Par`).

---

## 📊 Executive Dashboards & UI Showcase

The suite delivers a frictionless visual experience tailored for C-level decision-makers.

🔗 **[View Live Looker Studio Report (Demo Environment)](https://datastudio.google.com/reporting/3cbecd6a-3a7b-41d4-94d1-ca978cfd1428/page/rMc5F)**

![Vista General del Tablero C-Suite](assets/dashboards/tablero_01_2026-11-07%20180928.png)

### Dashboard Structure
| Page | Audience | Purpose | Key Visuals |
|------|----------|---------|-------------|
| **Pages 1-3** | Executive / Finance | Financial Benchmarks & B2B Margins | Revenue breakdown · Gross margin trends · Top product performance cards |
| **Page 4: Advanced Recommendation** | CCO / Operations | Treemap Graph Intelligence & Cross-selling | Hierarchical Treemap (Subcategories -> SKUs) colored by GVY Score · Audit table with conditional traffic lights |
| **Page 5: Master Inventory Governance** | Supply Chain Leads | Multi-filter Macro Control | Global inventory filters (Category, ABC Classification, Stock Status) · Autonomous PO tracking |

> *[ Insert Screenshots of Treemap & Master Inventory Governance here ]*

---

## 📂 Core Repository Notebooks (v4.0)

* `01-Generacion_Historica_Batch_final.ipynb`: Data cleaning, structuring, and synthetic feature engineering.
* `02-NOTEBOOK 02 - MOTOR DE KARDEX & CURVA DE VERHULST (V4.0).ipynb`: Monthly Kardex generation and Verhulst inventory curves.
* `03-NOTEBOOK 03 (MAESTRO): MARKET BASKET ANALYSIS CON FP-GROWTH Y BIGQUERY.ipynb`: Association rules mining and BigQuery persistence.
* `04-MNetwokX_G_Engine y GVY_Score.ipynb`: Topological graph engine, GVY scoring, and dual 70/30 capital allocation sheets.
* `05-NOTEBOOK 05 - REAL-TIME FRAMING POS EMULATOR (KNN & RPA)`: Seasonal POS transaction simulation anchored to database timestamps with automated supply chain reorder triggers.

---

## 🛠️ Skills & Technologies Demonstrated

`BigQuery` `Python` `Google Colab` `Looker Studio` `FP-Growth` `NetworkX` `KNN` `RPA Automation` `Data as a Product (DaaP)` `Supply Chain Analytics` `Graph Theory` `SQL Advanced Views` `Executive Data Literacy`

---

## 📂 Repository Structure

```text
dataground-daap-suite/
├── README.md
├── notebooks/
│   ├── 01_data_wrangling.ipynb
│   ├── 02_kardex_verhulst.ipynb
│   ├── 03_fp_growth_mining.ipynb
│   ├── 04_networkx_gvy.ipynb
│   └── 05_pos_emulator_rpa.ipynb
├── sql_views/
│   ├── vw_inventario_vivo.sql
│   ├── vw_canasta_reorden.sql
│   └── vw_recomendacion_avanzada_csuite.sql
└── dashboard/
    └── screenshots/
        ├── treemap_overview.png
        └── governance_panel.png
```
---

## 🔗 Portfolio & contact

| | |
|---|---|
| 🌐 Portfolio | [linktr.ee/dataground](https://linktr.ee/dataground) |
| 💼 LinkedIn | [Juan Fernando Mosquera](https://www.linkedin.com/in/juan-fernando-mosquera-araujo-226966180/) |
| ✍️ Medium | [@erre4tro](https://medium.com/@erre4tro) |

---

*Part of the [Datagroundr4](https://github.com/Datagroundr4) analytics portfolio.*

---
