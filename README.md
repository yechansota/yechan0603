# Statistics for Data Science with Python - Yechan Kim
## Load Dataset
import pandas as pd
import numpy as np
import seaborn as sns
import scipy.stats
import statsmodels.api as sm

## Task 1: Get Familiar With Data
The following describes the dataset variables:
·   CRIM - per capita crime rate by town

·ZN - proportion of residential land zoned for lots over 25,000 sq.ft.

·INDUS - proportion of non-retail business acres per town.

·CHAS - Charles River dummy variable (1 if tract bounds river; 0 otherwise)

·NOX - nitric oxides concentration (parts per 10 million)

·RM - average number of rooms per dwelling

·AGE - proportion of owner-occupied units built prior to 1940

·DIS - weighted distances to five Boston employment centres

·RAD - index of accessibility to radial highways

·TAX - full-value property-tax rate per $10,000

·PTRATIO - pupil-teacher ratio by town

·LSTAT - % lower status of the population

·MEDV - Median value of owner-occupied homes in $1000's

## Task 2: Create an IBM account
Skipped as it is optional
## Task 3: Load the Dataset in your Jupyter Notebook
boston_url = 'https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-ST0151EN-SkillsNetwork/labs/boston_housing.csv'
boston_df = pd.read_csv(boston_url)
boston_df.head()

## Task 4 - Generate Descriptive Statistics and Visualizations
### Task 4.1: For the "Median value of owner-occupied homes," provide a boxplot
= print (boston_df['MEDV'])
Name: MEDV, Length: 506, dtype: float64

sns.boxplot(x=boston_df['MEDV']).set_title("Median value of owner-occupied homes in $1000's")
plt.show()
Text(0.5, 1.0, "Median value of owner-occupied homes in $1000's")

### Task 4.2: Provide a bar plot for the Charles river variable
Column CHAS --> Charles River dummy variable (1 if tract bounds river; 0 otherwise)
print (boston_df['CHAS'].median())
print (boston_df['CHAS'].unique())

As there are two unique values (0,1) in the CHAS column, I assume to split this data and plot the orrurence of each is to be done for Task 4.2
ax = boston_df['CHAS'].value_counts().plot(kind='bar', color=['blue', 'green'])
ax.set_xlabel('CHAS')
ax.set_ylabel('Count')
ax.set_title('CHAS distribution bar plot')
plt.show()

### Task 4.3: Provide a boxplot for the MEDV variable vs the AGE variable (Discretize the age variable into three groups)
·MEDV - Median value of owner-occupied homes in $1000's --> y-Axis
·AGE - proportion of owner-occupied units built prior to 1940 --> x-Axis

### Making three groups according to the age
bins = [0, 35, 70, float('inf')]
labels = ['35 years and younger', 'between 35 and 70 years', '70 years and older']
boston_df['age_group'] = pd.cut(boston_df['AGE'], bins=bins, labels=labels)

ax = sns.boxplot(x='age_group', y='MEDV', data=boston_df)
ax.set_xlabel('Age Group')
ax.set_ylabel("Median value of owner-occupied homes in $1000's")
plt.show()
print (boston_df['age_group'])

Number | Age Range
0      | between 35 and 70 years
1      | 70 years and older
2      | between 35 and 70 years
3      | between 35 and 70 years
4      | between 35 and 70 years
...    | ...
501    | between 35 and 70 years
502    | 70 years and older
503    | 70 years and older
504    | 70 years and older
505    | 70 years and older
Name: age_group, Length: 506, dtype: object

### Task 4.4: Provide a scatter plot to show the relationship between Nitric oxide concentrations and the proportion of non-retail business acres per town
·NOX - nitric oxides concentration (parts per 10 million) --> X
·INDUS - proportion of non-retail business acres per town. --> Y
sns.scatterplot(x='NOX', y='INDUS', data=boston_df)
plt.title('Relationship between Non-Retail Business acres per Town and Nitric Oxides Concentrations')
plt.xlabel('Nitric oxides concentration (parts per 10 million)')
plt.ylabel('Proportion of non-retail business acres per town')
plt.show()

### Task 4.5: Create a histogram for the pupil to teacher ratio variable
·PTRATIO - pupil-teacher ratio by town --> this seems to be the variable looked for = "pupil to teacher ratio variable"

