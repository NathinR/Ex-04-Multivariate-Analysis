# Ex-04-Multivariate-Analysis
# AIM
To perform Multivariate EDA on the given data set.

# Explanation:
Exploratory data analysis is used to understand the messages within a dataset. This technique involves many iterative processes to ensure that the cleaned data is further sorted to better understand the useful meaning.The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.

# ALGORITHM:
### STEP 1
Import the built libraries required to perform EDA and outlier removal.

### STEP 2
Read the given csv file

### STEP 3
Convert the file into a dataframe and get information of the data.

### STEP 4
Return the objects containing counts of unique values using (value_counts()).

### STEP 5
Plot the counts in the form of Histogram or Bar Graph.

### STEP 6
Use seaborn the bar graph comparison of data can be viewed.

### STEP 7
Find the pairwise correlation of all columns in the dataframe.corr()

### STEP 8
Save the final data set into the file

# Program:
```
Name : R.NATHIN
Register Number : 212222230090
```
```
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
df = pd.read_csv("/content/SuperStore.csv")
df.head()
df.describe()
df.isnull().sum()
df['Postal Code'] = df["Postal Code"].fillna(df['Postal Code'].mode()[0])
df.isnull().sum()
df.dtypes
sns.scatterplot(x=df['Row ID'],y=df['Postal Code'])
states=df.loc[:,["State","Sales"]]
states=states.groupby(by=["State"]).sum().sort_values(by="Sales")
plt.figure(figsize=(17,7))
sns.barplot(x=states.index,y="Sales",data=states)
plt.xticks(rotation = 90)
plt.xlabel=("STATES")
plt.ylabel=("SALES")
plt.show()
states=df.loc[:,["State","Row ID"]]
states=states.groupby(by=["State"]).sum().sort_values(by="Row ID")
sns.barplot(x=states.index,y="Row ID",data=states)
plt.xticks(rotation = 90)
plt.xlabel=("State")
plt.ylabel=("ROW ID")
plt.show()
states=df.loc[:,["Segment","Row ID"]]
states=states.groupby(by=["Segment"]).sum().sort_values(by="Row ID")
sns.barplot(x=states.index,y="Row ID",data=states)
plt.xticks(rotation = 90)
plt.xlabel=("SEGMENT")
plt.ylabel=("ROW ID")
plt.show()
sns.barplot(x=df['Sales'],y=df['Ship Mode'],hue=df['Category'])
df.corr()
sns.heatmap(df.corr(),annot=True)
```

# OUTPUT:
![image](https://user-images.githubusercontent.com/118679646/230832751-6d749ca7-5337-4bdc-8797-007bcc103a34.png)
![image](https://user-images.githubusercontent.com/118679646/230832834-e4dc3254-dba3-48a4-acd2-8fe9d49376bf.png)
![image](https://user-images.githubusercontent.com/118679646/230832930-a24f3e72-6932-476f-b94b-829044fe6e74.png)
![image](https://user-images.githubusercontent.com/118679646/230832993-3982b445-2e14-40a3-9595-538bac1e3c2e.png)
![image](https://user-images.githubusercontent.com/118679646/230833064-85f73ac2-dd4a-4848-b20b-1673b81ef6ce.png)
