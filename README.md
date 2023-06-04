# Statistics for Data Science with Python - Yechan Kim
## Load Dataset
import pandas as pd
import numpy as np
import seaborn as sns
importscipy.stats.
import statsmodels.api as sm

## Task 1 : Get Familar With Data
· CRIM - per capita crime rate by town
· ZN - proportion of residential land zoned for lots over 25,000 sq.ft.
· INDUS - proportion of non-retail business acres per town.
· CHAS - Charles River dummy variable (1 if tract bounds river; 0 otherwise)
· NOX - nitric oxides concentration (parts per 10 million)
· RM - average number of rooms per dwelling
· AGE - proportion of owner-occupied units built prior to 1940
· DIS - weighted distances to five Boston employment centres
· RAD - index of accessibility to radial highways
· TAX - full-value property-tax rate per $10,000
· PTRATIO - pupil-teacher ratio by town
· LSTAT - % lower status of the population
· MEDV - Median value of owner-occupied homes in $1000's
## Task 2 : Create an IBM account
As this was an optional step, I skipped this one as I had created such an account previously. Also, I will use my Github account for uploading this file.
## Task 3: Load in the Dataset in your Jupyter Notebook
boston_url = 'https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-ST0151EN-SkillsNetwork/labs/boston_housing.csv'
boston_df=pd.read_csv(boston_url)
boston_df.head()

from prettytable import PrettyTable

data = {
    'CRIM': [0.00632, 0.02731, 0.02729, 0.03237, 0.06905, 0.02985],
    'ZN': [18, 0, 0, 0, 0, 0],
    'INDUS': [2.31, 7.07, 7.07, 2.18, 2.18, 2.18],
    'CHAS': [0, 0, 0, 0, 0, 0],
    'NOX': [0.538, 0.469, 0.469, 0.458, 0.458, 0.458],
    'RM': [6.575, 6.421, 7.185, 6.998, 7.147, 6.43],
    'AGE': [65.2, 78.9, 61.1, 45.8, 54.2, 58.7],
    'DIS': [4.09, 4.9671, 4.9671, 6.0622, 6.0622, 6.0622],
    'RAD': [1, 2, 2, 3, 3, 3],
    'TAX': [296, 242, 242, 222, 222, 222],
    'PTRATIO': [15.3, 17.8, 17.8, 18.7, 18.7, 18.7],
    'LSTAT': [4.98, 9.14, 4.03, 2.94, 5.33, 5.21],
    'MEDV': [24, 21.6, 34.7, 33.4, 36.2, 28.7]
}

table = PrettyTable()
table.field_names = list(data.keys())

for i in range(len(data['CRIM'])):
    table.add_row([data[key][i] for key in data.keys()])

print(table)
ax = boston.boxplot(column="Age", by="Sex")


## Become familiar with the dataset


Generate Descriptive Statistics and Visualizations
Question 1: For the 'Median value of owner-occupied homes' provide a boxplot
ax = sns.boxplot(y = 'MEDV', data = boston_df)
ax.set_title('Owner-occupied homes')
Text(0.5, 1.0, 'Owner-occupied homes')

boston_df.describe()
