pip install seaborn
# Statistics for Data Science with Python - Yechan Kim
## Load Dataset
import pandas as pd
#import plotly.express as px
import seaborn as sns
import matplotlib.pyplot as pyplot
import matplotlib.ticker as ticker
import scipy.stats
## Task 1: Get Familiar With Data
# CRIM: per capita crime rate by town
# ZN: proportion of residential land zoned for lots over $25,000 sq.ft.
# INDUS: proportion of non-retail business acres per town.
# CHAS: Charles River dummy variable (1 if tract bounds river; 0 otherwise)
# NOX: nitric oxides concentration (parts per 10 million)
# RM: average number of rooms per dwelling
# AGE: proportion of owner-occupied units built prior to 1940
# DIS: weighted distances to five Boston employment centres
# RAD: index of accessibility to radial highways
# TAX: full-value property-tax rate per $10,000
# PTRATIO: pupil-teacher ratio by town
# LSTAT: % lower status of the population
# MEDV: Median value of owner-occupied homes in $1000's
boston_df.describe()
boston_df.head(10)
## Task 2: Create an IBM account
Skipped as it is optional
## Task 3: Load the Dataset in your Jupyter Notebook
boston_url = 'https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-ST0151EN-SkillsNetwork/labs/boston_housing.csv'
boston_df=pd.read_csv(boston_url)
boston_df.head()
sns.boxplot(x=boston_df['MEDV']).set_title("Median value of owner-occupied homes in $1000's")
ax = sns.boxplot(y = 'MEDV', data = boston_df)
ax.set_title('Owner-occupied homes')
### The boxplot above shows the median value for the variable MEDV among with outliers
## Question 2: Provide a histogram for the Charles River variable
ax2 = sns.countplot(x = 'CHAS', data = boston_df)
ax2.set_title('Number of homes near the Charles River')
### The histogram shows that the majority of the houses are not near the Charles River
## Question 3: Provide a boxplot for the MEDV variable vs the AGE variable - Discretize the age variable into three groups of 35 years and younger, between 35 and 50 years and older
boston_df.loc[(boston_df['AGE'] <= 35), 'Age_Group'] = '35 years and younger'
boston_df.loc[(boston_df['AGE'] > 35) & (boston_df['AGE'] < 70), 'Age_Group'] = 'between 35 and 70 years'
boston_df.loc[(boston_df['AGE'] >= 70), 'Age_Group'] = '70 years and older'
ax3 = sns.boxplot(x = 'MEDV', y = 'Age_Group', data = boston_df)
ax3.set_title('Median value of owner-occupied homes per Age Group')
### The boxplot above shows that on average the median value of owner occupied homes is higher when the Age is lower
## Question 4: Provide a scatter plot to show the relationship between Nitric oxide concentrations and the proportion of non-retail business acres per town. What can you say about the relationship?
ax4 = sns.scatterplot(y = 'NOX', x = 'INDUS', data = boston_df)
ax4.set_title('Nitric oxide concentration per proportion of non-retail business acres per town')
