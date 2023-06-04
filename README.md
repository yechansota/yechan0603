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
	CRIM	ZN	INDUS	CHAS	NOX	RM	AGE	DIS	RAD	TAX	PTRATIO	LSTAT	MEDV
0	0.00632	18	2.31	0	0.538	6.575	65.2	4.09	1	296	15.3	4.98	24
1	0.02731	0	7.07	0	0.469	6.421	78.9	4.9671	2	242	17.8	9.14	21.6
2	0.02729	0	7.07	0	0.469	7.185	61.1	4.9671	2	242	17.8	4.03	34.7
3	0.03237	0	2.18	0	0.458	6.998	45.8	6.0622	3	222	18.7	2.94	33.4
4	0.06905	0	2.18	0	0.458	7.147	54.2	6.0622	3	222	18.7	5.33	36.2
5	0.02985	0	2.18	0	0.458	6.43	58.7	6.0622	3	222	18.7	5.21	28.7
![image](https://github.com/yechansota/yechan0603/assets/134902281/725cc319-1cf2-4a11-88b7-a329f66df2ce)
## Task 4 :Generate Descriptive Statistics and Visualizations
For the "Median value of owner-occupied homes" provide a boxplot
Column MEDV --> Median value of owner-occupied homes in $1000's As it is not mentioend to make any kind of grouping, I only plotted this single value as a box plot
print (boston_df['MEDV'])

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
