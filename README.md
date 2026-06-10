# 🚕 Optimising NYC Taxi Operations

A data analysis project exploring NYC Yellow Taxi trip data to uncover demand patterns, revenue trends, and operational inefficiencies — with actionable recommendations for routing, dispatching, and pricing.

---

## 📋 Project Overview

This project performs end-to-end analysis on NYC TLC Yellow Taxi trip records. Starting from raw Parquet files, the pipeline covers data cleaning, exploratory data analysis, geospatial visualisation, and strategic recommendations to optimise taxi operations across New York City.

**Dataset:** NYC TLC Yellow Taxi Trip Records (2023)  
**Sample Size:** ~300k–400k records (1% sample of full dataset)





---

## 🔧 Data Preparation & Cleaning

- Loaded and sampled Parquet files, grouping by pickup date and hour
- Fixed datetime columns (`tpep_pickup_datetime`, `tpep_dropoff_datetime`)
- Merged duplicate airport fee columns (`airport_fee` / `Airport_fee`)
- Corrected negative monetary values using `abs()`
- Imputed missing values:
  - `passenger_count` → median imputation
  - `RatecodeID` → mean imputation
  - `congestion_surcharge` → most-frequent value (2.5 or 0.0)
- Removed outliers: trip distance > 30 miles, tip amount > $40, fare > $100
- Dropped invalid records (zero distance with non-zero fare, mismatched locations)

---

## 📊 Exploratory Data Analysis

### General Trends
| Dimension | Key Finding |
|-----------|-------------|
| Day of week | Most trips on **Thursday**, fewest on **Monday** |
| Month | Peak in **October**, lowest in **August** |
| Hour of day | **Evening hours** (2 PM – 9 PM) are busiest |
| Payment | Majority pay by **credit card** |
| Revenue by quarter | **Oct–Dec** generates the highest share (27.1%) |

### Distance & Fare
- Strong correlation between trip distance and fare amount (**r = 0.96**)
- Highest total revenue generated in the **2–4 mile** and **10–20 mile** ranges
- Tip amount also increases with distance (**r = 0.82**)

### Geospatial Analysis
- Loaded NYC taxi zone shapefiles using **GeoPandas**
- Top pickup zones: **Upper East Side South**, **Midtown Center**, **JFK Airport**
- Top drop-off zones: **Upper East Side North**, **Upper East Side South**, **Midtown Center**
- Highest pickup/dropoff ratio: **East Elmhurst**, **JFK Airport**, **LaGuardia Airport**

### Detailed Insights
- Peak busy hours: **2 PM – 9 PM** (~200k trips at 6 PM across 2023)
- Weekdays consistently outperform weekends in trip volume
- Night-time hotspots: **East Village**, **West Village**, **JFK Airport**
- Day/night revenue split: **87.9% daytime**, **12.1% nighttime**
- Slowest route: **Seaport → Two Bridges/Seward Park**
- Tip percentage remains relatively stable (~15%) across all distance groups and times of day

---

## 💡 Recommendations

### Routing & Dispatching
- Deploy more taxis during **3 PM – 9 PM** peak hours
- Prioritise high-demand zones: **East Elmhurst, JFK Airport, LaGuardia Airport, South Jamaica, Penn Station/Madison Sq West**
- After drop-offs in low-pickup zones, redirect drivers to nearby high-demand zones
- Increase fleet coverage in **East & West Village** during late-night hours

### Strategic Cab Positioning
- Station more cabs near **Upper East Side South**, **Midtown Center**, and **JFK Airport**
- Align JFK Airport availability with flight arrival/departure schedules
- Scale up fleet on **Wednesday–Friday** before the evening rush
- Address seasonal demand spikes in **October, May, March, and November**

### Pricing Strategy
- Apply slight fare increases during peak demand at **JFK Airport (night)** and **Midtown (rush hours)**
- Optimise pricing during high-trip months (October, May, March, November)
- Introduce incentives for drivers to serve low-pickup zones like **Newark Airport**

---

## 🛠️ Tech Stack

- **Python** — pandas, numpy, matplotlib, seaborn
- **GeoPandas** — geospatial zone analysis
- **Jupyter Notebook** — interactive analysis
- **Parquet** — efficient data storage and loading

---

## 🚀 Getting Started

```bash
# Clone the repository
git clone https://github.com/your-username/nyc-taxi-operations.git
cd nyc-taxi-operations

# Install dependencies
pip install -r requirements.txt

# Launch notebooks
jupyter notebook
```

---

## 📄 Report

The full analysis report is available in [`report/Report_NYC_Taxi_Operations.pdf`](report/Report_NYC_Taxi_Operations_Starter_DurgaPrasad.pdf)

---

## 👤 Author

**Durga Prasad**  
[GitHub](https://github.com/your-username) · [LinkedIn](https://linkedin.com/in/your-profile)
