# DataAnalyst-SaraswathiJinka

Project Title: Data Analytical Platform for City of Vancouver Property Tax Report

Objective

The objective of this project was to analyze property tax data from the City of Vancouver for the years 2023 and 2024. The project aimed to derive insights regarding year-over-year trends, the impact of zoning classifications, regional differences, and comparisons across property types (e.g., strata and land).

**Dataset**

Source: Property tax datasets for 2023 and 2024 were downloaded from the City of Vancouver Open Data Portal.

Fields: Key fields included:
    
	• Property Type: Residential, strata, land, etc.
    
	• Zoning Classification: Associated zoning codes.
    
	• Tax Values: Assessed tax values for each property.
    
Methodology

1. Data Collection and Storage
•	Data Acquisition: The datasets for 2023 and 2024 were downloaded in Excel format from the City of Vancouver Open Data Portal.
•	Storage Solution: 
    The Excel files were uploaded to AWS S3.
    Datasets were organized into S3 landing zones for both years.
•	Security: KMS encryption was applied to secure the data at rest.



