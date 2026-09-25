🚲 Bike Share Analytics — Power BI Dashboard

An interactive analytics report on SF Bay Area Bike Share data. The report is built in Power BI and covers time trends, trip geography, station network efficiency, and user demographics.

📊 About the Project

The project implements a complete data analysis cycle for bike rental trip data: from building the data model to a finished multi-page dashboard with drill-through, conditional formatting, and calculated DAX metrics.

Tasks solved in the report:

Analysis of seasonality and trip volume growth (MoM / QoQ / YoY)
Identifying peak days of the week and peak hours
Geographic visualization of stations with drill-down to a specific station
Calculating a station load index and identifying under-/over-utilized stations
Determining the most popular routes
Demographic analysis of users (age, gender, subscription type)
🗂️ Report Structure

The report consists of 5 pages:

| Page | Description |
|---|---|
| **Time Series** | Trip dynamics by month/quarter/year, MoM/QoQ/YoY growth, load by day of week and hour (heat map) |
| **Geographic Analysis** | Map of stations with point size by trip volume and color by average duration, drill-through to a specific station |
| **Station Detail** *(drill-through, hidden from navigation)* | Average duration and trip volume for the selected station, hourly dynamics of departures/arrivals |
| **User Demographics** | Age groups, gender ratio, share of Subscriber vs Customer |
| **Network Efficiency** | Top 10 popular routes, most in-demand stations, station load index (underutilized / normal / overloaded) |

🧮 Data Model

The model is built as a snowflake schema:
bikeshare_regions ──┐
                     ├─→ bikeshare_station_info ──┬─→ station_ends ──┬─→ bikeshare_trips ←── Calendar
                     │                             │                  │
                     └─────────────────────────────┘                  (start_station_id — inactive relationship,
                                                                        activated via USERELATIONSHIP)


💡 Key Insights

Subscribers account for 86% of all trips, but their trips are on average shorter than those of one-time Customers — a typical pattern of commuter passengers vs. tourists.
Peak load occurs on weekdays during morning and evening hours (a pattern characteristic of home–work commutes), whereas on weekends the peak shifts to daytime hours.
Stations with a low load index are predominantly recently opened ones (less than 200 days in operation) — underutilization is more often related to how long the station has been operating than to its location.
The most popular route runs between the Ferry Building and Embarcadero stations — a zone of high tourist and commuter activity in San Francisco.

🛠️ Technologies
Power BI Desktop — visualization and data model
DAX — calculated measures and columns
Power Query — source data transformation                                                                        
