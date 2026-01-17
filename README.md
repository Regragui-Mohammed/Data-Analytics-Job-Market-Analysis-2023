# Overview
This project analyzes the data job market with a focus on Data Analyst roles, with the goal of identifying high-demand and high-paying skills that lead to better job opportunities.

The dataset is sourced from Luke Barousse’s Python course, containing job posting information such as job titles, salaries, locations, and required skills. Using Python-based analysis and visualization, the project investigates skill demand patterns, salary trends, and the best skill combinations for Data Analysts who want to maximize career growth.

# The Questions
The analysis aims to answer the following key questions:
1. What skills are most in demand for the top three most popular data roles?    
2. How do in-demand skills trend over time for Data Analysts?
3. How well do Data Analyst roles and associated skills pay?
4. Which skills are the most optimal for Data Analysts to learn? (high-demand + high-paying)

# Tools I Used
This analysis was conducted using the following tools:

- Python — used for data preparation, exploration, and analysis

        - Pandas — data manipulation and aggregation

        - Matplotlib — core visualization 

        - Seaborn — advanced statistical charts
- Jupyter Notebooks — interactive analysis, documentation, and experimentation

- Visual Studio Code — running scripts and project development

- Git & GitHub — version control, project tracking, and publishing results


# Data Preparation and Cleanup

To ensure accuracy and usability, the dataset underwent preprocessing steps including date conversion and skill parsing.

## Importing Libraries and Data

```python
# Importing necessary libraries
import ast
import pandas as pd
import seaborn as sns
from datasets import load_dataset
import matplotlib.pyplot as plt 

# Loading Data
dataset = load_dataset('lukebarousse/data_jobs')
df = dataset['train'].to_pandas()

#data cleanup
df['job_posted_date'] = pd.to_datetime(df['job_posted_date'])
df['job_skills'] = df['job_skills'].apply(lambda x : ast.literal_eval(x) if pd.notna(x) else x)
```
View my notebook with detailed steps here:[ "Importing and Cleanup"](<Part/Importing and Cleanup.ipynb>)


## Filtering for U.S.-Based Jobs
To narrow the analysis to a consistent job market, this project focuses on job postings located in the United States:

```python
df_US_DA = df[(df['job_country'] == 'United States') & (df['job_title_short'] == 'Data Analyst')].copy()
```
