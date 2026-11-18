# Phase 5c Priority 2 — A_s × c01 grid

## Configuration
- 5 A_s × 6 c01 (including c01=0 refs), 30 runs total
- tol_perturbations_integration = 1e-9
- Fixed background: scf_parameters shooting to Omega_scf=0.05

## Tests passed
1. A_s inertness at c01=0: 0.0e+00 across all A_s (no stray delta_s term)
2. Product law y(eps) = y_0 + eps*y_1 confirmed: equal-eps pairs agree
   at numerical floor (diff ~3e-8) over 50x range in eps (0.003 to 0.15)
3. K(l) constant across (A_s, c01) at fixed eps:
   - l=5:   K = 6.34e-3  (0.06% spread over 3 points)
   - l=20:  K = 1.27e-3  (0.08% spread)
   - l=200: K = 6.76e-6  (0.6% spread)
4. Log-log slope of |dC|/C vs eps:
   - l=5:   1.002 (20 points)
   - l=20:  1.002 (20 points)
   - l=200: 1.044 (7 points, under investigation)

## K(l) response kernel (per unit eps = A_s*c01)
- K(5)   = +6.34e-3
- K(20)  = +1.27e-3
- K(200) = +6.76e-6
- Signs all positive
- K(5)/K(20) = 5.0 ; K(20)/K(200) = 187
- Late-ISW-shaped (peaks at low l, sharp drop through acoustic region)

## Open item
- l=200 slope deviation from 1.0: investigate threshold / c01>1 unphysical

## K(l) response kernel — extended to low l

- K(2) = -4.31e-3  (SIGN FLIP — dominant ISW contribution changes sign at l=2)
- K(3) = +6.31e-3  (peak)
- K(5) = +6.34e-3  (peak)
- K(20) = +1.27e-3
- K(200) = +6.81e-6  (below tol=1e-9 floor for physical c01 < 1)

