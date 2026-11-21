# Gravitational Microlensing

**Maya Shechter and Yinon Gruper · Tel Aviv University**

This repository contains the Python notebooks for our gravitational microlensing lab project. We analyzed OGLE-2024-BLG-0010 and OGLE-2024-BLG-0056 to estimate the time of peak magnification ($t_0$), the minimum impact parameter ($u_0$), and the Einstein crossing time ($t_E$).

The notebooks are reusable for other OGLE microlensing events that have photometry in the standard `phot.dat` format and are well described by a point-source, point-lens model. The two events in our report are examples. To analyze a different event, update the photometry URL and the event-specific settings before running the notebook.

## Notebooks

| Notebook | What it does |
| --- | --- |
| [Part A — Parabolic Fit](PartA-ParabolicFit.ipynb) | Fits a weighted parabola to observations near peak magnification. Estimates the baseline flux from the faintest 30% of measurements and uses 10,000 bootstrap resamples to estimate parameter uncertainties. |
| [Part B — Two-Parameter Grid Search](PartB-2ParameterGridSearch.ipynb) | Fits $u_0$ and $t_E$ with the peak time and source fraction held fixed. Refines the grid-search result and estimates uncertainties from the chi-square profiles. |
| [Part B — Four-Parameter Grid Search](PartB-4ParameterGridSearch.ipynb) | Fits $t_0$, $u_0$, $t_E$, and the source fraction, allowing for blended light. Refines the grid-search result and estimates uncertainties from the chi-square profiles. |
| [Part B — Monte Carlo](PartB-MonteCarlo.ipynb) | Simulates and refits 100,000 noisy light curves using the OGLE observation times and photometric uncertainties to evaluate how well the fit recovers $u_0$ and $t_E$. |

## How to run

1. Open the notebook in Google Colab.
2. Use the default settings for OGLE-2024-BLG-0010, or replace `OGLE_URL` (called `DATA_URL` in the Monte Carlo notebook) with the direct `phot.dat` URL for your event.
3. Update the settings for your event. In Part A, set the number of near-peak points, the adopted source fraction, and the OGLE reference values and uncertainties. For the grid searches, set the initial guesses, fixed values, and search bounds. For Monte Carlo, update the parameters used to generate the simulated light curves.
4. Select **Runtime → Run all**.

