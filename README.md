# Ex-09-Data-Visualization-

## AIM
To Perform Data Visualization on a complex dataset and save the data to a file. 

# Explanation
Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature generation and selection techniques to all the features of the data set
### STEP 4
Apply data visualization techniques to identify the patterns of the data.
# CODE
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from google.colab import files
uploaded = files.upload()
df = pd.read_csv("tips.csv")
df
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-09/assets/133684710/926707e5-0951-4fde-97ba-7cc3f2e1ec86)
```
df.isnull().sum()
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-09/assets/133684710/4a962f67-f4c9-478f-a49d-f3c9252094ee)

## FINDING OUTLIERS
```
plt.figure(figsize=(5,5))
plt.title("Data with outliers")
df.boxplot()
plt.show()
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-09/assets/133684710/4ced0ae3-ba82-475e-aa53-5adcf71913db)

## REMOVING OUTLIERS
```
plt.figure(figsize=(8,8))
cols = ['size','tip','total_bill']
Q1 = df[cols].quantile(0.25)
Q3 = df[cols].quantile(0.75)
IQR = Q3 - Q1
df = df[~((df[cols] < (Q1 - 1.5 * IQR)) |(df[cols] > (Q3 + 1.5 * IQR))).any(axis=1)]
plt.title("Dataset after removing outliers")
df.boxplot()
plt.show()
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-09/assets/133684710/ba73160b-dc7d-44b0-9cf3-b0e41cd87f9c)

## 1.Which day of the week has the highest total bill amount?
```
sns.barplot(x="day", y="total_bill", data=df)
plt.title("Total Bill Amount by Day of Week")
plt.show()
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-09/assets/133684710/e7a503da-a130-4443-8fb9-657da8b9feb2)

## 2.What is the average tip amount given by smokers and non-smokers?
```
sns.boxplot(x="smoker", y="tip", data=df)
plt.title("Tip Amount by Smoking Status")
plt.show()
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-09/assets/133684710/3be39d7f-803c-42ea-9e4d-0b7abcf5e5e7)

## 3.How does the tip percentage vary based on the size of the dining party?
```
df["tip_pct"] = df["tip"] / df["total_bill"]
sns.scatterplot(x="size", y="tip_pct", data=df)
plt.title("Tip Percentage by Dining Party Size")
plt.show()
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-09/assets/133684710/cb2b767d-ae11-41c1-ba6f-b0259142236c)

## 4.Which gender tends to leave higher tips?
```
sns.boxplot(x="sex", y="tip", data=df)
plt.title("Tip Amount by Gender")
plt.show()
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-09/assets/133684710/1a937948-caae-47c5-93a2-f59ecfd8825b)

## 5.Is there any relationship between the total bill amount and the day of the week?
```
sns.scatterplot(x="day", y="total_bill", data=df)
plt.title("Total Bill Amount by Day of Week")
plt.show()
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-09/assets/133684710/e05dd060-6889-4978-9011-2632375519c5)

## 6.How does the distribution of total bill amounts vary across different time periods (lunch vs. dinner)?
```
sns.histplot(data=df, x="total_bill", hue="time", element="step", stat="density")
plt.title("Distribution of Total Bill Amounts by Time of Day")
plt.show()
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-09/assets/133684710/6cf7c790-74de-4444-8135-05d697a97304)

## 7.Which dining party size group tends to have the highest average total bill amount?
```
sns.barplot(x="size", y="total_bill", data=df)
plt.title("Average Total Bill Amount by Dining Party Size")
plt.show()
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-09/assets/133684710/f87e9da1-5af5-4098-b732-d4cc10fec419)

## 8.What is the distribution of tip amounts for each day of the week?
```
sns.boxplot(x="day", y="tip", data=df)
plt.title("Tip Amount by Day of Week")
plt.show()
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-09/assets/133684710/62c496e0-cd3e-44db-b2c0-d26972ca3854)

## 9.How does the tip amount vary based on the type of service (lunch vs. dinner)?
```
sns.violinplot(x="time", y="tip", data=df)
plt.title("Tip Amount by Time of Day")
plt.show()
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-09/assets/133684710/22830659-cc30-4b49-a6f4-9ecc4e64b026)

## 10.Is there any correlation between the total bill amount and the tip amount?
```
sns.scatterplot(x="total_bill", y="tip", data=df)
plt.title("Correlation between Tip Amount and Total Bill Amount")
plt.show()
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-09/assets/133684710/ea74774a-fae5-4d00-897e-10bfd2e844b1)

# RESULT:
Thus, Data Visualization is performed on the given dataset and save the data to a file.
