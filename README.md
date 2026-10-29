# Synchrotron light-source lattice tutorial

Open [notebook_00_light_source.ipynb](notebook_00_light_source.ipynb) and run it from top to bottom.

This intermediate tutorial builds a 3 GeV electron ring from scratch with 16 double-bend achromat cells. It covers periodic optics matching, dispersion-free straights, ring closure, chromaticity correction, RF focusing, radiation-integral convergence, 6D radiation equilibrium, and source-point beam sizes. It includes explanations, plots, numerical checks, and six design exercises.

The lattice is an ideal teaching model, with no external lattice files or MAD-X dependency. Allow about 60–90 minutes including exercises.

## Run

In your chosen Python environment:

```bash
python -m pip install xsuite numpy scipy pandas matplotlib jupyterlab ipykernel
python -m jupyterlab notebook_00_light_source.ipynb
```

Select the corresponding Python kernel. The first cell prints package versions. If you change geometry or design parameters, restart the kernel and run all cells to rebuild the derived lines.

## Validation

All 17 code cells executed successfully with Python 3.13, Xtrack 0.111.6, and Xobjects 0.6.10. Outputs are included. Execution took about 12 seconds in the local environment with available tracking kernels; first-time compilation can take longer.

The default model gives:

| Quantity | Result |
|---|---:|
| Circumference | 208.8 m |
| Tunes, without radiation | 11.22 / 4.18 |
| Corrected chromaticities | +1 / +1 |
| Energy loss per turn | 0.938 MeV |
| Horizontal equilibrium emittance | 98.5 nm |
| RMS relative momentum spread | 9.28 × 10⁻⁴ |
| RMS bunch length at the first straight | 5.16 mm |
| Horizontal / vertical amplitude damping times | 4.48 / 4.46 ms |
| Longitudinal amplitude damping time | 2.22 ms |

The emittance changes by 0.14% between 16 and 32 thick slices per bend. The notebook compares radiation-integral predictions with the full 6D radiation analysis and checks survey closure, matching targets, and analytical bend integrals.

The ideal lattice has essentially zero vertical equilibrium emittance; the separate vertical beam-size example explicitly assumes a finite vertical emittance. The tutorial does not establish dynamic aperture, momentum acceptance, or lifetime. Optional JSON export commands are provided at the end.
