# Optimal Fast Food Franchise Placement
### Geospatial Ranking & Predictive Success Modeling

## Project Overview
This project leverages **Big Data** processing techniques to identify optimal locations for new fast-food franchises. [cite_start]By integrating multi-source datasets—including business performance, socioeconomic demographics, and competitor density—the system generates a composite **"Success Score"** to forecast the viability of specific geographic locations.

## Data Sources
The pipeline ingests and processes three primary datasets using **Apache Spark**:
* **Yelp Academic Dataset**: Used to extract existing business locations, star ratings, and review counts to establish performance baselines.
* **U.S. Census Bureau (ACS 5-Year Estimates)**:
    * **DP05 (Demographics)**: Extracted total population metrics by Zip Code Tabulation Area (ZCTA).
    * **DP03 (Economics)**: Extracted Median Household Income to analyze consumer purchasing power.
* **OpenStreetMap (OSM)**: Processed raw restaurant data to identify competitor density and specific features like "drive-through" availability.

## Technical Features
### 1. Large-Scale Data Ingestion & Cleaning
* **Multi-Format Support**: Utilized PySpark to ingest JSON (Yelp) and CSV (Census/OSM) data.
* **Regex Feature Extraction**: Implemented advanced regular expressions (`regexp_extract`) to parse complex HStore/JSON-like strings in OSM data to identify amenity and cuisine types.
* **Data Normalization**: Standardized geographic identifiers across datasets by extracting 5-digit zip codes from Census ZCTA strings.

### 2. Analytical Transformations
* **Spark SQL Integration**: Created temporary views to perform complex three-way joins between Yelp, Demographic, and Economic datasets.
* **Socioeconomic Categorization**: Engineered features to segment geographic areas into "Low," "Medium," and "High" income brackets to analyze correlation with business success.
* **Feature Engineering**: Developed boolean features for drive-through presence and calculated competitive density metrics.

### 3. Predictive Modeling (Phase 2)
* **Random Forest Regression**: (Per project goals) Trained models using Spark-derived features to forecast location-specific success.
* **Scalable Deployment**: Designed the pipeline for cloud scalability, targeting deployment on **Azure** using Data Lake Storage and Azure Functions.

## Technical Stack
* **Languages**: Python (PySpark)
* **Processing Engine**: Apache Spark (Spark SQL, DataFrames)
* **Data Science Libraries**: Scikit-learn, Pandas, NumPy 
* **Visualization**: Matplotlib, Seaborn 
* **Cloud (Planned)**: Azure

## How to Run
1.  **Initialize Spark Session**: Ensure a local or cluster Spark environment is active.
2.  **Data Placement**: Store raw JSON and CSV files in the `/data` directory as specified in the notebook paths.
3.  **Execute Transformation**: Run the `final.ipynb` notebook to perform the ETL process and generate the final joined dataset for modeling.
