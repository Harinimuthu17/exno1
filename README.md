# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output-
```
Name: M.Harini
Register Number: 212222240035
```
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
data = pd.read_csv("/content/SAMPLEIDS.csv")
data.head()
```
![image](https://github.com/Harinimuthu17/exno1/assets/130278614/66304815-82bb-4828-8227-7b63b1be9666)

```
data = pd.get_dummies(data)
data.isnull().sum()
```
![image](https://github.com/Harinimuthu17/exno1/assets/130278614/fb48a003-c9a5-495a-ab96-16bd21102a4b)

```
columns_with_null = data.columns[data.isnull().any()]
import seaborn as sns
plt.figure(figsize=(10,10))
sns.barplot(columns_with_null)
plt.title("NULL VALUES")
plt.show()
```
![image](https://github.com/Harinimuthu17/exno1/assets/130278614/2e3f7639-f6f6-4e10-92ea-decc2ed1ecd5)

```
for column in columns_with_null:
    median = data[column].median()  
    data[column].fillna(median, inplace=True)
data.isnull().sum().sum()
```
![image](https://github.com/Harinimuthu17/exno1/assets/130278614/e82fcf34-3008-4e32-b8bc-df068c852645)

# IQR 
```
import pandas as pd
import seaborn as sns
ir = pd.read_csv("/content/iris (1).csv")
ir.head()
```
![image](https://github.com/Harinimuthu17/exno1/assets/130278614/d82c37b5-6137-41cb-8d67-fc52c5c056ff)

```
ir.describe()
```
![image](https://github.com/Harinimuthu17/exno1/assets/130278614/ee691782-28a6-49ce-a594-1d086de3ec0d)

```
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/Harinimuthu17/exno1/assets/130278614/31291486-2ee0-4425-b445-d22d69cf83cf)

```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/Harinimuthu17/exno1/assets/130278614/a00b9b93-e074-4277-8ebe-26a29d2568a6)


```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/Harinimuthu17/exno1/assets/130278614/da19fa68-4495-40f8-8643-013b25ced769)

```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/Harinimuthu17/exno1/assets/130278614/c7e7261a-71ef-4a5c-ae26-eb157683693a)

```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/Harinimuthu17/exno1/assets/130278614/26fd3ca9-680d-4cdd-b488-5c2eecf0ebfe)
```
# Z Score

```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("/content/heights.csv")
dataset
```
![image](https://github.com/Vanitha-SM/exno1-datascience/assets/119557985/f01f125b-7c8e-4fba-9a31-6c09ef3b6974)
```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)

```

```
iqr = q3-q1
iqr
```
![image](https://github.com/Vanitha-SM/exno1-datascience/assets/119557985/8a9a9dfd-0738-499d-95be-7a258f56424b)

```
low = q1 - 1.5*iqr
low
```
![image](https://github.com/Vanitha-SM/exno1-datascience/assets/119557985/6d918b46-664f-4910-9574-33fc03f6a372)
```
high = q3 + 1.5*iqr
high
```
![image](https://github.com/Vanitha-SM/exno1-datascience/assets/119557985/d3f8ec32-b8ac-436a-a851-9060cdadc505)
```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/Vanitha-SM/exno1-datascience/assets/119557985/16fa8456-0ad8-4e94-9a83-87fdfc6b5e80)
```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/Vanitha-SM/exno1-datascience/assets/119557985/5e6c94d4-04a9-46c6-bc4e-9c6912f96544)

# Result
Thus the given data is read,cleansed and the cleaned data is saved into the file.

