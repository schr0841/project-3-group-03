# Exploring Heart Disease Indicators: A Data Engineering Project

## Contributors: Gregory Schreiter, Marsha Cole, Blake Sandvick, Eriel Kabambi (Group-03)

### Description 
This project delves into the complexities of heart disease by analyzing datasets on heart disease indicators and the US population for the year 2022. The purpose of this work is to employ the ETL workflow in our database and transform the data to create different tables usable for analysis in various languages (SQL, Python...). By dissecting various indicators categorized by state, we constructed an entity relationship diagram (ERD) using PostgreSQL and conducted data analysis utilizing Python SQLAlchemy library to address our research questions.

### File contents
- [Resources folder](https://github.com/schr0841/project-3-group-03/tree/main/Resource): Contains the cleaned files utilized as our database. The primary file, `hd_csv`, contains various indicators of heart disease segmented by state within the population estimate. The secondary file, `us-regions_census`, houses the total population figures for each state.

- [Data folder](https://github.com/schr0841/project-3-group-03/tree/main/data): Contains the original csv files extracted from Kaggle and the US Census Bureau website.
  
- [Images folder](https://github.com/schr0841/project-3-group-03/tree/main/images): Contains various screenshots of our outputs.

### Database documentation
As a group, we were interested in working on a healthcare project, and we found the dataset to be large and suitable for our needs. We used Pandas to clean and transform the data, Pandera for data validation, PostgreSQL to create the schema and an entity relationship diagram (ERD), and SQLAlchemy to run various queries and find answers to our research questions.

## Project pipeline: 
### Datasets (csv and xlsx) -> Python (Pandas and Pandera) -> PostgreSQL -> Python(SQLAlchemy)

### Data Sources
The datasets were obtained from:
1. [Indicators of Heart Disease (2022 Update)](https://www.kaggle.com/datasets/kamilpytlak/personal-key-indicators-of-heart-disease/)

2. [National Population by Characteristics: 2020-2023](https://www.census.gov/data/tables/time-series/demo/popest/2020s-national-detail.html)

### Data Cleaning

Transformation of the datasets included:

- Splitting the ‘RaceEthnicityCategory’ to Race and Ethnicity (heart disease dataset)

- Limiting the scope of the project to the US states and the District of Columbia by dropping the US territories (both datasets)

- Replacing No/Yes values with numeric boolean values (0/1) (heart disease dataset)

- Converting data types (both datasets)

- Renaming of the columns (census data)

- Removing periods with regular expression (census data)

- Creating a new column to assign each state to a US region (census data)

### Data Validation

Once the csv files were cleaned in Python, we created validation tests using the Pandera Python package to check that the data values were as expected.  We were able to identify many null values in a column of our cleaned dataframe that we did not expect to be there. The following image represents the created test suite:

![validation1](https://github.com/schr0841/project-3-group-03/blob/main/images/validation1.png)

![validation2](https://github.com/schr0841/project-3-group-03/blob/main/images/validation2.png)

This allowed us to create an accurate schema in PostgreSQL that successfully loaded the data.


### Database Creation

Using the cleaned and validated csv files, we created a PostgreSQL database to house the tables. SQL was chosen because our csv files contain well-structured survey  response data. We created a schema in PostgreSQL and generated an Entity Relationship Diagram based on that:

![ERD](https://github.com/schr0841/project-3-group-03/blob/main/images/ERD.png)

The ERD clearly shows the two tables of data in our database.


### SQLAlchemy for database retrieval
Using a local PostgreSQL server, we were able to query the data using SQLAlchemy combined with psycopg2 and bring the results back into Python for further use.

#### Research Questions
Our initial query showed that there was not uniform sampling done in each state. Vermont had the highest sampling rate at 0.009, and California had the lowest at 0.0001:
![Q1](https://github.com/schr0841/project-3-group-03/blob/main/images/researchQ1.png)

#### How does the incidence of heart disease vary across states/regions of the US?
![Q2](https://github.com/schr0841/project-3-group-03/blob/main/images/researchQ2.png)
![Q3](https://github.com/schr0841/project-3-group-03/blob/main/images/researchQ3.png)

States:  
Highest - Arkansas at 8% 
Lowest - District of Columbia at 3%

Regions:  
Highest - South at 6% 
Lowest - West at 4.9%

#### Do males or females have a higher incidence of heart disease?
![Q4](https://github.com/schr0841/project-3-group-03/blob/main/images/researchQ4.png)
Males have a higher rate of heart disease at 7% than females (4%)

### Conclusion
This data engineering project demonstrates the process of extracting, transforming (using Python Pandas library), and loading data from csv files into a PostgreSQL database. Additionally, the Python SQLAlchemy library was used for reading data from the database and displaying it for future use. The provided scripts and documentation serve as a guide for understanding and replicating the ETL process for similar datasets. 

We learned that transformed csv files in pandas can sometimes result in columns with missing values. It is important to always check for this before creating a SQL database schema. Further work on this project could include creating interactive visualizations in Flask and researching ways to host the database on the web as opposed to a local server.

### Data ethics
The heart disease indicator dataset used during this project from Kaggle was legally obtained from the Center for Disease Control and the US Census Bureau. Each state health department collected the data using random digit dialing to administer the BRFSS Frequently Asked Questions (BRFSS) surveys continuously throughout the year. The data contained no personally identifiable information that would violate HIPAA. Furthermore, due to the anonymous nature of the survey and the fact that the covered entity (individual, organization, or agency that must follow HIPAA rules) did not administer the survey, there is no HIPAA obligation. 

### References
Center for Disease Control and Prevention (2018). BRFSS Frequently Asked Questions. Retrieved from https://www.cdc.gov/brfss/about/brfss_faq.htm

Endjin (2024). Data validation in Python: A look into Pandera and Great Expectations. Retrieved from https://endjin.com/blog/2023/03/a-look-into-pandera-and-great-expectations-for-Data-validation

Pytlak, Kamil (n.d.). Indicators of Heart Disease (2022 Update). Retrieved from Kaggle https://www.kaggle.com/datasets/kamilpytlak/personal-key-indicators-of-heart-disease/

United States Census Bureau (2024). National Population by Characteristics: 2020-2023. Retrieved from https://www.census.gov/data/tables/time-series/demo/popest/
2020s- national-detail.html

