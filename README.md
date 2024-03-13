# EXNO2DS
# AIM:
To perform Exploratory Data Analysis on the given data set.
      
# EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODING AND OUTPUT
#### EXPLORATORY DATA ANALYSIS
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
dt=pd.read_csv("/content/titanic_dataset.csv")
dt
```
![2-1](https://github.com/Divya110205/EXNO2DS/assets/119404855/8e8b0dbb-c93f-46e5-aa11-d16ba5c0fe76)

```
dt.info()
```
![2-2](https://github.com/Divya110205/EXNO2DS/assets/119404855/3d775523-53ab-46f8-a3d6-3f994bed9405)

```
dt.shape
```
![2-3](https://github.com/Divya110205/EXNO2DS/assets/119404855/a0e9a787-5423-4e8e-9cc5-ecf821d45f12)

```
dt.set_index("PassengerId",inplace=True)
dt.describe()
```
![2-4](https://github.com/Divya110205/EXNO2DS/assets/119404855/911f7e2b-c34e-460f-837b-2da5a5ba3278)

```
dt.rename(columns = {'Sex':'Gender'},inplace=True)
dt
```
![2-5](https://github.com/Divya110205/EXNO2DS/assets/119404855/3467b274-bf02-43a6-a098-916b09ddd2c0)

#### CATEGORICAL DATA ANALYSIS
```
dt.nunique()
```
![2-6](https://github.com/Divya110205/EXNO2DS/assets/119404855/4d341f16-03b4-4f27-a207-b066e921245b)

```
dt["Pclass"].value_counts()
```
![2-7](https://github.com/Divya110205/EXNO2DS/assets/119404855/67f260b1-0dc7-4d86-996c-c82b460f429f)

```
per=(dt["Pclass"].value_counts()/dt.shape[0]*100).round(2)
per
```
![2-8](https://github.com/Divya110205/EXNO2DS/assets/119404855/81258368-33d2-48af-98d7-ac11e6686126)

#### UNIVARIATE ANALYSIS
```
sns.countplot(data=dt,x="Pclass")
```
![2-9](https://github.com/Divya110205/EXNO2DS/assets/119404855/ec9feda4-b9df-440f-b1c7-a14049098b57)

```
sns.countplot(data=dt,x="Gender")
```
![2-10](https://github.com/Divya110205/EXNO2DS/assets/119404855/a2ec38ab-2d82-433e-a49d-4cb2c99e178e)

```
sns.countplot(data=dt,x="Age")
```
![2-11](https://github.com/Divya110205/EXNO2DS/assets/119404855/fb4088e2-a9fc-4e02-814d-02b2a5835a6e)

```
sns.countplot(data=dt,x="SibSp")
```
![2-12](https://github.com/Divya110205/EXNO2DS/assets/119404855/1e0243fd-597d-4c45-a05a-c0d8aa1502cd)

```
sns.countplot(data=dt,x="Parch")
```
![2-13](https://github.com/Divya110205/EXNO2DS/assets/119404855/d3b47e89-bb3e-491e-b0d8-ae00b0979451)

#### HISTOGRAM
```
plt.hist(dt['Age'], bins=20, color='green', edgecolor='black')
plt.title('Distribution of Passenger Ages')
plt.xlabel('Age')
plt.ylabel('Frequency')
plt.grid(True)
plt.show()
```
![2-14](https://github.com/Divya110205/EXNO2DS/assets/119404855/ba246585-a720-4fab-873b-73567ea5ef7c)

```
plt.hist(dt['Fare'], bins=20, color='red', edgecolor='black')
plt.title('Distribution of Passenger Fares')
plt.xlabel('Fare')
plt.ylabel('Frequency')
plt.grid(True)
plt.show()
```
![2-15](https://github.com/Divya110205/EXNO2DS/assets/119404855/6130d22a-2b46-4af1-8883-cd342951060f)

```
dt.Survived.unique()
```
![2-16](https://github.com/Divya110205/EXNO2DS/assets/119404855/6d933d12-e631-4212-9bdc-a83a8eb3f5a5)

#### BIVARIATE ANALYSIS
```
sns.catplot(x="Pclass",col="Embarked",kind="count",data=dt,height=5,aspect=.7)
```
![2-17](https://github.com/Divya110205/EXNO2DS/assets/119404855/e73face2-2542-47f3-afa8-fab3daf9e5ea)

```
sns.catplot(x='Pclass',hue="SibSp",data=dt,kind="count")
```
![2-18](https://github.com/Divya110205/EXNO2DS/assets/119404855/7f0364f3-15df-4af8-b011-744fa43f2e2e)

```
dt.boxplot(column="Fare",by="Pclass")
```
![2-19](https://github.com/Divya110205/EXNO2DS/assets/119404855/e5a06acd-2cdd-45df-b0d9-b428f7f97062)

```
dt.boxplot(column="Fare",by="Embarked")
```
![2-20](https://github.com/Divya110205/EXNO2DS/assets/119404855/7de02ea4-e263-4b52-b8cd-ba3e55e0a872)

```
sns.scatterplot(x=dt["SibSp"],y=dt["Parch"])
```
![2-21](https://github.com/Divya110205/EXNO2DS/assets/119404855/6b1a2a14-1239-480a-a125-f10225126718)

```
sns.scatterplot(x=dt["SibSp"],y=dt["Survived"])
```
![2-22](https://github.com/Divya110205/EXNO2DS/assets/119404855/d5a33481-773d-4c45-bfd0-072b608d5447)

```
sns.jointplot(x="Pclass",y="SibSp",data=dt)
```
![2-23](https://github.com/Divya110205/EXNO2DS/assets/119404855/ad905dcd-7dff-4012-9e9e-82dcda91476e)

```
sns.jointplot(x="Pclass",y="Parch",data=dt)
```
![2-24](https://github.com/Divya110205/EXNO2DS/assets/119404855/d7317586-48a1-42fe-8a76-6d77d408b099)

#### MULTIVARIATE ANALYSIS
```
fig,ax1=plt.subplots(figsize=(8,5))
pt=sns.boxplot(ax=ax1,x='Age',y='Gender',hue='Survived',data=dt)
```
![2-25](https://github.com/Divya110205/EXNO2DS/assets/119404855/48cbfb0e-ef2d-4b9d-941b-16a427b15f06)

```
sns.catplot(data=dt,col="Survived",x="Gender",hue="Pclass",kind="count")
```
![2-26](https://github.com/Divya110205/EXNO2DS/assets/119404855/90f8a6ea-0c82-4e31-a55b-4029d819f3f5)

#### CO-RELATION
```
corr = dt.corr()
sns.heatmap(corr,annot=True)
```
![2-28](https://github.com/Divya110205/EXNO2DS/assets/119404855/753556ae-60ef-447c-a059-d4afd4a8b67e)

```
sns.pairplot(dt)
```
# RESULT
Thus the Exploratory Data Analysis process is performed successfully on the given data using python code.
