# Uber Rides Analysis — New York City (2014–2015)

Exploratory data analysis and geographic clustering of Uber pickup data in New York City.

## Data

- **2014**: six monthly CSV files (April–September) with raw GPS coordinates (~960,000 rides)
- **2015**: one CSV file (January–June) with taxi zone LocationIDs (~10.3 million rides)
- **Taxi zone lookup**: zone names and boroughs from the NYC TLC

Both datasets are stratified-sampled at 5% (by month, weekday, and hour) to maintain temporal representativeness while keeping computation tractable.

## Structure
```
NOTEBOOKS/
├── 1. EDA and preprocessing.ipynb # Data preparation, cleaning, and exploratory analysis
└── 2. Models.ipynb # K-Means and DBSCAN clustering
DATA/ # Not versioned (see .gitignore)
├── DATA_raw/ # Original CSV files
├── DATA_created/ # Cleaned and sampled datasets
└── DATA_models/ # Clustering outputs
```


## Notebooks

### 1. EDA and preprocessing

- Merges and samples the 2014 monthly files
- Geocodes 2015 taxi zones via the Nominatim API to obtain coordinates
- Cleans both datasets (duplicates, missing values, coordinate bounds)
- Analyzes seasonal, weekly, and hourly ride patterns for each year
- Compares 2014 and 2015 across temporal and spatial dimensions

### 2. Models

- **K-Means (K=4)**: partitions 493,263 rides into four geographic clusters — Manhattan Center (73.4%), Brooklyn (12.0%), LaGuardia/Upper Manhattan (9.9%), and JFK/South Queens (4.8%). K selected via elbow method and silhouette score.
- **DBSCAN (eps=0.30, min_samples=5)**: applied to 180 aggregated zone locations, identifies 7 natural density clusters with 23.3% noise points (isolated peripheral zones).

## Requirements
pandas
numpy
scikit-learn
plotly
seaborn
matplotlib
geopy


## Key findings

- Manhattan accounts for ~73% of all pickups; airports (JFK, LaGuardia) form distinct clusters with later peak hours (9–10 PM).
- Demand follows a stable bimodal daily pattern (7–9 AM and 5–9 PM commute peaks) across both years.
- Between 2014 and 2015, weekly peaks shifted from Thursday–Friday toward Friday–Saturday, reflecting growing social and leisure use.
- Raw ride volume grew tenfold between the two periods, consistent with Uber's rapid expansion in NYC.


## Author
Mounia Tonazzini Agricultural Engineer & Data Scientist | AI & AgriTech

Location: Montpellier, France LinkedIn: www.linkedin.com/in/mounia-tonazzini GitHub: Mounia-Agronomist-Datascientist

Last Updated: April 2026: This project is part of the Jedha Bootcam certification