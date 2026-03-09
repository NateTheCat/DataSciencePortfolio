# Airport Complaint Trends and Operational Insights

## Overview

This project analyzes complaint data related to airport operations and Transportation Security Administration (TSA) processes across multiple airports. Using publicly available datasets, the analysis explores trends in complaint volume over time, identifies airports with the highest number of complaints, and examines the most common complaint categories.

The project focuses on transforming raw complaint data into clear visual insights that can support decision-making for airport management and transportation agencies.

---

## Datasets

The analysis uses several publicly available datasets containing airport complaint records and airport location data.

### TSA Complaint Data

Three datasets were used to analyze complaints at different levels of detail.

**Complaints by Airport**

* Records of total complaints by airport and month
* Features include airport code, reporting date, and complaint count
* 41,721 observations

**Complaints by Category**

* Complaint counts grouped by complaint type
* Includes categories such as baggage issues, hazardous materials, and passenger property mishandling
* 241,588 observations

**Complaints by Subcategory**

* More detailed breakdown of complaint types
* Includes both categories and subcategories
* 504,512 observations

### Airport Location Data

**IATA / ICAO Airport Codes Dataset**

Used to match airport codes with geographic coordinates for mapping visualizations.

Features include:

* Airport name
* Country and region
* IATA and ICAO codes
* Latitude and longitude

---

## Data Preparation

Several preprocessing steps were performed to clean and standardize the datasets:

**Date Formatting**

* Converted `year_month` and `pdf_report_date` columns into datetime format for time series analysis.

**Airport Code Standardization**

* Removed whitespace and standardized capitalization for airport codes.
* Replaced invalid values (e.g., `"nan"`, `"None"`, empty strings) with proper null values.

**Data Aggregation**

* Aggregated complaint counts by airport to calculate total complaints.
* Created time-series datasets to analyze monthly trends.
* Merged airport complaint totals with geographic coordinates for mapping.

These transformations enabled consistent analysis across the different datasets.

---

## Visualizations

Several visualizations were created to explore trends and patterns in airport complaint data.

### Complaint Trends Over Time

A time series line chart shows how total TSA complaints change over time, helping identify seasonal patterns or long-term increases in complaint volume.

### Top Airports by Complaint Volume

A bar chart highlights the **20 airports with the highest total complaints**, providing insight into where operational issues may be concentrated.

### Complaints by Category

A horizontal bar chart visualizes the **top complaint categories**, allowing comparison between the most common passenger concerns.

### Airport Complaint Heatmap

A heatmap shows monthly complaint counts for the top 20 airports, helping identify:

* peak complaint periods
* seasonal patterns
* airports with consistently higher complaint volumes

### Complaint Distribution by Airport

A boxplot displays the distribution of monthly complaint counts across major airports, highlighting variability and potential outliers.

### Geographic Distribution of Complaints

An interactive global map visualizes complaint totals by airport using scaled bubble markers. Larger markers indicate airports with higher complaint volumes.

---

## Key Insights

The analysis reveals several notable patterns:

* Certain airports consistently generate higher complaint volumes than others.
* Complaint patterns fluctuate over time, suggesting possible seasonal trends.
* A small number of complaint categories account for a large portion of total complaints.
* Larger or more heavily trafficked airports tend to receive more complaints.

These findings highlight potential areas where airport management or TSA operations could focus improvement efforts.

---

## Technologies Used

* JupyterLab
* Matplotlib
* NumPy
* Pandas
* Plotly
* Python
* Seaborn

---

## Ethical Considerations

The datasets used in this analysis are publicly available and originate primarily from government sources.

Key considerations include:

* Airport codes were cleaned and standardized to prevent incorrect data matching.
* Aggregated complaint counts may make smaller airports appear to have fewer issues compared to large airports with higher passenger traffic.
* Differences in airport size, passenger volume, and operational scale likely influence complaint counts.

Because the data is aggregated complaint data rather than individual-level information, there are no major privacy concerns.

---

## Why This Project Matters

Passenger complaints provide valuable feedback about airport operations and traveler experiences. By visualizing trends and identifying patterns across airports and complaint categories, this analysis demonstrates how data visualization can support operational decision-making and improve passenger service.