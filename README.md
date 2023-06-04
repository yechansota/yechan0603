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

boston_df.describe()
INDUS	CHAS	NOX	RM	AGE	DIS	RAD	TAX	PTRATIO	LSTAT	MEDV
count	506.000000	506.000000	506.000000	506.000000	506.000000	506.000000	506.000000	506.000000	506.000000	506.000000	506.000000	506.000000	506.000000	506.000000
mean	252.500000	3.613524	11.363636	11.136779	0.069170	0.554695	6.284634	68.574901	3.795043	9.549407	408.237154	18.455534	12.653063	22.532806
std	146.213884	8.601545	23.322453	6.860353	0.253994	0.115878	0.702617	28.148861	2.105710	8.707259	168.537116	2.164946	7.141062	9.197104
min	0.000000	0.006320	0.000000	0.460000	0.000000	0.385000	3.561000	2.900000	1.129600	1.000000	187.000000	12.600000	1.730000	5.000000
25%	126.250000	0.082045	0.000000	5.190000	0.000000	0.449000	5.885500	45.025000	2.100175	4.000000	279.000000	17.400000	6.950000	17.025000
50%	252.500000	0.256510	0.000000	9.690000	0.000000	0.538000	6.208500	77.500000	3.207450	5.000000	330.000000	19.050000	11.360000	21.200000
75%	378.750000	3.677082	12.500000	18.100000	0.000000	0.624000	6.623500	94.075000	5.188425	24.000000	666.000000	20.200000	16.955000	25.000000
max	505.000000	88.976200	100.000000	27.740000	1.000000	0.871000	8.780000	100.000000	12.126500	24.000000	711.000000	22.000000	37.970000	50.000000

## Task 2: Create an IBM account
Skipped as it is optional

## Task 3: Load the Dataset in your Jupyter Notebook
boston_url = 'https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-ST0151EN-SkillsNetwork/labs/boston_housing.csv'
boston_df = pd.read_csv(boston_url)


boston_df.head(5)
![image](https://github.com/yechansota/yechan0603/assets/134902281/36c150ef-b140-4bf0-b793-e99df6ff3993)

## Task 4 - Generate Descriptive Statistics and Visualizations
### Task 4.1: For the "Median value of owner-occupied homes," provide a boxplot
= print (boston_df['MEDV'])
![image](https://github.com/yechansota/yechan0603/assets/134902281/9442b569-1472-4f55-a0ea-3dda5f4bff0d)
sns.boxplot(x=boston_df['MEDV']).set_title("Median value of owner-occupied homes in $1000's")
plt.show()
Text(0.5, 1.0, "Median value of owner-occupied homes in $1000's")

### Task 4.2: Provide a bar plot for the Charles river variable
Column CHAS --> Charles River dummy variable (1 if tract bounds river; 0 otherwise)
print (boston_df['CHAS'].median())
print (boston_df['CHAS'].unique())

![image](https://github.com/yechansota/yechan0603/assets/134902281/748ecf24-2710-4010-a9af-3b777f207fac)

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
![image](https://github.com/yechansota/yechan0603/assets/134902281/c43f3c96-43aa-4fad-8ac7-816956c5ae84)

### Task 4.4: Provide a scatter plot to show the relationship between Nitric oxide concentrations and the proportion of non-retail business acres per town
·NOX - nitric oxides concentration (parts per 10 million) --> X
·INDUS - proportion of non-retail business acres per town. --> Y
sns.scatterplot(x='NOX', y='INDUS', data=boston_df)
plt.title('Relationship between Non-Retail Business acres per Town and Nitric Oxides Concentrations')
plt.xlabel('Nitric oxides concentration (parts per 10 million)')
plt.ylabel('Proportion of non-retail business acres per town')
plt.show()
![image](https://github.com/yechansota/yechan0603/assets/134902281/39502d03-96b4-4dee-95dc-cb29d729b3c1)

### Task 4.5: Create a histogram for the pupil to teacher ratio variable
·PTRATIO - pupil-teacher ratio by town --> this seems to be the variable looked for = "pupil to teacher ratio variable"

sns.histplot(data=boston_df, x="PTRATIO")
plt.xlabel('Pupil-teacher ratio by town')
plt.ylabel('Frequency')
plt.title('Frequency Plot of Pupil-Teacher Ratio by Town')
plt.show()
Text(0.5, 1.0, 'Frequency Plot of Pupil-Teacher Ratio by Town ')
![image](https://github.com/yechansota/yechan0603/assets/134902281/3e7bc34d-4d63-4a45-97b2-4e11a25a9f2b)

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

	Unnamed: 0	CRIM	ZN	INDUS	CHAS	NOX	RM	AGE	DIS	RAD	TAX	PTRATIO	LSTAT	MEDV	Age_Group	CHAS_T
0	0	0.00632	18.0	2.31	0.0	0.538	6.575	65.2	4.0900	1.0	296.0	15.3	4.98	24.0	between 35 and 70 years	FAR
1	1	0.02731	0.0	7.07	0.0	0.469	6.421	78.9	4.9671	2.0	242.0	17.8	9.14	21.6	70 years and older	FAR
2	2	0.02729	0.0	7.07	0.0	0.469	7.185	61.1	4.9671	2.0	242.0	17.8	4.03	34.7	between 35 and 70 years	FAR
3	3	0.03237	0.0	2.18	0.0	0.458	6.998	45.8	6.0622	3.0	222.0	18.7	2.94	33.4	between 35 and 70 years	FAR
4	4	0.06905	0.0	2.18	0.0	0.458	7.147	54.2	6.0622	3.0	222.0	18.7	5.33	36.2	between 35 and 70 years	FAR

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
![image](https://github.com/yechansota/yechan0603/assets/134902281/1739a067-f8e3-4d56-afcf-f26b24442d59)

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
**OLS Regression Results**
Dep. Variable:	MEDV	R-squared:	0.062
Model:	OLS	Adj. R-squared:	0.061
Method:	Least Squares	F-statistic:	33.58
Date:	Sun, 04 Jun 2023	Prob (F-statistic):	1.21e-08
Time:	15:23:26	Log-Likelihood:	-1823.9
No. Observations:	506	AIC:	3652.
Df Residuals:	504	BIC:	3660.
Df Model:	1		
Covariance Type:	nonrobust		
coef	std err	t	P>|t|	[0.025	0.975]
const	18.3901	0.817	22.499	0.000	16.784	19.996
DIS	1.0916	0.188	5.795	0.000	0.722	1.462
Omnibus:	139.779	Durbin-Watson:	0.570
Prob(Omnibus):	0.000	Jarque-Bera (JB):	305.104
Skew:	1.466	Prob(JB):	5.59e-67
Kurtosis:	5.424	Cond. No.	9.32

model.summary()
DIS coeff is a positive value; statistical difference as p-value < 0.05
