# Saber 11 – The Influence of Teachers on Colombian Students’ Academic Performance

## Project Overview

Students seeking to graduate from the final year of secondary education in Colombia (11th grade) are required to take the Saber 11 examination, commonly referred to as the ICFES after the institution responsible for administering the test. In addition to measuring students’ academic performance, the examination collects demographic and socioeconomic information about students and educational institutions, as well as data on parents’ employment and educational backgrounds and characteristics of the schools students attend.

In practice, the Saber 11 examination is widely used as a measure of academic quality and excellence among students and schools. Its results serve multiple purposes, including admission filters for higher education, a value proposition for schools seeking to attract students, and criteria for accessing scholarships and educational financing programs. Since all stakeholders involved in the education system seek to improve academic outcomes, understanding the conditions and characteristics of students and educational institutions associated with these results can support informed decisions about where to allocate resources to improve the educational process.

However, there is an important limitation: public Saber 11 records do not include teachers’ characteristics or any direct measure of teacher performance, despite their central and essential role in the educational process. For further discussion on why such information is not available, see La quinta puerta by García Villegas, Fergusson, and Cárdenas (2021).

Therefore, this project addresses both a methodological and a practical question: How can the Colombian government, using publicly available data, assess and account for the impact of teachers and educational institutions on Saber 11 examination outcomes?

## Data Sources

The project combines information from two main Colombian public data sources:

### DANE – Teacher Information

From the [DANE – National Administrative Department of Statistics](https://www.dane.gov.co/) databases, we obtained information about teachers, including:

- Age
- Educational attainment
- Employment and contracting status
- Educational levels or grades in which they teach
- Number of teachers
- Other relevant teacher characteristics

### ICFES – Student and School Information

From the [ICFES – Colombian Institute for the Evaluation of Education](https://www.icfes.gov.co/) databases, we obtained Saber 11 examination data covering the period from 2015 to 2024.

The datasets include:

- Saber 11 examination results
- School characteristics, such as school schedule, administrative sector, and geographic location
- Students’ socioeconomic characteristics
- Students’ demographic characteristics
- Other relevant information about students and educational institutions

By combining these sources, the project seeks to explore the relationship between teacher characteristics, school characteristics, and student academic performance using data analysis and Machine Learning techniques.

## Phases 

1. Data Collection — Ready
   Gathering data from different publicly available sources related to students, schools, teachers, and Saber 11 results.

2. Data Integration — Ready  
   Combining the different datasets using common identifiers to connect student, school, and teacher information.

3. Dataset Creation — Ready  
   Building the initial integrated dataset containing the relevant student, school, teacher, socioeconomic, and academic information.

4. Data Translation — In Progress  
   Translating the dataset from Spanish into English, including variable names, categories, labels, and relevant values.

5. First EDA  
   Exploring the initial dataset to understand the distribution of Saber 11 results and identify patterns, relationships, and potential data issues.

6. Data Cleaning  
   Handling missing values, duplicates, inconsistencies, invalid records, and other data-quality issues.

7. Second EDA  
   Exploring the cleaned dataset to identify relevant patterns and relationships between student, teacher, school, and academic characteristics.

8. Model Dataset Creation  
   Preparing the final dataset for modeling by selecting relevant variables, transforming the data, and defining the target and explanatory variables.

9. Model Training and Evaluation  
   Training and evaluating models to estimate the relationship between teacher and school characteristics and Saber 11 outcomes.

10. Findings and Conclusions  
    Interpreting the results, identifying the main findings, and discussing how they can support decisions about educational resources and policies.

## Version

![Pandas](https://img.shields.io/badge/pandas-2.3.2-150458?logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/numpy-2.3.4-013243?logo=numpy&logoColor=white)
![Seaborn](https://img.shields.io/badge/seaborn-0.13.2-4C72B0)
![Matplotlib](https://img.shields.io/badge/matplotlib-3.10.6-11557C?logo=matplotlib&logoColor=white)
![Scikit--learn](https://img.shields.io/badge/scikit--learn-1.7.2-F7931E?logo=scikit-learn&logoColor=white)