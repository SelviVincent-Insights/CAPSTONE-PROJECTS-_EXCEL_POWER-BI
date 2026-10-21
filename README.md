# Fleet Performance & Delivery Efficiency Dashboard

A logistics analytics project using **Excel** for data cleaning and analysis and **Power BI** for an interactive dashboard with DAX measures and AI visuals.

## Business Scenario

A logistics company wants to analyse its fleet performance in terms of **on-time deliveries**, **fuel efficiency** and **cost per km**, in order to optimise routes and fleet usage.

## Dataset

Source file: `logistics_project_dataset.xlsx`, provided with the module-end assignment.

| Table | Fields |
|---|---|
| Trip_Data (50 trips) | Trip_ID, Vehicle_ID, Driver_ID, Origin, Destination, Distance_km, Fuel_Consumed_L, Delivery_Status (On-Time / Late), Delivery_Date |
| Vehicle_Master (7 vehicles) | Vehicle_ID, Vehicle_Type, Capacity_kg, Maintenance_Cost |

Period covered: 1 January 2023 to 28 February 2023. Vehicle types: Truck, Van, Mini-Truck. 7 destinations, 10 drivers.

## Data Cleaning and Modelling

| Step | Detail |
|---|---|
| Missing fuel values | 3 trips (T016, T026, T044) had no fuel value. Replaced using **mean imputation** (mean of the other 47 trips = 91.88 L). |
| Data checks | No duplicate Trip_IDs, no zero distances, every Vehicle_ID in Trip_Data exists in Vehicle_Master. |
| Relationship | Trip_Data to Vehicle_Master on **Vehicle_ID** (many-to-one). |

The Excel workbook (`Fleet_Performance_Excel_Analysis.xlsx`) holds the cleaning, formulas, summary tables and four charts. All figures in it are formula-driven.

## DAX Measures

| Measure | Definition |
|---|---|
| Fuel Efficiency | Total distance / total fuel consumed (km per litre) |
| On-Time Delivery % | On-time trips / total trips |
| Cost per km | (Fuel cost + Maintenance Cost) / Distance, per trip; the card shows the average across trips |

**Assumption:** the assignment states "fuel cost = 100". This was treated as a flat 100 per trip.

## Dashboard

### Page 1: Fleet Overview
- Cards: On-Time Delivery %, Avg Cost per km, Fuel Efficiency, Total Trips, On-Time Trips
- Bar chart: On-Time Delivery % by Destination
- Line chart: Fuel Efficiency trend by Delivery Date
- Pie chart: Average Maintenance Cost by Vehicle Type

### Page 2: AI Insights
- **Q&A visual:** "Average Cost per km by vehicle type"
- **Key Influencers:** Delivery_Status explained by Distance_km, Vehicle_Type and Driver_ID
- **Decomposition Tree:** Cost per km explained by Vehicle Type, Maintenance Cost and Distance

## Key Findings

| Metric | Result |
|---|---|
| Total trips / on-time trips | 50 / 30 |
| On-Time Delivery % | 60% |
| Fuel Efficiency | 11.52 km/L |
| Average Cost per km | 18.03 |

- **Best on-time destinations:** Delhi and Pune (87.5% each). **Lowest:** Mumbai (33.3%), then Chennai (40%).
- **Cost per km by vehicle type:** Truck 21.58, Van 18.89, Mini-Truck 8.47.
- **Average maintenance cost by vehicle type:** Truck 14,186, Mini-Truck 9,033, Van 8,128.
- **Late deliveries:** the Key Influencers visual found no strong driver among distance, vehicle type or driver.

## Limitations

1. **Avg. Delivery Time** was requested in the assignment but could not be calculated: the dataset has no delivery time or duration column, only a delivery date.
2. **Small sample:** with only 50 trips, patterns (including the Key Influencers result) are indicative, not statistically strong.
3. **Fuel cost** is a flat assumed value (100 per trip), as given in the assignment.

## Repository Contents

| File | Description |
|---|---|
| `Fleet_Performance_Dashboard.pbix` | Power BI report (2 pages) |
| `Fleet_Performance_Dashboard.pdf` | PDF export of the dashboard |
| `Fleet_Performance_Excel_Analysis.xlsx` | Excel cleaning and analysis workbook |
| `README.md` | Project documentation |

## Tools

Microsoft Excel, Microsoft Power BI Desktop, DAX.

## Author

Selvi Vincent