sns.histplot(data=boston_df, x="PTRATIO")
plt.xlabel('Pupil-teacher ratio by town')
plt.ylabel('Frequency')
plt.title('Frequency Plot of Pupil-Teacher Ratio by Town')
plt.show()
Text(0.5, 1.0, 'Frequency Plot of Pupil-Teacher Ratio by Town ')

### Task 5: Use the appropriate tests to answer the questions provided.
Be sure to:
State your hypothesis.
Use α = 0.05
Perform the test Statistics.
State the conclusion from the test.
import scipy.stats
import statsmodels.api as sm

### Task 5.1: Is there a significant difference in median value of houses bounded by the Charles river or not? (T-test for independent samples)
### State the hypothesis
### H0: µ1 = µ2 ("there is no difference in median value of houses between those bounded by the Charles river (yes and no)")
### H1: µ1 ≠ µ2 ("there is a difference in median value of houses between those bounded by the Charles river (yes and no)")
chas_0 = boston_df[boston_df['CHAS'] == 0]['MEDV']
chas_1 = boston_df[boston_df['CHAS'] == 1]['MEDV']

### Perform t-test assuming unequal variance 
### levene_test = scipy.stats.levene(chas_0, chas_1, center='mean')
### Check if p-value from Levene's test is less than 0.05 to determine the equality of variances
if levene_test.pvalue < 0.05:
    # Perform Welch's t-test if variances are unequal
    t_test = scipy.stats.ttest_ind(chas_0, chas_1, equal_var=False)
else:
    # Perform Student's t-test if variances are equal
    t_test = scipy.stats.ttest_ind(chas_0, chas_1, equal_var=True)

### Conclusion
if t_test.pvalue < 0.05:
    print("Conclusion: There is a significant difference in median value of houses bounded by the Charles river.")
else:
    print("Conclusion: There is no significant difference in median value of houses bounded by the Charles river.")

### Task 5.2: Is there a difference in Median values of houses (MEDV) for each proportion of owner occupied units built prior to 1940 (AGE)? (ANOVA)
### State the hypothesis
### H0: µ1 = µ2 = µ3 (the three population means are equal)
### H1: At least one of the means differ
age_groups = ['35 years and younger', 'between 35 and 70 years', '70 years and older']
age_group_medv = [boston_df[boston_df['age_group'] == group]['MEDV'] for group in age_groups]
### Perform Levene's test for equality of variances
levene_test = scipy.stats.levene(*age_group_medv, center='mean')
### Check if p-value from Levene's test is greater than 0.05 to determine the equality of variances
if levene_test.pvalue > 0.05:
    # Perform one-way ANOVA if variances are equal
    f_statistic, p_value = scipy.stats.f_oneway(*age_group_medv)
else:
    print("The variances are unequal, so the assumptions for ANOVA are not met.")
### Conclusion
if p_value < 0.05:
    print("Conclusion: There is a significant difference in median values of houses for each proportion of owner occupied units built prior to 1940.")
else:
    print("Conclusion: There is no significant difference in median values of houses for each proportion of owner occupied units built prior to 1940.")

### Task 5.3: Can we conclude that there is no relationship between Nitric oxide concentrations and proportion of non-retail business acres per town? (Pearson Correlation)
### State the hypothesis:
### H0: Nitric oxide concentration is not correlated with non-retail business acres per town
### H1: Nitric oxide concentration is correlated with non-retail business acres per town
import scipy.stats
import seaborn as sns
### Scatter plot of NOX vs INDUS
ax = sns.scatterplot(x="NOX", y="INDUS", data=boston_df)
### Perform Pearson correlation test
correlation, p_value = scipy.stats.pearsonr(boston_df['NOX'], boston_df['INDUS'])
### Conclusion
if p_value < 0.05:
    print("Conclusion: There is a significant relationship between Nitric oxide concentrations and proportion of non-retail business acres per town.")
else:
    print("Conclusion: There is no significant relationship between Nitric oxide concentrations and proportion of non-retail business acres per town.")
### Task 5.4: What is the impact of an additional weighted distance to the five Boston employment centres on the median value of owner occupied homes? (Regression analysis)
**H0: DIS has no effect on MEDV
H1: DIS has an effect on MEDV**
import statsmodels.api as sm
X = boston_df['DIS']
y = boston_df['MEDV']
### Add an intercept (beta_0) to our model
X = sm.add_constant(X)

model = sm.OLS(y, X).fit()
predictions = model.predict(X)

### Print out the statistics
model.summary()
DIS coeff is a positive value; statistical difference as p-value < 0.05
