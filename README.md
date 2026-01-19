## Contents

| Notebook | What it does | Main outputs |
|---|---|---|
| `00_baseline_inference_metrics.ipynb` | Baseline HiCForecast inference + metrics + qualitative plots | Baseline predictions, metrics CSV, GT/Pred/Diff figures |
| `01_uncertainty_ensemble.ipynb` | Repeated inference (K runs) → mean prediction + pixel-wise std uncertainty maps | `pred_uncertainty_mean.npy`, `pred_uncertainty_std.npy`, uncertainty figures |
| `02_graph_diffusion_postprocess.ipynb` | Sparse top-k diffusion refinement applied to predictions (no retraining) | `pred_graphdiff.npy`, comparison figures, metrics CSV |
| `03_structure_aware_loss_metrics.ipynb` | Adds structure-aware diagnostics (insulation proxy + peak-weighted error) and evaluates variants | Structure metrics CSV + summary figures |

---

