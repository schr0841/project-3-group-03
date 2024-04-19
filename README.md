# Exploring Heart Disease Indicators: A Data Engineering Project

### Contributors: Gregory Schreiter, Marsha Cole, Blake Sandvick, Eriel Kabambi (Group-03)

### Description 
This project delves into the complexities of heart disease by analyzing datasets on heart disease indicators and the US population for the year 2022. The purpose of this work is to employ the ETL workflow in our database and transform the data to create different tables usable for analysis in various languages (SQL, Python, etc.). By dissecting various indicators categorized by state, we constructed an entity relationship diagram (ERD) using PostgreSQL and conducted data analysis utilizing the Python SQLAlchemy library to address our research questions.


### File Contents
- [Resource folder](https://github.com/schr0841/project-3-group-03/tree/main/Resource): Contains the cleaned files utilized as our database. The primary file, `hd_csv`, contains various indicators of heart disease segmented by state within the population estimate. The secondary file, `us-regions_census`, houses the total population figures for each state.

- [Data folder](https://github.com/schr0841/project-3-group-03/tree/main/data): Contains the original csv files extracted from Kaggle and the US Census Bureau website.
  
- [Images folder](https://github.com/schr0841/project-3-group-03/tree/main/images): Contains various screenshots of our outputs.


### Database Documentation
As a group, we were interested in working on a healthcare project, and we found the dataset to be large and suitable for our needs. We used Pandas to clean and transform the data, Pandera for data validation, PostgreSQL to create the schema and an entity relationship diagram (ERD), and SQLAlchemy to run various queries and find answers to our research questions.

## Project Pipeline
To execute the ETL process, follow these steps:
### Datasets (csv and xlsx) -> Python (Pandas and Pandera) -> PostgreSQL -> Python (SQLAlchemy)


### Data Sources
The datasets:
1. [Indicators of Heart Disease (2022 Update)](https://www.kaggle.com/datasets/kamilpytlak/personal-key-indicators-of-heart-disease/)

2. [National Population by Characteristics: 2020-2023](https://www.census.gov/data/tables/time-series/demo/popest/2020s-national-detail.html)


### Data Cleaning

Transformation of the datasets includes, but is not limited to:

- Splitting the ‘RaceEthnicityCategory’ column to Race and Ethnicity (heart disease dataset)

- Limiting the scope of the project to the US states and the District of Columbia by dropping the US territories (both datasets)

- Replacing No/Yes values with numeric boolean values (0/1) (heart disease dataset)

- Converting data types (both datasets)

- Renaming of the columns (census data)

- Removing periods with regular expression (census data)

- Creating a new column to assign each state to a US region (census data)


### Data Validation

Clean the datasets using the Python Pandas library, then create validation tests using the Pandera Python package to check that the data values are as expected.  
We were able to identify null values in a column of our cleaned dataframe that we did not expect to be there. This allowed us to create an accurate schema in PostgreSQL that successfully loaded the data. The following image represents the created test suite:

![validation1](https://github.com/schr0841/project-3-group-03/blob/main/images/validation1.png)

![validation2](https://github.com/schr0841/project-3-group-03/blob/main/images/validation2.png)


### Database Creation

Create the schema in PostgreSQL and generate the Entity Relationship Diagram, then create the tables and import the data. 
We created a PostgreSQL database to house the tables. The ERD clearly shows the two tables of data in our database. SQL was chosen because our csv files contain well-structured survey response data. 

![ERD](https://github.com/schr0841/project-3-group-03/blob/main/images/ERD.png)


### SQLAlchemy for Database Retrieval
Using a local PostgreSQL server, we were able to query the data using SQLAlchemy combined with psycopg2 and bring the results back into Python for further use.


## Research Questions
Our initial query showed that no uniform sampling was done in each state. 
- Vermont had the highest sampling rate at 0.009
- California had the lowest at 0.0001
  
![Q1](https://github.com/schr0841/project-3-group-03/blob/main/images/researchQ1.png)

### How does the incidence of heart disease vary across states/regions of the US?
![Q2](https://github.com/schr0841/project-3-group-03/blob/main/images/researchQ2.png)
![Q3](https://github.com/schr0841/project-3-group-03/blob/main/images/researchQ3.png)

States:  
- Highest - Arkansas at 8% 
- Lowest - District of Columbia at 3%

Regions:  
- Highest - South at 6% 
- Lowest - West at 4.9%

### Do males or females have a higher incidence of heart disease?
![Q4](https://github.com/schr0841/project-3-group-03/blob/main/images/researchQ4.png)
Males have a higher rate of heart disease at 7% than females (4%)


## Conclusion
This data engineering project demonstrates the process of extracting, transforming (using Python Pandas library), and loading data from csv files into a PostgreSQL database. Additionally, the Python SQLAlchemy library was used to read and display data from the database for future use. The provided scripts and documentation serve as a guide for understanding and replicating the ETL process for similar datasets. 

We learned that transformed csv files in Pandas can sometimes result in columns with missing values. It is essential to check for this before creating an SQL database schema. Further work on this project could include creating interactive visualizations in Flask and researching ways to host the database on the web as opposed to a local server.

## Data Ethics
The heart disease indicator dataset from Kaggle used during this project was legally obtained from the Centers for Disease Control. Each state health department collected the data using random digit dialing to continuously administer the BRFSS Frequently Asked Questions (BRFSS) surveys throughout the year. The data contained no personally identifiable information that would violate the Health Insurance Portability and Accountability Act (HIPAA). Furthermore, due to the anonymous nature of the survey and the fact that a covered entity (individual, organization, or agency that must follow HIPAA rules and protect the privacy and security of health information) did not administer the survey, there is no HIPAA obligation. 

## Powerpoint Presentation
[Heart Disease Presentation](https://docs.google.com/presentation/d/1nbJjvZ2oBHr72w8mUIXYPjzHL8iaukPHhhD4FCmoun8/edit?usp=sharing)


## References
Center for Disease Control and Prevention (2018). BRFSS Frequently Asked Questions. Retrieved from https://www.cdc.gov/brfss/about/brfss_faq.htm

Endjin (2024). Data validation in Python: A look into Pandera and Great Expectations. Retrieved from https://endjin.com/blog/2023/03/a-look-into-pandera-and-great-expectations-for-Data-validation

Pytlak, Kamil (n.d.). Indicators of Heart Disease (2022 Update). Retrieved from Kaggle https://www.kaggle.com/datasets/kamilpytlak/personal-key-indicators-of-heart-disease/

United States Census Bureau (2024). National Population by Characteristics: 2020-2023. Retrieved from https://www.census.gov/data/tables/time-series/demo/popest/2020s-national-detail.html

