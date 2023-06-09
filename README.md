# Ex02-Outlier
# AIM
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,
# ALGORITHM

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them

# CODE

DATA

import numpy as np

import pandas as pd

from scipy import stats

import seaborn as sns

df = pd.read_csv("bhp.csv")

print(df)


1.Remove outliers using IQR


median = df['price_per_sqft'].quantile(0.5)

Q1 = df['price_per_sqft'].quantile(0.25)

Q3 = df['price_per_sqft'].quantile(0.75)

IQR = Q3-Q1

df1=df[((df['price_per_sqft']>=Q1-1.5*IQR)&(df['price_per_sqft']<=Q3+1.5*IQR))]

print(df1)


3.Use zscore of 3 to remove outliers. This is quite similar to IQR and you will get
exact same result


from scipy import stats

z=np.abs(stats.zscore(df1['price_per_sqft']))

df1=df1[(z<3)]

print(df1)


(4) for the data set height_weight.csv


DATA


import numpy as np

import pandas as pd

from scipy import stats

import seaborn as sns

df = pd.read_csv("height_weight.csv")

print(df)


(i) Using IQR detect weight outliers and print them


median=df['weight'].quantile(0.5)

Q1 = df['weight'].quantile(0.25)

Q3 = df['weight'].quantile(0.75)

IQR = Q3-Q1

df1=df[((df['weight']>=Q1-1.5*IQR)&(df['weight']<=Q3+1.5*IQR))]

print(df1)


(ii) Using IQR, detect height outliers and print them
median=df['height'].quantile(0.5)


Q1 = df['height'].quantile(0.25)

Q3 = df['height'].quantile(0.75)

IQR = Q3-Q1

low=Q1-1.5*IQR

high=Q3+1.5*IQR

df1=df[((df['height']>=low)&(df['height']<=high))]

print(df1)

# OUTPUT

![image](https://user-images.githubusercontent.com/95520655/226828186-0b2ad8a7-a444-46c1-8020-5ed47bf1095c.png)
![image](https://user-images.githubusercontent.com/95520655/226828246-d48b8832-07d8-44aa-a878-80db0bad7e0b.png)
![image](https://user-images.githubusercontent.com/95520655/226828292-ecb9ed41-2723-407e-bb54-08072116cb1e.png)
![image](https://user-images.githubusercontent.com/95520655/226828342-66413c92-554e-41e4-b46c-b729d70992d7.png)
![image](https://user-images.githubusercontent.com/95520655/226828387-7db7306f-7fcd-42b3-8ee6-bd8d0a268d90.png)
![image](https://user-images.githubusercontent.com/95520655/226828423-026c9ee8-7e14-416f-8c8d-910fa792842a.png)

# RESULT

Thus the required output is displayed
