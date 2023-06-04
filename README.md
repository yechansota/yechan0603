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
= print (boston_df['MEDV'])



# Statistics for DS with Python
import pandas as pd
import plotly.express as px
import seaborn as sns
import matplotlib.pyplot as pyplot
import matplotlib.ticker as ticker
import scipy.stats

## Task 1 - Get Familiar with the Data
The following describes the dataset variables:


·      CRIM - per capita crime rate by town
·      ZN - proportion of residential land zoned for lots over 25,000 sq.ft.
·      INDUS - proportion of non-retail business acres per town.
·      CHAS - Charles River dummy variable (1 if tract bounds river; 0 otherwise)
·      NOX - nitric oxides concentration (parts per 10 million)
·      RM - average number of rooms per dwelling
·      AGE - proportion of owner-occupied units built prior to 1940
·      DIS - weighted distances to five Boston employment centres
·      RAD - index of accessibility to radial highways
·      TAX - full-value property-tax rate per $10,000
·      PTRATIO - pupil-teacher ratio by town
·      LSTAT - % lower status of the population
·      MEDV - Median value of owner-occupied homes in $1000's
## Task 2 - Create an IBM account
As this was an optional step, I skipped this one as I had created such an account previously. 
Also, I will use my Github account for uploading this file.

## Task 3 - Load in the Dataset in your Jupyter Notebook
boston_url = 'https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-ST0151EN-SkillsNetwork/labs/boston_housing.csv'
boston_df=pd.read_csv(boston_url)
boston_df.head()
## Task 4 - Generate Descriptive Statistics and Visualizations
### Task 4.1 For the "Median value of owner-occupied homes" provide a boxplot
Column MEDV --> Median value of owner-occupied homes in $1000's
As it is not mentioend to make any kind of grouping, I only plotted this single value as a box plot
print (boston_df['MEDV'])
sns.boxplot(x=boston_df['MEDV']).set_title("Median value of owner-occupied homes in $1000's")
### Task 4.2 Provide a bar plot for the Charles river variable
Column CHAS --> Charles River dummy variable (1 if tract bounds river; 0 otherwise)
print (boston_df['CHAS'].median())
print (boston_df['CHAS'].unique())
As there are two unique values (0,1) in the CHAS column, I assume to split this data and plot the orrurence of each is to be done for Task 4.2
ax = pyplot.bar(boston_df.CHAS.unique(),boston_df.CHAS.value_counts(),color=['blue','green'])
pyplot.xlabel('CHAS')
pyplot.ylabel('Count')
pyplot.title('CHAS distribution bar plot')
pyplot.xlabel('Charles River dummy variable (1 if tract bounds river; 0 otherwise)')

### Task 4.3 Provide a boxplot for the MEDV variable vs the AGE variable. (Discretize the age variable into three groups of 35 years and younger, between 35 and 70 years and 70 years and older)
·      MEDV - Median value of owner-occupied homes in $1000's --> y-Axis
·      AGE - proportion of owner-occupied units built prior to 1940 --> x-Axis
# Making three groups according to the age
boston_df.loc[(boston_df['AGE'] <= 35), 'age_group'] = '35 years and younger'
boston_df.loc[(boston_df['AGE'] > 35)&(boston_df['AGE'] < 70), 'age_group'] = 'between 35 and 70 years'
boston_df.loc[(boston_df['AGE'] >= 70), 'age_group'] = '70 years and older'
print (boston_df['age_group'])
ax = sns.boxplot(x='age_group', y='MEDV', data=boston_df)
pyplot.xlabel("proportion of owner-occupied units built prior to 1940")
pyplot.ylabel("Median value of owner-occupied homes in $1000's")
### Task 4.4 Provide a scatter plot to show the relationship between Nitric oxide concentrations and the proportion of non-retail business acres per town. What can you say about the relationship?
·      NOX - nitric oxides concentration (parts per 10 million) --> X
·      INDUS - proportion of non-retail business acres per town. --> Y
sns.scatterplot(x='NOX', y='INDUS', data=boston_df).set(title='Relationship between Non-Retail Business acres per Town and Nitric Oxides Concentrations')
pyplot.xlabel("nitric oxides concentration (parts per 10 million)")
pyplot.ylabel("proportion of non-retail business acres per town")

What can you say about the relationship?

