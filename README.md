# Gravitational Microlensing: Parameter Estimation Using Parabolic and Point-Lens Fits to OGLE Data

**Maya Shechter and Yinon Gruper · Tel Aviv University**

## Project overview

We analyzed OGLE I-band photometry for the microlensing events OGLE-2024-BLG-0010 and OGLE-2024-BLG-0056. In Part A, we fitted a parabola near the peak of each light curve and used bootstrap resampling to estimate uncertainties in the peak time $t_0$, the minimum impact parameter $u_0$, and the Einstein crossing time $t_E$. In Part B, we fitted a point-source, point-lens model using grid searches and numerical refinement, with the source fraction fixed or fitted depending on the analysis. We also used 10,000 Monte Carlo trials to test how well the two-parameter fit recovered $u_0$ and $t_E$ under simulated photometric noise.

The notebooks can be adapted to other OGLE microlensing events with standard `phot.dat` photometry. The point-lens analyses apply to events that are well described by the point-source, point-lens model. The parabolic fit also requires enough observations close to the peak.

## Analysis notebooks

| File | What it does | Inputs | Outputs |
| --- | --- | --- | --- |
| [PartA-ParabolicFit.ipynb](PartA-ParabolicFit.ipynb) | Estimates baseline flux from the faintest 30% of measurements, fits a weighted parabola near the peak, and uses 10,000 bootstrap resamples to estimate parameter uncertainties. | OGLE `phot.dat` URL, number of near-peak points, adopted source fraction, and OGLE reference parameters and uncertainties. | Estimates and bootstrap uncertainties for $t_0$, $u_0$, and $t_E$, reduced chi-square, and three PDFs showing the full light curve, the bootstrap histograms, and the near-peak fit with residuals. |
| [PartB-2ParameterGridSearch.ipynb](PartB-2ParameterGridSearch.ipynb) | Searches over $u_0$ and $t_E$ while holding $t_0$ and the source fraction fixed, then refines the best fit. | OGLE `phot.dat` URL, fixed peak time and source fraction, initial guesses, and grid bounds and steps. | Refined estimates and profile chi-square uncertainties for $u_0$ and $t_E$, a fit summary, full and zoomed light-curve plots with residuals, and a corner plot. |
| [PartB-4ParameterGridSearch.ipynb](PartB-4ParameterGridSearch.ipynb) | Searches over $t_0$, $u_0$, $t_E$, and the source fraction, allowing for blended light, then refines the best fit. | OGLE `phot.dat` URL, event-specific initial guesses, and grid bounds and steps for all four parameters. | Refined parameter estimates and profile chi-square uncertainties, a fit summary, full and zoomed light-curve plots with residuals, and a corner plot. |
| [PartB-MonteCarlo.ipynb](PartB-MonteCarlo.ipynb) | Generates noisy light curves at the OGLE observation times and refits each one to test recovery of $u_0$ and $t_E$. | OGLE `phot.dat` URL or uploaded local photometry file, input model parameters, random seed, and the number of trials (`N_TRIALS`). | `fits.csv` with the recovered parameters for each trial and `parameter_distributions.png` showing their distributions. |

## Photometry files

The input data come from the OGLE Early Warning System. Each `phot.dat` file contains observation times, I-band magnitudes, and magnitude uncertainties. The notebooks use these measurements to fit the light curves or to set the observation times and noise levels for the Monte Carlo simulations.

| File | Source and use |
| --- | --- |
| `data/OGLE-2024-BLG-0010/phot.dat` | Photometry for event 0010. Used in the Part A fit, both Part B grid searches, and the Monte Carlo analysis. |
| `data/OGLE-2024-BLG-0056/phot.dat` | Photometry for event 0056. Used in the Part A fit and the four-parameter Part B fit. |



