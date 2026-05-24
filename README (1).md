# Crop Yield Prediction Model
### Integrating Agronomic and Environmental Variables using Machine Learning

**Author:** Justina Grace Attah Akweh
**Program:** Code4Food Security Fellowship — Blossom Academy | WFP Ghana | KOICA  
**Date:** April 2026

---

## Overview

This project develops and evaluates a supervised machine learning pipeline 
to predict crop yield (tons/ha) from agronomic and environmental variables 
across 10,000 field observations covering four major crop types relevant 
to Ghana's food system: Maize, Cassava, Cocoa, and Rice.

The project includes an annotated Jupyter Notebook, 
and the dataset to be reproducible and 
deployable by agricultural practitioners, NGOs, and government agencies 
in Ghana and sub-Saharan Africa.

---

## Why This Matters

Smallholder farmers across sub-Saharan Africa face a reality where the 
difference between a good and poor harvest determines food security, 
income, and vulnerability. Yet most yield prediction tools are either 
too complex, too narrow, or locked behind proprietary systems 
inaccessible to frontline development organisations.

This pipeline is transparent, open-source, and built around variables 
routinely collected by agricultural programmes including Ghana's 
Ministry of Food and Agriculture (MoFA).

---

## Dataset

- **Source:** Kaggle (adapted to Ghanaian agricultural context)
- **Size:** 10,000 field-level observations
- **Adaptation:** Crop categories were replaced with Ghana-relevant 
  crops (Maize, Cassava, Cocoa, Rice) to align outputs with local 
  food security priorities
- **Key variables:** Rainfall (mm), Temperature (°C), Humidity (%),
  Soil pH, Soil Type, Fertilizer (kg), Irrigation method, 
  Planting Density, Previous Crop
- **Target:** Yield in tons per hectare

---

## Feature Engineering

Two agronomically meaningful features were engineered:

**Fertilizer Efficiency Index** = Fertilizer_Used_kg / (Rainfall_mm + 1)  
Captures nutrient-use effectiveness conditional on water availability — 
reflecting the well-established finding that fertilizer response 
flattens significantly under drought stress.

**Heat-Humidity Stress Index** = Temperature_C × Humidity_pct / 100  
Captures combined thermal and moisture stress during the growing season, 
a proxy for evapotranspiration demand that affects crop water use 
and yield outcomes.

---

## Models Trained

| Model | R² | RMSE (ton/ha) | MAE | MAPE |
|---|---|---|---|---|
| Linear Regression | 0.36 | — | — | — |
| Random Forest | >0.97 | — | — | — |
| **Gradient Boosting** | **0.9821** | **5.08** | **4.08** | **3.99%** |

Gradient Boosting achieved the best performance, with predictions 
within 4% of actual yield on average. Five-fold cross-validation 
confirmed stability with no overfitting.

---

## Key Findings

- **Fertilizer application rate** is the single strongest predictor 
  of yield variability
- **Seasonal rainfall** is the second most important predictor
- The engineered **Fertilizer Efficiency Index** appeared in the 
  top five features, validating the water-nutrient interaction hypothesis
- **Partial Dependence Plots** revealed a diminishing-returns 
  rainfall-yield curve consistent with known crop water response 
  functions — a finding with direct implications for climate 
  adaptation strategy
- Linear Regression (R² = 0.36) confirmed that yield-environment 
  relationships are fundamentally non-linear, justifying the 
  ensemble approach

---

## Tools & Methods

- **Python:** pandas, numpy, scikit-learn, matplotlib, seaborn
- **Models:** Linear Regression, Random Forest, Gradient Boosting
- **Validation:** 80/20 train-test split, 5-fold cross-validation
- **Interpretability:** MDI feature importance, Permutation 
  Importance, Partial Dependence Plots
- **Output:** Power BI-ready CSVs for interactive dashboard deployment
- **Documentation:** Full research proposal with literature review

---

## Files in This Repository

- `Crop_Yield_Prediction_Justina.ipynb` — full annotated ML pipeline
- `data/README.md` — dataset description and sourcing note

---

## My Perspective

The finding that fertilizer effectiveness is conditional on rainfall 
was the insight that stayed with me longest. 
It means that a blanket fertilizer recommendation ignores the most 
important variable: whether there is enough water for the nutrients 
to be absorbed at all.

That is not just an agricultural problem. It is a water problem. 
And it pointed me toward a deeper interest in how water availability 
shapes ecosystem outcomes across scales from a smallholder's 
maize field to an entire forest biome.

---

## Future Directions

- Extend to Ghana district-level data from MoFA
- Incorporate soil nutrient data (N, P, K) from ISRIC SoilGrids

---

## Data Note

The base dataset was sourced from Kaggle. Crop categories were 
adapted to reflect the Ghanaian agricultural context, replacing 
generic labels with locally relevant crop types including Maize, 
Cassava, Cocoa, and Rice. This contextualisation was intentional, 
the goal was to build a pipeline whose outputs would be meaningful 
to Ghanaian extension agents, policymakers, and food security 
practitioners. 

---


