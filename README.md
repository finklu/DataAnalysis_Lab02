# DataAnalysis Lab 02 — Graz Weather & Climograph

This repository contains the Jupyter notebook and dataset for **Assignment 01: Weather again** (`assignment01-weather.ipynb`), focusing on retrieving, exploring, and visualizing historical weather data for Graz, Austria.

## Project Overview

The notebook walks through:

1. **Data Retrieval (`Open-Meteo Archive API`)**
   - Fetches hourly historical weather data for the University of Graz main building (`47.0768° N, 15.4509° E`) from `2000-01-01` to `2026-11-22` (`Europe/Vienna` timezone).
   - Variables collected:
     - `temperature_2m`
     - `precipitation`
     - `wind_speed_10m`
   - Reference station info: [University of Graz Meteorological Station](https://climatephysics.uni-graz.at/de/meteorologische-station/).
   - Stores and reloads the dataset locally in Parquet format (`data/weather_graz.parquet`).

2. **Exploratory Data Analysis**
   - Inspects the dataset structure and summary statistics (`DataFrame.describe()`).
   - Creates exploratory plots to understand distributions, trends, and seasonal patterns.

3. **Climograph for Graz**
   - Aggregates the long-term hourly dataset using `pandas` (`groupby`, `.dt`, `sum`, `mean`, `agg`) to build a climograph featuring:
     - Average minimum and maximum temperatures
     - Cumulative precipitation
     - Number of rainy days
   - Compares the resulting climograph against existing online climate diagrams and evaluates the underlying timespan.

## Repository Structure

```text
.
├── assignment01-weather.ipynb   # Main analysis notebook
├── data/
│   └── weather_graz.parquet     # Cached hourly weather dataset for Graz
├── pyproject.toml               # Project metadata and dependencies
├── uv.lock                      # Locked dependency versions
└── .python-version              # Python 3.14
```

## Setup & Usage

This project uses [`uv`](https://docs.astral.sh/uv/) for Python environment and dependency management (Python `>= 3.14`).

1. **Install dependencies:**
   ```bash
   uv sync
   ```

2. **Launch Jupyter / run the notebook:**
   Open `assignment01-weather.ipynb` in VS Code or Jupyter and select the `.venv` kernel, or start Jupyter via `uv`:
   ```bash
   uv run jupyter notebook assignment01-weather.ipynb
   ```

   > **Note:** You can either re-fetch the data from the Open-Meteo API in the first cell or load the pre-saved dataset directly from `data/weather_graz.parquet`.