Physical interpretation:
- SW plateau is unchanged by c01/A_s (they don't affect recombination)
- All l=2-5 signal is therefore ISW
- Sign flip at l=2 means edm-modified dPhi/dtau is opposite to LCDM
  during deep DE domination (z<0.5), then reverses at z~1
- Signature plot: dC_l/C_l vs l shows negative dip at l=2, positive peak at l=3-5

Measurement limitation:
- l=200 signal at physical c01<1 is 3e-7 to 1e-6; near tol=1e-9 floor
- To map K(l) at acoustic scales requires tol=1e-10 or c01 -> 1 or P(k)
- Paper constraint from primary CMB at l>100 will be weak in the current specialization

## K(l) extended to low l — SIGN FLIP FOUND

Verified across 9 high-signal (A_s, c01) combinations. Universal:

    l=2:  K = -4.44e-3  (SIGN FLIP — ISW change reverses direction)
    l=3:  K = +6.28e-3  (peak)
    l=5:  K = +6.33e-3  (peak)
    l=20: K = +1.27e-3
    l=200: K = +6.81e-6 (below tol=1e-9 floor for physical c01<1)

Physical asymptote (extrapolating to eps->0):
    K_0(2) = -4.44e-3,  eps^2 correction: K/K_0 = 1 + 0.19*eps
    K_0(3) = +6.28e-3,  correction ~ +0.07*eps
    K_0(5) = +6.33e-3,  correction ~ +0.04*eps

Physical interpretation:
- A_s, c01 enter only perturbation equations, not recombination -> SW unchanged
- Entire l<=5 signal is ISW (large-angle)
- Sign flip: edm contribution to dPhi/dtau is opposite to LCDM during deep DE (z<0.5)
- Universal across parameter space; depends only on eps = A_s*c01

eps^2 correction origin (small, physical range fine):
- Not purely auto-correlation (b/a=0.19 vs K_0=4.4e-3 from |y_1|^2)
- Likely lensing of modified metric - footnote for paper
- At eps=0.15 correction is 3% (l=2), 1% (l=3), 0.6% (l=5)

Resolution of l=200 slope drift (was 1.044):
- c01>1 contamination pulls slope up
- Physical c01<1: only 2 points above 3e-7 floor at l=200
- K(200) signal at eps=0.15 is ~1e-6, near tol=1e-9 floor
- To constrain at acoustic scales: use P(k) at z=0 or tol=1e-10

## CORRECTION: ISW kernel argument for l=2 sign flip

j_l(x) peaks at x_peak ~ l+1/2. At l=2, k~1.4e-4 Mpc^-1, the peak
would sit at tau0-tau ~ 21000 Mpc -- BEYOND chi_rec = 14100 Mpc.
So j_2 NEVER samples its peak in the physical domain; its CMB
weight comes from the rising x^2/15 tail. For l=3, peak~16700 Mpc
(also beyond chi_rec), but j_3 at recombination sits at x~3.0,
close to peak. So l=3 samples the peak region and l=2 does not.
The sign flip reflects a redshift-dependent sign change in ISW
source across the two kernels' effective redshift slices.
(Corrected from earlier draft which quoted 21800 Mpc; the number
was arithmetically right but physically impossible -- chi_rec
caps the conformal distance integral at 14100 Mpc.)

## Lambda scan (P3): K(l; lambda) measurement

4 lambda values {0.1, 0.3, 0.6, 1.0}, 3 runs each (baseline c01=0,
A_s=0; A_s-only c01=0, A_s=0.3; physics c01=0.5, A_s=0.3), tol=1e-9.
All 12 runs exit=0, no shooting failures even at lambda=1.0.

A_s inertness: |dC/C| = 0.0e+00 for l=2,5,20 at ALL four lambda.
No stray delta_s term anywhere, for any lambda.

K(l; lambda) values:
   lambda    K(2)         K(3)         K(5)         K(20)
   0.1     -4.3145e-03   +6.3096e-03   +6.3414e-03   +1.2680e-03
   0.3     -1.2260e-02   +1.9112e-02   +1.9154e-02   +3.8341e-03
   0.6     -2.2469e-02   +3.8868e-02   +3.8789e-02   +7.7774e-03
   1.0     -3.2801e-02   +6.6558e-02   +6.6047e-02   +1.3273e-02

Effective power law d log|K| / d log lambda:
   K(5):  1.016   (linear -- B mechanism dominates)
   K(20): 1.019   (linear)
   K(2):  0.888   (SUB-linear -- new physics)

Ratio K(lambda)/K(0.1) vs naive prediction lambda/0.1:
   lambda   l=5 ratio/pred   l=2 ratio/pred
   0.1      1.000            1.000
   0.3      1.007            0.947
   0.6      1.019            0.868
   1.0      1.042            0.760

Sign of K(2) stays NEGATIVE across all four lambda (magnitude grows
from -4.3e-3 to -3.3e-2 -- 7.6x larger). Sign flip is robust.

V0(lambda) inference: K(5)*e^{lambda*phi(a=1)} is roughly constant
across lambda to ~7%, implying V0 grows ~7% from lambda=0.1 to
lambda=1.0 from shooting. This small V0 drift does not affect the
linear/sublinear conclusion.

Physical interpretation:
- At l=5, 20: B = c01*lambda*V0*e^{-lambda*phi} dominates, scales
  linearly in lambda as predicted. V0(lambda) drift contributes
  the 4% residual from unity.
- At l=2: BOTH lambda amplitude AND phi(a) rolling speed grow with
  lambda. The l=2 kernel integrates over a wide redshift slice
  (x^2/15 tail), so it weights the AVERAGE of dB/dtau, not the
  peak. Faster rolling at larger lambda sharpens the peak but
  leaves the average sublinear. Net K(2) ~ lambda^0.89.

NEW OBSERVABLE: K(2)/K(5) is lambda-dependent:
   lambda=0.1: ratio = -0.680
   lambda=0.3: ratio = -0.640
   lambda=0.6: ratio = -0.579
   lambda=1.0: ratio = -0.497
This breaks the amplitude-lambda degeneracy. K(5) measures
lambda*V0*e^{-lambda*phi}, while K(2)/K(5) measures lambda alone.
CMB data with <10% sensitivity to low-l shape can distinguish
lambda=0.1 from lambda=1.0.
