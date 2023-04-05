![Python](https://img.shields.io/badge/python-3.7-blue.svg)
[![Release Version](https://img.shields.io/badge/version-1.0.0-blue.svg)](https://github.com/dstoyak/Sauna-Scrape-and-Analysis/releases/tag/v1.0.0)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)


# Vancouver Rental Apartment Analysis

This project aims to analyze rental apartments in Vancouver listed on Craigslist, to determine if rental postings that have a sauna have a monthly rent premium associated with them. The project is divided into four main parts: proxy acquisition, data collection, data preprocessing, and data analysis.

## Table of Contents

- [Proxy Acquisition](#proxy-acquisition)
- [Data Collection](#data-collection)
- [Data Preprocessing](#data-preprocessing)
- [Data Analysis](#data-analysis)
- [Usage](#usage)
- [Requirements](#requirements)


## Proxy Acquisition

The `get_proxies.ipynb` notebook scrapes a list of appropriate proxies from a website. The list of proxies is then used in both the `page_scraper.ipynb` and `posting_scraper.ipynb` notebooks to facilitate web scraping with Selenium.

## Data Collection

`page_scraper.ipynb`: This notebook collects all posting URLs for each search performed. Searches were performed with the following keywords: "all rentals in Vancouver", "sauna", "steam room", and "pool". The URLs are saved in a CSV file called `van_sauna_pool_steam.csv` with the columns: URL, sauna, pool, and steam. True or false values indicate if each listing has a pool, sauna, or steam room.

`posting_scraper.ipynb`: This notebook imports the `van_sauna_pool_steam.csv` file and processes the URLs to extract relevant information. The scraped data includes the following columns:

- price
- bedrooms
- sqfts
- longitude
- name
- latitude
- bathrooms_level_two
- streetAddress
- country
- locality
- postal
- region
- housing_type
- links
- sauna
- pool
- steam

The data is saved as a CSV called `second_level_data_scrape.csv`.

## Data Preprocessing

`Vancouver_Data_Analysis.ipynb` takes in two input datasets: `second_level_data_scrape.csv` and `bc_schools.csv`. The latter dataset is obtained from the Statistics Canada website.

This notebook calculates the shortest distance to a school and adds it as a column to the `second_level_data_scrape.csv` dataframe. The final dataframe before analysis includes the following columns:

- price
- bedrooms
- sqfts
- longitude
- name
- latitude
- bathrooms_level_two
- streetAddress
- country
- locality
- postal
- region
- housing_type
- links
- sauna
- pool
- steam
- min_dist
- min_dist_school_name
- min_dist_school_type

## Data Analysis

The `Vancouver_Data_Analysis.ipynb` notebook performs the following analyses:

- Price distribution with Sauna
- Price distribution without Sauna
- Price vs Square Footage with Sauna
- Price vs Square Footage without Sauna
- Price vs Square Footage Regressions with Sauna
- Price vs Square Footage Regressions without Sauna
- Mean Price by Neighborhood with Sauna
- Mean Price by Neighborhood without Sauna
- Scatter Matrix
- Correlations
- PCA with KNN Impute using selected variables
- PCA with Iterative Impute using selected variables
- PCA with No Impute (Drop all NaN Rows) using selected variables
- OLS Regressions
- Factor Analysis
- CoVar
- Random Forest

## Usage

1. Run the `get_proxies.ipynb` notebook to get a list of proxies.
2. Run the `page_scraper.ipynb` and `posting_scraper.ipynb` notebooks to collect data and save it to the `second_level_data_scrape.csv` file.
3. Download the `bc_schools.csv` dataset from the Statistics Canada website.

4. Run the `Vancouver_Data_Analysis.ipynb` notebook, inputting the `second_level_data_scrape

## Requirements
- Python 3.7+
- Jupyter Notebook
- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn
- statsmodels

Make sure to install the required packages using pip or conda before running the notebooks.

## License

This project is licensed under the [MIT License](https://opensource.org/licenses/MIT). See the [LICENSE](LICENSE) file for more details.

