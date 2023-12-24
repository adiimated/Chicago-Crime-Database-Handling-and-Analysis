# Chicago-Crime-Database-Normalization

## Introduction

The crime data management system was developed to efficiently store, manage, and analyze crime-related data. This report outlines the methodology employed in creating this system, focusing on data import and parsing, preprocessing, and normalization.

### Data Import and Parsing

Tools Used: Python's with and open commands were utilized for reading the CSV file line by line.
Data Manipulation: Pandas, a powerful Python library, was employed for subsequent data manipulations.

### Data Preprocessing

Null Value Handling: Null values were identified and removed using df.dropna().

Irrelevant Data Elimination: Columns irrelevant to the specific problem statement were dropped.

Data Type Conversion:
- Location columns were transformed into categorical data types.
- Floating-point data types were converted into integers.

SQL Integration: The modified columns were then integrated into an SQL table using an executemany statement.

### Normalization

Objective: The normalization process aimed at restructuring the original Crimes table into a more efficient database schema.

Tables Created:

- Location: Stores unique location details. Columns include location_id (primary key), block, and location_description.
- Offense: Categorizes types of offenses. Columns include offense_id (primary key), iucr, primary_type, and description.
- Crime: The main table linking to both Location and Offense. Columns include id (primary key), date, location_id, offense_id, arrest, domestic, district, ward, community_area, year.

Advantages: This normalization minimized data redundancy and enhanced the efficiency of queries.
