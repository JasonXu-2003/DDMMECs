# DDMMECs
深圳市多介质环境中典型新污染物的演化归趋-风险模拟研究开源框架
================================================

English | [简体中文](#简体中文)

---

## Overview
This repository contains the full source code, data, and supplementary
materials for **“Data-driven multimedia modeling of emerging contaminants in urban environments (Shenzhen, China)”**  
(Manuscript under review, *Environmental Science & Technology*).

DDMMECs is an open, reproducible framework that couples a six-compartment mechanistic box model (air, water, soil, sediment, indoor dust, indoor surfaces) with machine learning to simulate the fate of PFOA (as a representative PFAS) in a coastal megacity (Shenzhen) and to perform screening-level health-risk assessment. The hybrid workflow first calibrates rate constants via XGBoost using OSSE-style synthetic observations, then applies an LSTM residual corrector to capture short-term dynamics, yielding substantial error reductions and city-scale risk estimates that remain well below screening thresholds. 

Note：Key ideas are documented in the manuscript and SI, including the six-box mass balance, rate-constant derivations, and the ML settings used in calibration and residual correction.

Features
* Six-compartment mass-conserving ODE model (SciPy, stiff solver) for PFAS fate across air/water/soil/sediment/indoor dust/indoor surfaces. 
* Surrogate-guided calibration using XGBoost; Latin-Hypercube Sampling to span the parameter space; documented hyper-parameters. 
* Residual correction using LSTM (Keras/TensorFlow) to recover sub-daily peaks; documented architecture and training curves. 
* Health-risk module for Incremental Lifetime Cancer Risk (ILCR) with cohort-specific factors and pathway apportionment. 
* Reproducible plotting scripts for all paper figures, including comparison panels, scatter-with-marginals, parameter bars with error bands, and shared-legend layouts.

Extensibility
* Swap the chemical. Replace PFOA physico-chemical properties and sources; the six-box scaffold remains (update params & units).
* Add compartments or processes. Extend box_model_core.py with additional sinks/sources (e.g., biota), preserving mass balance.
* Alternate learners. Drop-in other surrogates (e.g., LightGBM) or residual models (e.g., TCNs) with the same I/O schema.
* Policy scenarios. Modify emission/cleaning cadences, ventilation, or deposition parameters to assess intervention levers.

Reproducibility tips
* Random seeds are set to 42 in calibration scripts.
* TensorFlow results may vary by hardware; prefer CPU for determinism or configure platform-specific deterministic ops.
* All plotting scripts accept font size, figure size, margins, and spacing flags to regenerate camera-ready figures.



---
# Code is coming soon
