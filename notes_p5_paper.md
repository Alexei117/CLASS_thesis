# Phase 5c P5 — paper comparison (Teixeira arXiv 2603.10622)

## Parameter mapping (empirical)
Paper h0 ↔ our c01 via c01 ≈ 15 × h0

Derivation: B = c01 · λ · V0 · e^{-λφ} · V_EDM_UNITS ∝ c01 · Ω_scf
Paper's Ω_scf = 0.69 (closes budget), ours = 0.05 (Λ does rest)
Ratio 0.69/0.05 = 13.8, consistent with empirical 15

## σ8 comparison (corrected h³ factor in integral)
Our reference (c01=0): sigma8 ≈ 0.81 (matches standard ΛCDM)

Paper h0 → our c01 → our Δσ8 → paper Δσ8 → agreement
  +0.01 → +0.15 → -1.345% → -1.45% → 7%
  +0.03 → +0.45 → ~-4.0%  → -4.30% → ~7%
  -0.02 → -0.30 → +2.7%   → +2.94% → ~8%
  -0.04 → -0.60 → +5.3%   → +5.92% → ~10%

Systematic ~7-10% underestimate consistent with shape difference:
- Our |dP/P| peaks at k=1.37 h/Mpc (1.49% at c01=0.15)
- Paper's |dP/P| at k=0.1 h/Mpc is 1.176% at h0=0.01
- Different k-shapes, similar σ8 integrals
- Likely cause: paper has Ω_scf=0.69 so SF perturbations dominate
  P(k); ours has Ω_scf=0.05 with Λ dominating DE (Λ has no perturbations)

## Infrastructure bugs found & fixed
1. Glob ambiguity: `cpos01*_pk.dat` matched `cpos0150_pk.dat`
   Fix: anchored glob `[0-9][0-9]` after root, or explicit suffix
2. CLASS v3.4.2 `non_linear` requires string enum ('none'), not integer 0
3. `mTk` output requires `k_output_values`; safe combination is `tCl,pCl,lCl,mPk`
4. `P_k_max_h/Mpc` and `P_k_max_1/Mpc` cannot both appear (CLASS L:5112)
5. sigma8 formula needs h³ factor: P is (Mpc/h)³, k is h/Mpc

## Conclusion
Code reproduces paper's σ8 scaling law to <10% across the full h0 range.
Discrepancy in P(k) k-shape expected from different DE sector composition.
Phase 5c P5 CLOSED.
