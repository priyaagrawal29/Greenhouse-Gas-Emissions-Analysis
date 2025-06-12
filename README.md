# Greenhouse-Gas-Emissions-Analysis
## Project Summary
This project involves an in-depth analysis of greenhouse gas emissions data from the United Kingdom (UK). The objective of the analysis is to determine how to reduce greenhouse gas emissions in the UK due to the UK's agreement with the United Nations Framework Convention on Climate Change treaty and the Kyoto Protocol which are a commitment to maintain greenhouse gas concentrations at a certain level. This ensures that climate change caused by humans does not get to a point where it would be hazardous. The analysis was conducted in Python and visualizations were generated in Tableau. The insights derived from the visualizations will help the UK's government understand what affects greenhouse gas emissions and develop strategies for reducing greenhouse gas emissions.
## Research Questions
- Is there a relationship between emissions and land area?
- Does population have an effect on emissions?
- Which greenhouse gas has the most emissions?
- How have greenhouse gas emissions changed over time?
- Which regions have the highest and lowest emissions?
- Can patterns in the data inform strategies to reduce emissions?
- How do emission amounts in England compare to those in Northern Ireland, Scotland, and Wales?
- Are there any existing programs or efforts in place to decrease emissions?
- How do emissions vary by local authority?
- Which sectors have the highest greenhouse gas emissions?
- Do Mid-year Population (thousands) and Area (km2) have an effect on each other?
- How does Mid-year Population (thousands) influence CO2 emissions within the scope of influence of LAs (kt CO2)?
- What causes the differences in territorial emissions between the regions?
- Which greenhouse gas contributes the most to territorial emissions in each region?
## Data
Datasets used for this project:
- [2005 to 2022 local authority greenhouse gas emissions dataset](https://assets.publishing.service.gov.uk/media/667ad86497ea0c79abfe4bfd/2005-2022-local-authority-ghg-emissions-csv-dataset.csv): Contains public sector information licensed under the Open Government Licence v3.0. License: [https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/](https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/)
- [UK regions GeoJson](https://www.kaggle.com/datasets/dorianlazar/uk-regions-geojson/data)
### 2005 to 2022 Local Authority Greenhouse Gas Emissions Dataset
This dataset includes the territorial emissions, CO2 emissions within the scope of influence of local authorities, mid-year populations, and areas for the emissions of each greenhouse gas in each local authority greenhouse gas sub-sector in the UK from 2005-2022. Some rows are missing data for the Country Code, Region Code, Second Tier Authority, Mid-year Population, and Area columns. This dataset is from the UK government and the data was collected by the Department for Energy Security and Net Zero National Statistics of energy consumption for local authority areas and the UK National Atmospheric Emissions Inventory in the UK's annual inventory of greenhouse gas emissions.
### UK Regions GeoJSON
This document includes the coordinates for the borders of the twelve UK regions. This document is from Kaggle and was used to generate geospatial visualizations.
## Folders
- 01 Project Management: Contains the project brief.
- 02 Data: Contains two subfolders:
    - Original Data: Contains original datasets.
    - Prepared Data: Contains datasets that are cleaned and ready for analysis.
- 03 Scripts: Contains Jupyter Notebooks with Python code for the analysis.
- 04 Analysis: Contains an HTML version of a map of the greenhouse gas emissions in the various UK regions.
## Tools Used
- Python and Jupyter Notebooks: To write and execute code.
- Numpy: For numerical operations.
- Pandas: For data analysis, cleaning, and manipulation.
- OS: For connecting with the device's operating system.
- Matplotlib and Matplotlib.pyplot: For creating various types of visualizations.
- Seaborn: For creating statistical visualizations.
- Scipy: For more complicated numerical operations.
- Folium: For creating interactive maps.
- JSON: For handling a JSON/GeoJSON file.
- Sklearn: For running machine learning algorithms.
- Pylab: For creating visualizations and manipulating data.
## Techniques
The following techniques were used in this project:
- Data profiling
- Data cleaning
- Data wrangling
- Exploratory data analysis
- Data visualizing in Python
- Linear regression
- Clustering analysis
- Time-series analysis
- Storytelling with Tableau
## Cleaning and Analyzing Data
The first step of data cleaning required checking for mixed-type data. I found that there were three columns with mixed-type data which were the Country Code, Region Code, and Second Tier Authority columns. I changed the data types for these three columns to string. The second step of data cleaning required checking for duplicates. I did not find any duplicates in the dataset. The third step of data cleaning required checking the value counts of each column to ensure that all values were spellt correctly and correctly formatted. I did not find any spelling or formatting errors in the dataset. The fourth step of data cleaning required checking for missing values. I found that there were missing values in five columns which were the Country Code, Region Code, Second Tier Authority, Mid-year Population, and Area columns. For the Country Code, Region Code, and Second Tier Authority columns, I replaced the missing values with "Unknown". For the Mid-year Population column, I replaced the missing values with the mean mid-year population as the mean seemed to be a more appropriate value to impute than the median. For the Area column, I replaced the missing values with the median area as the median seemed to be a more appropriate value to impute.

I conducted exploratory data analysis to explore the relationships between the various numeric variables: Territorial emissions (kt CO2e), CO2 emissions within the scope of influence of LAs (kt CO2), Mid-year Population (thousands), and Area (km2). The correlation heatmap of these variables did not show a strong relationship between any of the variables.

![image](https://github.com/user-attachments/assets/d19c5834-72b4-4f5a-8cb9-50b488cb7c31)

I visualized Territorial emissions (kt CO2e) and CO2 emissions within the scope of influence of LAs (kt CO2) as they had a correlation coefficient of 0.50 which was the largest correlation coefficient between any of the variables. This did not result in a good correlation as approximately half of the data points on the scatterplot follow the trendline, and half do not.

![image](https://github.com/user-attachments/assets/ce190c16-2cd9-45c8-829a-70229e5ff114)

I generated a pair plot to visually see the relationships between all the numeric variables. The visualizations in the pair plot showed potential for further exploration into the relationship between Mid-year Population (thousands) and Area (km2).

![image](https://github.com/user-attachments/assets/22df6e38-365c-44e8-be25-a3574e5fac29)

I hypothesized that as area increases, mid-year population increases. To test my hypothesis, I first used the linear regression machine learning algorithm which involved splitting the dataset into a training set and a test set, creating and fitting a regression object on the training set, and creating a prediction for y on the test set. The linear regression was not a good fit for the data as many data points do not follow the regression line, which indicates that the linear regression did not accurately predict the effect of area on mid-year population.

![image](https://github.com/user-attachments/assets/36965b8e-b37b-4228-a25e-94e7c8fd8ff9)

Since the linear regression technique was not adequate for describing the relationship between area and mid-year population, I conducted a cluster analysis which resulted in four clusters. The cluster with the largest area, the pink cluster, has the second-highest mid-year population and highest territorial emissions. The cluster with medium area, the dark purple cluster, has the second-lowest mid-year populations of all the clusters and lower territorial emissions than the pink cluster. The cluster with low area, the purple cluster, has the highest mid-year populations and the second-lowest territorial emissions. The cluster with very low area, the light pink cluster, has the lowest mid-year populations and territorial emissions. The results of the cluster analysis led to the conclusion that mid-year population does not increase as area increases.

![image](https://github.com/user-attachments/assets/a8f70670-0332-4336-bb93-169df16ddd24)

I conducted a time series analysis to look at the change in territorial emissions overtime from 2005-2022. This required decomposing the time series using an additive model, analyzing the separate time series components, conducting a Dickey-Fuller test to test for stationarity, and then stationarizing the data. I found that territorial emissions have decreased consistently from 2005 to 2022 with three slight increases, once in 2010, once in 2012, and once in 2021. I also found that there is no seasonality in the data along with no unexplained noise. The stationary time series curve:

![image](https://github.com/user-attachments/assets/c0af8a46-6c4f-40ab-acf8-9e938b207b0c)

## Results and Recommendations
Results and Reccomendations:
- Mid-year population does not increase as area increases.
- It is possible that territorial emissions increase as area increases.
- Greenhouse gas emission reduction strategies should be focused on the local authorities within the pink cluster as these represent the areas that have the most emissions.
- The highest priority for greenhouse gas emission reduction strategies should be on local authorities in the pink cluster, followed by the dark purple cluster, purple cluster, and the light pink cluster.
## Visualizations
View visualizations generated for this project here: [Visualizations on Tableau Public](https://public.tableau.com/app/profile/priya.agrawal4103/viz/UKGreenhouseGasEmissionsAnalysis/GreenhouseGasEmissions)
The Tableau visualizations do not contain the time series analysis as it was not relevant to the final results.
## Contact
If you would like more details about the project, or if you have any questions, please feel free to contact me through [LinkedIn](https://www.linkedin.com/in/priya-agrawal-0929) or [email](mailto:priya.agrawal0929@gmail.com).
