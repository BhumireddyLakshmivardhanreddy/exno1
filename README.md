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

# Coding and Output
```
import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS (1).csv")
df
```
![image](https://github.com/user-attachments/assets/0dbb2377-563a-49f0-b180-0244b79557b3)
```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/dee50806-df17-4179-9261-2cad1797a722)
```
df.isnull().any()
```
![image](https://github.com/user-attachments/assets/0cf4f349-2bb2-454a-84de-581e0d04c1b5)
```
df.dropna()
```
![image](https://github.com/user-attachments/assets/d87b5fc6-3a03-49b0-a090-1f6ff0019ea6)
```
df.fillna(0)
```
![image](https://github.com/user-attachments/assets/111f809c-307c-4a38-8c5f-6995f869167c)
```
df.fillna(method="ffill")
```
![image](https://github.com/user-attachments/assets/825ba37b-56cf-4f91-8f9b-46e477507935)
```
df.fillna(method="bfill")
```
![image](https://github.com/user-attachments/assets/5f229ba9-70cc-4927-af9a-4b14821cdb76)
```
df_dropped = df.dropna()
df_dropped
```
![image](https://github.com/user-attachments/assets/d3ada1b6-7517-4f0e-b031-c592a15f6c84)
```
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![image](https://github.com/user-attachments/assets/ec87473c-db99-449f-ba36-75e6468b3c09)
```
import pandas as pd 
import seaborn as sns
import matplotlib.pyplot as plt
ir=pd.read_csv('/content/iris.csv')
ir
```
![image](https://github.com/user-attachments/assets/2cd9f539-9928-4a08-9b5a-ef37f8a3e7b1)
```
ir.describe()
```
![image](https://github.com/user-attachments/assets/1ecff25e-502a-4cd2-83af-76c56ce916c2)
```
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/42c6b150-12e5-4216-ba9c-5ba489f6a7bd)
```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/user-attachments/assets/7a42ba38-c4a1-4c57-a84d-b4dc3afd90d1)
```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![Screenshot 2024-08-17 141347](https://github.com/user-attachments/assets/0b202fce-9b64-41f5-90eb-8c3aa11e28c2)
```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/user-attachments/assets/27776ce0-4ad0-461b-b9c3-91b3353e724b)
```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/a57e1fce-b649-4f1f-a61d-c81ed16550d7)
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("/content/heights.csv")
dataset
```
![image](https://github.com/user-attachments/assets/4b81ba5d-ec2c-4c59-ad9a-a4169bd927ee)
```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
iqr = q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/84ee3f64-7051-4d46-bd91-2265c4cec1ac)
```
low = q1 - 1.5*iqr
low
```
![image](https://github.com/user-attachments/assets/87a76f79-d404-4bb5-ba6c-5d2fd215172a)

```
high = q3 + 1.5*iqr
high
```
![image](https://github.com/user-attachments/assets/09c7c729-683d-47ce-97c0-a338c91f6693)

```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/user-attachments/assets/97d652c8-ce82-44d1-b331-13e818aa7013)

```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/user-attachments/assets/83c6ffac-596a-416b-a1ff-b68a60ad3e60)
```
df1 = df[z<3]
df1
```
![image](https://github.com/user-attachments/assets/32416580-d577-4aab-aa11-43933c0c6464)

# Result
Hence the data was cleaned , outliers were detected and removed.
