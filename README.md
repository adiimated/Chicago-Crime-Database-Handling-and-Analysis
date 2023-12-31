# Chicago-Crime-Database-Normalization

## Introduction

The crime data management system was developed to efficiently store, manage, and analyze crime-related data. This report outlines the methodology employed in creating this system, focusing on data import and parsing, preprocessing, and normalization.

## Data Import and Parsing

Tools Used: Python's with and open commands were utilized for reading the CSV file line by line.

Data Manipulation: Pandas, a powerful Python library, was employed for subsequent data manipulations.

### Data Preprocessing

1. Null Value Handling: Null values were identified and removed using df.dropna().

2. Irrelevant Data Elimination: Columns irrelevant to the specific problem statement were dropped.

3. Data Type Conversion:
- Location columns were transformed into categorical data types.
- Floating-point data types were converted into integers.

4. SQL Integration: The modified columns were then integrated into an SQL table using an executemany statement.

## Normalization

Aimed at restructuring the original Crimes table to enhance efficiency, the normalization process divided the data into three distinct, interconnected tables: Location, Offense, and Crime.

Schema:
| Location | Offense | Crime |
| ------------- | ------------- | ------------- |
| Stores unique location details | Categorizes types of offenses | Main table linking to Location and Offense |
| Columns: location_id (primary key), block, location_description | Columns: offense_id (primary key), iucr, primary_type, description | Columns: id (primary key), date, location_id, offense_id, arrest, domestic, district, ward, community_area, year |


Advantages: This normalization minimized data redundancy and enhanced the efficiency of queries.

## Reconstructing the original table with Join

We used SQL JOIN operations to merge data from the Crime, Location, and Offense tables. This was essential to reassemble the separated data, which had been normalized for database efficiency, into a complete dataset. We specified join conditions using location_id and offense_id to ensure that related data from each table was accurately combined. By carefully selecting relevant columns through the SELECT statement, we included necessary details like crime ID, date, location, and offense type in our final dataset.

Finally, we loaded the resulting comprehensive dataset into a Pandas DataFrame. This step was crucial as it transformed the data from a database-centric format into a format more conducive for in-depth analysis using Python tools. In essence, we reversed the database normalization to some extent, transforming the data from multiple related tables into a single, unified dataset ready for analysis.
