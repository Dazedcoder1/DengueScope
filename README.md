# DENGUESCOPE-A-Multi-Modal-Ensemble-Framework-for-Dengue-Forecasting.
A Multi-Modal Ensemble Framework for Short-Term Dengue Forecasting

**Overview**

DENGUESCOPE is an open-source, reproducible forecasting framework designed to predict short-term dengue incidence across all 27 Brazilian states. The framework integrates epidemiological surveillance data, climatic and environmental drivers, spatial information, and digital behavioral signals to deliver accurate and operationally relevant early warning forecasts.

The system combines complementary machine learning and deep learning models—CatBoost, Long Short-Term Memory (LSTM) networks, Temporal Convolutional Networks (TCN), and Temporal Fusion Transformers (TFT) using a weighted ensemble strategy to enhance robustness, generalization, and interpretability.


**Research Motivation**

Traditional dengue surveillance systems suffer from reporting delays and limited anticipatory capacity. Recent advances in machine learning, deep learning, and digital epidemiology provide an opportunity to develop proactive forecasting systems that support timely public health decision-making.

1.DENGUESCOPE addresses this need by:

2.Integrating heterogeneous data modalities

3.Quantifying the contribution of digital behavioral signals

**Framework Architecture**

The DENGUESCOPE pipeline consists of:

CatBoost: Structured tabular learning with categorical and climatic features

LSTM: Long-range temporal dependency modeling

TCN: Efficient temporal convolutional feature extraction

Temporal Fusion Transformer (TFT): Attention-based multivariate forecasting

Weighted Ensemble Module: Performance-based model aggregation

Each model is trained independently under time-stratified validation and combined at inference time.
Providing uncertainty-aware and explainable predictions

Ensuring full reproducibility through open-source design

**Data Sources**

The framework integrates:

Epidemiological dengue case counts

Meteorological variables (temperature, rainfall, humidity)

Environmental indicators (remote sensing indices)

Digital behavioral signals (Google Trends)

Spatial administrative boundaries

All data are temporally aligned and preprocessed using standardized pipelines.

**Experiments & Evaluation**

Time-stratified cross-validation

Nationwide evaluation across all Brazilian states

Baseline comparisons with classical statistical models

Ablation studies and explainability analysis

Metrics: MAE, RMSE, R²

**Reproducibility**

This repository provides:

Modular preprocessing and modeling pipelines

Configurable experiment scripts

Explainability modules (feature attribution)

Clear directory structure for extension and reuse

All results reported in the associated research proposal can be reproduced using the provided code.

**Citation**

If you use this repository, please cite the associated research work and reference this repository as software.

**License**

Open-source license for research and public health use.



**Ablation Study**

The ablation study evaluates the contribution of individual data modalities and model components to the overall forecasting performance. Each variant is trained and evaluated under identical time-stratified validation settings across all Brazilian states.

| Experiment ID    | Configuration Description             | Data Components Used                               | Model Components                           | Performance Impact           |
| ---------------- | ------------------------------------- | -------------------------------------------------- | ------------------------------------------ | ---------------------------- |
| A0 (Baseline)    | Statistical baseline                  | Historical dengue cases only                       | ARIMA                                      | Reference baseline           |
| A1               | Tree-based ML without digital signals | Epidemiological + climatic                         | CatBoost                                   | ↑ Accuracy vs. A0            |
| A2               | Deep temporal model                   | Epidemiological + climatic                         | LSTM                                       | ↑ Temporal learning          |
| A3               | Spatial–temporal modeling             | Epidemiological + climatic + spatial               | ST-LSTM                                    | ↑ Spatial coherence          |
| A4               | Digital signals only                  | Google Trends                                      | CatBoost                                   | Moderate predictive power    |
| A5               | Epidemiological + climatic + digital  | Dengue + climate + Google Trends                   | CatBoost                                   | ↑ Early-warning capability   |
| A6               | Hybrid deep learning                  | Epidemiological + climatic                         | LSTM + TCN                                 | ↑ Robustness                 |
| A7               | Attention-based temporal modeling     | Epidemiological + climatic + digital               | Temporal Fusion Transformer                | ↑ Feature attribution        |
| A8               | No digital behavior                   | All except Google Trends                           | Ensemble                                   | ↓ Lead-time performance      |
| A9               | No climatic covariates                | Dengue + digital                                   | Ensemble                                   | ↓ Seasonal stability         |
| A10 (Full Model) | **Proposed DENGUESCOPE**              | **Epidemiological + climatic + digital + spatial** | **CatBoost + LSTM + TCN + TFT (Ensemble)** | **Best overall performance** |


**Research Questions and Results Mapping**

The following table summarizes the primary research questions addressed in this study and maps them to the corresponding experimental findings.

| Research Question                                                                  | Methodological Component                             | Key Result                                         |
| ---------------------------------------------------------------------------------- | ---------------------------------------------------- | -------------------------------------------------- |
| RQ1: Can short-term dengue incidence be accurately forecast at a nationwide scale? | Multi-model ensemble with time-stratified validation | Accurate 1–4 week forecasts across all states      |
| RQ2: Do digital behavioral signals improve predictive performance?                 | Google Trends integration + ablation                 | Digital signals improved lead-time and accuracy    |
| RQ3: Do ensemble methods outperform individual models?                             | Weighted ensemble vs single models                   | Ensembles reduced variance and improved robustness |
| RQ4: Can explainable AI improve model interpretability?                            | Feature attribution analysis                         | Clear contribution of climate and digital features |
| RQ5: Is the framework reproducible and operational?                                | Open-source modular pipeline                         | Fully reproducible nationwide forecasting system   |
