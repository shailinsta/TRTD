# TRTD: Temporal Riemannian Trust Deformation

**Temporal Riemannian Trust Deformation (TRTD) for Continuous Zero-Trust Verification under Federated Network Drift**

This repository contains the experimental notebook, generated figures, and result tables for the TRTD framework.

## Overview

TRTD is a geometry-aware framework for federated intrusion detection and continuous Zero-Trust verification under concept drift. Network behaviour is represented as trajectories on the manifold of symmetric positive-definite (SPD) covariance states. Local traffic changes are encoded as tangent-space deformations and transported between successive reference states using affine-invariant parallel transport. TRTD combines geometric deviation with a temporal deformation residual to derive a drift-adaptive trust score and Zero-Trust policy boundary.

Federated clients transmit clipped low-rank tangent deformations with differential-privacy protection; the server updates the global behavioural state through the Riemannian exponential map.

## Key Results (Paper §5)

- Mean MCC of **0.374 ± 0.046** and balanced accuracy **0.681** across dataset–drift combinations.
- vs Distance-only: **+0.102 MCC** (p < 0.0001).
- vs Fixed-θ: **−0.050 FIR** (p = 0.0002).
- Under stealth drift: mean MCC improvement remains **+0.094**.
- Recovery latency reduced from **5.8 → 3.8** rounds vs Distance-only.
- FIR of **0.078** vs **0.128** for Fixed-θ.
- At ε = 1.50, MCC remains above 0.35 across all four datasets.
- Low-rank representation reduces communication volume by **25%** (max |ΔMCC| = 0.011).

## Repository Structure

```
TRTD/
├── TRTD_complete_pipeline.ipynb   # Full experimental notebook (leakage-free pipeline)
├── README.md
├── requirements.txt
├── figures/
│   ├── fig1_mcc_heatmap.png
│   ├── fig2_ablation_bars.png
│   ├── fig3_recovery_fir.png
│   ├── fig4_ece.png
│   └── fig5_privacy_utility.png
├── results/
│   ├── tableA_detection.csv
│   ├── tableB_ablations.csv
│   ├── tableC_rq1_gap.csv
│   ├── tableD_privacy_utility.csv
│   ├── tableE_rank.csv
│   ├── mcc_by_variant_drift.csv
│   ├── summary_metrics.csv
│   └── wilcoxon_stats.csv
└── tables/                        # Same CSVs for convenience
    └── ...
```

## Datasets

Experiments use four public network-security datasets:

- NF-CSE-CIC-IDS2018
- NF-ToN-IoT
- UNSW-NB15 (test set)
- CIDDS-001 (OpenStack)

Four drift regimes: **abrupt**, **gradual**, **recurring**, and **stealth**.

## Colab Notebook

Interactive version of the pipeline:

https://colab.research.google.com/drive/16j4PAllcbsoSo4JxTJDCZw_hAfnLRBFb?usp=sharing

## How to Run

```bash
pip install -r requirements.txt
jupyter notebook TRTD_complete_pipeline.ipynb
```

Or open the notebook in Google Colab via the link above.

## Ablation Variants

| Variant              | Description                                      |
|----------------------|--------------------------------------------------|
| Full TRTD            | Temporal residual + adaptive θ + DP + low-rank  |
| Distance-only        | Instantaneous geometric distance only            |
| Fixed threshold θ    | Adaptive θ replaced by fixed threshold           |
| No-DP-noise          | Differential privacy disabled                    |
| Full-rank            | Dense tangent (no low-rank compression)          |

## Citation

If you use this code or results, please cite the TRTD paper:

```
Shailendra Mishra, Megha Rathi, Saumitya Srivastava, Reem Alshenaifi, Indu Dohare.
Temporal Riemannian Trust Deformation (TRTD) for Continuous Zero-Trust Verification under Federated Network Drift.
```

## Authors

1. Shailendra Mishra (Corresponding author) – Majmaah University  
2. Megha Rathi – Jaypee Institute of Information Technology  
3. Saumitya Srivastava – Jaypee Institute of Information Technology  
4. Reem Alshenaifi – Majmaah University  
5. Indu Dohare – Motilal Nehru National Institute of Technology Allahabad  

## License

Research code released for reproducibility. Please respect dataset licenses of the underlying public IDS benchmarks.

## DOI

(To be added after Zenodo release)
