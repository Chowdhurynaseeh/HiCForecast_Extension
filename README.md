## Contents

| Notebook | Experiment | What it does | Main outputs |
|---|---|---|---|
| `00_baseline_inference_metrics.ipynb` | Baseline reproduction | Runs the repository-provided HiCForecast pretrained inference pipeline on the Chr19 example, reconstructs predicted contact maps, applies fixed GT matching, and reports baseline metrics. | Baseline predictions, GT-matching heatmap, PCC/SSIM/PSNR/MAE/MSE metrics, GT/Pred/Error qualitative figures |
| `Exp 1A Deterministic repeat control.ipynb` | Exp 1A: Repeated deterministic inference | Runs the same pretrained checkpoint repeatedly on identical inputs to test whether deterministic inference produces meaningful uncertainty. | Prediction mean, near-zero pixel-wise standard deviation maps, deterministic uncertainty negative-control results |
| `Exp 1B Seeded checkpoint ensemble.ipynb` | Exp 1B: Seeded checkpoint ensemble | Fine-tunes three ensemble members from the pretrained checkpoint using different random seeds and computes ensemble mean, ensemble standard deviation, uncertainty-error correlation, and high/low uncertainty error ratios. | Ensemble mean maps, ensemble std maps, uncertainty reliability table, top-5% uncertainty error analysis, uncertainty reliability figure |
| `Exp 2A Sparse graph diffusion.ipynb` | Exp 2A: Sparse graph diffusion | Applies sparse top-`k` row-normalized graph diffusion as a non-learned post-processing step to test whether graph-inspired smoothing improves or harms predictions. | Graph-diffused predictions, graph diffusion metrics, GT/GraphDiff/Error comparison figures |
| `Exp 2B Uncertainty-guided refiner.ipynb` | Exp 2B: Uncertainty-guided residual refiner | Trains a lightweight patch-level residual refiner using ensemble mean and ensemble standard deviation as two input channels. | Refined predictions, trained refiner checkpoint, validation loss, refined prediction metrics |
| `Shared evaluation (initial).ipynb` | Initial structure-aware diagnostics | Evaluates the first structure-aware diagnostic setup for baseline, deterministic uncertainty mean, and graph diffusion. | Initial TAD insulation proxy and peak-weighted $\ell_1$ metrics, insulation-profile diagnostic plots |
| `Shared evaluation (main).ipynb` | Final shared evaluation | Evaluates the final compared methods under the same structure-aware diagnostics: baseline, seeded ensemble mean, graph diffusion, and uncertainty-guided refiner. | Final structure-aware metric table, Table III values, TAD insulation proxy scores, peak-weighted $\ell_1$ scores, structure-aware trade-off figure |

## Recommended Execution Order

1. `00_baseline_inference_metrics.ipynb`
2. `Exp 1A Deterministic repeat control.ipynb`
3. `Exp 1B Seeded checkpoint ensemble.ipynb`
4. `Exp 2A Sparse graph diffusion.ipynb`
5. `Exp 2B Uncertainty-guided refiner.ipynb`
6. `Shared evaluation (initial).ipynb`  *(optional initial diagnostic check)*
7. `Shared evaluation (main).ipynb`  *(final evaluation used in the manuscript)*

The final manuscript primarily uses the results from Exp 1B, Exp 2A, Exp 2B, and `Shared evaluation (main).ipynb`. The deterministic repeat-control notebook is retained as a negative-control uncertainty experiment.
