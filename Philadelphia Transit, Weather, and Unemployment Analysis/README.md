# Philadelphia Public Transportation, Bike Ridership, Unemployment, and Weather Analysis

## Overview

This project analyzes public transportation usage, bike share ridership, unemployment trends, and weather patterns in Philadelphia over a 10-year period (2015–2025). By integrating datasets from SEPTA, Indego, the U.S. Bureau of Labor Statistics, and historical weather reports, the project uncovers trends, seasonal effects, and correlations between transportation usage, economic factors, and weather.

---

## Datasets

### Bike Share Ridership (Indego)

* **Source:** Indego Philadelphia public trip datasets (quarterly CSVs, 2015–2025)
* **Observations:** 8,811,118 entries
* **Features:** Trip duration, start/end dates, bike type, season, start/end month and year

### Public Transit Ridership

* **Source:** SEPTA and related public transit sources
* **Observations:** 2,961 entries
* **Features:** County, municipality, transportation mode, season, year, day type, riders on/off

### Transit Mode Aggregates

* **Source:** SEPTA & public reports
* **Observations:** 456 entries
* **Features:** Year, month, season, transportation mode, average daily riders

### Unemployment

* **Source:** U.S. Bureau of Labor Statistics
* **Observations:** 132 entries
* **Features:** Year, month, season, labor force, employment, unemployment, unemployment rate

### Weather

* **Source:** Philadelphia daily weather reports
* **Observations:** 3,773 entries
* **Features:** Daily temperature metrics, precipitation, snowfall, wind, daylight duration, weather code, season, freezing days

---

## Data Processing

### Bike Share Data

* Merged 41 quarterly CSV files spanning 2015–2025 into a single DataFrame
* Dropped unnecessary columns (station IDs, trip IDs, location coordinates)
* Standardized date formats across all CSVs using regex and `pd.to_datetime`
* Extracted month, year, and season from start dates
* Filled missing `bike_type` values based on Indego's historical introduction of electric bikes (pre-May 2019 → standard bike)
* Reformatted bike types for consistency with other transportation modes (`standardbike` and `electricbike`)

### Public Transit & Transit Mode Aggregates

* Cleaned SEPTA ridership data and standardized column names
* Aggregated ridership by year, month, season, and transportation mode
* Prepared transit data to merge with bike ridership, unemployment, and weather

### Unemployment Data

* Cleaned BLS unemployment data
* Converted monthly unemployment statistics into a consistent format
* Added season column to facilitate seasonal analysis
* Prepared labor force, employment, and unemployment rate metrics for integration with transportation data

### Weather Data

* Aggregated daily weather data into monthly averages grouped by year, month, and season
* Calculated derived features such as average temperature, precipitation, wind, total daylight hours, and freezing days
* Standardized metrics to align with transportation and unemployment datasets

### Database Creation & Integration

* Created SQLite database (`transportation.db`) with separate tables for bike share, transit, unemployment, and weather
* Merged datasets into a unified table (`merged_data`) with:

  * Year, month, season
  * Transportation mode (`trans_mode`)
  * Average daily riders and total bike rides
  * Labor force, employment, unemployment, unemployment rate
  * Weather metrics (temperature, precipitation, wind, daylight, freezing days)

---

## Analysis & Use Cases

* Compare usage trends across bikes and public transit over time
* Examine correlations between ridership, weather, and economic conditions
* Explore seasonal patterns in transportation usage
* Provide insights for urban planning, public transportation scheduling, and bike infrastructure development

---

## Technologies Used

* BeatuitfulSoup
* JupyterLab
* Matplotlib
* NumPy
* Pandas
* SQL
* SQLite
* Urllib

---

## Outputs

* Cleaned, integrated dataset combining bike ridership, public transit, unemployment, and weather
* Aggregated tables for monthly and seasonal analysis
* Database ready for visualization, statistical analysis, or machine learning

---

## Why This Project Matters

This project demonstrates the power of data integration by combining multiple public datasets into a single analysis-ready resource. It allows exploration of urban mobility, seasonal trends, economic factors, and weather impacts in Philadelphia, providing actionable insights for policy, transportation planning, and infrastructure development.