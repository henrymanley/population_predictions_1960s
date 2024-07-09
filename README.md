# Population predictions for the 1960s by county-age-year

**Data Appendix for Kose, Manley, Miller (forthcoming):** _Backcasting Population Data for Children in the 1960s with Supervised Learning_
---

## Background
Before the Survey of Epidemiological End Results (SEER) posted their first intercensal tabulation in 1969, the only available measure of population counts $-$ by county, age, and year $-$ was from the decadal Census. Consequently, there are no publicly available population counts for the years 1961-1968. Kose, Manley, Miller (forthcoming) documents this occurence and puts forth a neural network model that predicts population counts for ages 1-20 in the years 1961-1968. Their predictions draw from a collection of over 200 predictive features and outperform a linear interpolation benchmark by 57\%. 

## Data provided in this repository
This repository contains one CSV file: `kose_manley_miller_population_predictions.csv`. This file contains five variables: 
- `superfips`: county identifier
- `age`: age (integer: 0-20).
- `year`:
- `truth`:
- `li`:
- `yhat`:
