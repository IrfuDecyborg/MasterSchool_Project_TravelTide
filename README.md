# MasterSchool_Project_TravelTide

# 🧳 TravelTide
**Customer Segmentation for an Online Travel e-Booking Platform**

This repository documents the complete analytics workflow of **TravelTide**, a digital travel company aiming to improve customer retention through a personalized **rewards and perk system**.  
It covers the entire lifecycle — from **data extraction (SQL)** and **feature engineering** to **segmentation (rule-based + ML)** and **business insights** that guide reward strategy.

---

## 🧠 Project Overview
**Goal:** Identify meaningful customer segments and match them with suitable perks (discounts, upgrades, or bonuses) to increase engagement and lifetime value.

**Business Problem:**  
Elena Tarrant (Head of Marketing) wanted to understand *which perks appeal to which traveler types*.  
The task: analyze user behavior, create actionable personas, and recommend perk strategies.

**Analytical Phases**
1. **Data Understanding & Cleaning** – SQL joins, cohort filtering, handling missing/outliers  
2. **Feature Engineering** – build RFM metrics + behavioral indicators  
3. **Segmentation** – Rule-based logic and ML (K-Means)  
4. **Business Recommendations** – interpret personas, map perks, visualize results

---

## 📓 Notebooks

All notebooks connect directly to the **TravelTide PostgreSQL database** via SQLAlchemy and can run in Colab or Jupyter.

| Notebook | Description |
|-----------|--------------|
| **01_TravelTide_EDA.ipynb** | Schema overview, data cleaning, and exploratory plots. |
| **02_TravelTide_FeatureEngineering.ipynb** | Builds user-level metrics: conversion rate, loyalty index, promo responsiveness. |
| **03_TravelTide_RuleBasedSegmentation.ipynb** | Defines personas using RFM + CLTV thresholds and assigns tailored perks. |
| **04_TravelTide_Clustering_ML.ipynb** | Applies K-Means to discover natural clusters; includes scaling, PCA, and silhouette scoring. |
| **05_TravelTide_Final_Presentation.ipynb** | Combines visuals and insights for the executive summary. |

---

## 🗂️ Repository Structure



---

## 🧩 Data Description
Four main relational tables:

| Table | Description |
|--------|-------------|
| **users** | Demographics: birthdate, gender, marital status, home country |
| **sessions** | Interaction logs: clicks, discounts, bookings, cancellations |
| **flights** | Flight details: origin, destination, airline, base fare, bags |
| **hotels** | Hotel data: nights, rooms, check-in/out times, price per night |

Aggregated into:
- **Session-level dataset** → feature engineering  
- **User-level dataset** → segmentation & persona mapping  

---

## ⚙️ Key Features & Metrics
Behavioral variables created to capture engagement and value:

| Metric | Description |
|---------|--------------|
| `conversion_rate_per_session` | % of sessions resulting in a booking |
| `promo_responsiveness` | Share of discounted successful bookings |
| `loyalty_index` | Ratio of kept bookings / total trips |
| `avg_session_duration_min` | Mean active session time |
| `RFM_sum`, `RFM_loyalty` | Composite Recency-Frequency-Monetary scores |
| `CLTV` | Proxy for customer lifetime value |

---

## 🤖 Machine-Learning Segmentation
Implemented in **Thread 05** (`04_TravelTide_Clustering_ML.ipynb`)

- **Model:** K-Means (3 – 4 clusters) with scaling and silhouette analysis  
- **Visualization:** PCA (2-D projection) for interpretability  
- **Resulting clusters:**  
  1. High Engagement / High Value  
  2. Highly Engaged Explorers  
  3. Low Engagement / Low Value  
  4. Inactive Travelers  

**Outcome:** confirmed and complemented rule-based personas; ML revealed hidden “explorer” behavior patterns.

---

## 🧮 Rule-Based Segmentation
Developed in **Thread 07** (`03_TravelTide_RuleBasedSegmentation.ipynb`)

- Combined **RFM**, **CLTV**, and behavioral thresholds:  
  - `conversion_rate > 0.75` → High-Value  
  - `trip_length ≤ 3 days` → Business Flyer  
  - `promo_responsiveness > 0.25` → Discount Hunter  
  - Family signals (seats ≥ 3 & rooms ≥ 2) → Family Traveler  
- Defined personas: **Loyal High**, **Family Value**, **Business Flyer**, **Discount Hunter**, **Steady Explorer**, **Casual Inactive**, etc.  
- Assigned contextual perks: free nights, upgrades, or discount vouchers.  
- Exported final mapping: `user → persona → perk_offer`.

---

## 💡 Insights & Business Impact
1. **Loyal High** and **Family High Value** users show top CLTV & low cancellations — prime for premium rewards.  
2. **Discount Hunters** respond best to promotions (+15 % higher engagement).  
3. **Steady Explorers** browse heavily but rarely book → recommend personalized nudges.  
4. **Casual/Inactives** need re-engagement emails or reminders.  
5. ML clusters validated these patterns and revealed “Explorers” not captured by static rules.

---

## ⚖️ Rule-Based vs ML Comparison (Summary)

| | **Rule-Based** | **ML (K-Means)** |
|--|--|--|
| Logic | Business thresholds (RFM + CLTV) | Data-driven behavior patterns |
| Clarity | Easy to explain & act on | Reveals hidden groups |
| Value | Direct perk assignment | Validates & refines personas |
| Combined Benefit | Interpretability + Discovery = Balanced segmentation |

---

## 🧾 Reports & Deliverables
- **Executive Summary (PDF)** – one-page business report  
- **Final Presentation (PPTX)** – 12-slide deck (EDA → Personas → Insights)  
- **Exported CSVs:**  
  - `user_perk_mapping.csv` (rule-based)  
  - `user_clusters_kmeans.csv` (ML)  
  - `user_agg_features.csv` (clean features)

---

## 🧰 Tech Stack
**Languages & Libraries:** Python (pandas, numpy, matplotlib, seaborn, scikit-learn, sqlalchemy)  
**Database:** PostgreSQL (SQL joins & aggregation)  
**Environment:** Google Colab / Jupyter  
**Version Control:** Git + GitHub  

**Skills Demonstrated:**  
EDA • SQL • Feature Engineering • RFM Modeling • Clustering • Visualization • Business Storytelling • Insight Presentation

---

## 🚀 Outputs
- Segmented user dataset with persona & perk assignment  
- ML clustered dataset for validation  
- Visual plots for presentation  
- Ready-to-use executive summary

---

## 🏁 Conclusion
This project showcases the **end-to-end Data Analytics process** — from raw SQL data to actionable marketing insights.  
By combining **rule-based interpretability** with **ML-based discovery**, TravelTide can deliver targeted rewards that boost engagement and long-term customer loyalty.

---

**Author:** Md Erfan  
**Program:** Masterschool – Data Analytics (Mastery Project 2025)
