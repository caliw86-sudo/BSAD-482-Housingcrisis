## Wrangling.md:Data Preparation Process

##Overview
This document outlines the data cleaning and preparation process undertaken prior to analysis. All datasets were processed using Tableau Prep to ensure consistency, remove errors, and prepare the data for integration and visualization. The objective of wrangling was to standardize formats, remove irrelevant information, and ensure accurate cross-dataset comparisons.


## Housing Supply Data (CMHC)
The housing supply dataset obtained from CMHC initially contained inconsistent column naming, null year values, and fields formatted as text rather than numeric values. Several rows contained blank or metadata entries that were not relevant to analysis. During cleaning, rows with null year values were removed, column names were standardized for clarity (e.g., Net_Change_Total, New_Added), and numeric fields were converted from text to proper numeric format. The Year variable was standardized as a whole number to ensure compatibility with other datasets. Unnecessary columns not directly related to net housing supply were removed to reduce noise in the dataset. Annual net housing change was treated as a proxy for housing supply responsiveness, and no seasonal adjustments were made because the dataset was annual.


## Population Data (Statistics Canada)
The population dataset contained additional metadata rows and formatting inconsistencies upon export. These non-data rows were removed so that only relevant year and population values remained. The Year field was standardized to whole number format, and the Population variable was converted to numeric format to allow proper aggregation. The dataset was checked for consistency with the housing supply dataset to ensure overlapping years could be analyzed. Population growth was used as a proxy for housing demand pressure, and no migration breakdown was included due to scope limitations.


## Rental Market Data (CMHC Rental Survey)
The rental market dataset required more substantial restructuring. It was originally formatted in wide format, with separate columns for each unit type (e.g., studio, 1-bedroom, 2-bedroom). The dataset also included quality flags and non-numeric characters that interfered with analysis. During cleaning, metadata and flag columns were removed, and the dataset was pivoted into long format so that unit types and average rent values were structured appropriately. Fields were renamed for clarity (Unit_Type, Avg_Rent), and rent values were converted to numeric format. The Year variable was standardized to the whole number format to match the other datasets. For consistency and clarity of analysis, 1-bedroom units were selected as the representative affordability indicator. In cases where municipal-level rental data was unavailable, regional data was used as a proxy with acknowledgment of scope limitations.


## Dataset Integration
When combining datasets, differences in year coverage created challenges. Some datasets did not share identical time ranges, and direct physical joins initially resulted in row duplication and null values. To resolve this, relational modeling was used in Tableau Desktop to connect datasets by Year rather than performing strict inner joins. This approach preserved data integrity while allowing cross-variable comparisons. Only overlapping years were used when analyzing relationships between variables, and no interpolation was performed for missing years.


## Summary of Data Preparation Decisions
Across all datasets, the cleaning process focused on standardizing year formats, converting measures to numeric values, removing null and metadata rows, and renaming fields for clarity. The goal was to maintain transparency while ensuring compatibility across datasets for system-level analysis. No artificial smoothing, interpolation, or transformation of core variables was performed, preserving the integrity of the empirical findings.
