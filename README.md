# IndyGo-Transit-Dashboard


The IndyGo Ridership Dashboard is an interactive visualization tool developed for IndyGo, the public transit agency in Indianapolis.It provides actionable insights into ridership patterns using historical and real-time data. The dashboard enables planners, policymakers, and the public to better understand how transit services are used, guiding smarter service planning, optimizing resources, and improving rider experience.


Our dashboard was built to answer the following key questions about IndyGo ridership:

1. What is the total ridership across different time scales (day, week, month, year)?

2. How does ridership vary across different route categories, such as high-frequency routes, rapid transit, and coverage services?

3. What are the ridership trends for specific routes over the past 12 months?

4. How do ridership levels change across different time frames, including monthly, by bid period, or over rolling five-week windows?

5. What are the changes in ridership over time, such as month-to-month, year-over-year, or week-to-week?

6. Which stops experience the highest and lowest ridership, and how can these insights inform resource allocation?


**Data** :



The IndyGo ridership dataset was provided by IndyGo and integrates multiple sources, including:

GPS trackers (bus movement and scheduling)

Automatic Passenger Counters (APCs) (boarding and alighting counts)

Schedule & service data (planned trips and routes)

Coverage: 2022 – 2024
Format: CSV files structured into fact and dimension tables for use in Power BI.

| Table Name               | Records    | Notes / Issues                                                     |
| ------------------------ | ---------- | ------------------------------------------------------------------ |
| **DimBlock**             | 880        | Some missing `BlockDesc` and negative IDs                          |
| **DimDate**              | 1,096      | Clean, complete calendar table                                     |
| **DimRoute**             | 1,236      | Missing `RouteMode`, `RouteColor`                                  |
| **DimStop**              | 19,349     | Gaps in `DeleteDate` field                                         |
| **DimTrip**              | 226,133    | Some negative TripKeys                                             |
| **DimVehicle**           | 2,570      | Missing `DeleteDate` in some entries                               |
| **DimUser / DimUser2**   | 2,123 each | Major missing values in `LogonID`, `Email`, `Phone`                |
| **FactSegmentAdherence** | 20.6M      | Core adherence/ridership data, very large; required heavy cleaning |


**Data Cleaning & Challenges**

Working with the IndyGo dataset required significant preprocessing to ensure accurate and reliable analysis.

- Challenges Encountered

Missing Values: Several fields (e.g., RouteMode, RouteDescIVR, DeleteDate, and user contact fields) were incomplete.

Invalid / Negative IDs: Some tables (e.g., DimTrip, DimBlock, DimVehicle) contained negative keys or inconsistent identifiers.

Incomplete Metadata: Gaps in route/service type classification limited precise grouping of routes.

Large Dataset Size: The FactSegmentAdherence table contained over 20 million rows, creating performance and computational challenges when loading into Power BI.

- Cleaning Steps Taken

Imputed or flagged missing values in route, stop, and user tables.

Corrected negative or invalid IDs to ensure referential integrity.

Standardized field names, formats, and data types across tables.

Aggregated and filtered the FactSegmentAdherence table for efficient dashboard integration.

Documented assumptions and transformations for transparency and reproducibility.


**Visualization**



1. Total Ridership by Year, Quater, Month and Day
<img width="445" height="340" alt="image" src="https://github.com/user-attachments/assets/2b976685-3e04-4fa7-9adb-f47e57ba5afa" />



The first visualization is a line chart titled "Total Ridership by Year, Quarter, Month, and Day," showing cyclical ridership trends from April 2022 to June 2024, with weekday ridership consistently higher than weekends.




 2.Total Ridership based on Highest and Lowest Stops

 
 <img width="445" height="340" alt="image" src="https://github.com/user-attachments/assets/e8059423-a3e6-4c9b-bfe9-8d3f74db2157" />


Combination of bar charts and a geographic map Key insights suggest increasing service frequency at busy downtown stops and adjusting service at lower- ridership suburban locations i.e.,Delaware St & New York St as the busiest stop and 10th St & Euclid Ave as the least busy, with central Indianapolis showing the highest activity. Clear weekday vs. weekend variations support the need for peak-hour scheduling, and seasonal fluctuations highlight the influence of weather and special events on transit demand.


3.Enhanced dashboard visualization showing Total Ridership trends by Year, Month, and Day, with breakdowns across days of the week and months for detailed temporal analysis


<img width="445" height="340" alt="image" src="https://github.com/user-attachments/assets/22a4a78d-18a2-41a4-9999-2076582f8202" />


The redesigned dashboard introduced filters by year, month, and day, enabling better peak period identification.

