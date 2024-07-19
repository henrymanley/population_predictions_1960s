# Population predictions for the 1960s, by county-age-year
Data appendix to Kose, Manley, Miller (2024)
---
>[!NOTE]
> Data and documentation in this repository are from the 07/19/2024 release

## Background
Before the Survey of Epidemiological End Results ([SEER](https://seer.cancer.gov/)) posted its first intercensal tabulation in 1969, the only available measure of population counts $-$ by county, age, and year $-$ was from the decadal Census. Consequently, there are no publicly available population counts for the years 1961-1968. Kose, Manley, Miller (2024) documents this occurence and puts forth a neural network model that predicts population counts for ages 1-20 in the years 1961-1968. Their predictions draw from a collection of over 200 predictive features and outperform a linear interpolation benchmark by 59\%. 

## Data provided in this repository
### 1. Prediction files
Each predictions ZIP file $-$ `kmm_population_predictions_1960s_[release date].zip` and `kmm_population_predictions_1970s_1980s_[release date].zip` $-$ contains one CSV file with ten variables: 

- `superfips`: county identifier
- `county_name`: US county name
- `state_abb`: two-character US state abbreviation
- `age`: single year of age (0-20).
- `year`: year
- `truth`: "true" population count reported by \{1960: the 1960 Census, 1969-1989: SEER\}
- `births`: the count of live births
- `li`: age-based linear interpolation of population counts between decadal endpoints (e.g., the interpolation of the counts of 5-year olds between 1960 and 1969)
- `yhat`: population prediction generated by the neural network model
- `kmm_population`: composite population measure, based on our list of implementation recommendations below

The file `kmm_population_predictions_1960s_[release date].zip` contains observations for the 1960s. The file `kmm_population_predictions_1970s_1980s_[release date].zip` contains observations for the 1970s and 1980s. We split these data into two files to respect GitHub's file size restriction of 25 MB. We recommend appending these two files, in practice. Though, if the principal interest is to use solely the population predictions for 1961-1968, the `kmm_population_predictions_1960s.zip` file will suffice. 

### 2. County identifier crosswalk file
The file `kmm_superfips_xwalk_[release date].csv` is a county indentifier crosswalk that links our preferred, time-constant, identifier $-$ "super FIPS" codes $-$ to FIPS and NCHS codes. The process by which we build our super FIPS code is described in the appendix to our paper. In general, super FIPS-level aggregation is meaningfully different from using FIPS codes for only a handful of counties. Most common are counties in Virginia, New York City, Hawaii, and Alaska.

## A note on the years available in our data
We include data for the 1970s and 1980s as a complement to the 1960s predictions, in terms of usability and scope. For instance, if a researcher is interested in studying a program administered in the 1960s and 1970s, our data makes it easy to use both our population predictions (`yhat`) in the 1960s and Census-based estimates (`truth`) in the 1970s without having to query another data source. Version release history can be found [here](https://github.com/henrymanley/population_predictions_1960s/commits/main/).

## Our recommended implementation
To ensure researchers use the "best" measures of population for their empirical usecase, we recommend that: 
- For the years 1960 and 1969-1989, use `truth` as your measure of population
- For the years 1961-1968, use `yhat` as your measure of population
- For 0-year olds (in all years), use `births` as your measure of population

Taken together, the `kmm_population` variable in our data implements these recommendations. 

## Citation
Please use the following citation when using this data:

Kose, Esra, Manley, Henry, Miller, Douglas L. 2024. _Backcasting Population Data for Children in the 1960s with
Supervised Learning._
