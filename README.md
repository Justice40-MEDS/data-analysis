# Data Analysis for an Improved Climate and Economic Justice Screening Tool
This repository houses Python notebooks for exploration of the data from the Climate and Economic Justice Screening Tool (CEJST). It also contains calculations for a cumulative approach and a spatial clustering approach to burden aggregation.
## About
Two methods are used to add layers to the original CEJST. The first method, a cumulative analysis, simply adds together the total number of CEJST thresholds exceeded by the census tract (see table below for threshold information). This means each census tract will have a score of 0-8 (based on burdens) or 0-31 (based on indicators).
The hotspot analysis will use Getis-Ord Gi* (Gi*) to identify spatial clusters that represent statistically significant hot or cold spots, based on the total number of burden or indicator thresholds exceeded. Gi* examines an individual census tract and its neighbors to assign a z-score based on the global statistics for the entire United States (Getis & Ord 1992). The z-score will be mapped to identify hot or cold spots that show areas of significantly high or low burdens, respectively, compared to areas with no significant clustering.
These new approaches will generate census tract-level cumulative burden scores that better reflect the total impact of climate stressors on communities, as compared to the original CEJST scoring index. Additionally, there will be a demographic layer that will not affect the scoring index but be used to compare demographic composition of DACs in the original CEJST and in the new approaches. This repository contains graphs of the demographic breakdown of the new methods.
### Burden and Indicator Thresholds
| Burden | Indicators | Socioeconomic Burden |
| ------------- | ------------- | ------------- |
| Climate change | Expected agriculture loss rate ≥ 90th percentile OR Expected building loss rate ≥ 90th percentile OR Expected population loss rate ≥ 90th percentile OR Projected flood risk ≥ 90th percentile OR Projected wildfire risk ≥ 90th percentile | Low Income* |
| Energy | Energy cost ≥ 90th percentile OR PM2.5 in the air ≥ 90th percentile  | Low Income* |
| Health | Asthma ≥ 90th percentile OR Diabetes ≥ 90th percentile OR Heart disease ≥ 90th percentile OR Low life expectancy ≥ 90th percentile | Low Income* |
| Housing | Historic underinvestment = Yes OR Housing cost ≥ 90th percentile OR Lack of green space ≥ 90th percentile OR Lack of indoor plumbing ≥ 90th percentile OR Lead paint ≥ 90th percentile | Low Income* |
| Legacy pollution | Abandoned mine land present = Yes OR Formerly Used Defense Site (FUDS) present = Yes OR Proximity to hazardous waste facilities ≥ 90th percentile OR Proximity to Superfund or National Priorities List (NPL) sites ≥ 90th percentile OR Proximity to Risk Management Plan (RMP) sites ≥ 90th percentile | Low Income* |
| Transportation | Diesel particulate matter ≥ 90th percentile OR Transportation barriers ≥ 90th percentile OR Traffic proximity and volume ≥ 90th percentile | Low Income* |
| Water and wastewater | Underground storage tanks and releases ≥ 90th percentile OR Wastewater discharge ≥ 90th percentile | Low Income* |
| Workforce development | Linguistic isolation ≥ 90th percentile OR Low median income ≥ 90th percentile OR Poverty ≥ 90th percentile OR Unemployment ≥ 90th percentile | Less than high school education > 10% |
## Data
The MEDS Justice40 team has found 3 aggregate data sources from Verion 2.0 of the CEJST tool. These data sources can be found in the original tool's github repository [here](https://github.com/agilesix/j40-cejst-2-dev-fork/blob/main/data/data-pipeline/README.md).
- `usa_v2.csv` is a large csv file containing 74134 observations of 242 variables. It has all the burdens and their unique criteria, including raw numbers/percentages as well as boolean values for whether a census tract meets a criteria or burden threshold. This file does not contain geospatial data, nor information on state or county, only census tract.
- `2.0-communities` csv file with 74134 observations of 136 variables. A pared down version of usa_v2.csv, still not 100% exactly what's different between the two. This file does have information on state and county, which is what we will use for our preliminary statistical analysis.
- `2.0-shapefile-codebook` geospatial data encoded in a shapefile with a companion codebook csv. Still don't know exactly what the codebook tells us or how to use it in tandem with the shapefile.
## Repository Structure
```
data-analysis│
├── README.md
├── .gitignore
├── LICENSE
│
├── docs/
│  ├──demographic-viz.qmd           # Cumulative analysis demographic breakdown visualization
│  ├──demographics.ipynb            # Data analysis for demographic visualization
│  ├──gistar-tuning.ipynb           # Hotspot analysis (Getis-ord Gi*)
│  ├──initial-exploration.ipynb     # Initial exploration of data files
│  └──mapping-viz.ipynb             # Mapping for both cumulative and hotspot analysis
├── env-files/
│  ├──justice40-env.yml             # Environment for project
│  ├──pythonenv_instructions.txt    # Instructions for Python environment and user kernel
│  └──requirements.txt              # Libraries and software requirements
├── fonts/
├── images/
│  ├──burden_map.png                # Static map of cumulative burden analysis
│  ├──dac.png                       # Graph of demographics of DAC and Non-DAC
│  ├──dem_burd.png                  # Graph of demographics of cumulative burden analysis
│  ├──dem_ind.png                   # Graph of demographics of cumulative indicator analysis
│  ├──ind_map.png                   # Static map of cumulative indicator analysis
│  ├──pop_burd.png                  # Graph of populations for cumulative burden analysis
│  └──pop_ind.png                   # Graph of populations for cumulative indicator analysis
```
## Authors
- [Josephine Cardelle](https://github.com/jocardelle)
- [Kat Le](https://github.com/katleyq)
- [Haylee Oyler](https://github.com/haylee360)
- [Kimberlee Wong](https://github.com/kimberleewong)
