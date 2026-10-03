# Power BI: San Francisco Bay Area Bike Share Dashboard

![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black) ![Google BigQuery](https://img.shields.io/badge/Google_BigQuery-669DF6?style=for-the-badge&logo=googlebigquery&logoColor=white)

An interactive Power BI report analyzing bike share trips in the San Francisco Bay Area (2013–2018). It covers trip volume trends, period-over-period growth, peak usage times, geographic analysis down to individual stations, underused stations, popular routes and user behavior.

## Data Source
Public dataset **`bigquery-public-data.san_francisco_bikeshare`** from Google BigQuery, connected directly in Power BI (Get Data → Google BigQuery → Import).

Tables used (all except `bikeshare_station_status`):
- `bikeshare_trips`: trips with start/end time, duration, stations, user type, gender, birth year
- `bikeshare_station_info`: stations with name, coordinates, capacity (docks), region
- `bikeshare_regions`: regions (San Francisco, San Jose, Oakland, Berkeley, Emeryville, etc.)

## Tasks
1. **Data model:** explore the data and link the tables in Model view
2. **Visualizations:**
   - **[A] Time series:** monthly, quarterly and yearly trip volume; MoM, QoQ and YoY growth; average daily trips; trips and duration by weekday; peak hours; busiest month in San Jose
   - **[B] Geography:** trip volume and average duration on a map with drill-through to a specific station
   - **[C] Insights:** underused stations (metric and visualization) and the most popular route
   - **[D] User analysis:** customers vs subscribers, gender and age breakdown
3. **Design:** filters, titles, axis labels, legends, and a clear visual style

## Report Pages
| # | Page | What it shows |
|---|---|---|
| 1 | **Overview** | KPI cards (total trips, avg trips per day, avg duration, % subscribers), monthly trend, key insights |
| 2 | **Dynamics** | Monthly trip volume, MoM / QoQ / YoY growth table |
| 3 | **Period Comparison** | Compare trip volume for any two months or quarters (Period A vs Period B, growth %) |
| 4 | **Days & Hours** | Trips and avg/median duration by weekday, heatmap of hours × weekdays, San Jose by month |
| 5 | **Map** | Stations on a map sized by trip volume and colored by avg duration, station table |
| 6 | **Station (drill-through)** | KPIs for the selected station, monthly trend, top-10 destinations |
| 7 | **Stations & Routes** | 10 least-used stations, top-10 routes (with and without round trips) |
| 8 | **Users** | Subscribers vs customers, duration by user type, age groups, gender, hourly usage by user type |

Every page has slicers for **Year**, **Region** and **User type**.

## Key Insights
- **Growth:** trip volume grew 3–4× from ~30K trips per month (2013–2016) to 85–130K (2017–2018), about **1.95 million trips** in total
- **Commuting pattern:** peaks on **Tuesday and Wednesday** at **8:00 and 17:00**, with about half as many trips on weekends
- **Leisure on weekends:** weekend trips last **~32 min** vs **~14 min** on weekdays
- **Subscribers are the core:** **~82% of trips** come from subscribers, with a median trip of ~9 min
- **Customers (one-time users)** ride **~40 min** on average, typical for tourists
- **Underused stations:** measured by **turnover = average trips per day per dock**, which compares large and small stations fairly. The lower the value, the worse the station is used. Weak stations could be moved closer to transport hubs (BART, Caltrain)

## Underused Stations Metric
Raw trip counts unfairly compare large and small stations, so the report uses:

    Trips per dock per day = Trips / Docks (capacity) / Days in period

The 10 stations with the lowest value are shown in a separate table.

## Data Model & DAX
- **Star schema:** `bikeshare_trips` (fact) → `bikeshare_station_info` (start station) → `bikeshare_regions`
- **Calendar (Date) table** for time intelligence
- **DAX measures:** total trips, avg trips per day, avg and median duration, % subscribers, MoM % / QoQ % / YoY % growth, Period A vs Period B comparison, trips per dock per day, trips without round trips
- **Calculated columns:** weekday, hour, year-month, quarter, age group, route (start → end)

## Tools
Power BI Desktop, Power Query, DAX, Google BigQuery

## Files
- `SF_Bikeshare_Yakhiya.pbix`: Power BI report (interactive)
- `SF_Bikeshare_Yakhiya.pdf`: PDF export of the report (8 pages)

## How to View
- **No Power BI installed:** open `SF_Bikeshare_Yakhiya.pdf`
- **Interactive version:** open `SF_Bikeshare_Yakhiya.pbix` in [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free)
- To refresh the data, sign in to Google BigQuery with your Google account

## Topics Covered
**Power BI**
- Google BigQuery connection, Power Query transformations
- Data modeling: relationships, star schema, calendar table
- DAX measures and time intelligence (MoM, QoQ, YoY)
- Drill-through pages, slicers, tooltips
- Visuals: KPI cards, line and column charts, matrix heatmap, map, bar charts, donut charts, tables

**Analytics**
- Time series and trend analysis
- Period-over-period growth
- Peak hours and weekday seasonality
- Geospatial analysis
- Station utilization (turnover per dock)
- Route analysis
- User segmentation: subscribers vs customers, gender, age

## Keywords
`power-bi` `powerbi` `dax` `power-query` `data-modeling` `google-bigquery` `dashboard` `data-visualization` `business-intelligence` `time-intelligence` `kpi` `drill-through` `geospatial-analysis` `bike-sharing` `mobility-analytics` `user-segmentation` `data-analyst` `portfolio-project`
