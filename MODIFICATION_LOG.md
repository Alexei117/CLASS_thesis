(.venv) diego@diego-83jc:~/class_mycosmo$ python3 -c "                                      
import numpy as np
a = np.loadtxt('/home/diego/class_public/output/test_vanilla00_background.dat')
b = np.loadtxt('/home/diego/class_mycosmo/output/test_lcdm_limit00_background.dat')
print('Test 1  shapes:  vanilla', a.shape, '  mycosmo', b.shape)
assert a.shape[0] == b.shape[0], 'row count differs - not the same a-grid'
assert np.allclose(a[:, 0], b[:, 0]), 'a-column differs - not the same a sampling'
print('Test 1  max |H_vanilla - H_mycosmo| / |H| =', np.max(np.abs(a[:, 3] - b[:, 3]) / np.abs(a[:, 3])))
"
Test 1  shapes:  vanilla (40000, 23)   mycosmo (40000, 23)
Test 1  max |H_vanilla - H_mycosmo| / |H| = 0.0


(.venv) diego@diego-83jc:~/class_mycosmo/source$ python3 -c "
import numpy as np
a2 = np.loadtxt('/home/diego/class_public/output/test_vanilla00_background.dat')
b2 = np.loadtxt('/home/diego/class_mycosmo/output/test_edm_as_cdm00_background.dat')
print('Test 2  shapes:  vanilla', a2.shape, '  mycosmo', b2.shape)
assert a2.shape[0] == b2.shape[0], 'row count differs - not the same a-grid'
assert np.allclose(a2[:, 0], b2[:, 0]), 'a-column differs - not the same a sampling'
print('Test 2  max |H_vanilla - H_edm|/|H| =', np.max(np.abs(a2[:, 3] - b2[:, 3]) / np.abs(a2[:, 3])))
"
Test 2  shapes:  vanilla (40000, 23)   mycosmo (40000, 24)
Test 2  max |H_vanilla - H_edm|/|H| = 1.5860014692134212e-10

ODE (in perturbations)
Residual ≤ 3e-4. Verified physics-correct in every measurable way. Residual is a numerical artifact from the extended state vector's effect on ndf15 error-norm computation. Tight tolerance doesn't help. Not fixable without restructuring (or without native CLASS support for multiple dust species). Irrelevant for physics: 10× below Planck measurement precision, 100× below Phase 5b-3 coupling effects.
