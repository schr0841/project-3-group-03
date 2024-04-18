# Project-3 for the University of Minnesota Data Visualization and Analytics Bootcamp
## Contributors: Gregory Schreiter, Marsha Cole, Blake Sandvick, Eriel Kabambi(Group-03)
### Description 
This project aims to delve into the complexities of heart disease by analyzing datasets on heart disease indicators and the US population for the year 2022. The purpose of this work is to employ the ETL workflow to our database and transform the data in creating different tables usable for analysis in various languages (SQL, Python,..).
By dissecting various indicators categorized by state, we construct an entity relationship diagram (ERD) using Postgres and conduct data analysis utilizing Python and SQL Alchemy to address our research questions.

### File contents
Resources folder: contains the cleaned files utilized as our database. The primary file hd_csv contains various indicators of heart disease segmented by state within the population estimate. The secondary file named "us-regions_census," houses the total population figures for each state.

Data folder:  contains the original csv files extracted from Kaggle and the census website.
Images folder:  contains various screenshots of our outputs.

### Database documentation
As a group, we were interested in working on a healthcare project, and we found this dataset to be large and suitable for our needs. We used pandas to clean up the data, Postgres to create a schema and an entity relationship diagram (ERD), and SQL Alchemy to run various queries and find answers to our research questions.

### Data ethics
The data used during this project was all legally obtained from the Center for Disease Control and US Census Bureau. The data contained no personally identifiable information that would violate HIPAA. At no point in our data exploration or analysis did we think that this data should not be used from an ethical perspective.



## Project pipeline: csv/xlsx -> Python (pandas/pandera) -> PostgreSQL -> Python(SQLAlchemy)

### Data Sources
Pytlak, Kamil (n.d.). Indicators of Heart Disease (2022 Update). Retrieved from Kaggle: https://www.kaggle.com/datasets/kamilpytlak/personal-key-indicators-of-heart-disease/
246022 entries across 40 columns. Key columns: Demographics, health status, medical history, lifestyle, etc.


United States Census Bureau (2024). National Population by Characteristics: 2020-2023. Retrieved from: https://www.census.gov/data/tables/time-series/demo/popest/2020s-national-detail.html
67 entries across 4 columns. Key columns: State, total population (18+ yrs), total number (18+ yrs), total percent 


### Data Cleaning

Transformation of the datasets included:

Splitting the ‘RaceEthnicityCategory’ to Race and Ethnicity 
Limiting the scope of the the project to the US states and the District of Columbia by dropping the US territories (both datasets)
Replacing No/Yes values with numeric boolean values (0/1) 
Converting datatypes (both datasets)
Renaming of the columns
Removing periods (with regular expression)
Creating a new column to assign each state to a US region

### Data Validation

Once the csv files were cleaned in python, we created validation tests using the Pandera python package to check that the data values were as expected.  We were able to identify many null values in a column of our cleaned dataframe that we did not expect to be there. The following image represents the created test suite:

![validation1](https://github.com/schr0841/project-3-group-03/blob/main/images/validation1.png)

![validation2](https://github.com/schr0841/project-3-group-03/blob/main/images/validation2.png)


This allowed us to create an accurate schema in PostgreSQL that successfully loaded the data.


### Database Creation

Using the cleaned and validated csv files, we created a PostgreSQL database to house the tables. SQL was chosen because our csv files contain well-structured survey  response data. 

We created a schema in PostgreSQL and generated an Entity Relationship Diagram based on that:

![ERD](https://github.com/schr0841/project-3-group-03/blob/main/images/ERD.png)

The ERD clearly shows the two tables of data in our database.


### SQLAlchemy for database retrieval

Using a local PostgreSQL server, we were able to query the data using SQLAlchemy combined with psycopg2 and bring the results of those queries back into Python for further use.



