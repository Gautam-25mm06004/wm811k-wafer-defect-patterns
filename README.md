# Wafer-Map Defect Pattern Recognition and Yield-Loss Analysis (WM-811K)

**Remade project.** Based on the idea of [seunghyun949-dot/wafer-map-defect-classification](https://github.com/seunghyun949-dot/wafer-map-defect-classification) (WM-811K classification with a lot-aware split). This version takes a different, laptop-friendly approach: interpretable spatial features in the spirit of Wu, Jang & Chen (IEEE TSM, 2015) with Random Forest / gradient boosting instead of a CNN, plus yield-loss and lot/slot analysis.

**Data:** WM-811K (811,457 wafer bin maps, 172,950 expert-labelled into 9 classes). The notebook downloads it from Kaggle with your API key (environment variables, `~/.kaggle/kaggle.json`, or a hidden prompt; the key is never saved), or you can place `LSWMD.pkl` in `data/` yourself.

## What it does
- Audits labels, map sizes, duplicate maps and conflicting labels.
- Ranks patterns by total excess die loss (Pareto) and tests lot clustering and slot effects (permutation and χ² tests, FDR-controlled).
- Engineers 77 interpretable features (radial profile, 13-region density, Radon projections, largest-cluster geometry, spatial clustering).
- Trains Random Forest and gradient boosting on a lot-aware split, compares with a raw-pixel baseline, and shows how a random split overstates accuracy.
- Error analysis, feature-family importance by class, and predictions on unlabeled production wafers.

## Run
```bash
pip install -r requirements.txt
jupyter notebook wm811k_defect_patterns.ipynb   # needs ~4-6 GB free RAM for the first load; set CONFIG['quick'] = True for a fast trial
```
