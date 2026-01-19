# HiCForecast Extension: Uncertainty, Graph Diffusion, and Structure-Aware Diagnostics

This repository contains an experimental extension of **HiCForecast** (Pinchuk et al., 2025) focused on improving the *interpretability* and *diagnostic evaluation* of Hi-C time-series forecasting.

The work reproduces the baseline inference pipeline and implements three extension directions:

1. **Uncertainty estimation (ensemble-style repeated inference)**
2. **Graph diffusion post-processing (graph-aware refinement without retraining)**
3. **Structure-aware diagnostics (TAD/loop–sensitive losses used as evaluation metrics)**

> **Scope note:** This repository does **not** retrain the HiCForecast model. Structure-aware losses are implemented and validated as diagnostics; training integration is planned as future work.

---

## Contents

| Notebook | What it does | Main outputs |
|---|---|---|
| `00_baseline_inference_metrics.ipynb` | Baseline HiCForecast inference + metrics + qualitative plots | Baseline predictions, metrics CSV, GT/Pred/Diff figures |
| `01_uncertainty_ensemble.ipynb` | Repeated inference (K runs) → mean prediction + pixel-wise std uncertainty maps | `pred_uncertainty_mean.npy`, `pred_uncertainty_std.npy`, uncertainty figures |
| `02_graph_diffusion_postprocess.ipynb` | Sparse top-k diffusion refinement applied to predictions (no retraining) | `pred_graphdiff.npy`, comparison figures, metrics CSV |
| `03_structure_aware_loss_metrics.ipynb` | Adds structure-aware diagnostics (insulation proxy + peak-weighted error) and evaluates variants | Structure metrics CSV + summary figures |

---

