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
![2-1](https://github.com/Divya110205/EXNO2DS/assets/119404855/d12e34b6-a208-46d2-9e02-2860002e8089)

```
dt.info()
```
![2-2](https://github.com/Divya110205/EXNO2DS/assets/119404855/729875bb-e3fc-4c91-89da-883bc2400d29)

```
dt.shape
```
![2-3](https://github.com/Divya110205/EXNO2DS/assets/119404855/a0eef082-ae2d-4d5c-ad46-419a4daf7e98)

```
dt.set_index("PassengerId",inplace=True)
dt.describe()
```
![2-4](https://github.com/Divya110205/EXNO2DS/assets/119404855/c8b82f77-4b64-41f4-b8c6-6da80df4791b)

#### CATEGORICAL DATA ANALYSIS
```
dt.nunique()
```
![2-5](https://github.com/Divya110205/EXNO2DS/assets/119404855/24404bf7-7cbe-4dfe-934e-4df366660737)

```
dt["Survived"].value_counts()
```
![2-6](https://github.com/Divya110205/EXNO2DS/assets/119404855/018abaad-a788-4cf6-b2ae-a2ab28772793)

```
per=(dt["Survived"].value_counts()/dt.shape[0]*100).round(2)
per
```
![2-7](https://github.com/Divya110205/EXNO2DS/assets/119404855/44a97d7b-081e-470b-b88a-130d20867e4d)

#### UNIVARIATE ANALYSIS
```
sns.countplot(data=dt,x="Survived")
```
![2-8](https://github.com/Divya110205/EXNO2DS/assets/119404855/6923fca1-1bb8-426b-8913-bf5efc5f8870)

```
dt.Pclass.unique()
```
![2-9](https://github.com/Divya110205/EXNO2DS/assets/119404855/d506691d-69cd-4ec5-be17-d1e34caa37cc)


```
dt.rename(columns = {'Sex':'Gender'},inplace=True)
dt
```
![2-10](https://github.com/Divya110205/EXNO2DS/assets/119404855/af221019-adaa-4f5f-85a6-3f4b13d0cb33)


```
sns.catplot(x="Gender",col="Survived",kind="count",data=dt,height=5,aspect=.7)
```
![2-11](https://github.com/Divya110205/EXNO2DS/assets/119404855/59a84a4b-8b93-4896-9a7d-0b5046695f72)


```
sns.catplot(x='Survived',hue="Gender",data=dt,kind="count")
```
![2-12](https://github.com/Divya110205/EXNO2DS/assets/119404855/cac9226f-2cb4-4693-99ab-aa262cd28e3a)


```
dt.boxplot(column="Age",by="Survived")
```
![2-13](https://github.com/Divya110205/EXNO2DS/assets/119404855/17ab0861-c128-47e7-a313-116bedd8e100)


```
sns.scatterplot(x=dt["Age"],y=dt["Fare"])
```
![2-14](https://github.com/Divya110205/EXNO2DS/assets/119404855/359b469f-9633-44f0-aa1b-d7474f573f2a)


```
sns.jointplot(x="Age",y="Fare",data=dt)
```
![2-15](https://github.com/Divya110205/EXNO2DS/assets/119404855/290d6166-e4f3-471b-8582-72600004084f)


#### MULTIVARIATE ANALYSIS
```
fig,ax1=plt.subplots(figsize=(8,5))
pt=sns.boxplot(ax=ax1,x='Pclass',y='Age',hue='Gender',data=dt)
```
![2-16](https://github.com/Divya110205/EXNO2DS/assets/119404855/cfad821e-1d27-4c6d-96da-a43c261076c6)


```
sns.catplot(data=dt,col="Survived",x="Gender",hue="Pclass",kind="count")
```
![2-17](https://github.com/Divya110205/EXNO2DS/assets/119404855/633922ee-abf2-400f-bd54-1e6d0533467e)


#### CO-RELATION
```
corr = dt.corr()
sns.heatmap(corr,annot=True)
```
![2-18](https://github.com/Divya110205/EXNO2DS/assets/119404855/b567f5df-36f7-4dd0-9948-248e116c1514)

```
sns.pairplot(dt)
```
![2-19](https://github.com/Divya110205/EXNO2DS/assets/119404855/fff650c4-8ab7-4bbd-b4d9-043659f1a7fe)



# RESULT
        <<INCLUDE YOUR RESULT HERE>>
