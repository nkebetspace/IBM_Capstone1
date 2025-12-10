1. Project Overview

This project walks through an end-to-end data science workflow:

Collect SpaceX Falcon 9 launch data using a REST API and web scraping

Clean and combine multiple data sources into a single analysis-ready dataset

Perform exploratory data analysis (EDA) with visualisations and SQL

Build geospatial Folium maps to understand launch site locations and proximities

Develop an interactive Plotly Dash dashboard

Train and evaluate several classification models to predict landing success

The final deliverables are:

Cleaned datasets

Jupyter notebooks (EDA, SQL, mapping, machine learning)

A Plotly Dash app

Presentation slides with key insights

2. Data Sources

SpaceX REST API

Historical launch records, booster details, payloads, and landing outcomes

Wikipedia (web scraping)

Additional launch history tables to complement API data

Derived CSVs / lab datasets

dataset_part_1.csv, dataset_part_2.csv

spacex_launch_geo.csv (launch site coordinates and geo features)

spacex_launch_dash.csv (dashboard-ready dataset)

SQLite database containing SPACEXTABLE for the SQL lab

3. Repository Structure

Adjust names if they differ slightly in your repo.

.
├── spacex_api_data.ipynb                     # API data collection
├── spacex_web_scraped.ipynb                  # Wikipedia web scraping
├── datawranglinglab.ipynb                    # Data cleaning and feature engineering
├── edadataviz.ipynb                          # EDA with data visualisation
├── jupyter-labs-eda-sql-edx_sqllite.ipynb    # EDA with SQL on SPACEXTABLE
├── lab_jupyter_launch_site_location.ipynb    # Folium maps and proximity analysis
├── SpaceX_Machine_Learning_Prediction_Part_5.ipynb   # Classification model building
├── spacex-dash-app.py                        # Plotly Dash interactive dashboard
├── dataset_part_1.csv
├── dataset_part_2.csv
├── spacex_launch_geo.csv
├── spacex_launch_dash.csv
└── README.md

4. Methodology
4.1 Data Collection

API:

Called the SpaceX REST API to pull launch records, boosters, payload mass and landing results.

Normalised JSON into pandas DataFrames and saved to CSV.

Web scraping:

Scraped Falcon 9 / Falcon Heavy launch tables from Wikipedia using requests + BeautifulSoup.

Converted HTML tables into structured DataFrames.

4.2 Data Wrangling

Merged API and scraped data to focus on Falcon 9 launches only.

Standardised column names and dropped unused or duplicate columns.

Fixed data types (e.g. dates → datetime, numeric strings → floats).

Handled missing values (e.g. proper NaN for landingPad, PayloadMass).

Engineered features such as:

Class / LandingClass (1 = successful landing, 0 = failure)

LaunchYear

Simplified orbit categories

4.3 Exploratory Data Analysis (EDA)

Visual EDA (edadataviz.ipynb):

Flight number vs launch site (success vs failure)

Payload vs launch site

Success rate by orbit type

Payload vs orbit type

Yearly trend of launch success

SQL EDA (jupyter-labs-eda-sql-edx_sqllite.ipynb):

Distinct launch sites and their activity

Payload sums and averages by customer / booster version

First successful drone-ship and ground-pad landings

Counts of each landing outcome and ranking by frequency

Queries on specific customers (e.g. NASA (CRS)), payload ranges and date windows

4.4 Geospatial Analysis (Folium)

lab_jupyter_launch_site_location.ipynb:

Plotted all launch sites on a world map using latitude/longitude.

Added marker clusters coloured by landing success / failure.

Zoomed in to a selected launch site and measured distances to:

Coastline

Railway

Highway

Displayed distances on the map (e.g. ~0.58 km to coast, ~1.34 km to railway).

4.5 Interactive Dashboard (Plotly Dash)

spacex-dash-app.py:

Dropdown to select launch site (or all sites).

Range slider to filter payload mass.

Pie chart:

Success counts for all sites

Or success vs failure for a selected site

Scatter plot:

Payload mass vs landing class, coloured by booster version category

The dashboard lets users interactively explore how success varies by site, payload and orbit.

4.6 Predictive Modelling

SpaceX_Machine_Learning_Prediction_Part_5.ipynb:

Prepared features (launch site, orbit, payload mass, booster attributes, etc.) and target (Class).

Train/test split and encoding of categorical variables.

Trained and evaluated four classifiers:

Logistic Regression

Support Vector Machine (SVM)

K-Nearest Neighbours (KNN)

Decision Tree

Test accuracies (approximate):

Logistic Regression: 0.83

SVM: 0.83

KNN: 0.83

Decision Tree: 0.66–0.67

Selected Logistic Regression as the preferred model:

High accuracy (~83%)

Simple and easy to interpret

Confusion matrix: correctly predicts most landings, with a few false positives and no false negatives in the test set.

5. Key Findings

Launch sites: KSC LC-39A and CCAFS SLC-40 have the strongest landing performance and the largest share of successful launches.

Orbits: LEO and ISS orbits show higher success rates than some higher-energy orbits (e.g. GTO), indicating that risk is partly orbit-dependent.

Payload: Successful landings occur across a wide payload range; very heavy payloads are handled mostly by newer booster versions.

Trends over time: Success rates have improved significantly over the years as hardware and procedures matured.

Geospatial: All SpaceX launch sites in this dataset are coastal and close to major infrastructure, balancing logistics and safety.

Prediction: A simple Logistic Regression model can predict landing success with ~83% accuracy, making it useful for rough risk and cost estimation.

6. How to Run the Project Locally
6.1 Prerequisites

Python 3.8+

Recommended: virtual environment (e.g. venv or conda)

6.2 Install Dependencies

From the root of the repo:

pip install -r requirements.txt


If you don’t have a requirements.txt, a minimal set might include:

pip install pandas numpy matplotlib seaborn scikit-learn folium plotly dash sqlalchemy

6.3 Run the Notebooks

Start Jupyter:

jupyter notebook


Open and run notebooks in a logical order, for example:

spacex_api_data.ipynb

spacex_web_scraped.ipynb

datawranglinglab.ipynb

edadataviz.ipynb

jupyter-labs-eda-sql-edx_sqllite.ipynb

lab_jupyter_launch_site_location.ipynb

SpaceX_Machine_Learning_Prediction_Part_5.ipynb

Adjust paths if your files are organised differently.

6.4 Run the Dash Dashboard

From the project root:

python spacex-dash-app.py


Then open the printed URL in your browser (usually http://127.0.0.1:8050/).

7. Screenshots (Optional Section)

You can add images into the README or just reference them in your slides, for example:

EDA plots (success by orbit, yearly trend).

Folium maps (global sites, outcome clusters, proximity map).

Dashboard screenshots (overall pie chart, site-specific pie, payload vs success).

Confusion matrix and accuracy bar chart for the models.

8. Acknowledgements

This project is based on the IBM Data Science Capstone (SpaceX Falcon 9) on Coursera / IBM Skills Network.
All data belongs to their respective sources (SpaceX API, Wikipedia, IBM lab datasets).
