# Analysis of Rare Disease Wikipedia Article Traffic (2015-2024)

## Goal of the Project

The goal of this project is to collect, process, and analyze monthly pageview data for a specified subset of rare disease-related articles from English Wikipedia, covering the period from July 1, 2015, through September 30, 2024. The analysis aims to visualize trends in article traffic to better understand user engagement with rare disease content over time.

## Data Acquisition and Processing

The data was acquired using the Wikimedia Foundation's Pageviews API, which provides access to desktop, mobile web, and mobile app traffic data starting from July 2015 through the previous complete month.

The subset of Wikipedia articles used in this project represents a large number of articles related to rare diseases. This list was compiled using a database maintained by the National Organization for Rare Diseases (NORD) and matching them to corresponding Wikipedia articles that are either about a rare disease or have a section mentioning a rare disease.

## Data Files

The following JSON data files are included in this repository:

### Monthly Mobile Access Data

- Filename: `rare-disease_monthly_mobile_201507-202409.json`
- Description: Contains summed monthly pageviews from mobile web and mobile app access for each article.

### Monthly Desktop Access Data

- Filename: `rare-disease_monthly_desktop_201507-202409.json`
- Description: Contains monthly pageviews from desktop access for each article.

### Monthly Cumulative Access Data

- Filename: `rare-disease_monthly_cumulative_201507-202409.json`
- Description: Contains the total monthly pageviews from all access types (mobile and desktop) for each article.

## Data Schema

Each JSON file is structured as a dictionary with article titles as keys and their respective time series data as values.

- Key: Article title (string)
- Value: Dictionary
  - Key: Timestamp in YYYYMM format (string)
  - Value: Pageviews count (integer)

Example Entry:

```json
{
  "Article_Title": {
    "201507": 123,
    "201508": 456,
    ...
  },
  ...
}
```

## Analysis

The analysis was conducted using Python and Jupyter Notebook. Three key visualizations were produced:

1. **Maximum Average and Minimum Average Page Requests**

   - Identified articles with the highest and lowest average monthly pageviews for both desktop and mobile access over the entire time series.
   - Visualization Filename: `max_min_average_page_requests.png`

2. **Top 10 Peak Page Views**

   - Identified the top 10 articles by the highest single-month pageviews for both desktop and mobile access.
   - Visualization Filename: `top10_peak_page_views.png`

3. **Fewest Months of Data**
   - Identified articles with the fewest months of available data for both desktop and mobile access.
   - Visualization Filename: `fewest_months_of_data.png`

Each visualization includes clearly labeled axes, a legend, and a title to facilitate understanding of the data presented.

## Visualizations

- `max_min_average_page_requests.png`: Displays time series for articles with the maximum and minimum average page requests for desktop and mobile access.
- `top10_peak_page_views.png`: Shows time series for the top 10 articles by peak page views for desktop and mobile access.
- `fewest_months_of_data.png`: Illustrates time series for articles with the fewest months of available data for desktop and mobile access.

## Code and Notebooks

- Notebook Filename: `data_acquisition_and_analysis.ipynb`
- Contains all the code for data acquisition, processing, and analysis, along with detailed descriptions and explanations for each step.

## License and Terms of Use

### Source Data License

The source data is provided by the Wikimedia Foundation and is licensed under the Creative Commons Attribution-ShareAlike 3.0 Unported License (CC BY-SA 3.0).

### Wikimedia Foundation Terms of Use

- Link: [Wikimedia Foundation Terms of Use](https://foundation.wikimedia.org/wiki/Terms_of_Use)

Summary of Compliance:

1. Attribution: This project uses data from the Wikimedia Foundation. Proper attribution is provided by linking to the Wikimedia Foundation and the specific APIs used.
2. ShareAlike: Any modifications or additions to the data are shared under the same or a compatible license.
3. Non-Endorsement: The Wikimedia Foundation does not endorse this project.

How the Terms of Use Apply to This Dataset:

- The dataset created is a derivative work based on Wikimedia content (pageview data).
- As required, attribution is given to the Wikimedia Foundation.
- The dataset is shared under the same license terms, allowing others to use and adapt the data under similar conditions.

## API Documentation

- [Pageviews API Documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews)
- [Wikimedia REST API Reference](https://www.mediawiki.org/wiki/API)
- [API Terms of Use](https://www.mediawiki.org/wiki/Wikimedia_REST_API#Terms_and_conditions)

## Reproducibility Instructions

### Requirements

- Programming Language: Python 3.x
- Environment: Jupyter Notebook
- Python Libraries:
  - pandas
  - matplotlib
  - requests
  - json
  - matplotlib.dates

### Steps to Reproduce

1. Clone the Repository: Download or clone this repository to your local machine.

2. Install Dependencies: Ensure all required Python libraries are installed.

   ```bash
   pip install pandas matplotlib requests json
   ```

3. Run the Notebook:

   - Open `data_acquisition_and_analysis.ipynb` in Jupyter Notebook.
   - Execute the cells sequentially to perform data acquisition, processing, and analysis.
   - The notebook includes detailed explanations and comments for each step.

4. Data Files:

   - The JSON data files will be generated when running the notebook.
   - Ensure you have an active internet connection to access the Wikimedia APIs.

5. Visualizations:
   - The plots will be generated and saved as PNG files in the repository directory.
   - They can also be viewed within the Jupyter Notebook output cells.

## Data Processing Workflow

1. Data Acquisition:

   - Fetch monthly pageview data for each article using the Pageviews API.
   - Collect data separately for mobile web, mobile app, and desktop access.
   - Sum mobile web and mobile app data to get total mobile access pageviews.

2. Data Storage:

   - Store the fetched data in JSON files with the specified naming convention.
   - Remove the 'access' field from the API response as it is misleading for mobile and cumulative files.

3. Data Analysis:

   - Load the JSON data files into pandas DataFrames.
   - Process and clean the data (e.g., handling missing values).
   - Perform analyses to identify articles with maximum/minimum average pageviews, top peak pageviews, and fewest months of data.

4. Visualization:
   - Generate time series plots for the analyses.
   - Ensure all graphs have appropriate scales, labels, legends, and titles.

## Contact Information

For any questions, issues, or contributions, please contact:

- Name: Priyam Gupta
- Email: pgupta1@uw.edu

## License

This project's code is licensed under the MIT License. See the LICENSE file for details.

## Acknowledgements

- Wikimedia Foundation: For providing access to the Pageviews API and the wealth of data.
- National Organization for Rare Diseases (NORD): For the database of rare diseases used to compile the article list.
- Sample Code License: Portions of the code are based on sample code licensed under CC-BY.
