## EXNO-3-DS

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set.
STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING AND OUTPUT:
       import pandas as pd
       df=pd.read_csv("C:\Users\priya\Downloads\Encoding Data.csv")
       df

[386858163-e84bed62-736a-4948-9746-a11b447b5b24](https://github.com/user-attachments/assets/b1287e89-4fde-41c5-a49c-654b51ff4db7)

from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
pm=['Hot','Warm','Cold']
e1=OrdinalEncoder(categories=[pm])
e1.fit_transform(df[["ord_2"]])

![386858347-8531eb16-4ff7-4f5e-8737-a639a7396f40](https://github.com/user-attachments/assets/13163f2e-9002-4f73-9345-48aefa2bcf22)

df['bo2']=e1.fit_transform(df[["ord_2"]])
df

![386858491-fbffce5a-76b4-4c0a-a4a1-5f27b1ba19fc](https://github.com/user-attachments/assets/b194979b-0f5f-47ce-b5f4-8c92f61d0e5e)


le=LabelEncoder()
dfc['ord_2']=le.fit_transform(dfc['ord_2'])
dfc


![386858668-85ab2c6c-a836-401b-9f11-a294445f59ae](https://github.com/user-attachments/assets/5857d6d1-c390-48f8-ae54-1225012b5d96)

from sklearn.preprocessing import OneHotEncoder
df

![386858971-0d868af7-1876-4c2f-b6fb-8881b8717113](https://github.com/user-attachments/assets/7564b64a-6063-4c63-bb67-3f112fd91569)

ohe=OneHotEncoder(sparse_output=False)
enc=pd.DataFrame(ohe.fit_transform(df[['nom_0']]))
df=pd.concat([df,enc],axis=1)
df

![386859290-33946df2-f821-4b6d-8c21-e0ca68c6e93a](https://github.com/user-attachments/assets/90709fdb-3c50-4805-9fb5-f013c84b7acb)

pd.get_dummies(df,columns=["nom_0"])

![386859351-bdc2fa38-449c-43bc-89a1-30bf5d07a3a3](https://github.com/user-attachments/assets/44bb165f-c1dd-488b-9c24-a8a420297a3a)

pip install --upgrade category_encoders

![386859665-9f6bcb63-2881-49e4-96f3-b59340664ddb](https://github.com/user-attachments/assets/8531cbc3-af9d-4f91-9f3e-cac5ad1caf48)

from category_encoders import BinaryEncoder
from category_encoders import BinaryEncoder
import pandas as pd
df=pd.read_csv("C:\Users\priya\Downloads\data.csv")

be=BinaryEncoder()
nd=be.fit_transform(df['Ord_2'])

df1=pd.concat([df,nd],axis=1)
df1=df.copy()

df1


![386860227-90dc7d32-03b0-42d4-aefe-b0420d67d39a](https://github.com/user-attachments/assets/1cc84662-9241-4d70-b768-6232c7c5a8a6)

from category_encoders import TargetEncoder
te=TargetEncoder()

cc=df.copy()
new=te.fit_transform(X=cc["City"],y=cc["Target"])

cc=pd.concat([cc,new],axis=1)
cc

![386860467-dffb9424-60f1-46e9-897a-e40e3c182823](https://github.com/user-attachments/assets/43771930-3f73-48cc-8f54-0df76d152508)

import pandas as pd
from scipy import stats
import numpy as np
df=pd.read_csv("C:\\Users\\priya\\Downloads\\Data_to_Transform.csv")
df

![386860581-6ccca6df-60cc-48ce-9a9a-1e33d27bf7ee](https://github.com/user-attachments/assets/5edf7920-9111-4d15-8d5b-df411c14b5fd)

df.skew()

![386860651-6b56ede2-c09b-4d1f-9979-4edfc2ea49b2](https://github.com/user-attachments/assets/540d9553-8585-4168-9b82-708e16b6e236)

np.log(df["Highly Positive Skew"])

![386860763-aa53ccfe-4fce-4a99-8dfb-5177b2801421](https://github.com/user-attachments/assets/fc06941d-a359-4407-bc86-abb5d2dc448b)

np.reciprocal(df["Highly Positive Skew"])


![386860809-ee086a44-5d08-4b04-8463-9fb5d5e4cce3](https://github.com/user-attachments/assets/fd9bdd58-bcf8-4bc1-ac53-1e2361ca4ebf)

np.reciprocal(df["Moderate Positive Skew"])

![386860923-520ae0d3-8a6c-4482-8702-f0433ef735ce](https://github.com/user-attachments/assets/99dfbb1b-f5d8-4c58-9d61-b8db1eadb5e8)

np.square(df["Highly Positive Skew"])

![386861096-f5bd85d9-ebfe-467e-aae0-c50402fe627d](https://github.com/user-attachments/assets/96821955-5ab2-4e77-b1df-575952aa6b81)

df["Highly Positive Skew_boxcox"],parameters=stats.boxcox(df["Highly Positive Skew"])
df

![386861176-7fb6ae6c-1d06-41a9-97e2-78081636cfb7](https://github.com/user-attachments/assets/0ff79c38-c5ed-4f20-9e7c-9e6c96a3b6b0)

df["Moderate Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df['Moderate Negative Skew'])

from sklearn.preprocessing import QuantileTransformer

qt=QuantileTransformer(output_distribution='normal')
df["Moderate Negative Skew_1"]=qt.fit_transform(df[["Moderate Negative Skew"]])
df

![386861328-99d30b9d-8883-495c-8adc-92c397db3645](https://github.com/user-attachments/assets/c96f1408-004b-4ee9-950a-46d2e0105661)

import matplotlib.pyplot as plt
import seaborn as sns
import statsmodels.api as sm
import scipy.stats as stats
sm.qqplot(df['Moderate Negative Skew'],line='45')
plt.show()

![386861535-a3677edf-eb67-43ba-b9ec-de4aae746fd7](https://github.com/user-attachments/assets/4b4ba7c6-7307-4065-bd74-784306e79bc7)

sm.qqplot(df['Moderate Negative Skew_1'],line='45')


![386861617-2e9cb7a7-b7b4-4096-b57b-fa5e37a8d51a](https://github.com/user-attachments/assets/c62dd62b-8c42-47c2-bed9-864b4fc1777c)

df["Highly Negative Skew_1"]=qt.fit_transform(df[["Highly Negative Skew"]])
sm.qqplot(df['Highly Negative Skew'],line='45')
plt.show()

![386861731-409c7073-844f-4d5b-b71d-a90b4c326ad7](https://github.com/user-attachments/assets/317764c8-0c8d-4b0d-8302-6ffcf5e05ecf)

sm.qqplot(df['Highly Negative Skew_1'],line='45')
plt.show()


![386861867-b5631112-ce82-4e62-a86a-e291d98dd07f](https://github.com/user-attachments/assets/e324af1e-46bf-40e0-abc6-7f3855faec74)

sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')


![386861966-5c954d69-55fe-40be-94ce-4715666e6f03](https://github.com/user-attachments/assets/75eabc3d-f7ca-492e-aa12-6b383c28f359)



          



# RESULT:
       Thus the given data,Feature Encoding,Transformation process and save the data to a file was performed successfully.

       














       
       
