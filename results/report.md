# FloodGuard AI - Results Summary

_Generated automatically by the notebook on 2026-10-15 19:50. Research prototype - not an operational forecast system._

## Run identity
- **Model**: LarNO (Latent Autoregressive Neural Operator), official pretrained checkpoint
- **Checkpoint**: `model_epoch_992_error@0.000055821` (epoch 992), experiment `20260220_183648_006352`
- **Model source**: https://huggingface.co/holmescao/LarNO (exp_weights.zip)
- **Code**: official repository https://github.com/holmescao/LarNO, entry point `test.py`
- **Dataset**: LarNO benchmark, Futian district Shenzhen, `region1_20m` (20 m / 5 min, 6 h events)
- **Evaluated events**: event65, event66 (official test split, subset)
- **Ground truth**: MIKE+ hydrodynamic simulations (not field observations)

## Hardware & runtime
- **Environment**: Google Colab = True | Linux | Python 3.13.15
- **Device**: GPU: Tesla T4
- **Official inference wall time (all evaluated events)**: 84.8 s
- **Determinism**: eval mode, fixed event order, no dropout; predictions are deterministic

## Evaluation metrics (official implementation, verified by independent recomputation)
| Event | R2 | MSE | RMSE | MAE | PeakR2 | CSI |
|---|---|---|---|---|---|---|
| event65 | 0.993608 | 1.7e-05 | 0.004119 | 0.001988 | 0.986346 | 0.846333 |
| event66 | 0.993779 | 1.7e-05 | 0.004162 | 0.002035 | 0.986853 | 0.852405 |
| Overall (mean±std) | 0.993693±0.000086 | 0.000017±0.000000 | 0.004140±0.000021 | 0.002012±0.000024 | 0.986599±0.000253 | 0.849369±0.003036 |

- Metrics are computed by the official `test.py` on all 72 timesteps x 400 x 560 cells, in metres.
- Independent recomputation from the saved arrays matched the official values within 1e-4 (see Section H).

## Observations from the visualizations
- The rainfall event totals 24.2 mm (domain mean); reference flooding is spatially concentrated.
- Maximum reference depth for event65: 2.20 m; flooded footprint (depth > 3 cm at any time): 14.63% of cells.
- LarNO reproduces the flood footprint well (CSI ≈ 0.85) and the peak frame (PeakR² ≈ 0.987).
- The model output is not constrained to be non-negative (observed minimum across predictions: -0.0259 m), a known characteristic of the official model; map displays floor values at 0.

## Known limitations & error sources
- Ground truth is a **simulated** reference (MIKE+), not observed flooding; the confidential drainage network is not an input.
- Released data is a 20 m downsample of the paper's 5 m experiments - metrics differ from the paper's headline numbers.
- Rare extreme events, sensor/forcing errors and unmodelled infrastructure outfalls are not represented.
- **These numbers describe the Shenzhen benchmark only and are not evidence of predictive accuracy in Egypt or anywhere else.**

## Egypt disclaimer
No LarNO prediction for Egypt is produced anywhere in this notebook. See `Egypt_data_readiness_checklist.md`
(Part 2) for the required data and validation steps before any Egypt experiment could be scientifically defensible.
