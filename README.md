# Ex-08-Data-Visualization-
# AIM
To Perform Data Visualization on a complex dataset and save the data to a file.

# Explanation
Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

# ALGORITHM
## STEP 1
Read the given Data

## STEP 2
Clean the Data Set using Data Cleaning Process

## STEP 3
Apply Feature generation and selection techniques to all the features of the data set

## STEP 4
Apply data visualization techniques to identify the patterns of the data.

## READING THE GIVEN FILES
```python
import pandas as pd
df=pd.read_csv("/content/Superstore.csv",encoding='unicode_escape')
df.head()
```
## DATA VISUALIZATION USING SEABORN :
```python
import seaborn as sns
from matplotlib import pyplot as plt
```
LINE PLOT:
```python
plt.figure(figsize=(9,6))
sns.lineplot(x="Segment",y="Region",data=df,marker='o')
plt.xticks(rotation = 90)
sns.lineplot(x='Ship Mode',y='Category', hue ="Segment",data=df)
sns.lineplot(x="Category",y="Sales",data=df,marker='o')
```
![1](https://github.com/lokeshrahulv/ODD2023-Datascience-Ex-08/assets/118423842/3fab6268-b779-4b4f-822d-4f8121780e95)
![2](https://github.com/lokeshrahulv/ODD2023-Datascience-Ex-08/assets/118423842/71e9215d-618f-4739-8409-779d88cadbc9)
![3](https://github.com/lokeshrahulv/ODD2023-Datascience-Ex-08/assets/118423842/0951396b-ed7f-4667-9e0a-345c84ee6266)

SCATTERPLOT:
```python
sns.scatterplot(x='Category',y='Sub-Category',data=df)
sns.scatterplot(x='Category', y='Sub-Category', hue ="Segment",data=df)
plt.figure(figsize=(10,7))
sns.scatterplot(x="Region",y="Sales",data=df)
plt.xticks(rotation = 90)
```
![4](https://github.com/lokeshrahulv/ODD2023-Datascience-Ex-08/assets/118423842/9f10d405-7133-4d81-a30c-524d3eba4079)
![5](https://github.com/lokeshrahulv/ODD2023-Datascience-Ex-08/assets/118423842/d5650aab-40f5-45c7-8602-efdb3411dff3)
![6](https://github.com/lokeshrahulv/ODD2023-Datascience-Ex-08/assets/118423842/58c02a19-deee-4f8c-9b1f-afc6e72bd978)

BOXPLOT:
```python
sns.boxplot(x="Sub-Category",y="Discount",data=df)
sns.boxplot( x="Profit", y="Category",data=df)
```
![8](https://github.com/lokeshrahulv/ODD2023-Datascience-Ex-08/assets/118423842/8dab21f4-d548-4918-98b8-1ade343e1325)
![7](https://github.com/lokeshrahulv/ODD2023-Datascience-Ex-08/assets/118423842/1770b683-d1ca-4269-b729-afd19d23ee97)

VIOLIN PLOT:
```python
sns.violinplot(x="Profit",data=df)
```
![9](https://github.com/lokeshrahulv/ODD2023-Datascience-Ex-08/assets/118423842/d7a79301-e451-44ce-b5df-9a68590a61cc)

BARPLOT
```python
sns.barplot(x="Sub-Category",y="Sales",data=df)
plt.xticks(rotation = 90)
sns.barplot(x="Category",y="Sales",data=df)
plt.xticks(rotation = 90)
```
![11](https://github.com/lokeshrahulv/ODD2023-Datascience-Ex-08/assets/118423842/fd67a3fe-7b5a-4ff8-b91f-12e2822cd4c4)
![10](https://github.com/lokeshrahulv/ODD2023-Datascience-Ex-08/assets/118423842/11663f40-9b64-4eef-ad41-7ff2be81b7ad)

POINTPLOT
```python
sns.pointplot(x=df["Quantity"],y=df["Discount"])
```
![12](https://github.com/lokeshrahulv/ODD2023-Datascience-Ex-08/assets/118423842/cf0525b5-b5c0-4383-9547-cb58ab152d9c)

COUNT PLOT
```python
sns.countplot(x="Category",data=df)
sns.countplot(x="Sub-Category",data=df)
```
![14](https://github.com/lokeshrahulv/ODD2023-Datascience-Ex-08/assets/118423842/810906a4-509e-46da-b5ea-37f264982755)
![13](https://github.com/lokeshrahulv/ODD2023-Datascience-Ex-08/assets/118423842/c0444589-325d-4b04-a065-fc2eaa084063)

HISTOGRAM
```python
sns.histplot(data=df,x ='Ship Mode',hue='Sub-Category')
```
![15](https://github.com/lokeshrahulv/ODD2023-Datascience-Ex-08/assets/118423842/04153e27-4b83-4c8d-a4fb-d0d3cc44c69e)

KDE PLOT
```python
sns.kdeplot(x="Profit", data = df,hue='Category')
```
![16](https://github.com/lokeshrahulv/ODD2023-Datascience-Ex-08/assets/118423842/adf8f7d0-3792-47d3-9ff5-e480bb5c9cf3)

## DATA VISUALIZATION USING MATPLOTLIB :

PLOT
```python
plt.plot(df['Category'], df['Sales'])
plt.show()
```
![17](https://github.com/lokeshrahulv/ODD2023-Datascience-Ex-08/assets/118423842/9c63a96f-6f63-4fcc-90b2-61ab3e56d197)

    HEATMAP:

df.corr()
plt.subplots(figsize=(12,7))
sns.heatmap(df.corr(),annot=True)

![18](https://github.com/lokeshrahulv/ODD2023-Datascience-Ex-08/assets/118423842/19424aaf-e14f-4b45-89cf-4991b738147a)

    PIECHART:

df1=df.groupby(by=["Ship Mode"]).sum()
labels=[]
for i in df1.index:
    labels.append(i)
colors=sns.color_palette("bright")
plt.pie(df1["Sales"],labels=labels,autopct="%0.0f%%")
plt.show()

df3=df.groupby(by=["Category"]).sum()
labels=[]
for i in df3.index:
    labels.append(i) 
plt.figure(figsize=(8,8))
colors = sns.color_palette('pastel')
plt.pie(df3["Profit"],colors = colors,labels=labels, autopct = '%0.0f%%')
plt.show()

![21](https://github.com/lokeshrahulv/ODD2023-Datascience-Ex-08/assets/118423842/7ccc113f-82b6-46b0-84ac-934f74d9fb99)
![20](https://github.com/lokeshrahulv/ODD2023-Datascience-Ex-08/assets/118423842/b906cbe7-9eda-472d-a5be-34782202cb83)

    HISTOGRAM:

plt.hist(df["Sub-Category"],facecolor="peru",edgecolor="blue",bins=10)
plt.show()

![22](https://github.com/lokeshrahulv/ODD2023-Datascience-Ex-08/assets/118423842/fcc2959c-0bb1-4767-a48f-61a0264915d4)

    BARGRAPH:

plt.bar(df.index,df['Category'])
plt.show()

![23](https://github.com/lokeshrahulv/ODD2023-Datascience-Ex-08/assets/118423842/b6ffe0b0-85ce-4a28-9bf2-9d2f122cfd24)

    SCATTERPLOT:

plt.scatter(df["Region"],df["Profit"], c ="blue")
plt.show() 

![24](https://github.com/lokeshrahulv/ODD2023-Datascience-Ex-08/assets/118423842/5853588a-ad9e-459c-a60d-2575f525caca)
## RESULT:
Hence, Data Visualization is applied on the complex dataset using libraries like Seaborn and Matplotlib successfully and the data is saved to file.
