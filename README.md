# Where_to_live_for_your_health?

## Introduction
This is an investigation into how an individual’s choice in residence may impact their health. Cancer rates are the main parameter to determine the overall health of each county in the United States. Cancer is currently the second leading cause of death in the nation, the causes of which have been linked to many poor health choices, including environmental factors, making it a very good indicator of the health of populations. A dataset from the NIH that includes cancer type, demographic information, and location for each across the United States is used for this analysis. Two additional datasets describe the environmental status of each county in the United States. Air quality datasets were gathered from the Environmental Protection Agency that shows air quality indexes for common air pollutants such as NO2, O3, and CO. Additionally, a water quality dataset was gathered from the Center for Disease Control (CDC) to observe the heavy metal contaminants in the drinking water sources for each county. These three datasets can describe a basic picture of each US County’s environment, and how this environment might be correlated with cancer rates.  
  
Final story can be found at: http://sheraning.georgetown.domains/pw%20test/mycancer.html#clean

Python code for conducting analysis techniques is in air_water_cancer.ipynb

## Dataset
### Air Data
Days with AQI
Number of days in the year having an Air Quality Index value. This is the number of days on which measurements from any monitoring site in the county or MSA were reported to the AQS database.  
  
Days Good
Number of days in the year having an AQI value 0 through 50.
  
Days Moderate
Number of days in the year having and AQI value 51 through 100.
  
Days Unhealthy for Sensitive Groups
Number of days in the year having an AQI value 101 through 150.
   
Days Unhealthy
Number of days in the year having an AQI value 151 through 200.

Days Very Unhealthy
Number of days in the year having an AQI value 201 or higher. This includes the AQI categories very unhealthy and hazardous. Very few locations (about 0.3% of counties) have any days in the very unhealthy or hazardous categories.

AQI Max
The highest daily AQI value in the year.

AQI 90th %ile
90 percent of daily AQI values during the year were less than or equal to the 90th percentile value.

AQI Median
Half of daily AQI values during the year were less than or equal to the median value, and half equaled or exceeded it.

Days CO
Days NO2
Days O3
Days SO2
Days PM2.5
Days PM10  

A daily index value is calculated for each air pollutant measured. The highest of those index values is the AQI value, and the pollutant responsible for the highest index value is the "Main Pollutant." These columns give the number of days each pollutant measured was the main pollutant. A blank column indicates a pollutant not measured in the county or CBSA.
  
New columns created in the clean set
Since each county did not collect data for 365 days each year, each Good, hazardous, Unhealthy etc Day column must be normalized by the number of days that were recorded. 

For example:
Good days_Norm = GoodDays/ Days with AQI
Therefore, this column shows the percentage of “good days” each year based on the number of days AQI was taken for that county, that year.
This also applied for the Days CO, NO2, etc.

### Water Data
'Year': 2011-2015
'FIPS': includes State and County code in one variable
'Value': the concentration of arsenic (?g/L)
'County': County Name
'State': State Abbreviation
'Quality': a categorical data by binning the mean into three categories
  		binning rule: level < 1 (?g/L) means non-detected arsenic
    		level in 1~10 (?g/L) means less than MCL = "no harm"
        			level in 10~60 (?g/L) means "harmful"
Maximum Contaminant Levels = MCL

### Cancer Data
‘Categories’ : ‘Groups’ (groups are subcategories of categories)

'All': 'Total'
'Cancer Type': 'Lung Cancer'
'Race/Ethnicity': 'White Hispanic', 'White Non-Hispanic',  'Black (includes Hispanic)', 'Amer. Indian/Alaskan Native (includes Hispanic)', 'Asian or Pacific Islander (includes Hispanic)',  'Hispanic (any race)'
'Sex': 'Males', 'Females'
'Age': '<50', '50+', '<65', '65+'

Columns (NA indicates not useful):
'County': County Name
'FIPS': includes State and County code in one variable
'Met Healthy People Objective of ***?': NA
'Age-Adjusted Incidence Rate(†) - cases per 100,000': numeric
'Lower 95% Confidence Interval': for Age Adjusted rate
'Upper 95% Confidence Interval': for Age Adjusted rate
'Average Annual Count': numeric
'Recent Trend': categorical
'Recent 5-Year Trend (‡) in Incidence Rates': numeric (is a percentage)
'Lower 95% Confidence Interval.1': for 5 year trend
'Upper 95% Confidence Interval.1': for 5 year trend
'Category': categorical, described above
'Group': categorical, described above
'State': State full name
'SEER': NA, registry id where data came from
'NPCR': NA, registry id where data came from
