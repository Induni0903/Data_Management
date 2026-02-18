
# New York City Real Estate Insights & Data Pipeline
## Data Science Master’s Project (Data_Management)
This project focuses on building an end-to-end data pipeline to analyze the New York City housing market. By integrating property listings with urban amenity data and walkability scores, we derive comprehensive insights into how geographical and neighborhood characteristics influence real estate pricing.

## Project Overview
The objective is to analyze housing prices in NYC by correlating property-specific features (square footage, type) with external neighborhood factors (amenities, transit accessibility).

Key Goals:

* Multi-Source Acquisition: Automated data retrieval via APIs and Web Scraping.

* NoSQL Architecture: Systematic storage and querying using MongoDB.

* Data Enrichment: Integrating spatial data (OSM) and lifestyle metrics (Walk Score).

* Data Quality: Comprehensive profiling to ensure "analysis-ready" datasets.

## Architecture & Data Acquisition
The project utilizes three distinct data streams to create a unified view of the market:

* Kaggle API: Dataset based on the house price, house type, broker titles, number of bedrooms and bathrooms, property square footage, address, state, administrative and local areas, street names and geographical coordinates for New York City will be assessed through the Kaggle API. Dataset :- https://www.kaggle.com/datasets/nelgiriyewithana/new-york-housing-market
  
* OpenStreetMap (OSM) API: To extract the speci ic amenities like schools, hospitals and public transport stations and stop locations in New York, Overpass API, an OpenStreetMap (OSM) query tool along with requests library is used to retrieve data.

* Web Scraping: To get insights further about the neighbourhood of the listed house locations, data is extracted from this website: https://www.walkscore.com/score/. Extracted data contains information on walk score, transit score and bike score which corresponds to neighbourhood of the houses that listed in the dataset obtain from Kaggle platform. Walk score is a metric that measures the walkability of a speci ic location which evaluates how convenient to access everyday amenities. Transit score evaluates the availability and usefulness of public transportation.

## Data Storage 
To handle the diversity and scale of data, a NoSQL database (MongoDB) is selected for storage. Following are some queries that we intend to analyse to gain a comprehensive understanding of the 
housing market in New York. 
* Unveiling the geographical patterns in New York’s housing market by identifying high and low-value areas in real estate. 
* Impact of property features such as space, number of rooms vs price. 
* Variations in New York housing by neighbourhood and its features.

## Data Profiling & Quality Control
To ensure the integrity of our insights, we implemented a rigorous data quality framework:

* Handling Missingness: Imputed or removed records missing critical pricing or coordinate data.
* Outlier Detection: Used statistical thresholds (Z-score/IQR) to identify and handle anomalous property prices or square footage.
* Geospatial Validation: Cross-referenced coordinates to ensure all points fell within the official New York City administrative boundaries.
* De-duplication: Identified and removed duplicate listings often found in real estate datasets.

Gemini said
This is a solid foundation for a Master’s level project. To make it stand out on GitHub, your README needs to balance technical depth with clear documentation of your data engineering pipeline.

Here is a comprehensive README template tailored to your New York Housing Market analysis.

New York City Real Estate Insights & Data Pipeline
Data Science Master’s Project
This project focuses on building an end-to-end data pipeline to analyze the New York City housing market. By integrating property listings with urban amenity data and walkability scores, we derive comprehensive insights into how geographical and neighborhood characteristics influence real estate pricing.

## Project Overview
The objective is to analyze housing prices in NYC by correlating property-specific features (square footage, type) with external neighborhood factors (amenities, transit accessibility).

Key Goals:

Multi-Source Acquisition: Automated data retrieval via APIs and Web Scraping.

NoSQL Architecture: Systematic storage and querying using MongoDB.

Data Enrichment: Integrating spatial data (OSM) and lifestyle metrics (Walk Score).

Data Quality: Comprehensive profiling to ensure "analysis-ready" datasets.

## Architecture & Data Acquisition
The project utilizes three distinct data streams to create a unified view of the market:

Source	Method	Key Attributes
Kaggle API	Python API	Price, Broker title, Bedrooms/Bathrooms, Sqft, Lat/Long.
OpenStreetMap (OSM)	Overpass API	Locations of Schools, Hospitals, and Transit Stations.
WalkScore.com	BeautifulSoup/Scrapy	Walk Score, Transit Score, and Bike Score per neighborhood.
Web Scraping Logic
We extracted data from various neighborhood-specific URLs (e.g., Astoria, Bedford-Stuyvesant) to capture the "livability" of each area. This involved parsing HTML to retrieve numeric scores that quantify how convenient a location is for daily errands and commuting.

## Data Storage & Integration
Why MongoDB?
Given the semi-structured nature of web-scraped data and the varying attributes of geographic amenities, MongoDB was chosen for its schema flexibility.

The Integration Pipeline
Normalization: Standardized neighborhood names and coordinates across all three sources.

Merging: Joined Kaggle housing data with WalkScore metrics based on neighborhood strings.

Proximity Analysis: Calculated the distance from each listed house to the nearest OSM-sourced amenity (School, Hospital, Station) to create "Proximity Features."

## Data Profiling & Quality Control
To ensure the integrity of our insights, we implemented a rigorous data quality framework:

Handling Missingness: Imputed or removed records missing critical pricing or coordinate data.

Outlier Detection: Used statistical thresholds (Z-score/IQR) to identify and handle anomalous property prices or square footage.

Geospatial Validation: Cross-referenced coordinates to ensure all points fell within the official New York City administrative boundaries.

De-duplication: Identified and removed duplicate listings often found in real estate datasets.

## Analytical Focus
The unified dataset in MongoDB allows us to answer:

* Value Mapping: Which NYC neighborhoods offer the highest/lowest value per square foot?

* Feature Impact: How much does an additional bedroom increase price compared to a 10-point increase in Walk Score?

* Amenity Influence: Does proximity to a subway station or school have a statistically significant impact on property premiums?

## Deliverables
* Unified MongoDB Database: A comprehensive NoSQL collection containing integrated NYC housing data.

* End-to-End Pipeline: Python scripts for automated scraping, API fetching, and cleaning.

* Technical Documentation: Detailed report on challenges (e.g., handling scraping rate limits) and solutions.
