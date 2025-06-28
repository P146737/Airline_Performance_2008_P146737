# STQD6324 Data Management Assignment 2
## Airline On-Time Performance Analysis on 2008 Dataset

### Name: A Pavethra A/P Avadiar
### Course: STQD6324 Data Management (Semester 2, 2024/2025)

## Project Objective
This project explores **flight delay and cancellation patterns** using the **2008 Airline On-Time Performance Dataset**. It applies **Apache Hive** for data preprocessing and analysis, and **Python (Pandas, Matplotlib, Seaborn)** for visualizations. The goal is to uncover patterns in delays and identify critical contributing factors using structured big data processing.

## Tools and Technologies 
1. Apache Hive - Big Data querying and transformation
2. Python - Data wrangling, analysis and visualization

## Related links
For question 2, please download the dataset `delay_export.csv`(https://drive.google.com/file/d/1cx4tFCsLWfqWAMcgVsnXLPDDs-lZWxJ4/view?usp=share_link), to be able to run the final 2 codes of the analysis.

## Dataset Overview
**Records**: 2,389,217
**Variables**: 29
**Note**: This dataset **only includes flight records from months January to April**, not the full year of 2008.

## Data Processing Steps in Hive
1. **Raw Table Creation (airline_2008)**:
- Loaded dataset without headers using 'EXTERNAL TABLE' with 'TEXTFILE' format.
- Verified with 'SELECT *' and counted total rows which resulted in 2,389,217.

2. **Cleaning ('airline_2008_cleaned')**:
- Replaced 'NA' and blank strings with 'NULL'.
- Casted types for proper numerical processing.

3. **Deduplication ('airline_2008_deduplicated')**:
- Removed 4 duplicated rows using 'SELECT DISTINCT *'.
- Final cleaned dataset rows resulted in **2,389,213** rows.

4. **Null Check**:
- Ensured essential columns like 'Year', 'FlightNum', 'Origin', 'Dest' had **0 nulls**.

5. **Cancellation Categories**:
- Verified consistency: A (Carrier), B (Weather), C (NAS), D (Security)

# Analysis Overview
### **Question 1: Delay Patterns**
#### 1. Best Time of Day for Punctual flights
- **Finding**: Morning Flights (5a.m. to 11a.m.) have the lowest average delays.
- **Avg Delay**: Dep is approximately 5.88 minutes, Arr is approximately 5.37 minutes
- **Morning is the best time to fly for punctuality.**

#### 2. Best Days to Travel
- **Finding**: Wednesday and Saturday show the best on-time performance.
- **Worst Day**: Friday has the highest delays due to weekend congestion.

#### 3. Best Months (within Jan-Apr subset)
- **Important Notes**: The dataset only contains flight records **January to April**, so **seasonal comparison such as summer vs winter** are not possible. All findings are limited to these four months.
- **Finding**: **April** has the lowest delays.
- **Worst Month**: February, likely due to winter weather.
- Spring travel is more reliable than winter (within this data slice).

### Visuals:
- Bar plots comparing **AvgDepDelay** and **AvgArrDelay** across time, days and months.

### **Question 2: Delay Factors**
#### Top 5 Contributors (Total Delay Minutes):
| Cause               | Minutes     | % Share |
|--------------------|-------------|---------|
| Late Aircraft       | 12.26M      | 37.5%   |
| NAS Delay           | 9.45M       | 28.9%   |
| Carrier Delay       | 9.21M       | 28.2%   |
| Weather Delay       | 1.72M       | 5.3%    |
| Security Delay      | 0.05M       | 0.14%   |
**Late aircraft** is the most dominant reason for delays, followed by NAS, and carrier-related issues.

#### Correlation Matrix:
- **High correlation**:
  - 'DepDelay' ↔ 'ArrDelay'
  - 'CarrierDelay', 'LateAircraftDelay' → strongly related to both.
- **Negligible correlation**: 'SecurityDelay'

### **Question 3: Cancellation Trends**
#### Cancellation Distribution:
| Cancelled | Code | Description                      | Count    |
|-----------|------|----------------------------------|----------|
| 1         | A    | Carrier                          | 26,075   |
| 1         | B    | Weather                          | 25,744   |
| 1         | C    | NAS                              | 12,617   |
| 1         | D    | Security                         | 6        |
| 0         | —    | Not Cancelled                    | 2,324,771 |
- Total cancelled flights: **64,442** which is approximately 2.7% of all flights.
- Main causes: **Carrier-related** and **weather-related** issues.
- April had the **fewest cancellations**, confirming better reliability.

### **Question 4: Problematic Routes**
- ORD to LGA and vice versa is the most problematic route with the highest delays and cancellations.
- Busy airport pairs like LAX-SFO also show high delay volumes.
- ORD (Chicago O'Hare) confirms operational inefficiencies, whereas YV (Mesa Airlines) is frequently among the most delayed carriers.
- Flights YV-7487, MQ-3408 and 9E-5897 had extreme average delays, though low frequency could skew the results.
- Flight 9E-5897 had both high delays and 4 cancellations.

#### Summary and Recommendation:
- ORD to LGA, LAX to SFO and ATL to LGA are high-risk routes for delays and cancellations.
- Carriers like YV, MQ (American Eagle) and 9E (Pinnacle Airlines) had significantly higher average delays.
- It is recommended to consider rescheduling or avoiding these specific flight numbers or routes, where possible. Airlines should review performance and resourcing on these critical routes.


## Conclusion
This project demonstrates the use of big data tools (Hive+Python) to analyze real-world airline performance data. Key patterns in flight delays and cancellations were identified, with actionable recommendations provided for optimizing airline operations and passengers' travel planning.
  

