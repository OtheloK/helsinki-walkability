# Helsinki Walkability & Population Density Prediction

A machine learning project that processes Helsinki map data to predict population density and classify neighborhoods using OpenStreetMap features.

## Overview

This project extracts spatial features from Helsinki's road network and points of interest (POIs), then trains Random Forest models to:
- **Regression** — predict the number of residents per 250m grid cell
- **Classification** — categorize each cell as Dense, Medium, or Sparse

## Data Sources

| Source | Description |
|--------|-------------|
| [OpenStreetMap](https://www.openstreetmap.org/) via `osmnx` | Road network and POIs (shops, transit stops, restaurants, schools, parks) |
| [HSY Population Grid 2023](https://hri.fi/data/en_GB/dataset/vaestotietoruudukko) | Official 250m × 250m population grid for Helsinki |

> **Note:** The population grid shapefile is not included in this repository due to file size. Download the 2023 SHP from the link above, extract the zip, and place all files in the same folder as the notebook.

## Features Engineered

- `transit_count` — number of public transport stops within 500m
- `shop_count` — number of shops within 500m
- `food_count` — number of restaurants/cafes within 500m
- `school_count` — number of schools within 500m
- `park_count` — number of parks within 500m
- `street_count` — number of street intersections within 500m
- `poi_total` — total POIs across all categories

## Requirements

```
osmnx
geopandas
shapely
pandas
numpy
matplotlib
scikit-learn
```

Install GIS libraries:
```bash
pip install osmnx geopandas shapely
```

## How to Run

1. Clone this repository
2. Download the HSY population grid shapefile from the link above
3. Extract and place all `.shp`, `.dbf`, `.prj`, `.shx` files in the same folder as the notebook
4. Open `helsinki_walkability_v2.ipynb` in Jupyter Notebook
5. Run cells in order (Cell 1 installs libraries — restart kernel after)

## Project Structure

```
helsinki-walkability/
│
├── helsinki_walkability_v2.ipynb   # Main notebook
└── README.md                       # This file
```

## Results

The notebook produces:
- Helsinki road network map
- Feature distribution histograms and correlation matrix
- Regression: predicted population density heatmap across Helsinki
- Classification: neighborhood type map (Dense / Medium / Sparse)
- Feature importance charts and model evaluation metrics
