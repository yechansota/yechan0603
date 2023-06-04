# Statistics for Data Science with Python - Yechan Kim
## Load Dataset
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

# Task 3: Load the Dataset in your Jupyter Notebook
boston_url = 'https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-ST0151EN-SkillsNetwork/labs/boston_housing.csv'
boston_df = pd.read_csv(boston_url)
boston_df.head()

# Task 4 - Generate Descriptive Statistics and Visualizations

# Task 4.1: For the "Median value of owner-occupied homes," provide a boxplot
sns.boxplot(x=boston_df['MEDV']).set_title("Median value of owner-occupied homes in $1000's")
plt.show()

# Task 4.2: Provide a bar plot for the Charles river variable
ax = boston_df['CHAS'].value_counts().plot(kind='bar', color=['blue', 'green'])
ax.set_xlabel('CHAS')
ax.set_ylabel('Count')
ax.set_title('CHAS distribution bar plot')
plt.show()

# Task 4.3: Provide a boxplot for the MEDV variable vs the AGE variable (Discretize the age variable into three groups)
bins = [0, 35, 70, float('inf')]
labels = ['35 years and younger', 'between 35 and 70 years', '70 years and older']
boston_df['age_group'] = pd.cut(boston_df['AGE'], bins=bins, labels=labels)
ax = sns.boxplot(x='age_group', y='MEDV', data=boston_df)
ax.set_xlabel('Age Group')
ax.set_ylabel("Median value of owner-occupied homes in $1000's")
plt.show()

# Task 4.4: Provide a scatter plot to show the relationship between Nitric oxide concentrations and the proportion of non-retail business acres per town
sns.scatterplot(x='NOX', y='INDUS', data=boston_df)
plt.title('Relationship between Non-Retail Business acres per Town and Nitric Oxides Concentrations')
plt.xlabel('Nitric oxides concentration (parts per 10 million)')
plt.ylabel('Proportion of non-retail business acres per town')
plt.show()

# Task 4.5: Create a histogram for the pupil to teacher ratio variable
sns.histplot(data=boston_df, x="PTRATIO")
plt.xlabel('Pupil-teacher ratio by town')
plt.ylabel('Frequency')
plt.title('Frequency Plot of Pupil-Teacher Ratio by Town')
plt.show()

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
