# NYPD-TRAFFIC-ACCIDENT_2018--Data-Cleaning

# INTRODUCTION
As a Data Analyst, i was given a task to clean the data gathered by New York Police Department concerning Accident occurrences from January- December 2018. Each record represents an individual accident including the Date, Time, Geographical Information (such as: Borough, location, off_street, cross_street and on_street) of the accident, type of vehicle involved, the severity of the accident and the cause of the accident. 
-	this data can be used to identify trends in the frequency of accident occurrences in a specific area or even a certain period.
-	we can identify the patterns in times of the day when accidents most likely occur.
-	which area has the highest number of accidents leading to death or injury.
-	we can also know how aware the public is to safe driving practices and also how effective traffic control is.

all the developed questions and initial insight into the data helped me while cleaning the data and also serve as a point of reference on how to go about the cleaning.
the data contained 57864 rows.
The following task was performed:
-	Exploratory Data Analysis (EDA)
-	Data Cleaning

# DATA EXPLORATION
I started with EDA (Exploratory Data Analysis) process. 
-	checked if the columns in my dataset is properly formatted
    - checked if data-items does not contain leading or trailing spaces, 
    - texts are in lowercase for easy readability
    - all data-item are spelled well and in better naming conventions for easy interpretations.
-	checked to see if there are no duplicate rows
-	identified number of unique values against duplicates for each column
-	checked the data type of each columns to know if data are consistent mainly the date and time columns
-	check for sum of missing values in each column
-	filter out some important columns (related to date, time, geographical information, type of vehicle, accident severity and causes of accident)

  
#  EDA Findings
-	the columns are properly pre-formatted
-	a result of zero (0) was returned for duplicate rows in the dataframe. This indicates that there are no duplicate rows in the Dataframe. each row is unique, and there are no identical rows based on all columns. this is a positive outcome as it suggests data integrity and helps ensure accurate analyses without concerns about duplicate entries.
-	A list concerning distinct rows for each column was returned. the "unique_key" has the highest number of unique values. this column can represent our primary key that will identify all other rows, thereby ensuring data integrity.
-	From the values returned for missing values. This identified
     - the columns: unique key, date, time and accident severity (all injured and killed) are highly populated with values. 
     - the geographic info (borough, location, on_street, off_street and cross_street) display inconsistent data, with only location being the most populated.
     - the columns related to vehicle 3-5 and cause_vehicle 3-5 shows a large amount of missing values.
-	I noticed the location column can be split into more conventional columns of longitude and latitude, which are easier read by visualization and analytical tool.
-	from the accident severity category, although the pedestrians_injured', 'cyclist_injured', 'motorist_injured' columns, are fully populated, the 'total_injured' column has 1 value missing. same applies to the 'pedestrians_killed','cyclist_killed', 'motorist_killed' columns, with the 'total_killed' missing 5 values. we can asssume the total number of injured and killed respectively is the sum of pedestrians, cysclist and motorist injured and killed respectively.


# DATA CLEANING
-	the date and time datatype were changed from object to datetime to enhance data consistency
-	all columns with "unspecified" values and empty were made NaN to maintain consistency and also to get a better visual view of missing values later using the missingno library
-	location column containing coordinates was split into separate columns of longitude and latitude to make it easier to perform analysis and visualizations.
-	I changed both coordinate columns (longitude and latitude) to float datatype for easy calculations and accessibility by visualization tools.
-	from my EDA findings for accident severity, I used the sum of the cyclist, motorist and pedestrian killed and injured respectively to fill the missing value rows of the total killed and injured respectively.
-	from further geographic study, the latitude of New york is 40.7128 and the longitude is 74.0060. therefore, any values that fall outside this range was obviously incorrect entries. these rows were identified and changed to missing values (NaN) thereby increasing the Missing value of longitude and latitude by 16.
-	columns with more than 30000 of missing values were dropped, with the consideration of essential columns for further analysis in mind.
-	I also deleted the location column since it has been split into longitude and latitude
-	I saved my more refined dataframe as a csv file.	

#  CONCLUSION AND RECOMMENDATION
Based on the refined dataframe the most obvious issue is the large amount of missing values in few columns especially the geographical information columns (Borough and on_street).
this problem can be solved using some special process such as using google api or using dummy data, which pose a threat to further analysis to be done. It all depends on the kind of insights you are trying to get from the data. 
This all depends all the kind of insights you want to get from the dataset. 




 - 
