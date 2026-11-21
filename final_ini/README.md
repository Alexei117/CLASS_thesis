# Phase 5c — curated ini files

33 inis reproducing all Phase 5c results (P1–P5) and the 5 P6 plots.
Run from parent directory: `./class final_ini/p5_paper_cp001.ini`

## Subsets

### p1_ee_* (6) — EE linearity at tol=1e-9
c01 ∈ {0, 0.1, 0.5, 1, 2, 5}, A_s=0.01, λ=0.1.
Proves EE residual scales linearly in c01 once tol=1e-9.
Data in `output_archive_5c_p1_2nd/`.

### p2_* (3) — K(ℓ) kernel + A_s inertness
- As0p3_c0    : reference (A_s=0.3, c01=0)
- As0p3_c0p5  : signal    (A_s=0.3, c01=0.5) — for K(ℓ) plot
- As0p03_c0   : A_s=0.03, c01=0 — for inertness check vs As0p3_c0

Full 30-file A_s×c01 grid preserved in main dir (`test_5c_p2_*.ini`).

### p3_L* (8) — λ-scan
4 λ ∈ {0.1, 0.3, 0.6, 1.0}, each baseline (c01=0, A_s=0) and physics (c01=0.5, A_s=0.3).
Yields K(5) ∝ λ^1.02, K(2) ∝ λ^0.89 (new observable K(2)/K(5)).

### p4_kc* (8) — kc-scan
One baseline (kc1p0_baseline; kc doesn't affect c01=0 so this serves all) +
7 physics at kc ∈ {1.0, 0.3, 0.1, 0.03, 0.01, 0.003, 0.001}.
Yields k_eff(ℓ): k_eff(5)=2.7e-3, k_eff(200)=2.1e-2 Mpc^-1.

### p5_paper_* (8) — paper comparison (Teixeira 2603.10622)
c01 mapping to paper's h0 via c01 = 15·h0:
  c0 → 0       cp001 → +0.01   cpos015 → +0.15 (≡ h0=+0.01)
  cp045 → +0.45 (≡ h0=+0.03)   cneg01 → -0.01
  cneg015 → -0.15              cn030 → -0.30 (≡ h0=-0.02)
  cn060 → -0.60 (≡ h0=-0.04)
Reproduces σ8 shift to <8% across full paper range.

## Plot regeneration
Plots live in `output/plots/01_*.png` … `05_*.png`.
See `handoff_class_phase5c_complete.txt` §12 for the plotting script.
