# STQD6324 Data Management Assignment 2
## Airline On-Time Performance Analaysis on 2008 Dataset

### Name: A Pavethra A/P Avadiar
### Course: STQD6324 Data Management (Semester 2, 2024/2025)

## Project Objective
This project explores **flight delay and cancellation patterns** using the **2008 Airline On-Time Performance Dataset**. It applies **Apache Hive** for data preprocessing and analysis, and **Python (Pandas, Matplotlib, Seaborn)** for visualizations. The goal is to uncover patterns in delays and identify critical contributing factors using structured big data processing.

## Tools and Technologies 
1. Apache Hive - Big Data querying and transformation
2. Python - Data wrangling, analysis and visualization

## Dataset Overview
**Records**: 2,389,217
**Variables**: 29
**Note**: This dataset **only includes flight records from months January to April**, not the full year of 2008.

## Data Processing Steps in Hive
1. **Raw Table Creation (airline_2008)**:
- Loaded dataset without headers using 'EXTERNAL TABLE' with 'TEXTFILE' format.
- Verified with 'SELECT *' and counted total rows which resulted in 2,389,217.

2. **Cleaning ('airline_2008_cleaned')**:
- Replaced 'NA' and blank strings with 'NULL'
- Casted types for proper numerical processing

3. **Deduplication ('airline_2008_deduplicated')**:
- Removed 4 duplicated rows using 'SELECT DISTINCT *'
- Final cleaned dataset rows resulted in **2,389,213** rows.

4. **Null Check**:
- Ensured essential columns like 'Year', 'FlightNum', 'Origin', 'Dest' had **0 nulls**.

5. **Cancellation Categories**:
- Verified consistency: A (Carrier), B (Weather), C (NAS), D (Security)

# Analysis Overview
### ** Questio 1: Delay Patterns**