There seems to be a (positive) correlation between Nictirc oxides concentration and the proportion of non-terail business acress. 
### Task 4.5 Create a histogram for the pupil to teacher ratio variable
·      PTRATIO - pupil-teacher ratio by town --> this seems to be the variable looked for = "pupil to teacher ratio variable"
sns.histplot(data=boston_df, x="PTRATIO")
pyplot.xlabel('pupil-teacher ratio by town')
pyplot.title("Frequency Plot of Pupil-Teacher Ratio by Town ")
## Task 5: Use the appropriate tests to answer the questions provided.
Be sure to:

State your hypothesis.

Use α = 0.05

Perform the test Statistics.

State the conclusion from the test.
### Task 5.1: Is there a significant difference in median value of houses bounded by the Charles river or not? (T-test for independent samples)
Assuming the question is to use the MEDV values and the CHAS values. This is not really clear to me as non native english speaker
State the hypothesis
* $H_0: µ_1 = µ_2$ ("there is no difference in median value of houses between bounded by the Charles river (yes and no)")
* $H_1: µ_1 ≠ µ_2$ ("there is a difference in median value of houses between bounded by the Charles river (yes and no)")
print (boston_df['CHAS'].unique())
scipy.stats.levene(boston_df[boston_df['CHAS'] == 0]['MEDV'],
                   boston_df[boston_df['CHAS'] == 1]['MEDV'], center='mean')

# since the p-value is less than 0.05 we can assume un-equality of variance

scipy.stats.ttest_ind(boston_df[boston_df['CHAS'] == 0]['MEDV'],
                   boston_df[boston_df['CHAS'] == 1]['MEDV'], equal_var = False)
**Conclusion:** Since the p-value is less than alpha value 0.05, we reject the null hypothesis as there is enough proof that there is a statistical difference in MEDV (price) based on CHAS (bound to river)
### Task 5.2: Is there a difference in Median values of houses (MEDV) for each proportion of owner occupied units built prior to 1940 (AGE)? (ANOVA)
State the hypothesis
* $H_0: µ_1 = µ_2 = µ_3$ (the three population means are equal)
* $H_1:$ At least one of the means differ
scipy.stats.levene(boston_df[boston_df['age_group'] == '35 years and younger']['MEDV'],
                   boston_df[boston_df['age_group'] == 'between 35 and 70 years']['MEDV'], 
                   boston_df[boston_df['age_group'] == '70 years and older']['MEDV'], 
                   center='mean')
# since the p-value is greater than 0.05, the variance are  equal.
low = boston_df[boston_df['age_group'] == '35 years and younger']['MEDV']
med = boston_df[boston_df['age_group'] == 'between 35 and 70 years']['MEDV']
high = boston_df[boston_df['age_group'] == '70 years and older']['MEDV']
f_statistic, p_value = scipy.stats.f_oneway(low, med, high)
print("F_Statistic: {0}, P-Value: {1}".format(f_statistic,p_value))
**Conclusion:** Since the p-value is smaller than 0.05, we will reject the null hypothesis as there is a significant evidence that at least one of the means differ.

### Task 5.3: Can we conclude that there is no relationship between Nitric oxide concentrations and proportion of non-retail business acres per town? (Pearson Correlation)

State the hypothesis:
* $H_0:$ Nitric oxide concentration is not correlated with non-retail business acres per town
* $H_1:$ Nitric oxide concentration is correlated with non-retail business acres per town
Since they are both continuous variables we can use a pearson correlation test and draw a scatter plot
NOX - nitric oxides concentration (parts per 10 million)
INDUS - proportion of non-retail business acres per town.
ax = sns.scatterplot(x="NOX", y="INDUS", data=boston_df)
# as done before
scipy.stats.pearsonr(boston_df['NOX'], boston_df['INDUS'])
**Conclusion:** Since the p-value is below 0.05, we reject the Null hypothesis and conclude that there exists a relationship between  Nitric oxide concentration and non-retail business acres per town.

### Task 5.4: What is the impact of an additional weighted distance  to the five Boston employment centres on the median value of owner occupied homes? (Regression analysis)
·      DIS - weighted distances to five Boston employment centres --> X
·      MEDV - Median value of owner-occupied homes in $1000's --> Y 

* $H_0: DIS has no effect on MEDV
* $H_1: DIS has an effect on MEDV
import statsmodels.api as sm

X = boston_df['DIS']
y = boston_df['MEDV']

## add an intercept (beta_0) to our model
X = sm.add_constant(X) 

model = sm.OLS(y, X).fit()
predictions = model.predict(X)

# Print out the statistics
model.summary()



DIS coeff is a positive value; statistical difference as p-value < 0.05
