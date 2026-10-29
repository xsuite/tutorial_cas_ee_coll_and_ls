# BESSY II–inspired light-source lattice tutorial

Open [notebook_00_light_source.ipynb](notebook_00_light_source.ipynb) and run it from top to bottom.

This intermediate tutorial builds a self-contained, 1.7 GeV teaching ring inspired by BESSY II: 240 m circumference, 16 double-bend achromat cells, and nominal tunes 17.84 / 6.82. Each 15 m cell has one focusing quadrupole between the bends and three quadrupoles on each outer side. Four families match both tunes, zero straight-section dispersion, and a horizontal source-point beta of 1.2 m.

The cell phase advances are 401.4° / 153.45°, with horizontal / vertical straight-centre beta functions of 1.2 / 3.22 m. All 16 cells are identical, with 5.6 m magnet-free straights. Real BESSY II has alternating high- and low-beta straights and a more elaborate magnet layout. This is a toy design, not an operational BESSY II model.

It covers periodic optics matching, dispersion-free straights, ring closure, chromaticity correction, RF focusing, radiation-integral convergence, 6D radiation equilibrium, and source-point beam sizes. It includes explanations, plots, numerical checks, and six design exercises.

The lattice is an ideal teaching model, with no external lattice files or MAD-X dependency. Allow about 60–90 minutes including exercises.

## Run

In your chosen Python environment:

```bash
python -m pip install xsuite numpy scipy pandas matplotlib jupyterlab ipykernel
python -m jupyterlab notebook_00_light_source.ipynb
```

Select the corresponding Python kernel. The first cell prints package versions. If you change geometry or design parameters, restart the kernel and run all cells to rebuild the derived lines.

## Validation

All 18 nonempty code cells executed successfully with Python 3.13, Xtrack 0.111.6, and Xobjects 0.6.10. Outputs are included. Execution took about 15 seconds in the local environment with available tracking kernels; first-time compilation can take longer.

The default model gives:

| Quantity | Result |
|---|---:|
| Beam energy | 1.7 GeV |
| Circumference | 240 m |
| Cell / straight length | 15 / 5.6 m |
| Tunes, without radiation | 17.84 / 6.82 |
| Phase advances per cell | 401.4° / 153.45° |
| Straight-centre beta functions, without radiation | 1.20 / 3.22 m |
| Corrected chromaticities | +1 / +1 |
| RF voltage / frequency / harmonic number | 1.5 MV / 499.654 MHz / 400 |
| Energy loss per turn | 170.7 keV |
| Horizontal equilibrium emittance | 15.4 nm |
| RMS relative momentum spread | 6.99 × 10⁻⁴ |
| RMS bunch length at the first straight | 3.05 mm |
| Horizontal / vertical amplitude damping times | 16.05 / 15.95 ms |
| Longitudinal amplitude damping time | 7.95 ms |

The emittance changes by 0.11% between 16 and 32 thick slices per bend. Chromaticities are rematched after slicing the sextupoles. The notebook compares radiation-integral predictions with the full 6D radiation analysis and checks survey closure, matching targets, and analytical bend integrals. The borrowed tune targets do not establish nonlinear acceptance for this different lattice.

The emittance is a calculation for this toy, not a BESSY II performance claim. At fixed optics it scales to roughly 48 nm at 3 GeV; changing the energy must not be confused with optimizing the lattice.

The ideal lattice has essentially zero vertical equilibrium emittance; the separate vertical beam-size example explicitly assumes a finite vertical emittance. The tutorial does not establish dynamic aperture, momentum acceptance, or lifetime. Optional JSON export commands are provided at the end.

## Reference parameters

- [BESSY II lattice design (1993)](https://proceedings.jacow.org/p93/PDF/PAC1993_1474.PDF): reference energy, circumference, cell count and nominal tunes.
- [BESSY II straight-section optics (2011)](https://accelconf.web.cern.ch/ipac2011/papers/thpc155.pdf): representative high- and low-beta source points.

Magnet lengths and strengths, the uniform-cell layout, and the RF voltage are choices for the tutorial. No external lattice file is needed to run it.
